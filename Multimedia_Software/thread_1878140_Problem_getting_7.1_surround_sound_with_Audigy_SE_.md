---
title: "Problem getting 7.1 surround sound with Audigy SE 7.1 PCI sound card"
date: 2011-11-09
forum: Multimedia Software
---

### Post by Origanic on 2011-11-09
Hello,
 I'm very new with Ubuntu and I got Ubuntu 11.10 dual installation with Window 7. I tried many times to get my sound card to output 7.1 surround sound but failed every time. Ubuntu recognizes the sound card and its options, but when I tested the sound, only L & R speakers worked. 

I tried the sound in Window 7 with its driver and it works. So, it has to be the driver issue in Ubuntu.

Can anyone help me setting up the Audigy SE 7.1 driver in Ubuntu 11.10?
Much appreciated!

---

### Post by MoreOrLess on 2011-11-09
```
gksu gedit /etc/pulse/daemon.conf
```
You'll see a part like this:
```
# Default
default-sample-channels=2
# For 5.1
# default-sample-channels=6
# For 7.1
# default-sample-channels=8
```
Uncomment the =8 line and comment the =2 line (by putting a '#' in front). Save the file and quit. Log out and back in.

---

### Post by Origanic on 2011-11-09
Hi MoreOrLess,
 I tried your method but the surround sound did not work properly. Here was the portion of code that I changed:


; default-sample-format = s16le
; default-sample-rate = 44100
#; default-sample-channels = 2 (Original set for stereo)
# this is for 7.1 channels output
; default-sample-channels = 8
#; default-channel-map = front-left,front-right (original set for stereo)
; default-channel-map = front-left,front-right,front-center,side-left,side-right,rear-left,rear-right,subwoofer

I added the comment about the 7.1, added the sample channel, and also tried to edit the channel-map (I added the other 6 speakers hoping this will work!) by adding the line above. I don't know if this make an impact or not, but it did not work properly.  

I tested the speakers by opening the SOUND program in SETTING and used the TEST SPEAKERS option. Only the L & R speaker work. The rest of the speakers had no sound.

Then I tried to open a movie to test out. All speakers worked for some reason, but the sound in the movie skips randomly such as 1 way conversation. You can hear the background sound, sometime the main character talk, but not the other character in a conversation. It's quite frustrating. 

Thanks again for your helps

---

### Post by MoreOrLess on 2011-11-09
Oh, well I guess Ubuntu uses ';' instead of '#' in the pulse configuration files (I just copied/pasted from archwiki)...

So, given that, TRY AGAIN.

---

### Post by Origanic on 2011-11-11
Thanks for your inputs.
 I uncommented out the "sample-channel" and "channel-map" and the sound still did not worked properly. Reboot and play test movie and same affect observed. 
 I also tried the "TEST SPEAKERS" option and they still only work with L & R speakers.
 Thank you for your inputs!

---

### Post by Origanic on 2011-11-15
Can someone help me with this problem? I'm still searching for a solution to play the surround sound with Audigy SE 7.1 card. 

Thanks!

---

