---
title: "Interlace output or deinterlace output"
date: 2015-06-10
forum: Mythbuntu
---

### Post by ceesquared on 2015-06-10
Mythbuntu 14.04, DVB card TV display. When watching live TV, video leads audio by a small amount when watching SD Tv (720i) but not when watching HD TV (1080i). This applies to both live and recordings ( I know that both are basically the same). The TV will accept 720i/1080i or 720p/1080p. As the inputs are interlaced(freesat DVB) why convert to deinterlaced(p) before sending to the TV? Is there any advantage in setting output to 1080i and let the TV do the work of deinterlacing, which it is designed to do. I do not use any non-interlaced material.

---

### Post by blm-ubunet on 2015-06-10
The audio delay difference could be caused by the different amount of post processing the TV has to do with 720i vs 1080i ( & 720p vs 1080p).
The TV has to decode de-interlace & scale 576i/720i to its native output 1080p.
The TV does not have to scale 1080i/p.

The mpegts streams contain accurate timing information to allow AV sync. So problem should not occur unless source material is in error.

The latest TVs de-interlacing could be a match for the older video cards that don't have good vector adaptive de-interlacing.
A lot of TVs can not de-interlace the full screen of motion; they spec the number lines of resolution for motion tracing.

Some excellent test signals avail here:
[http://www.avsforum.com/forum/26-home-theater-computers/1157287-hd-1080i-test-pattern-determine-vector-adaptive-deinterlacing-others-icl-ticker.html](http://www.avsforum.com/forum/26-home-theater-computers/1157287-hd-1080i-test-pattern-determine-vector-adaptive-deinterlacing-others-icl-ticker.html)

I think it is better to do all processing in PCs GPU & only output native resolution (progressive) & change refresh rates to match source material.
If you are driving an old VGA CRT with no video engine then interlaced output is fine.

IMO If you have GT240 or GPU with better actual shader performance, the GPU has excess shader processing power to de-interlace/scale/sharpen/denoise etc

---

