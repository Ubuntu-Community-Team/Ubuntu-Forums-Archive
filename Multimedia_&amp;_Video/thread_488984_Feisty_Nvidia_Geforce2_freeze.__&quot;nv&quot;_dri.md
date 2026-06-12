---
title: "Feisty Nvidia Geforce2 freeze.  &quot;nv&quot; driver works"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by lostpoet on 2007-06-30
I've done some searching in the forums and haven't located my specific problem.  I have been using Ubuntu since Dapper on this machine.  Edgy worked fine.  Nvidia Geforce2 always worked.  I installed Feisty and now the "nvidia" driver causes the screen/computer to freeze.  The cap lock and scroll lock lights flash on the keyboard and no inputs respond.  I must restart with the power button to get out of it.  The legacy glx from the repository does the same thing.  I also tried a couple of versions of the drivers on the Nvidia web site and they did the same thing.  The "nv" driver does not cause the problem.  I'd really like to get my glx back.  Thanks.

---

### Post by kurian on 2007-07-11
i do have the same problem i use geforce2 integrated GPU ...is there anyone who can help us???

---

### Post by Malmsdoom on 2007-07-12
I have the same problem, only nvidia can solve the problem.

---

### Post by FuturePilot on 2007-07-15
Exact same problem with Nvidia GeForce2 Go on my laptop. Weird thing is it doesn't happen with Dapper. Every release starting with Edgy freezes my laptop with the Nvidia driver. The "nv" driver is fine, but darn slow.
Using the 9631 driver on Dapper, there is no freezing. However the 9631 driver on Edgy, Feisty, and even on Gutsy make it Freeze.

Strange. It's driving me nuts.

---

### Post by ronniew on 2007-08-17
I have the same thing happening here.... any solutions yet?

---

### Post by EndPerform on 2007-08-17
I had lockup problems on my nVidia Geforce 6800 on my desktop for the past year and a half over the course of a couple of different distributions, Feisty included.  I have upgraded to  Gutsy (development version of Ubuntu) on my machine, and I haven't seen it lock up yet.  The difference?  New version of Xorg.  There's something with Xorg in Feisty and other distributions that doesn't play nice with the nVidia driver.

For reference, I'm using Gutsy and the latest driver from nVidia.

---

### Post by tseliot on 2007-08-17
Maybe you should try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by FuturePilot on 2007-08-18
I'm almost convinced now this isn't a driver issue. It's either a kernel issue or a xorg issue. I've been using the 9631 driver on Dapper and I've never had it freeze once. However, every other release freezes with the same driver.
Dapper+9631- **No Freeze**
Edgy+9631- Freezes
Feisty+9631- Freezes
Feisty+**9639**- Freezes
Gutsy+9631- Freezes

---

### Post by ronniew on 2007-08-19
I believe I found the fix for this ongoing problem with the GeForce2 Go random freeze. 

It is in the kernel. I did some testing last night with the frame buffer in the kernel "OFF" and all seems fine now.

Test yourself and let me know your results 


:)

---

### Post by FuturePilot on 2007-08-19
How do you turn this off in the kernel?

---

### Post by tseliot on 2007-08-19
> **FuturePilot said:**
> How do you turn this off in the kernel?
I think you would have to recompile your kernel for that.

Did you ask here?
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by FuturePilot on 2007-08-19
Ok, I've posted a thread over there. Here's the link if anyone else would like to add something.
[http://www.nvnews.net/vbulletin/showthread.php?t=96850]("http://www.nvnews.net/vbulletin/showthread.php?t=96850")

---

### Post by ronniew on 2007-08-19
you don't have to recompile the kernel you just have to reconfigure xserver-xorg


just say no to the kernel framebuffering option


sudo dpkg-reconfigure xserver-xorg

---

### Post by EndPerform on 2007-08-19
> **ronniew said:**
> you don't have to recompile the kernel you just have to reconfigure xserver-xorg


just say no to the kernel framebuffering option


sudo dpkg-reconfigure xserver-xorg

That may work for some, but I have my doubts.  As a previous poster mentioned, things were fine prior to the release of Xorg 7.2.  Once that was released, my lockup issues begun, and every distro I tried gave me the same problem.  Now, with Gutsy comes a new version of Xorg, and since then, I haven't had a single issue with lockups at all.  Hopefully when people upgrade come October, this issue can be put to rest.

---

### Post by tseliot on 2007-08-20
> **ronniew said:**
> you don't have to recompile the kernel you just have to reconfigure xserver-xorg


just say no to the kernel framebuffering option


sudo dpkg-reconfigure xserver-xorg
Ah, that option... it thought you were referring to the one in the kernel.

---

### Post by FuturePilot on 2007-08-20
Turning the frame buffer off didn't help. Still freezing.:(

---

### Post by rmujica on 2007-08-20
I'm having the same problems, I have a GeForce 2 MX integrated GPU and I previously used Dapper and the NVIDIA drivers without any problems. Now, I uninstalled Dapper and installed Feisty directly (from the downloadable ISO) and I installed the drivers using:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
``` just as I did with dapper, and the drivers installed "correctly", I rebooted, the NVIDIA logo appeared, and the Ubuntu Login Screen freezed.

---

### Post by FuturePilot on 2007-08-21
So it seems to be confirmed that Dapper works fine with the Nvidia drivers but other releases don't. What changed? It's got to be either the kernel or xorg.:(

---

### Post by FuturePilot on 2007-08-22
Anyone have anymore ideas? I haven't gotten anywhere. It's still freezing.](*,)

---

### Post by FuturePilot on 2007-08-23
Filed a bug report
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/134310]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/134310")

---

### Post by FuturePilot on 2007-08-23
Ok. help me test this possible solution:D
```
gksudo gedit /etc/init.d/powernowd
```
Right below the very first line #! /bin/sh
Add this```
exit 0
```
Save and reboot

Now an explanation:
Apparently there's a bug in the Nvidia driver where it can't keep up with the CPU frequency scaling. So what happens is it just freezes. So by adding that to powernowd you are disabling CPU frequency scaling. If you also have a setting for CPU scaling in your BIOS you might want to try disabling that too.

---

### Post by Bruegger on 2007-09-05
FuturePilot,
okie, same gpu and same problem with 9639 drivers. working it with 8776patched drivers.
are you using the 9639 drivers? 

Bruegger

---

### Post by FuturePilot on 2007-09-05
I've tried them all. Lol
I'm currently using the 9631 driver and it hasn't frozen on me since I disabled powernowd.

---

### Post by Bruegger on 2007-09-06
Great Tip.Thanks for sharing it.
Works on 9639 too.Atleast doesnt hang or freeze with capslock and scrolllock flashing on the kb's.Facing the foll problems still though:
1.The screen is lagging...things dont appear fast on the desktop.Like words typed on terminals dont appear fast, or pages scrolled dont appear to move with the scrolling. 
2. Sometimes get a fps of appx 3000 and most times fps of 450.
3. Opening some of the programs like screen resolution gui restarts the gnome desktop.

Any idea what could be causing this?

p.s. Are you able to run compiz-fusion on this card???

Bruegger

---

### Post by FuturePilot on 2007-09-06
Hmm. Not sure about those other problems.:confused:
I could run Compiz Fusion, but this card suffers badly from the black window bug despite the different workarounds. They reduce it but don't fix it. And also it's not powerful enough. If I try to run it, it slows everything down way too much. So I just stick with fast Metacity.

---

### Post by Bruegger on 2007-09-07
Ok.
2 of my 3  issues seem solved now. Tweaked my xorg.conf with some options.
No lags in terminal, no lags while scrolling pages.
Only inconsistent FPS issue persists. Sometimes its 400, sometimes 500, sometimes 1050 and sometimes 3000.
So i think there's still something wrong with my xorg.conf.Any one any ideas???
Will be trying Beryl and Compiz-Fusion soon. Will keep this thread updated on the developments.

---

### Post by Bruegger on 2007-09-09
Heres the update.
Beryl or Desktop effects dont seem to go well with the 9639 driver.
Screen has a lotta lags, jagged lines and occassional freezing.
And i like to have my 3d desktop effects, so changed back to Patched 8776 drivers.
Beryl works beautifully with this driver. No problems with it till now.

Will try compiz -fusion in a couple of days and update.

---

### Post by Bill Collecta on 2007-09-10
Dude! you got like the same PC as me. Where did you download this Patched driver? I just removed Ubuntu from my computer simply cause I couldn't stand having no working GPU driver.

---

### Post by Bruegger on 2007-09-10
Bill,
I followed this guide [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/) to install the patched 8776 drivers 
Let me know if you need any more help.

---

### Post by Bill Collecta on 2007-09-11
Thanks man, I'll look in it soon, at the moment I uninstalled Ubuntu after I totally bricked it.

Installing the driver failed, had to reconfigure Xorg but bricked it <.<

---

### Post by Bruegger on 2007-09-11
Don't Give up yet.
Even i am learning something new everyday and that is what is drawing me closer to ubuntu and linux.
Try it and you might just never want to leave it.

---

### Post by Bill Collecta on 2007-09-11
Hell yeah!!

It worked dude, love Ubuntu :D

---

### Post by Bruegger on 2007-09-11
Bravo!!!
I am happy it worked for you.

---

### Post by kurian on 2007-11-15
hi...............iam back again ... iam using nvidia geforce 2 itegrated gpu everything worked fine in dapper drake...but when i use feity things went upside down after that i tried many latest linux versions....opensuse10.3, sabayon, freespire...but all having the same problem black windows coming in the screen and the xserver automatically shuts down after some time......


Is this the problem of NVIDIA DRIVER??????

OR 

KERNEL??????

WHETHER THE SAME PROBLEM IS EXPERIENCED WITH GUTSY GIBBON>???????

---

### Post by kurian on 2007-11-15
> **Bruegger said:**
> Bravo!!!
I am happy it worked for you.

hi iam having ur same configuration when anythings works fine please let me know...:)

---

### Post by Bruegger on 2007-11-15
Kurian,
Glad to know we share the same m/c config. Presently i m on gutsy 7.10 and using nvidia driver 96.43.1. Installed this through envy 0.9.8.Make sure you delete all our previous nvidia drivers before you use envy to instal the latest divers. This should work for you too. Incase it doesnt, you can alwys use the 8776 patched drivers. This works extremly well on the 7.10 kernel too. 
Let me know if you need any more help.
Cheers!

---

