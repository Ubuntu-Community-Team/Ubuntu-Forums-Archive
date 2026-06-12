---
title: "MythTV - no sound on watching TV"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by halitech on 2008-02-13
Hi all

I recently got my TV Tuner card working and I'm trying to setup MythTV. I have installed TVtime and sound and video work perfect there but when I go into MythTV, I get the video but no audio. I have also installed the DVD option and I have sound there. I have an Asus My Cinema card (seen as an saa7134 card) and I do have the cable hooked up from the audio out jack to my sound card. The radio portion also works fine so this leads me to believe I'm just screwing something up from within MythTV. 

I have tried muting/unmuting line in (as suggested in other threads to no avail. I'm using Ubuntu 7.04 on a P4 1.8, kernel 2.6.20-16. 

Any other info needed to help me out just let me know and I'll post it.

Thanks

---

### Post by halitech on 2008-02-13
no one has any ideas or has the right person just not seen this thread yet?

---

### Post by halitech on 2008-02-14
ok, think I'm a little farther ahead. I did some playing in VLC tonight and I can open the tv stream using /dev/video1 (which I'm guessing is fine anyway since I have video) and /dev/dsp1 for audio. It was a little scratchy but it did work. Now I just need to figure out what settings to use in myth

---

### Post by x-dragon on 2008-02-14
You can adjust the sound settings of Mythtv in the front-end, when clicking configuration => general ; there are your settings you need to change.

---

### Post by halitech on 2008-02-14
I've been playing with the settings in there, so far to no avail. I'm upgrading to Gutsy to see if that will make any difference.

---

### Post by halitech on 2008-02-14
ok, so I've upgraded to Gutsy, removed all myth tv stuff and installed Mythbuntu with the control center and I'm still in the same boat, I have sound in TvTime, sound in Myth using DVDs but no sound when I'm watching tv. Am I just not meant to be able to record from the tv or my vcr without going back to windows?

---

### Post by halitech on 2008-02-14
ok, I tried loading the TV in vlc and had sound then I loaded Myth and suddenly had sound. Not sure what I did but it's working so not going to look a gift horse in the mouth :D

---

