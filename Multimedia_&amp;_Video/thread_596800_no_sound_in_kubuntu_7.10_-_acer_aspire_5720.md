---
title: "no sound in kubuntu 7.10 - acer aspire 5720"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by rahulgurjar on 2007-10-29
Hi all,
I just installed Kubuntu 7.10 amd64 on my lappy and it can't seem to play sound, although it seems to have found the audio card. The laptp specs are 
intel core 2 duo T5250, 1 gb ram, 120gb hdd

At the console, when I type in ```
lspci | grep Audio
```
I get the following
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

As well, when I use the manual volume control on the side of the laptop KDE detects the volume is being changed, and shows the volume as having increased or decreased.
In Amarok, if I try playing an mp3, it looks like its playing, but theres no sound. I put the volume in Amarok to max, as well as KDE's volume to max. I tried using headphones as well, in all 3 input jacks, to no avail. 
The 5720 is marked with Dolby Digital Live, this wouldn't cause problems would it?
In System Settings -> Sound System, I have kept the default settings, so the audio device is set to auto detect, but i tried ALSA and ESD and neither worked.

Any troubleshooting help would be greatly appreciated.

---

### Post by LeeDavis on 2007-11-10
Hi,

I had the same problem (it was the only thing stopping me from erasing vista ;)) until this morning when I came across this link:

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720)

I followed the instructions and rebooted and the sound is working spot on now.

~Lee

---

### Post by Lukyan on 2007-11-19
Hi! I had the same problem therefore I followed the guide of above, but I still have a problem... I'm not able to use the microphone! How can I check if something is wrong?

Thanx in advance!

---

### Post by Lumo on 2007-11-27
I can use the microphone, but only when I go into volume control > options then select a source I don't want, then reselect the one I want.

If I don't do this neither the internal mic or mic port work, but when I do do this I can get them to both work. Hope this helps.

I have to do this everytime I reboot or resume from hibernation - anyone have any ideas why?

---

### Post by DakoCwerf on 2007-12-20
try to install your backports - worked for me

> sudo aptitude install linux-backports-modules-generic

---

### Post by slugworth1987 on 2008-04-01
i have an issue with the 5720.093 i keep getting errors on the 2nd line of code on the wiki then if it does work i get this in the terminal.

> 

nothing else i type in something and nothing happens so i press ctrl + C and try again i also get "- r is a unknown command" with the \user -r\" command i have changed the user -r to my login (sean)
i have also tried sean:sean-laptop and sean@seanlaptop still no joy... im on ubuntu 7.10... any ideas?

---

