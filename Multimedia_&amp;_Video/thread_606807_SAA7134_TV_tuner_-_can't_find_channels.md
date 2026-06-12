---
title: "SAA7134 TV tuner - can't find channels"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Rzadzins on 2007-11-08
Hello, 

I can't find any channels :( Here's what i did.

I've got a:

05:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

From dmesg i've learned the card numer is 77 and the tuner number is 61, so i've set those in /etc/modprobe.d/saa7134:
options saa7134 card=77 tuner=61

I've loaded ivtv and i2c-dev drivers with modprobe (no parameters here)

I can see the drivers loaded properly, because /dev/video0 has been created.

Now, when i run mplayer-rc2 tv:// i get a black screen. I tried cycling thru all the channels. I also tried the -tvscan autostart option to find any channels for me in europe-east and europe-west (Poland cable tv). In both cases i got "0 found".

In dmesg, when changing channels i get the following error:
[ 1834.227301] tuner 0-004b: i2c i/o error: rc == -5 (should be 4)

This line is repeated each time i change the channel.

What can i do to get tv image or rather, to find any channels? I'm running a fresh install of ubuntu gutsy. Thanks for your help in advance!

---

