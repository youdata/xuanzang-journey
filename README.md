# 玄奘西行 · 西行求法舆图

贞观三年至十九年（629–645），玄奘自长安西行求法、经中亚入天竺、携经东归的路线，画在一张可缩放的地形图上。

A zoomable map of Xuanzang's journey to India and back (629–645), in Chinese: the route over the relief of Asia,
41 stations from 长安 to 那烂陀 and home again, each with a card — when he was there, what happened, and a line from
《大唐西域记》 or 《慈恩传》 — and a tour of 16 stops in the order of the journey.

Live: https://youdata.github.io/xuanzang-journey/

- **地图即全图**：东经 54°–120°、南纬 4°至北纬 50°，地形为 ETOPO 2022，越放大山川越清楚（凌山、铁门、瓦罕走廊）。
- **路线与站点**：放大缩小都保持同样粗细；两站之间按两书所记的山口、河渡取道，路线为示意。
- **站名与卡片**：站名随缩放逐级出现；点站点或搜索古名、今名（高昌、吐鲁番）即见卡片：站次、时间、阶段、今地、记事与原文。
  41 站另加 6 处山川（莫贺延碛、玉门关、大清池、大雪山、葱岭、信度河），原文 47 条均与维基文库本逐字核对。
- **题签**：标题与数字、年表与十七年、657 部与 1,335 卷、沿途高程，置于海上与高原的空白处。
- **导览**：▶ Play 依行程顺序看 16 处，再看四块题签。

The relief is read from [world-tiles-earth](https://github.com/youdata/world-tiles-earth) (`../world-tiles-earth/world-relief/`),
so this repository holds only the page (`index.html`, the reader and its plugins inside it). The lettering in the two brush
faces is drawn as glyph outlines (`outline_fonts.mjs`, run by `build_map.py`), so no font files are shipped.

## How it is made

From `infographic-examples/xuanzang-journey/` (`build_map.py`, `station_notes.json`, `tour.json`, `texts/`), with rx (`~/rx-cli`):

```sh
python3 build_map.py && python3 check_notes.py        # → xuanzang-map.json (brush faces as outlines); every quote checked against texts/
rx export xuanzang-map.json --out site --app /rx-graphic-editor/web/index.html --canvas --lock-layers \
  --tiles dir --tile-base world-relief=../world-tiles-earth/
rx publish site --to github:youdata/xuanzang-journey --yes
```

Sources: 《大慈恩寺三藏法师传》《大唐西域记》（维基文库）；今地从季羡林等《大唐西域记校注》；地形 ETOPO 2022（NOAA）；
海岸湖泊 Natural Earth；沿途高程 AWS Terrain Tiles. Licence: [LICENSE.md](LICENSE.md).
