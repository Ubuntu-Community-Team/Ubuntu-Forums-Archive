---
title: "Dell Inspiron E1705 SubWoofer Not Working"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by rhopkins on 2006-12-01
I am currently using Ubuntu Edgy on a Dell Inspiron E1705. I have managed to get everyone working perfectly including wireless and video with beryl. The only thing I can't get working is the subwoofer on the bottom of the computer. Has anyone else had this issue and if so, how is it fixed? Any ideas or how-to are welcome. Thanks in advance.

Rick

---

### Post by SnowPunk98 on 2007-02-12
Also have the same problem with the bottom speaker not working, is ALSA something that I need or how do we get this working?

---

### Post by fmaste on 2007-02-20
Edit the file /etc/modprobe.d/alsa-base

    sudo nano /etc/modprobe.d/alsa-base

Add the line

    options snd-hda-intel model=ref

Now reboot your computer
Open the volume control that is next to the clock (If it is nos there add it with right click and Add to panel)
Go to File -> Change device and select HDA Intel (Alsa mixer)
then go to Edit -> Preferences and check the one that is LFE, is the subwoofer
unmute it and start playing your favorite music
If LFE is not there (Like it happened to me) follow this HOWTO and install the newest version of Alsa: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and when says "Manually tell the driver which flavor you are using" change 3stack with ref

For more info or to change the way your volume buttons behave go here [http://ubuntuforums.org/showthread.php?t=335285]("http://ubuntuforums.org/showthread.php?t=335285")

---

### Post by freehunt on 2007-05-09
Wow, that was a big difference. I just enabled it on my laptop, and... wow. Thank you very much. I just have once concern. When I use the volume buttons on the front of my laptop, how do I make it adjust the PCM volume, rather than master? When it turns down the master volume, the sub is still playing at full volume, and defeats the purpose. The PCM volume seems to turn them both down at the same rate. Thanks.

---

### Post by DDLxMaN on 2007-05-14
> **freehunt said:**
> Wow, that was a big difference. I just enabled it on my laptop, and... wow. Thank you very much. I just have once concern. When I use the volume buttons on the front of my laptop, how do I make it adjust the PCM volume, rather than master? When it turns down the master volume, the sub is still playing at full volume, and defeats the purpose. The PCM volume seems to turn them both down at the same rate. Thanks.

I have addressed this problem one time befor but here is it again!

First goto System>Preferences>Sound

Next click on PCM in the list at the bottom

Hold down Shift-Ctrl and while holding them down, press the ext. volume up/down button.

Thats all there is to it, now your volume control will work the PCM level so that the Sub woofer and speakers will raise and lower at the same time!!

Much love! :KS

---

