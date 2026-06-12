---
title: "can't get nvidia 8400gs drivers to work right"
date: 2009-07-22
forum: Multimedia Software
---

### Post by aaron_the_dude on 2009-07-22
Hey, I have been playing around with ubuntu for about a month now and I have to say that I am impressed at it and am no longer much of a windows fan.  I am slowly learning the ways of the penguin, but I recently got a new video card, an nvidia geforce 8400gs and I want to use it correctly in this operating system but can't get the drivers to work and miss my "wobbly" windows.  I tried going straight to the nvidia site and download the linux geforse series 8 drivers but that didn't work, then I tried envy to get it to work.  I could still use the computer with my video card, but if I try to use desktop effects, it just tells me that desktop effects could not be enabled.  Could anyone help me out please?  Also, hopefully small downloads because I only have access to dial up here.

---

### Post by xc3RnbFO8P on 2009-07-22
The best way is to make a fresh install of Ubuntu.

---

### Post by bender1234 on 2009-07-22
Which driver did you get? If you got the 185.something driver it is utterly broken.
If you try to remove it, it will leave some garbage files that mess up when you try to change the driver.

have a look at this post if this is the case:
[http://ubuntuforums.org/showthread.php?t=1182507](http://ubuntuforums.org/showthread.php?t=1182507)

post #6

---

### Post by aaron_the_dude on 2009-07-22
I don't think I used 185 but I'm not sure though.  It isn't showing the same symptoms as him.  When I put [FONT=monospace]dmesg[/FONT] into the terminal, I get a nice long list that doesn't resemble his.  Is there a good way to check?  Also, I really rather not fresh install ubuntu if I could help it because it took me a few nights to get all the updates last time through my 56K.

---

### Post by Arup on 2009-07-22
I have been on 185 stable before I upgraded to 190 beta on my 8400GS, didn'tn face a single issue with 185 and neither am I facing any issues with 190 beta. I use via .sh downloaded from nvidia site.

---

### Post by aaron_the_dude on 2009-07-22
Sorry to lead you guys through a loop, but I was wrong on my last post.  I tried a little more experimentation on it, and it turns out that I was showing a few of the signs of his same problems, just like this.

damien@damien-desktop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
I went through damien-d's little step by step, and at the point where you use dmesg to make sure all the nvidia is flushed out, i got....
aaron@aaron-desktop:~$ dmesg | grep nvidia
[   12.864485] nvidia: module license 'NVIDIA' taints kernel.
[   13.125566] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.125577] nvidia 0000:01:00.0: setting latency timer to 64

It might have to do with, the step before that, it asks you to use the code
sudo nvidia-installer --remove.  but the terminal told me that --remove wouldn't work so I used --uninstall instead and that might have something to do with it, I'm not sure.

Any help from there?  I would like to get ALL of the nvidia out before I put some nvidia back in.

---

### Post by Arup on 2009-07-22
Remove exisiting drivers. Dowload .sh from nvidia, install build-essential, go to synaptic and mark compelte remove linux restricted modules. Do a ctrl+alt+f1 login and then do a sudo /etc/init.d/gdm stop make sure your .sh nvida is in your Home folder. Do a sudo .sh NVIDIAxxxxxxxxx

Say yes to all option and in end do a sudo reboot.

---

### Post by aaron_the_dude on 2009-07-22
Hmm...I thank you for the help but I don't quite understand.  On the first step, I should remove existing drivers but I don't know how.  I am trying to remove all traces that nvidia was on my computer.  also, when i use the terminal and type sudo apt-get install .sh, it says it can't find it.  I'm still trying to get out of the newbie faze so could you give instructions like i'm retarded, that usually helps best.

---

### Post by hman1169 on 2009-07-23
Arron, Arup has it right...

Remove exisiting drivers. Dowload .sh from nvidia, install build-essential, go to synaptic and mark compelte remove linux restricted modules. Do a ctrl+alt+f1 login and then do a sudo /etc/init.d/gdm stop make sure your .sh nvida is in your Home folder. Do a sudo .sh NVIDIAxxxxxxxxx

Say yes to all option and in end do a sudo reboot.

First go to synaptic package manager... Type Nvidia in the search box...
"go to synaptic and mark completely remove linux restricted modules" (I right clicked on every NVIDIA green checked box I had and said, COMPLETELY REMOVE...

Then I followed this
ctrl+alt+f1 login and then do a sudo /etc/init.d/gdm stop make sure your .sh nvida is in your Home folder. Do a sudo .sh NVIDIAxxxxxxxxx
(mine was NVIDIA-Linux-x86-185.18.14-pkg1.run)

185 is finally working after numerous attempts... Thank you Arup, I had been hammering on this one for a couple days... I forgot to completely remove everything with the Synaptic Package Manager...

Hope this helps!

---

### Post by aaron_the_dude on 2009-07-23
I didn't have any doubt that Arup wasn't right if he got it to work himself.  I just didn't understand the instructions.  But I got a little impatient waiting for a reply so I followed this link:
[http://forums.nvidia.com/index.php?showtopic=99513](http://forums.nvidia.com/index.php?showtopic=99513)
and it got my drivers to work and I get my window wobble effect.  While looking back, it is the same as you and arup were saying, just in "hold my hand while doing it" format.  But thank you for all your help, I have been trying to get this to work for a week.  You may go ahead and mark this thread solved.  My only problem is now when I click play on Neverball, the window goes away.  But that is a problem I'll work on later.  Thank you very much.

---

