---
title: "No DTS or Dolby Digital via spdif from TV recordings - just Dolby Prologic"
date: 2012-11-11
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-11-11
Even though I have checked the boxes, in general settings audio page, for digital in mythtv's audio setup, my receiver only indicates it is getting a prologic signal via the spdif cable. If I set mythtv to also upconvert stereo to 5.1, then my receiver indicates Dolby Digital for everything I play, so I know it can work.

I have mythtv's audio device set,  in general settings audio page, to my nvidia motherboard's spdif output, and in the advanced section, it is set to default. I read a suggestion to turn off mixing (on the next config page) but that didn't help. I have left it off for now.

---

### Post by nickrout on 2012-11-11
> **ubnewbie2 said:**
> Even though I have checked the boxes, in general settings audio page, for digital in mythtv's audio setup, my receiver only indicates it is getting a prologic signal via the spdif cable. If I set mythtv to also upconvert stereo to 5.1, then my receiver indicates Dolby Digital for everything I play, so I know it can work.

I have mythtv's audio device set,  in general settings audio page, to my nvidia motherboard's spdif output, and in the advanced section, it is set to default. I read a suggestion to turn off mixing (on the next config page) but that didn't help. I have left it off for now.If you are not upconverting then you will get what is in the TV stream delivered by your broadcaster.

---

### Post by ubnewbie2 on 2012-11-11
> **nickrout said:**
> If you are not upconverting then you will get what is in the TV stream delivered by your broadcaster.

Well, I believe that the local digital broadcasts contain digital surround sound.  I need to check a recording file to be sure. Is there an easy command/program to see if digital info is in the video file? 

Does upconverting turn prologic into discrete channels, or is it just an completely artificial surround effect.

---

### Post by nickrout on 2012-11-11
mediainfo filename.mpg will give you the information. The file name of a recording can be figured out - it is in the format channelid_yyyymmddhhmm00.mpg, eg 2010_20120815223000.mpg for a programme that started recording at 10.30 pm on 15 August 2012 on channel 2010.

Some broadcasters put two audio streams, a 5.1 ac3 stream and a stereo aac or mp2 stream. To switch streams while watching use the menu (m) button and follow your nose.

I don't know how the upmixing is done. I think, but don't know that it is:

left --> left rear
right --> right rear
left+right --> centre
left+right filtered to low freq --> LFE.

---

### Post by ubnewbie2 on 2012-11-12
Thanks for that.  

Using mediainfo I found which channels are transmitting AC3 and, using them to test, have been able to configure it to work properly.  My receiver now indicates digital surround for these channels when playing my recordings.

---

### Post by nickrout on 2012-11-12
Pleased i could help.

---

