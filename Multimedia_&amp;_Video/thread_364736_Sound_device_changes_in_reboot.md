---
title: "Sound device changes in reboot"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-02-18
I have successfully (After 2 months) managed to get a working install of mythtv. I am using a nvidia 5200 fx video card, a Hauppauge 1300 HVR tv card, and on board sis sound.

My problem is that evey time I reboot i have to enter mythtv frontend and go the the settings and alter the device allocation of the sound card, this is beacuase it changes every time i reboot!!
Some times it is dev/dsp, some times its dev/dsp1, and some times its dev/dsp2, This has to be done after EVERY reboot!! 

the other audio devices represent the tv card and they will not out put sound to the speakers!!

Any help will be greatly appreciated!!

---

### Post by thingy on 2007-02-18
ugh! this seems to be happening a lot now days...not your sound issue but the fact that people actually need device names to be pointing to specific devices.

i have no easy solutions for you but can advice you on where you need to look at for a solution.

its udev which is assigning the /dev/dsp? devices to hardware it detects at boot. now, udev does have *extreme* configurability in that it allows you to exactly specify which device you want to map /dev/dsp1 to for example but to do that you need to write a udev rule <--- not easy last time i looked at this.

:-(


to start you off, here's some info on udev rules.

this article is about removable devices but you can follow the links in it for more info.

[http://www.ubuntuforums.org/showthread.php?t=168221&highlight=udev+rules+howto](http://www.ubuntuforums.org/showthread.php?t=168221&highlight=udev+rules+howto)

---

### Post by Dubstar_04 on 2007-02-19
ok thanks for info it sounds like that could be used to solve my problem, however i read all the infomation and non of it mentions sound, and i don't know where to begin!!

anyone else have this problem??

---

### Post by Dubstar_04 on 2007-02-20
Anyone offer advice?

---

### Post by Dubstar_04 on 2007-03-05
Please please please please please could someone help me with this??? 
Ubuntu thinks my video card hauppauge HVR 1300 is a sound device and when i reboot my pc the sound device changes and I have to change it in the settings almost every time!!!

This pc is a mythbox for my dads birthday that is in just over a week away  and i can't give it to him if it doesn't work!!

This is my out put from lspci; I hope it helps.

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:07.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:07.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
wood@mythtv:~$

---

### Post by thingy on 2007-03-06
ok!

install an irc client and join the [freenode]("http://freenode.net/irc_servers.shtml") network's #ubuntu channel tomorrow at 8pm GMT. I'll read up on udev rules and see if we can get udev to give your sound cards specific device filenames and hence resolve the issue.


oh, my irc name will be thingy as well!

---

### Post by Dubstar_04 on 2007-03-06
Thanks for that its really good of you. However I have some intersting news. I got really annoyed with my problem and installed fedora thinking that this would solve the problem, however the same problem exists there too!! Therefore the problem is either a udev problem as you suggest or problem with the way that the hardware is recognised, causing the pc to think that it is a sound card.
What I have done for now is reinstalled ubuntu and i'm going to use one of my old tv cards that use a different tuner chip and doesn't foul the sound!!

I will hope fully see you on irc tomorrow. 
Cheers, Dubstar.

---

### Post by Dubstar_04 on 2007-03-07
Hey thingy thanks for all your help tonight. unfortunatly the problem still occurs!!

i can specify in mythtv dev/sis/dsp but that device isn't always written!! so the sound is on and off with reboots and shutdown / restarts!! the weird thing is that the device /dev/cx88/dsp looks to be written every time but unfortunatly that is'nt the sound device!!

I really don't have the experince to carry this any further and i would really appreciate your help again.

Thanks for all you have done.

Dubstar_04

---

### Post by thingy on 2007-03-08
Hi

Umm...im confused about the descripion you just said. Can you post a screenshot or two to show me where in mythtv you are specifying the /dev/sis/dsp device, and which after rebooting seems to disappear or change into something else...

Yesterday, I asked that the tests you could do was to ensure that /dev/sis/dsp is always the SIS sound card and that the /dev/cx88/dsp is always the Hauppauge card when you reboot or shut down the machine.

Can you confirm that the udevinfo -a -p /dev/sis/dsp  and the udevinfo -a -p /dev/cx88/dsp always return the same information between reboots?

umm anyway, we'll talk tonight...8pm  ish

c u

---

### Post by Dubstar_04 on 2007-03-08
I have attached two screen shots. 
One as requested is of the mythtv setup screen with the /dev/sis/dsp and /dev/dsp/mixer specified in the settings.

The other shows the file browser looking at the sis and cx88 directories and you can see that the sis/dsp file has not been written.

The cx88 dsp is not actually needed as it is just used by mythtv for sound decoding of live tv.

---

### Post by Dubstar_04 on 2007-03-08
Thingy I have shut down and rebooted numerous time and the sound device has stayed the same every time. it had never done that before!!!

The only problem is that the saa7134-dvb module isn't loaded on reboot, however im sure that this is just a easy fix!

thanks for all your help.

Dubstar_04

---

### Post by thingy on 2007-03-09
hi ya

See this thread on how to load modules at boot:

[http://www.ubuntuforums.org/showthread.php?t=102961&highlight=load+module+boot](http://www.ubuntuforums.org/showthread.php?t=102961&highlight=load+module+boot)

---

### Post by Dubstar_04 on 2007-03-10
Hi Thingy, the modules all load at boot. just not reboot!!
the sound device is working great though i'm so pleased.

---

### Post by thingy on 2007-03-10
did you:

Edit your /etc/modules file and insert a 'saa7134-dvb' right after the saa7134 line?

If it doesn't load up when you boot up each time, i.e. doesn't matter if its a cold boot(i.e. system just powered up) or a warm boot(reboot) then it must actually be saying something during the start messages indicating what the problem was. Did you see any output in dmesg or /var/log/messages?

---

### Post by Dubstar_04 on 2007-03-31
New feisty install and the problem is back!!!  One of my tv cards keeps becoming the default sound card!! I have change the prioriyies on the alsa base file

```
 /etc/modprobe.d/alsa-base 
``` 

This method did the trick in edgy, but its not working in feisty!!

Any ideas??

---

### Post by Dubstar_04 on 2007-04-02
This problem seems to be sorted. I set all the system>preferences>sound items to the correct card and put all the settings in the alsa base to the same value of 2. and that seems to of done the trick!!

---

