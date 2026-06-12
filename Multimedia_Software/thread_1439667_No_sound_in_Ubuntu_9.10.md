---
title: "No sound in Ubuntu 9.10"
date: 2010-03-26
forum: Multimedia Software
---

### Post by ravisunny2 on 2010-03-26
[FONT=Times New Roman][SIZE=3][COLOR=black]Hi,[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=black]I just loaded **ubuntu 9.10** on an old PIII in dual boot mode with win98SE.[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=black]The pc has a **DS-XG YMY470** Yamaha sound card, and the sound is available in Win98SE.[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=black]In ubuntu, there is no sound while playing games or playing music.[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=black]I tried the initial diagnostics as suggested in the stickie with the following results:[/COLOR][/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3][COLOR=black]**aplay –l**[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]aplay: device_list:223: no soundcard found...[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=black]**lspci –v**[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]00:09.0 Multimedia audio controller : Yamaha Corporation DS1L Audio[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]Flags : medium devsel, IRQ 12[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]Memory at e6000000 (32-bit, non-prefetchable) [Size=32k][/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]Capabilities : <**access denied**>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=black]Kernel modules : snd-ymfpci[/COLOR][/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Is there any way to get the sound started, or do I need to change this card ?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Thank you.[/SIZE][/FONT]

---

### Post by ravisunny2 on 2010-04-04
Bump. Still no sound. Do I need to change my BIOS settings ?
 
The thing is that at various points of my career, I've used varous os including Unix (a long time ago).
 
My kids won't touch Linux with a ten foot pole.
 
I'm trying to get them to give Linux a try.
 
The sound problem does not help at all.

---

### Post by cchhrriiss121212 on 2010-04-05
You should definately check bios settings. Alsa does not seem to have this device as supported in its database:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha)

You could follow this guide if you have the time:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The access denied means that you are not part of the right groups. Try going to Users & Groups in the system menu and adding yourself to the relevent groups (audio, pulse etc.).

If you want the kids to use linux I would check you have supported hardware before getting them to try it out.

---

### Post by gaspros on 2010-04-05
I am having sound problems in 9.10 as well. Try using a live CD for 9.04 Jaunty and see if it recognises your sound card.

Troubleshooting sound problems can be found here
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) 

I dont really have a solution for you in 9.10 I am sorry to say.

---

### Post by ravisunny2 on 2010-04-09
Okay. Thanks guys.
 
There seems to be no easy way out.
 
I will study the info in the above links, and report back.
 
 
**PS**
 
karmic koala is running fine on my **C2D**. :)
 
I am trying to keep the same distro on both the PIII & C2D.

---

### Post by lidex on 2010-04-11
First thing for audio in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Still no sound? I'll need more info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by ravisunny2 on 2010-05-08
[COLOR=black][FONT=Times New Roman][SIZE=3]Stll trying to get sound in the PIII. I have checked the Alsa site.[/SIZE][/FONT][/COLOR]
 
[FONT=Times New Roman][SIZE=3]I have also done some googling on how to make a **.deb** file. It seems that instead of **make install, **I should use **checkinstall**.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have two PCs. One is my work PC, the other for the kids.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I want to create the **.deb** files on **my PC**, burn to cd, copy the **.deb** to the PIII, and install the .**deb **files using[/SIZE][/FONT]
 
[SIZE=3]**[FONT=Times New Roman]sudo dpkg [/FONT]****[FONT=Consolas]&#8208;[/FONT]****[FONT=Times New Roman]i package.deb[/FONT]**[/SIZE]
 
[FONT=Times New Roman][SIZE=3]Is this feasible ? How should how I modify the Alsa instructions ?[/SIZE][/FONT]
 
 
[COLOR=black][FONT=Times New Roman][SIZE=3]I got this from the **Alsa **site:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Make a directory to store the alsa source code in: [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd /usr/src[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]mkdir alsa[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cp /downloads/alsa-* .[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-driver package:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure --with-cards=ymfpci --with-sequencer=yes ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-lib package: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]cd ..[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-utils package: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]cd ..[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now insert the modules into the kernel: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]modprobe snd-ymfpci ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss[/SIZE][/FONT][/COLOR]

---

