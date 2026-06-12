---
title: "Ubuntu 10.10 doesn't display on Vaio laptop's screen"
date: 2010-10-23
forum: Multimedia Software
---

### Post by khoi0107 on 2010-10-23
Hi guys !!! I
Recently I install ubuntu 10.10 on my Sony Vaio laptop. After the CD boot I always got a black screen, after a week i figured that there's nothing wrong, it's just the screen doesnt show up on my laptop's screen. So I use an external monitor and It showed up as normal.
 
But I need to have it show up on my laptop's screen.
I tried to use "additional driver" to activate latest Nvidia driver but after that even my external monitor doesnt work too. Latest driver doesnt work properly i guess.
I did try to install older driver version manually but after I turned of gdm, install driver and reboot, my ubuntu always starts with tty1 command terminal. tried ctrl+alt+7 but it stucked at (checking battery state), startx doesnt help me return to graphical screen too.

I got help from a moderator here but the best result so far  is to edit my /etc/default/grub. Change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Sudo update-grub
after the reboot I have it shows up on my laptop's screen. But it seems low-bit color,a bit grand to me(compared to external monitor, both w/o driver). Anw i checked system/preference>monitor . It showed up that my monitor:unknown. I can't choose other resolutions, refresh rate = 0. 
[IMG]http://img87.imageshack.us/img87/7461/testll.jpg[/IMG]

I always know its my widescreen is the problem. I have had a lot of problems dealing wgames/application (on windows) can't work on 16:9 mode.  
**Can anybody help me install a stable Nvidia driver, or help my ubuntu to recognize my monitor plz**

I've tried 2 weeks for this and Im hopeless now, I'm newbie so sorry for any dump question :(. Everything I tried in the past weeks is in here [http://ubuntuforums.org/showthread.php?t=906865&highlight=khoi0107&page=13](http://ubuntuforums.org/showthread.php?t=906865&highlight=khoi0107&page=13)
Sorry for my English, Im not native spearker :( 
**My laptop is SONY VAIO VPCCW19FX, Nvidia GeForce GT 230M, widescreen monitor**
Plz help

---

### Post by RebateFX on 2010-10-23
I know this may not be helpful but from my experience, the hardware Sony uses in their VAIOs is well, to put it bluntly.. weird. I had a similar experience with my Vaio X with a GMA500 chipset. I tried all of the suggestions to get the gfx working properly including installing Jolicloud which proudly boasted of working out of the box with a fully accelerated GMA500 driver set, but on the Sony it was impossible. 

I have tried Ubuntu on other Vaio laptops and they all had one problem or another.

My HP DV6 has the same Nvidia GTX 230M chipset as you and the Nvidia drivers work just fine.

My suggestion is to just stick with windows if you are using a Vaio laptop. It seems to me that Sony goes out of their way every time to make sure linux is not going to work on their hardware ;)

---

### Post by khoi0107 on 2010-10-23
so nobody ever used ubuntu on their Vaio laptop? my major is EE and I want to learn embedded linux. I can't afford another laptop atm. So plz if anybody can help? :(

---

### Post by disappearedng on 2010-10-24
> **khoi0107 said:**
> so nobody ever used ubuntu on their Vaio laptop? my major is EE and I want to learn embedded linux. I can't afford another laptop atm. So plz if anybody can help? :(

I use it on 10.04. Works fine with nvidia (at least you can adjust the brightness). 

10.10 just break it completely. Check [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all)

my eyes are burning from the screen.

---

### Post by khoi0107 on 2010-10-24
so u used 10.04 on ur Vaio? did it go black screen when u install it or u have to use external monitor too? 
What is last version that works for u in 10.04? Im downloading 10.04 now 
Thanks !!!

---

