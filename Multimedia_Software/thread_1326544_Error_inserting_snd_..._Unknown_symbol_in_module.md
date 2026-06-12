---
title: "Error inserting snd ... Unknown symbol in module"
date: 2009-11-14
forum: Multimedia Software
---

### Post by LeFou on 2009-11-14
k, this is getting pretty silly. Review my post history for my sound problems if you care; I don't feel like going into it again.

Through the magic of trying everything everybody suggested (except :reinstall the whole OS") I was able as of a week ago to get my sound working by just doing

sudo modprobe snd-hda-intel

after booting. I should have my head examined, but I decided not to leave well enough alone; I wanted this to happen automatically during boot and so I added 

snd-hda-intel

to /etc/modules

hahaha, I know.. that's why I'm called LeFou. After reboot, sound did not work and when I tried manually modprobing again I got

FATAL: Error inserting snd (/lib/modules/2.6.24-24-lpia/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-24-lpia/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)

"Ye Gods!" I thought. "Better not do it that way!" So I removed the line from /etc/modules and assumed life would go on as before.

No suck luck. After rebooting, I still get the above error when I "modprobe snd-hda-intel"

---

### Post by LeFou on 2010-02-01
Have a couple hours of downtime here and thought I might revisit the sound issue .. 

If you're just joining us, a recap:

-Dell Mini13 netbook, ubuntu 8.4 was preinstalled and worked great
-Removing pulseaudio caused the wireless card and sound card to stop working, even though ALSA is also present here
-Eventually I bit the bullet and built ndiswrapper so that wireless now works
-Then I figured out I could make sound work by just going 
"sudo modprobe snd-hda-intel"

It annoyed me to have to do all these modprobes every time I boot, so I did what the post above says. Then I un-did it. now I get


FATAL: Error inserting snd (/lib/modules/2.6.24-24-lpia/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd

... and so on

Please note that I am angry. Have spent about 10 hours so far trying to undo the damage that removing pulseaudio did to this machine.

---

### Post by LeFou on 2010-02-01
This, incidentally, did *not help

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

It said stop all applications using sound devices (none are, so i didn't do anything) and reload alsa modules. So I 
modprobe snd-hda-intel

And got the same error as above.

---

