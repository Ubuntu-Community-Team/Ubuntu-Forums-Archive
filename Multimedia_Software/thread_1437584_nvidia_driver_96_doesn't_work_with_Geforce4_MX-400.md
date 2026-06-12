---
title: "nvidia driver 96 doesn't work with Geforce4 MX-4000"
date: 2010-03-24
forum: Multimedia Software
---

### Post by mamboze on 2010-03-24
Hi,

I've been having big problems getting 9.10 to work with a Geforce4 MX-4000 card. I know it is not a hardware problem because I've got a dual boot win xp/9.10 setup and the video card works very well under win xp. The monitor is a Samsung P2250. The issue is that the highest resolution available after installing the recommended nvidia 96 driver is 800x600, the same as that before the driver was installed. This is very frustrating because the monitor requires 1920x1080 

I'm not sure whether the driver is at fault or the xorg.conf settings. 

Should I try installing the nvidia site drivers? I've checked out several forum threads on xorg.conf settings but I'm really not sure how to go on this. What I need is an entry level guide to setting up xorg.conf. The manual here 
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)
is not that user friendly. 

I desperately want to get 9.10 working properly with this if that's possible. Any help would be most welcome.

---

### Post by mamboze on 2010-04-03
OK if the lack of response is any guide, it looks as tho this mx4000 and driver 96 issue on 9.10 may well have no solution.

Anyhow I downloaded Lucid 10.04 beta 1 and installed it and the 96 driver, slight improvement in resolution. I can now get 1024x768, but nothing higher, nowhere near the 1920x1080 needed.

I've run out of ideas on this. I'm been forced, most reluctantly, to use winxp as a, I hope, temporary solution. 
I'm absolutely surprised at the problems I've experienced with nvidia drivers on 9.10 and 10.04. From 7.04 to 9.04 I had no problems with video drivers, but massive seemingly insuperable ones since. This is hardly progress!

I'm at a loss to understand why tho. Do I have to go back and stay with 9.04 to get a usable version of ubuntu for my hardware? Or is editing xorg.conf a possible way out of this problem?

Moderators, if I'm on the wrong forum could you please move this thread. 

Any help much appreciated, I'm desperate

---

### Post by Smokin Whale on 2010-10-12
Try a new driver: [http://www.nvidia.com/object/linux-display-amd64-96.43.18-driver.html](http://www.nvidia.com/object/linux-display-amd64-96.43.18-driver.html)

Otherwise... time to upgrade. Old hardware can't be supported forever. A Geforce FX5200 or above works well with Ubuntu 10.04.  If you can, get something Nvidia PCIe with DX10.

---

### Post by JackDeth on 2010-11-05
I feel your pain. I just got a new 500GB hard drive and went to install Ubuntu 10.10 on it and couldn't get the display to detect properly. Eventually I got it to display ok but cannot get Compiz or other effects to work at all.

Following several online suggestions I tried various drivers in the repository with no go. I tried installing the latest drivers for my MX 4000 from the Nvidia site. Whenever I tried to install the Nvidia 96 drivers or the drivers from their site, upon reboot, it would get taken to a black screen with a text login prompt. It would let me into the GUI.

After hours of working on this, I eventually ran across this page:
[http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/#comment-86227499]("http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/#comment-86227499").

It's not a perfect solution. It's temporary. But it works in getting the display and all available resolutions working. I still, however, cannot use Compiz or similar effects.

All of that worked fine with Ubuntu 9.10 and under. But since 10.04 it will not use my video card correctly. What gives?!?


And no, I don't really think this card is all that old. I cannot upgrade it because all the newer cards after that model require PCIe, which my motherboard doesn't support. I can only use PCI and AGP. My computer isn't ancient by any stretch. It's a 2Gz AMD with 2GB of memory. It's more than adequate to support the effects as it did with 9.10. And no, I cannot afford a new motherboard or new computer, much less a new video card.

What gives? Were there changes in the kernel that did this?

:mad:

---

### Post by sandwormblues on 2011-02-03
mx-4000 is still being manufactured and sold in the U.S. and other countries.  NVIDIA at least is trying to support Linux.  Ubuntu used to support this card and now it doesn't, which means ubuntu has lost functionality--plain and simple.

This card is going to be used for a television broadcast, so i need a stable and reliable nvidia 96xx driver (ideally with compiz support).  if i can't get this card working in 10.04 then it's looking like karmic is the best option, which is a bit of a shame.

---

### Post by cascade9 on 2011-02-03
> **sandwormblues said:**
> mx-4000 is still being manufactured and sold in the U.S. and other countries.  NVIDIA at least is trying to support Linux.  Ubuntu used to support this card and now it doesn't, which means ubuntu has lost functionality--plain and simple.

This card is going to be used for a television broadcast, so i need a stable and reliable nvidia 96xx driver (ideally with compiz support).  if i can't get this card working in 10.04 then it's looking like karmic is the best option, which is a bit of a shame.

They havent made MX-4000s for years now. All the MX-4000 on sale are old stock. 

It is possible to get the 96.xx drivers going with 10.10 (and 10.04 as well AFAIK). I've seen this come up recently, I really wish that canonical would fix jockey so that it gets the drivers..... 

You can manually install the newest 96.xx drivers from the nvidia site, or use the PPA here with 10.10, (possibly with 10.04 as well)- 

[https://launchpad.net/~dajhorn/+archive/nvidia-96/]("https://launchpad.net/%7Edajhorn/+archive/nvidia-96/")

I havent used it, I found the PPA on this thread- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10068387](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10068387)

I got confirmation that at least one of those methods works with 10.10 recently- 

[http://www.uluga.ubuntuforums.org/showthread.php?p=10419233](http://www.uluga.ubuntuforums.org/showthread.php?p=10419233)

As for why the 96.xx drivers didnt work in the 1st place, its beause ubuntu pushed xorg to a newer version than was supported by the 96.xx drivers avaible at that time. Sooner or later nvidia will just cut current xorg support for the 96.xx drivers, the same as they have with 71.xx (yes, new versions of 71.xx come out but they wont support the newer versions of xorg). 

nVidia supports linux when it suits them....see "Optimus".

---

### Post by bill 974 on 2011-02-03
The above mentioned link [https://launchpad.net/~dajhorn/+archive/nvidia-96/]("https://launchpad.net/%7Edajhorn/+archive/nvidia-96/") worked great for me. It finished all my problems with GeForce MX-4000 card. Now compiz is working great!

---

### Post by AgentZ86 on 2011-07-19
> **bill 974 said:**
> The above mentioned link [https://launchpad.net/~dajhorn/+archive/nvidia-96/]("https://launchpad.net/%7Edajhorn/+archive/nvidia-96/") worked great for me. It finished all my problems with GeForce MX-4000 card. Now compiz is working great!

I'm not sure what I'm suppose to do with this.

I have a fresh install of 11.04 64bit and the MX4000 card; and the only option I get is to install the experimental driver.

Are you saying to add the PPA repository again or NO or how did you fix up your system ? Please clarify.


Thanks

---

### Post by BicyclerBoy on 2011-07-19
The legacy driver was broken by the Xorg changes..
If you were using *buntu10.04 you may not have had any problems..
nVidia rebuilt it for later Xorg..
[http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html)

This version may not be available in std *buntu distro repositories for natty.
So either search for a ppa with a correct version or install the driver the nVidia way...
Full instructions are contained in the 40+ page readme on the nVidia driver downloads page.
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/README/index.html)

The previously linked ppa is the right version BUT only for maverick..

---

### Post by AgentZ86 on 2011-07-19
> **BicyclerBoy said:**
> The legacy driver was broken by the Xorg changes..
If you were using *buntu10.04 you may not have had any problems..
nVidia rebuilt it for later Xorg..
[http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html)

This version may not be available in std *buntu distro repositories for natty.
So either search for a ppa with a correct version or install the driver the nVidia way...
Full instructions are contained in the 40+ page readme on the nVidia driver downloads page.
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.19/README/index.html)

The previously linked ppa is the right version BUT only for maverick..


UGGG! well I could probably work through it but I don't want to deal with this. I think I'll just get a FX5500 cheap card or something to replace this MX4000, seems like a shame cause we only really use it for work station.

My problem may not be related to the currently installed driver either.

The main thing is that it seems like when I open ebay to add images and select basic, then browse to the .gvfs file for my server shares. The buttons and backround of those pages are just white with black texts. So it's very difficult to navigate and select things because the button borders are not there. For example after I select an image file and want to select OK, well the OK button is black text only. No button and no button border or color.

Same with the gnome navigation at the top that shows the file structure.

Just black text on white back. Seems to still work but something is really missing.

When you ctrl+a to select all the image files they are not highlighted so you don't know if they will be added to ebay unless you click OK.

But then the ebay screen where the files would come into the page is white as if it's still showing the gnome screen in white.

I had assumed this was because some of my 3d stuff was not available but now I'm not so sure.

I have the fresh install of 11.04 and not sure if I need to install the Real Java or is icetea default OK, I never usd the icetea cause I had some trouble with it in the past and always installed the java plugin for mozilla etc. and it always worked great.

Have you experienced anything similar and/or do you think this is video related or plugin related ?

I did not install any restricted extras or anything at this point either. Mainly because java and flash seems to be installed in 11.04 by defaults??

Please advise
Thanks

---

### Post by AgentZ86 on 2011-07-19
One last thing, this only seems to occur for adding images when using the website feature of sites that want you to browse to the image files.

Otherwise I can use gnome to browse files and server files just fine.

? :confused:

Same problem with yahoo when adding an attachement, or even facebook browse to images etc. all the same effect. So perhaps this is plugin related.

I wish I could figure this out.

---

### Post by AgentZ86 on 2011-07-19
well i installed the java plugin which was not installed by default even though 11.04 says that java run time and icetea is installed when you go to firefox add ons the java plugin is not there.

Anyhow that did not solve anything, so back to the drawing board.

It would be nice to know if this was video or plugin related topic.

How can I test 3d is working or not ?

---

### Post by AgentZ86 on 2011-07-20
Having trouble turning of gdm (x server) I found lots of commands to do it but it seems to freeze in the middle of running some sort of script and never gives me back to the command prompt.

---

### Post by mc4man on 2011-07-20
You might want to start a thread(s) for issues not in the topic of this thread
As far as 11.04  - there is no nvidia driver 96 available  - you can try installing the mesa3d driver and see if it works
The package is - libgl1-mesa-dri-experimental

As far as a fx5200 card - for 11.04 that would be a very poor choice, 3d support is broken altogether

---

### Post by AgentZ86 on 2011-07-21
> **mc4man said:**
> You might want to start a thread(s) for issues not in the topic of this thread
As far as 11.04  - there is no nvidia driver 96 available  - you can try installing the mesa3d driver and see if it works
The package is - libgl1-mesa-dri-experimental

As far as a fx5200 card - for 11.04 that would be a very poor choice, 3d support is broken altogether

Yep, i'll start a new thread and I'm not so sure it's vid related either.

With exception of the topics I've mentioned regarding the loss of graphics on the screens where you would normally browse to a file etc. The computer is working perfectly as far as I know. This is the thing that is throwing me off. I'm not sure I'm having video trouble due to driver support or if it's a plugin or something else.

Thanks for the help, and FYI I was thinking FX5500 not the fx5200.

But I would want something I can just plugin so maybe FX6200 or something higher might be better.

Problem is with this one desktop we have that machine only has PCI or AGP so I have limits to the type of cards I can get that might be compatible for Ubuntu 11.04. PCIe would mean a whole different computer.

Thanks again

---

### Post by AgentZ86 on 2011-07-21
I can't turn off the x server to install the 96 driver.

I run the driver script but says x server is still running no matter what I do

---

### Post by mc4man on 2011-07-21
I would research any FX5000 series card before purchasing IF you're trying to run natty with unity - 2 relevant bugs

nvidia drivers
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178)

nouveau (mesa 3d drivers
[https://bugs.launchpad.net/unity/+bug/762478](https://bugs.launchpad.net/unity/+bug/762478)

If you are still trying to install the 96 drivers on Natty - they won't work, not compatible with the xserver in natty (1.10.1

---

### Post by duuchung on 2011-07-25
I have been trying to sort out why my ubuntu could not function for the last 2 weeks. It was in a coma and was dying like an old man.I used a Geforce2 MX-400.

My earlier version was 10.04LTS. I downloaded some programme updates. One day suddenly my box started to hang. I did some googling and knew that was a nvidia problem. I searched and tried the advice from the ubuntu forum but to no avail. I decided to upgrade to 10.10.

After upgrading, the situation turned from sour to bitter. I could not even boot into the recovery mode. Luckily there is and was the ubuntu community. I have done a lot of tests.

After inserting /etc/XII/xorg.cnf with the driver for nvidia being "na" with the modes "1080xxx", I could boot into that mode. My ps/2 keyboard was not supported. I had to find a usb keybord. I booted into the login mode. The mouse and keyboard did not move. I read something from the forum saying these device had to be unplugged and plugged again. Finally my ubuntu came back. Now, ever time the box is turned on, the unpluging goes on.

The ordeal did not end. The nightmare lingered. I did not know that the mysql and apache2 were shut down. I could not hooked up into my php based programmes. There were more and more googling and testing. The link to start them on boot were severed upon upgrading. Today I tried to start each of them one by one manually. Bingo. I could get into phpmyadmin 2 hours ago.

Don't give up. There is always hope. It came too late.

---

### Post by AgentZ86 on 2011-07-27
Ok it I purchased a GS8400 PCI nvidia card and the described issue still exists for a fresh install of 11.04 64bit.

Put the card in and Unity was setup at default so this tells me it detected 3D settings etc. 

I activated the nvidia (current) proprietary because the experimental driver that installed by default had the same symptoms.


So in short I would have to say that the fresh install of 11.04 seems to have a problem with something that I cannot diagnose.

Which is that any browser that allows or asks you to  browse to a file is not functional.

Please advise if anyone has similar issues. Cannot post files/images to facebook, cannot attach files to any webmail system.

Cannot add images to craigslist etc.

And all 3D are working so I now suspect plugins ? 

Please advise and thanks to all for the replies

---

### Post by kelvin spratt on 2011-07-27
> **AgentZ86 said:**
> I can't turn off the x server to install the 96 driver.

I run the driver script but says x server is still running no matter what I do
You can do this with the the nvidia drivers without shutting down your desktop if the drivers are in the home folder open up a terminal in your browser
"sudo sh NVIDIA-Linux-<arch>-<version>.run--no-x-check" when installed then reboot

---

### Post by AgentZ86 on 2011-07-27
> **kelvin spratt said:**
> You can do this with the the nvidia drivers without shutting down your desktop if the drivers are in the home folder open up a terminal in your browser
"sudo sh NVIDIA-Linux-<arch>-<version>.run--no-x-check" when installed then reboot

hmm, i'll keep that in mind thanks

I wish I knew that before I purchased the other card, but the new card will have some advantages anyhow. 

Thanks I really need to remember this for my other warehouse machines etc.

---

### Post by duuchung on 2011-07-28
Just 1 or 2 lines in the xorg.conf will save or kill you. I've googled almost all ubuntu forums. I finally stumbled into linusquestions and found the cure. I copy my xorg.conf for your reference. V10.04 and 10.10 create more trouble than fun for everyone. Finally the dust kicked up has fallen. 




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    HorizSync 30-83
    VertRefresh 50-75
EndSection

# add this one
Section "Module"
        Load "glx"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver     "nvidia" 
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    SubSection     "Display"
                   Viewport 0 0
                  #This is the most important View.
                   Depth 24
                   Modes "1280x1024"
   EndSubSection
EndSection

---

### Post by AgentZ86 on 2011-07-28
THanks

---

### Post by duuchung on 2011-08-30
I upgrded to 11.04. The machine hung halfway through. Knoppix could not app-get update and upgrade. I found an old version ubuntu cd for rescue.

v11.04 would not start at all. There was more and more search. The only cure is to get into xorg.conf, take away "nvidia" and use "nouveau" instead.

Hoping that my comrades would esaily get help from this forum.

---

