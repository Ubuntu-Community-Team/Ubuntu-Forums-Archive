---
title: "[HOWTO] SPDIF Sound for Boxee under Mythbuntu"
date: 2011-07-21
forum: Mythbuntu
---

### Post by beartard on 2011-07-21
I have an NVidia card with HDMI output.  It's connected to the SPDIF header on my motherboard to send digital audio over HDMI.  This works find for MythTV (and hulu desktop), but didn't work for Boxee.

I searched all over the net in MythTV, Boxee, and Mythbuntu related places and couldn't find a solution.  What I needed was actually in the XBMC wiki.  I'm posting it here in case anyone has a similar problem getting audio working for Boxee from within Mythbuntu.

Original link is [http://wiki.xbmc.org/index.php?title=XBMC_for_Linux_specific_FAQ](http://wiki.xbmc.org/index.php?title=XBMC_for_Linux_specific_FAQ)

1. Create an asound.conf file in /etc (or .asoundrc in your user's home directory) containing the following:
```
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,1"
        period_time 0
        period_size 1024
        buffer_size 8192
        #periods 128
        #rate 44100
        rate 48000
     }
     bindings {
        0 0
        1 1
     }
}
```
Be sure to replace the **pcm "hw:0,1"** line with your own hardware (found by typing **aplay -l**).  Save the file and reload ALSA (**sudo alsa reload**).

2. In Boxee's settings for audio hardware, use "custom" for both output and passthrough device.  Fill in the blanks with **plug:dmixer** and **iec958**, respectively.

Everything should work great at this point!

---

