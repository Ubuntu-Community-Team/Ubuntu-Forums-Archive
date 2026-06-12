---
title: "Realtek HD Audio Sound - Not working"
date: 2010-01-24
forum: Multimedia Software
---

### Post by ßeyond on 2010-01-24
Hello.

I'm running Ubuntu 9.10, but so far I've been unable to get sound to work. I know my sound card is Realtek, because I've had to install the HD Audio Codec Driver when I was on Windows. I downloaded the driver for Linux and it is currently sitting in my home folder. When I tried to ```
sudo ./install
``` the driver, it failed for the following reason:

```
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

Remove Folder.....
./install: 108: alsaconf: not found

```It may also help to know that my computer is an Apple iMac.

Thanks.

[B]MAJOR UPDATE:
I just followed the comprehensive sound guide and discovered that apparently my sound card is not detected. I ran both "aplay -l'' and "lspci -v".[/B]

---

### Post by ßeyond on 2010-01-24
Apologetic bump... I really need an answer.

---

### Post by ßeyond on 2010-01-24
I know you guys have this information.

---

### Post by ßeyond on 2010-01-29
I'm completely lost. I've searched Google countless times for an answer, but it just doesn't seem to be out there.

---

### Post by Allwynd on 2010-01-29
i feel u mon, i had semi-similar problem with ubuntu 9.04, but upgrated to 9.10 and had it fixed
if ur hardware is quite new, ubuntu should detect it and install proper driver (im a linux noob, thats all i know)
did u tried System > Administration > Hardware Drivers?
id ure lacking some drivers, that could fix it.. i hope so :)
i wish u luck fixing ur sound, cuz linux is great... if a guy can get the hang of it.. then its and awesome experience .. now if im not sure i just ask and learn :D

---

### Post by MrNatural on 2010-01-29
I'm also running a RealTek sound card (ACL880) with 9.10, and cannot get sound to work. I know the sound card is OK, because I have a dual-boot setup with Windows, and I get sound with Windows.

This is really aggravating, because 9.10 is working beautifully otherwise...

Alan

---

### Post by bdragos on 2010-02-21
Have you guys found a solution for this? I have the same problem.
Thanks,

---

### Post by lyall on 2010-03-07
at the command line enter **gnome-alsamixer**
check you setting 

it is a place to check

good luck and have fun learning

---

