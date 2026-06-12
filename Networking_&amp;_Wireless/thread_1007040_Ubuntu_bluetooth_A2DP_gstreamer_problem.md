---
title: "Ubuntu bluetooth A2DP gstreamer problem"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by skdeka on 2008-12-10
Hi All,
  I installed BlueZ-4.x on my Ubuntu Hardy(8.04) and I can pair with A2DP headsets. I have ~/.asoundrc file as follows

pcm.bluetooth {
        type bluetooth
        device 00:07:A4:B7:0D:16
}

Also route the sound to bluetooth using:
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth"

I tried to play music with Banshee-1.4.1 and got the following gstreamer error--->
-------------------------------------------
   at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 

(Banshee:14847): GStreamer-CRITICAL **: 
Trying to dispose element fakesink, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

[Error 11:44:56.092] GStreamer resource error: OpenWrite

-------------------------------------------
rhythmbox log
-------------------
administrator@BANUNXPAC03:~$ rhythmbox

(rhythmbox:14899): Rhythmbox-WARNING **: Could not open device /dev/radio0

(rhythmbox:14899): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed

(rhythmbox:14899): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed
-------------------------------

Can any one help me in solving the problem.

Thanks in advance.

---

### Post by skdeka on 2008-12-12
Finally BlueZ-4.x working on Ubuntu Hardy

---

### Post by kraymore on 2009-02-11
i am getting this error in banshee:

[Error 11:43:01.206] GStreamer resource error: OpenWrite

i don't know what could be wrong, or how to solve it.  

i have a bluetooth adaptor but no bluetooth headphones.  this has never happened before.  i also get a orange icon that happens to have a small in it next to any song i try to play.  

your or anyone have any ideas ?

---

