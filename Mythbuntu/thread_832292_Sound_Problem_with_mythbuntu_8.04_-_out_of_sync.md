---
title: "Sound Problem with mythbuntu 8.04 - out of sync"
date: 2008-06-17
forum: Mythbuntu
---

### Post by mr. 100prozent on 2008-06-17
Hello there, i am relatively new at mythtv and mythbuntu. I have a question concerning sound output of mythtv. Now i route a cable from my TV-Card (a BT878 analog only) to the mainboards line-in. Now i have sound but it is not in sync with video, there is at least two seconds delay. Also my recordings dont have sound (i checked the .nuv files with mplayer). How can i access the sound from mythtv or how are the settings for mythtv to catch the sound from the PCI bus. I had a Hauppauge HVR-1300 with which i had no luck (same problems) i used the hack with sox player ("sox -c2 -t alsa hw:2,0 -t alse default") and with arecord ... | aplay but the problem was always the same, i got the sound directly from the card but it was out of sync.
My Kernel is 2.6.24-19-generic
Outputs from lspci and /proc/asound/cards look fine. I can post them if they would be helpful.
Thank you.
Rob

---

### Post by klc5555 on 2008-06-18
You can't use an audio pass-through cable. The cable is dumping the sound directly into your motherboard/soundcard in real time, but mythtv is buffering the video signal for a few seconds on the hard-disk and recording it. You never actually watch Live TV, you only watch Very Recently Recorded TV. Mythtv and your hard disk never see the passed-through audio, so neither "Live TV" nor recordings work.

The audio from the capture card needs to run through the PCI bus. I'm not sure if this describes precisely the driver setup you need to do this with your specific card, but the bttv driver discussion for the Hauppauge WinTV-Go found at  

[http://mythtv.org/wiki/index.php/Hauppauge_WinTV-Go](http://mythtv.org/wiki/index.php/Hauppauge_WinTV-Go)

certainly seems to address the problem of getting a bttv card to work sans passthrough cable with the various bt audio driver options.

Cheers! :)

---

### Post by mr. 100prozent on 2008-06-18
Thanks for the tip. I plugged the today received Hauppauge PVR-150 in and it worked nearly out of the box. I messed around for four full days with a HVR-1300 and with an analog Win-TV without any luck. Now tv works fine (for now) and i start to add some other features. I just can give everybody a good tip - dont try the HVR-1300 go for the PVR-150 it will work out of the box whereas the HVR wont work at all.
Anyway, thanks for help.

---

