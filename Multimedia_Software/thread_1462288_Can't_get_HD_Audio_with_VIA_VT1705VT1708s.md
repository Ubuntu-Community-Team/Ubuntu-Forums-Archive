---
title: "Can't get HD Audio with VIA VT1705/VT1708s"
date: 2010-04-25
forum: Multimedia Software
---

### Post by Luigi Panache on 2010-04-25
[COLOR=green]I installed Ubuntu a week ago, and I've had few problems I couldn't solve.
However, even after much trying I couldn't get my motherboard's onboard audio to output in 5.1 surround like my Windows 7 OS can. Ubuntu simply claims my card is Stereo Duplex.
I tried using [these]("http://driverscollection.com/?H=VT1708&By=VIA&SS=Linux") drivers that I found online. The instructions didn't work one hundred percent, but after I somehow got through all the errors and compiled my new kernel I faced a command prompt interface (no graphics of any sort). I deleted my Linux partition, and installed Ubuntu 9.10 Desktop Edition 64-bit fresh.

After that, I remember seeing somewhere that I should install the package "linux-backports-modules-alsa-generic meta-package" to enable 5.1 audio on my card. After installing it, the ALSA mixer had a new option at the bottom left: (I'm new to this forum, so I can't figure out spoiler tags to not break the page width, sorry)
[http://img256.imageshack.us/img256/1139/screenshotty.png](http://img256.imageshack.us/img256/1139/screenshotty.png)

I checked the VIA website, and they say Smart 5.1 is a way to use the Line-out, Line-in, and Microphone ports as your three 3.5 mm outputs. This is what Windows 7 does for my surround system, and it works.
Of course, I enable it and turn everything on. I try a sound test (something in the terminal, I can't remember what) and it claims it's playing noise on all my outputs one at a time. I still only hear noise on front left and front right.
I try rebooting, making sure Smart 5.1 is enabled, and testing again but to no luck. I can't hear any surround sound.

So now here I am, my first forum post! Hopefully somebody will be able to work me through this! Thanks a bunch in advance!

Here are my system specs, if it'll help:
**Operating Systems:** Ubuntu 9.10 Desktop Edition x64, Windows 7 x64 Ultimate
**Motherboard:** ASRock N68-S
    **Audio Codec:** VIA VT1705 or VIA VT1708s (Not sure, Windows 7 says it's VT1705, Ubuntu 9.10 says it's VT1708s)
**CPU:** AMD Athlon X2 Regor II 250
**Video Card:** nVidia 9500 GT
**Hard Drive:** 640 GB WD Caviar Black Edition
    Partitioned to dual boot Win 7/Ubuntu with GRUB2
**PSU:** Eagle VoltasX 550 Watt
[/COLOR]

---

### Post by eMJayy on 2010-05-01
I'm having that exact same issue that you're describing. As it turns out, we're using the same motherboard (ASRock N68-S). 

As near as I can figure it, the audio chip on this board seems to have 2 parts - VT1708S, which controls a 2 channel mode, and VT1705, which is a separate part of the same chip that controls HD audio. Apparently, they require separate audio drivers. I haven't had much luck in finding info about the VT1705 part of the chip. I suspect that the problem might be that it relies heavily on the windows driver software to work and there probably isn't an equivalent Linux driver for it out there. I'll probably have to take a look at the kernel audio driver list to see if VT1705 is listed, but I'm not expecting it to be. 

Now that I know there's someone else out there looking for an answer to this particular issue, I'll keep researching it. If I don't find a solution, I have a SoundBlaster Audigy SE PCI card lying around that I was previously using on my old PC that delivers HD audio flawlessly in Ubuntu.

---

### Post by Luigi Panache on 2010-05-01
[COLOR=green]I've looked all over VIA's own website, and I can't seem to find **any** HD Audio system that works with Linux! This may just be a losing battle.

I'm glad I'm not the only person affected by this lack of support for Linux, but I sure don't know how to approach this problem...[/COLOR]

---

### Post by sabujakash on 2010-09-29
I am having the exact same problem :(. hope someday it would be fixed

---

### Post by Luigi Panache on 2010-09-29
[COLOR="Green"]I never did find a solution to this problem. In the end, I just bought a new motherboard and upgraded my system, fixing the problem in one way...
You could always go for a cheap (or expensive) sound card. I haven't run into a PCI sound card that wasn't supported in Ubuntu yet. It might even improve your sound.[/COLOR]

---

### Post by sabujakash on 2010-09-29
Just found this link which claims to VIA HD audio [driver]("http://drivers.viaarena.com/via_linux_hd_audio_fc4-c6&mdv2006-07.0_hd_audio_driver_ig_v0.82a.tar.gz") for linux... haven't gave it a try yet. Not too comfortable playing with linux drivers... 'll try it sometime soon when I get time...

But you guyz can give it a try and let me know whether this fixes the problem or not.

---

### Post by Luigi Panache on 2010-09-29
[COLOR="Green"]I've come across that archive too, and I've had no luck with it at all. Reading the manual, it constantly refers to Ubuntu 6.10. Ubuntu has come a long way in these four years from 6.10 up to 10.10 which comes out in a mere few days.
ALSA has already included its default support for the VIA VT 1708s integrated sound, it seems this driver won't do much to assist that.[/COLOR]

---

### Post by Yellow Pasque on 2010-09-29
The driver you linked to is so old (2006) that I doubt it supports the VT1708 codec (probably only the original VIA 8237/8251-based HD Audio).

---

### Post by lidex on 2010-09-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by sabujakash on 2010-10-03
Here is the link to the [result]("http://www.alsa-project.org/db/?f=31ea1cc305222da2f85b4ceb8639d951ee2bee57") of the script

For some reason the now even the stereo sound is not playing at all!!! must have screwed something while fiddling with it... now have almost given up hope to get surround sound out of this motherboard in ubuntu... :( 


Currently I am thinking about getting  Creative SoundBlaster X-Fi, USB external sound card. Do any of you have some personal experience with it, whether it works in ubuntu or not... Or if you have suggestion about external soundcard which works well with ubuntu let me know...

---

### Post by sabujakash on 2010-10-03
The reason I don want PCI card is then I would be able to use it with my Laptop as well...

---

### Post by lidex on 2010-10-03
Please remove alsa-backports, if installed, and upgrade alsa to full 1.0.23 version via the alsa-upgrade link in my sig. Report you results.

---

### Post by Gulo gulo on 2010-10-22
Hi

I lost front audio after alsa upgrade to 1.0.23 headphone and mic doesen`t work anymore . Anybody out there who can help a newbee.

HDA-Intel - HDA ATI SB VIA VT1708S 


[ATTACH]173129[/ATTACH]

[ATTACH]173130[/ATTACH]

---

### Post by lidex on 2010-10-22
> **Gulo gulo said:**
> Hi

I lost front audio after alsa upgrade to 1.0.23 headphone and mic doesen`t work anymore . Anybody out there who can help a newbee.

HDA-Intel - HDA ATI SB VIA VT1708S 


[ATTACH]173129[/ATTACH]

[ATTACH]173130[/ATTACH]

So did it work before the upgrade?

---

### Post by misa2210 on 2011-11-26
This thread is closed, but it seems that the issue is still remained :-)

I've got the same problem with ECS A55F-M3 (using VT1705) :
  + Output : front panel works, but back panel doesn't
  + Input (Mic/Line-in) : not confirm yet, but it should work, I guess :-D 

cheers,
Misa

---

