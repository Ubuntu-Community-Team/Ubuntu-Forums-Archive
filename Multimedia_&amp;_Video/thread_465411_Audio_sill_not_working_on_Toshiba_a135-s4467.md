---
title: "Audio sill not working on Toshiba a135-s4467"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by billybob9187 on 2007-06-05
Hi guys new to the forums and linux but i am having problems with the audio drivers on this machine. When i pull up devices in terminal i get the hda intel hd audio device and the hda intel modem. i have been trying all the fixes i could find but they don't seem to work and i think it is because ubuntu already sees the audio device. Ive tried switching the device in the audio prefrences and still nothing if anyone has any ideas that would be great. I am open to anything and maybe its because i am not sappost to use terminal or something just let me know i am sure i must have made a newb mistake somewere.

---

### Post by moeFinley on 2007-06-09
I had a similar problem using a ThinkPad T41 which has an Intel sound card and modem.  I tried lots of things (user permisions, installing the latest ALSA) but nothing worked.

In the end I install Kubuntu which uses a different sound system and it all works fine!  But I didn't want to make the switch to KDE so I looked around for something else and found MintLinux.  It's built around Ubuntu Fiesty and still uses Gnome but with lots of nice extras (such as Beryl, Flash and Pidgin).

However if you not wanting to start a fresh install I can't only recommend using 'lspci' and 'lspci -n' and googling the output to search for the very latest driver for your device.

Can you disable the modem in you bios?

---

### Post by moeFinley on 2007-06-10
I just noticed something weird.  When I booted my laptop back up from hibernation the sound didn't work even though everything looked fine?!  Even when I did a full restart it did't come back?

I shut down, waited a bit and booted back up and my sound was back.  This suggests that something is changed with the hardware in hibernation?

---

### Post by mimagabooks on 2007-11-09
Try this

[http://ubuntuforums.org/showthread.php?p=3741293#post3741293](http://ubuntuforums.org/showthread.php?p=3741293#post3741293)

---

