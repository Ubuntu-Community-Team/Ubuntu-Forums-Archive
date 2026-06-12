---
title: "No sound in flash with Google Chrome and 10.04"
date: 2010-07-04
forum: Multimedia Software
---

### Post by Kapli on 2010-07-04
Hi,
I just did a fresh install of Ubuntu 10.04 and right after installing all the updates and stuff like that I installed Google Chrome from the official Google website and I started it up and went to youtube.com and everything worked fine. Then I started installing other normal programs like Wine and SMPlayer and stuff, not that much really.. the only other addon I remember installing for Chrome was Java that I installed with 
sudo apt-get install sun-java6-jre sun-java6-plugin
And I probably rebooted the computer a few times too and now I have no sound in flash anymore, video works fine. 
Any suggestions to what could be the problem? I have googled a lot for a solution and I have installed the padevchooser or something to check if all the volumes are up, they are, there are also no duplicates of the libflashplayer.so.

Owh, and I might add that I have no sound in the new IM program Empathy, not sure why... I have sound in everything else though, like at startup and in every media player and stuff like that :S

Thanks in advance,
Kapli

---

### Post by Kapli on 2010-07-05
Ok so I have noticed something.
I am running Spotify via Wine and if I reboot my computer and just start Chrome and then go to youtube I do get sound in flash. However I do not get sound in spotify if I start it after I hear sound in flash, it then says there's a problem with my soundcard. Now if I reboot my computer again and start spotify first, and then Chrome afterwards I get sound in spotify but then there's no sound in flash... So obviously there's a problem there, anyone know what might cause it?

Edit: Ok so I googled some more and found the solution, just change the sound settings in winecfg to use ALSA not OSS like the spotify website says to do and now I get sound from everything. It seems that spotify muted all other sound, but now it works perfectly :D

---

