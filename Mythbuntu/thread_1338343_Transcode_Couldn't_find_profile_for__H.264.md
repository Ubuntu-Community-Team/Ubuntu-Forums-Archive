---
title: "Transcode: Couldn't find profile for : H.264"
date: 2009-11-26
forum: Mythbuntu
---

### Post by mars76 on 2009-11-26
Hi All,

  I am unable to transcode the recordings which i have recorded using HD-PVR.

  I am getting the following Error:
  
```

AFD: Opened codec 0x91a6f90, id(H264) type(Video)
2009-11-26 10:14:35.568 AFD: codec AAC has 2 channels
2009-11-26 10:14:35.610 AFD: Opened codec 0x91a7700, id(AAC) type(Audio)
2009-11-26 10:14:35.666 Found video height of 1088.  This is unusual and more than likely the video is actually 1080 so mythtranscode will treat it as such.
2009-11-26 10:14:35.695 Transcode: Looking for autodetect profile: Autodetect from 1080i
2009-11-26 10:14:35.738 Transcode: Couldn't find profile for : H.264
2009-11-26 10:14:35.779 Transcoding aborted, no profile found.
2009-11-26 10:14:35.824 Transcoding /recordings/mythtv/recordings/3622_20091126050000.mpg failed

```DO i need to change my STB settings to output in 720P ??

In my Recording Profiles i have changed the Codec to MPEG-4 for all these options

Autodetect from RTJpeg/MPEG4
Autodetect from MPEG-2
High Quality
Medium Quality
Low Quality

Still no luck..

thanks
mars.

---

### Post by mars76 on 2009-11-26
Nevermind, i am able to resolve it..

Created a new Transcoder profile "Autodetect from 1080i" and set the Codec to MPEG-4 and it is working fine..

> **mars76 said:**
> Hi All,

  I am unable to transcode the recordings which i have recorded using HD-PVR.

  I am getting the following Error:
  
```

AFD: Opened codec 0x91a6f90, id(H264) type(Video)
2009-11-26 10:14:35.568 AFD: codec AAC has 2 channels
2009-11-26 10:14:35.610 AFD: Opened codec 0x91a7700, id(AAC) type(Audio)
2009-11-26 10:14:35.666 Found video height of 1088.  This is unusual and more than likely the video is actually 1080 so mythtranscode will treat it as such.
2009-11-26 10:14:35.695 Transcode: Looking for autodetect profile: Autodetect from 1080i
2009-11-26 10:14:35.738 Transcode: Couldn't find profile for : H.264
2009-11-26 10:14:35.779 Transcoding aborted, no profile found.
2009-11-26 10:14:35.824 Transcoding /recordings/mythtv/recordings/3622_20091126050000.mpg failed

```DO i need to change my STB settings to output in 720P ??

In my Recording Profiles i have changed the Codec to MPEG-4 for all these options

Autodetect from RTJpeg/MPEG4
Autodetect from MPEG-2
High Quality
Medium Quality
Low Quality

Still no luck..

thanks
mars.

---

### Post by stratoscape on 2011-02-21
> Nevermind, i am able to resolve it..

Created a new Transcoder profile "Autodetect from 1080i" and set the Codec to MPEG-4 and it is working fine..


Thanks for updating this! This worked for me as well.

Strato

---

