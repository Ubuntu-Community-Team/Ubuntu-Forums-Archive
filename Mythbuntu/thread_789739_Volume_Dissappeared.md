---
title: "Volume Dissappeared"
date: 2008-05-10
forum: Mythbuntu
---

### Post by sirganya on 2008-05-10
I'm having a strange problem. I did a clean install of 8.04 which has been problematic to say the least. 7.10 was very stable. But I'm stuck on this particular issue, the volume control doesn't work. irw verifies that lirc is picking up the signal but it does nothing. Play pause and all the other commands work but when I change the volume nothing happens, no OSD appears, even when I use the keyboard. I can see all the other OSD elements, position, channel details etc but the volumes gone.. what could be going on? I'm stumped and hoping no to have to do another install.. any ideas?

---

### Post by nasha on 2008-05-11
Check your lircd.conf and lircrc are correct for your remote

---

### Post by ctucker10 on 2008-05-11
> **sirganya said:**
> I'm having a strange problem. I did a clean install of 8.04 which has been problematic to say the least. 7.10 was very stable. But I'm stuck on this particular issue, the volume control doesn't work. irw verifies that lirc is picking up the signal but it does nothing. Play pause and all the other commands work but when I change the volume nothing happens, no OSD appears, even when I use the keyboard. I can see all the other OSD elements, position, channel details etc but the volumes gone.. what could be going on? I'm stumped and hoping no to have to do another install.. any ideas?

My problem was similar to yours except that the OSD displayed the volume indicator bar. While it indicated that the volume was changing, it did not. 

To fix the problem I went to the audio settings page at Utilitiies/Setup => Setup => General and changed the audio output device to /dev/dsp. After that I logged out and back in again.

Hope this helps.

---

