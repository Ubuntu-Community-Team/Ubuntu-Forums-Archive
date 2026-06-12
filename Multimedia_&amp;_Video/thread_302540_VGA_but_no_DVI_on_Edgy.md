---
title: "VGA but no DVI on Edgy"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by voided3 on 2006-11-18
Hello. I just upgraded to Edgy and my video driver configured and working on my Radeon 9250, but I only get signal out of the VGA port on the card and I use the DVI port since I have an LCD. How should I go about doing this? Thanks!

---

### Post by jkwarras on 2006-11-18
> **voided3 said:**
> Hello. I just upgraded to Edgy and my video driver configured and working on my Radeon 9250, but I only get signal out of the VGA port on the card and I use the DVI port since I have an LCD. How should I go about doing this? Thanks!

Same here. ATI X740XL (medion). DVI doesn't work, only VGA :neutral:

---

### Post by Mr.Vitale on 2006-11-18
Same Here...

I upgraded to the ATI Drivers from their site.. so i guess they are latest, however i am running them under 6.06.

I have a 9250 PCI 265 Pro with a dual monitor setup (one on the VGA which works, the other LCD on the DVI)... and the DVI is not working!!

I was gonna upgrade to Eft over my fall break hoping it might solve my dual(but not dual anymore) monitor issue.

--Alex

---

### Post by epennings on 2006-11-21
I also experienced issues with DVI. My screen turns black when gdm is activated. I tried to shutdown gdm with some key-combo's (CTRL+ALT+Fx, CTRL+ALT+BACKSPACE) to get a commandline but that didn't work either. I have an ATI Radeon 9600 + HP1825 LCD Monitor.

I had similar problems with Dapper, but I could solve it by choosing "safe install" and install the official ATI drivers later. However, when I tried to do the same on Edgy it didn't work. 

My setup is currently working fine because I upgraded from Dapper, but the DVI issue is preventing me from doing a clean install :(

---

### Post by voided3 on 2006-11-24
I see that I'm not alone... any ideas?

---

### Post by SIZABANTU on 2006-11-24
I have a radeon 9550 and it works great i have no DVI problems even thou when i log on it tells me that the mode is not supported, thus i have never installed any drivers for my card just installed ubuntu 6.10 and that was it .Mabe you guys shouldnt worry so much about ATI drivers they only make things wishy washy.Either way good luck!:)

---

### Post by voided3 on 2006-11-24
I'll agree, they aren't the greatest, but the performance with the drivers is much better than without; on 6.06, my computer would lock up with the stock drivers, and on 6.10 i would get 1500fps on glxgears, whereas with the drivers i get about 2095fps. Plus I would have to run an xorg config to get all of my screen resolutions anyway. If there was no performance difference, I would keep the stock drivers but until then, here we are.

---

### Post by SIZABANTU on 2006-11-24
Come to think about it i need drivers ](*,)

---

### Post by SIZABANTU on 2006-11-24
Ok i got the drivers installed every thing works great not and GLX is not as slugish all i did was run $ sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx good luck ;)

---

### Post by voided3 on 2006-11-28
Well, this is half possible solution, and half bump since no one else has posted a possible solution. I noticed that under device manager, my AGP 9250 card is recognized as two separate cards, one listed as "RV280 [Radeon 9200 PRO]" and the other as "RV280 [Radeon 9200 PRO] (Secondary)". When you look under the advanced tab, the list is exactly the same except the (Secondary) lacks the "info.linux.driver      strlist  fglrx_pci" item on the list, so it seems we need to install the driver for both "halves" of the video card, assuming the secondary out is the DVI. I know in Windows, if you have a single monitor connected on either the DVI or VGA out, it makes that the primary, which I suppose this driver does not. So, would setting up the secondary output as a mirror image dual monitor setup in xorg make the DVI work? If yes, how do we do it? Thanks!

---

### Post by epennings on 2006-11-29
I managed to find a workaround for my problem.  

First install Edgy in text mode from the alternative cd
Then start Ubuntu in recovery mode. 

You have to change your xorg.conf to use the vesa driver instead of the default ati driver. The vesa driver is very slow, but it is compatible with (almost) every video card. 

You can change it manually in a text editor :
```
vim /etc/X11/xorg.conf
```
Under section [COLOR="Red"]"Device"[/COLOR] replace [COLOR="Red"]Driver "ati"[/COLOR] with [COLOR="Red"]Driver "vesa"[/COLOR]
Save ([COLOR="Red"]:w[/COLOR]) and quit ([COLOR="Red"]:q[/COLOR]).

Alternatively you can also type this :cool:  
```
sed 's/"ati"/"vesa"/' /etc/X11/xorg.conf > tmp && mv tmp /etc/X11/xorg.conf
``` 

Restart your computer in normal mode
```
shutdown -r now
```

You should be able to load Edgy in graphical mode now.
Install the fglrx driver using [[COLOR="RoyalBlue"]this guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Hope this helps :D

(btw my graphics card has a primary (1:0:0) and secondary (1:0:1) bus too. my xorg.conf uses the primary bus and DVI works fine.)

---

### Post by fvgm on 2007-01-07
hi guys, sorry for my english..
i also have **radeon 9250** and DVI output don´t work with Edgy, but in Dapper everything runs Ok (both using fglrx.)

It is occurs because in dapper, the fglrx version is 8.24.8. On edgy, the fglrx version is newer, they are removing our old ATI cards from support... The new version of fglrx does not support our old ATI cards.

The solution, for me is use the OpenSource "radeon" driver...
just change in xorg.conf, in Device section, the "fglrx" by "radeon"...

however, "radeon" driver has half of "fglrx" performance runing "glxgears -printfps"

---

### Post by madcow72 on 2007-01-08
Hey there!  I just bought a secondary 19" LG Flatron DVI Monitor to replace an older 15" Dell LCD VGA monitor on a dual head system.  I'm using an ATI Radeon 9250 video card with the ATI 8.28.8 Driver.  As you all know, I have now run into the same problems that all of you are having.  However, I did notice something interesting, because the first time I plugged the new monitor in I used a DVI->VGA converter (new monitor will take both DVI and VGA inputs) and my old Big Desktop configuration was working out of the box.  I wanted to do a dpkg-reconfigure xserver-xorg  and reinstall the driver to correct any settings for my new monitor and also change to the DVI connection - which is when I've started having my problems.

Since then I've realized that I can still keep my dual head system with the ATI driver installed, as long as I convert DVI->VGA and use the analog connection on the monitor.  Stupid, but it works for now.  More on that if I can figure anything else out.

On the other hand, after months of headache and instability of using ATI cards, I plan on switching to an NVidia at the earliest convenience and never coming back.

---

### Post by Aidan1234 on 2007-01-08
Don't be so fast to switch to nvidia.

every time i boot edgy from the time i installed it, i get the same problem.

After the login screen, the monitor turns the shade of orange that it should, but then these weird lines appear on screen. Like little smidgens of what should be there. Also, no task bars. Just this screen.

It happens w/ both nVidia and ATI.

(btw, both ports of my graphics card are digital.)

---

### Post by madcow72 on 2007-01-09
It doesn't really make sense to me yet, but I realized that using the digital port from the graphics card out and using the DVI->VGA converter gives me no problems with the monitors.  It's a quick fix and not really the greatest, but it seems to work as long as your monitors can also accept VGA input as well as DVI.  Using the radeon drivers as suggested by epennings above did not work for my card (yet).  I've worked on the mergedfb to get both monitors running for dual-head display.  I don't get any errors, but all I seem to get is mirroring.

I did find [[COLOR="Blue"]this very interesting howto[/COLOR]]("http://ozlabs.org/~jk/docs/mergefb/") about our problem where the author is using a DVI output of a laptop for dual-head, but alas, I couldn't get it to work either.  The problem may be in my lack of understanding of xrandr or something.  Let me know if this works for anyone else!

---

### Post by charwhee on 2007-02-05
I am having the same problem. I installed 6.10 (x64) on my system and upgraded to the latest proprietary ATI drivers (x.33). Graphics works fine over vga but not over DVI. tselliot has a post on a different forum saying to add another option in the 'Device' secition, which I did, but it didn't work. This seems bizarre. I mean, I can do Ctrl-Alt-F1 and get the command-line, so the connection between the computer and monitor is fine. It's when X tries to start that things get wiggy. Is there a setting for a DVI connection that we are missing? I feel like such a dolt, but I haven't found anything out there that addresses this problem.

---

### Post by jkwarras on 2007-02-18
AFAIK, disabling vga=xxx option in menu.lst will disable the framebuffer and make DVI works for fglrx driver. BUT switching between users as well as switch to console doesn't work and will hang your PC.

---

### Post by guyg on 2007-02-20
I am running Edgy, and my card is ATI Firegl Mobility T2 (= radeon 9600). When I use the open source 'radeon' driver, VGA output works but DVI doesn't. When I switch to the 'fglrx' driver, DVI works.

This is also consistent with cat /proc/acpi/ibm/video which shows "dvi: enabled" for fglrx and "dvi: disabled" for the radeon driver. Doing 'echo dvi_enable > /proc/acpi/ibm/video' has no effect.

So, at least for me, this seems like a bug in the driver. I'll post a bug for this.

---

### Post by mwolfe on 2007-02-25
> I am having the same problem. I installed 6.10 (x64) on my system and upgraded to the latest proprietary ATI drivers (x.33). Graphics works fine over vga but not over DVI. tselliot has a post on a different forum saying to add another option in the 'Device' secition, which I did, but it didn't work. This seems bizarre. I mean, I can do Ctrl-Alt-F1 and get the command-line, so the connection between the computer and monitor is fine. It's when X tries to start that things get wiggy. Is there a setting for a DVI connection that we are missing? I feel like such a dolt, but I haven't found anything out there that addresses this problem.

I have this same problem. I had the ubuntu release installed for the ati fglrx driver, then i installed the newest version that must be installed manually, and now when i boot the computer, when gdm starts i get no signal message. I'll have to figure out how to revert back to the other driver.. I really want a graphics card (driver) that works better than this..

---

### Post by madcow72 on 2007-04-11
Coming back to this thread after a long while.  I no longer use any ATI cards and my life is way better with NVidia.  However, for anyone else running into this problem, I noticed [this page]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI") in the Ubuntu help community about this DVI issue.

---

### Post by hotani on 2007-04-19
I'm using feisty and tried adding this card with no success. Turns out the on-board intel chip performs better than the radeon! This is at work, so I had no choice but to use what they gave me. The intention was to get a dual head setup going, but it's proving to be more trouble than it's worth. 

I tried recompiling the driver per the howto posted above, but couldn't get past the second step because it wasn't available for some reason.

Still no DVI support for this card in Feisty, sorry to say. :( And judging by the performance when only one monitor is connected and using desktop-effects, I'm guessing a dual head setup would be rather painful.

---

### Post by jkwarras on 2007-04-22
In feisty, I still can't plug DVI with the fglrx driver. I get a 'no signal' message from the monitor.

---

### Post by mwolfe on 2007-04-22
Here is how i fixed that problem,
remove fglrx and use the default driver. I  dont do much gaming but i can now run aiglx with beryl and it runs really good.. well actually i have to switch to metacity when i want to watch a movie because the video part sometimes doesnt work right. But i get good performance in everything else... I dont know how it does with games but honestly it seems fine for everything else. Honestly, my system seems much more stable though without fglrx.  This probably isnt the answer your looking for, but its made me happy so far.

---

### Post by jkwarras on 2007-04-24
The problem is that I need TV-Out, and the open source driver doesn't support it. I've installed the GATOS patch to enable it but it doesn't work. So I have to stick to fglrx until this change.

---

### Post by Kythas on 2007-10-03
I encountered this same issue. However, when my screen turned black and I got the "No Signal" message from my monitor, I hit CTRL-ALT-F1 and got the command prompt.

I then browsed to the /etc/X11 directory and did "sudo rm xorg.conf".

Rebooted and the DVI now works like a charm. While I can't install beryl/compiz because of the lack of the xorg.conf file, I consider that a small price to pay at this point.

---

