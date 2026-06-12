---
title: "nvidia 8800 gts not working"
date: 2013-02-02
forum: Multimedia Software
---

### Post by mreos on 2013-02-02
I have been using the on board video and decided to try using old nvidia 8800 gts with no luck. Unable to get display working. It shows either blocks on screen or line streaks acoss the screen once it reaches ubuntu login.

Output
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 8800 GTS 512] (rev a2)
ubuntu 12.04.1 LTS
Asus P8Z68-V

I also went to system settings and tried additional drivers but nothing is listed.
 
In order to get back to post this, I had to go into BIOS and set iGPU as initial.

Anything else I can try?

TIA

---

### Post by Bashing-om on 2013-02-02
mreos; Hi !

See this thread about all you want to know about the intell/AMD hybrid situation.
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

edit: link corrected to proper address.
[INDENT][INDENT][INDENT]hth 

[/INDENT][/INDENT][/INDENT]

---

### Post by mreos on 2013-02-02
Here's the message I got when clicking on your link:

> Sorry - no matches. Please try some different terms.  

---

### Post by Bashing-om on 2013-02-02
mreos;

Don't know how I got that link messed up:
This is the correct link:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

Sorry to have inconvenienced you with this delay.

[INDENT]just try'n to help

[/INDENT]

---

### Post by mreos on 2013-02-03
From that post:
> [FONT=Arial][SIZE=2]If you do not own a AMD hybrid graphic card, please leave this thread, and post your problems in a thread made for AMD single graphic or Intel single graphic.[/SIZE][/FONT] 

Didn't think it would be so complicated to add a video card and get it working with Ubuntu. Everything else seems to just work so I assumed video card would be the same.

Thanks for trying to help!

---

### Post by Frogs Hair on 2013-02-03
I have an 8 series card and there are 7 different drivers available in additional drivers . This is with an AMD CPU though. :confused:

---

### Post by mreos on 2013-02-03
I tried the following:

> sudo apt-get install nvidia-current
sudo apt-get install nvidia-current-updates

In the BIOS I switched from iGPU to PCIe/PCI

It initially showed the ubuntu logo, then several flashes and now it is showing a black screen with login prompt. After I login with the same username/password, it shows nothing. I tried the command startx and nothing.

Am I better off doing a full back up and then reinstalling ubuntu? Will that help?

---

### Post by Bashing-om on 2013-02-03
mreos;
I have no direct experience with hybrid graphics, passing on what little info I have picked along the way.
With hybrid graphics the kernel gets confused as to which driver it should load for the graphics, In the past one had to tell the kernel via Xorg.conf which driver to load. A one or the other situation. As I understand it no driver exist in pure linux to handle both cards at the same time.
Presently there is hope in the BumbleBee project that may relate to your hardware configuration:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
For starters, if this approach  is an appropriate solution, a google search on "bumblebee ubuntu" will provide much more info.

[INDENT]here to assist as we can


[/INDENT]

---

