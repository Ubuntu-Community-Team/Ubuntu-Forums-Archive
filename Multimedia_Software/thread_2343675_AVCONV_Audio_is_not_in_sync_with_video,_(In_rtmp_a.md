---
title: "AVCONV: Audio is not in sync with video, (In: rtmp audio + rtmp video, Out: rtmp mix)"
date: 2016-11-18
forum: Multimedia Software
---

### Post by alessandro.marin on 2016-11-18
[COLOR=#333333][FONT=Arial]Strange behaviour while muxing two live rtmp strem audo/video using the following command: [/FONT][/COLOR]

```

[COLOR=#333333][FONT=Arial]avconv -thread_queue_size 512 -rtmp_live live -i "[/FONT][/COLOR][rtmp://streaming.com/live/]("rtmp://streaming-media-1.choruscall.com/live/777")in0[COLOR=#333333][FONT=Arial]" -thread_queue_size 512 -rtmp_live live -i "[/FONT][/COLOR][rtmp://streaming.com/live/]("rtmp://streaming-media-1.choruscall.com/live/U58442443")in1[COLOR=#333333][FONT=Arial]" -c:v copy -c:a copy -map 0:v -map 1:a -flags +global_header -async -1 -rtmp_live live -f flv "[/FONT][/COLOR][rtmp://streaming.com/live/output]("rtmp://streaming-media-1.choruscall.com/live/output")[COLOR=#333333][FONT=Arial]"
 [/FONT][/COLOR]
```

[COLOR=#333333][FONT=Arial]it produces a stream where the VIDEO is late about 5 sec.(audio comes before video in correct time) in this situation the audio and video are not sync. [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Without -async -1 the audio is mixed in the correct way while the video is stretched respect to its source, only with -async -1 parameter I can have a correct behavior of the video but it is late respect to audio. [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Also, I've tried with -vsync option (0,1,2,drop,-1) but they didn't have any effect. [/FONT][/COLOR]

---

