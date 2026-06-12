---
title: "Premidia2 and the SPARC iso install"
date: 2006-05-03
forum: Multimedia &amp; Video
---

### Post by vikrant on 2006-05-03
I was getting sick of Solaris 10, and saw that Dapper had a SPARC install.  So, I figured what the heck.  I had a few problems with the partitions acting up at first, but once I got that setup correctly the install went very well.  

Once the install was completed,  The xorg failed to start up.  I used the glint driver during the install, because I believe the card is a 3D Labs Premidia2.  First thing I do need to do is verify that 100%. (i am 99%)

I am a dabbler when it comes to Linux.  I do have a few machines with it installed, but when the install errors and comes to troubleshooting hardware in the environment I can get turned around.  Where does one I start?

I know there are logs, and a couple .conf out there.  I think in the X11 directory and the xorg???  I am happy with the command line, but I like a challenge and I think the video is going to be the next one I try and tackle. 

Any suggestions guys and gals?

Thanks in Advanced, 
-Vik

---

### Post by christhemonkey on 2006-05-03
The config file for the X server is /etc/X11/xorg.conf
The log file is /var/log/Xorg.0.log
Hope that helps!

---

### Post by vikrant on 2006-05-03
Thanks Chris, 

     I'll mess around with things tonight.  I did see this post from netztier ([http://www.ubuntuforums.org/showpost.php?p=955542)](http://www.ubuntuforums.org/showpost.php?p=955542)).  What does the "cfb" and the "cfb32" modules do?  I can not read german.  :P

-Vik

---

### Post by christhemonkey on 2006-05-03
Well, honestly i dont know,
had a quick google around for it and it is one of three things:


Canadian Forces Base: unlikely....

Composite Fractal Behavior: something to do with market analysis, so also unlikely

OR
Some sort of Xfree86 framebuffer device, a driver for displaying graphics.
(deduced from [here]("http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/cfb/") and [here]("http://lists.debian.org/debian-powerpc/1999/01/msg00081.html"))

Where the 32 just stands for 32 bit compatibiliy (i think).

---

### Post by vikrant on 2006-05-03
HAHAHA...  Personally I like Composite Fractal Behavior.  It just sounds cooler. 

In looking up information on cfb modules it looks like it is assoicated with the ffbsun driver, but I could be wrong.

Once I get home I will check out the log file and post it if I can not find any information on the error.  

Thanks again, 
-Vik

---

### Post by vikrant on 2006-05-03
OK... I have verified that the video card is a 3Dlabs Permedia 2 Graphics Processor.  

Here is the link to the video card [http://www.techsource.com/products/datasheets/gfx8p.htm](http://www.techsource.com/products/datasheets/gfx8p.htm)

However, from what I can gather from the X.org website about the error in the logs is that I am not using the correct driver or the chipset is not supported.  

I am getting the error below:  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(EE) No devices detected.

Fatal server error:
no screens found
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From the X.org website it said you could try the vesa driver or the vga.  It's worth a shot.  I'll post back on how it goes.  Anyone out there using this card in their Ultra 5, 10, 40, or 60's?

-Vik

---

### Post by vikrant on 2006-05-03
Well, I am having no luck.  I have read [here]("https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001928.html")  about the troubles with this card and a couple other posts.  None of which really pointed me in the right direction or I overlooked something.  I have tried to edit the Xorg.conf file with the vesa and vga driver.  Just for kicks I added the "cfb" and the "cfb32" modules with the sunffb driver.  Same results.

I do see the Ubuntu loading screen at the startup, but shortly after X bombs out with the "no screens found" error.  I have attached the current conf and log files to this post.  I am not real sure what to try next.  Any suggestions out there?   

Thanks, 
-Vik

---

### Post by christhemonkey on 2006-05-04
Well at that adress the person said they had found a solution;
[https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001932.html](https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001932.html)

Though i am unsure of whether this will help at all, duing to it being quite old (2003)


Later on, it mentions what drivers to use for what card;

[https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001935.html](https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001935.html)

> PGX24      works      4.2 (r128)
So maybe try r128 driver?

Lol, im running out of ideas....
Your Xserver and log dont seem to detail very much about why it fails.
My only thought is that maybe the vesa driver (the generic one) doesnt support your card.

---

### Post by netztier on 2006-05-04
[QUOTE=vikrant] Once the install was completed,  The xorg failed to start up.  I used the glint driver during the install, because I believe the card is a 3D Labs Premidia2.  First thing I do need to do is verify that 100%. (i am 99%) [/QUOTE]

What SPARC-based workstation are you using? And what is Sun's Name of their video adapter in that box?

If these are Permedia Chips, then maybe they're also on the Creator 3D cards, and finding a more appropriate driver than "sunffb" eventually might speed up graphics performance on my Ultra 60s too. They're even being dwarfed by the onboard ATI Chip in the Ultra 5 :-¦

regards

Marc

---

### Post by vikrant on 2006-05-04
The specs on the SUN box are the following:

SUN Enterprise 250
1 gig of RAM
2 x 18.1 Gig HD's 

From what I can tell the SUN equivalent of the Video card is a Sun PGX32.

I must have over looked that post about the r128 driver.  I'll try that one once I get home tonight.  I was wondering the same thing about the 2003 date on that thread. :)

Thanks for all the help guys.  I might just mess around with this if things quite down at work.  shhh  Don't tell anyone.  LOL 

-Vik

---

### Post by netztier on 2006-05-04
[QUOTE=vikrant]
From your xorg.conf

Section "Device"
[INDENT]Identifier	"3DLabs Permedia II 2D+3D"
[COLOR="Red"]	Driver		"vga"[/COLOR]
	Option		"UseFBDev"		"true"[/INDENT]
EndSection 
[/QUOTE]

This tells us you are using the vga driver - which most probably won't work. If it really is a Permedia, you should use "permedia" instead of "vga" here, as is suggested by the link christhemonkey had found:
[(https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001935.html)]("https://lists.dulug.duke.edu/pipermail/aurora-sparc-devel/2003-February/001935.html").

If this doesn't help, you might want to try r128 for a PGX24 instead.

regards

Marc

---

### Post by vikrant on 2006-05-04
Yeah,  The VGA driver was where I stopped last night.  I was tring all sorts of drivers in there.  However, I did not try permedia or the r128.  I must have been tired when reading the post I linked to.  I missed it completely.  I will jump on the server and see if either one of them work. 

Thanks Again, 
-Vik

---

### Post by vikrant on 2006-05-04
When trying to load the permedia driver i get this message in the log. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I](II) LoadModule: "permedia"
(WW) Warning, couldn't open module permedia
(II) UnloadModule: "permedia"
(EE) Failed to load module "permedia" (module does not exist, 0)[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And from the 2003 post it says the X version is 3.3.6.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I]GFX8P      works      3.3.6 (permedia)
PGX32      works      3.3.6 (permedia)[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

According to the xorg log I am running the following:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I]X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-21-sparc64 sparc[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How would one go about loading the old permedia module?  or would I have to load the old version of XFree86 first?  (I am very lacking in this area please be gentle).  :)

I am also confused about xorg-server and the XFree86.  Are these two related?  In the 2003 post, they are talking about the versions of XFree86 4.x and the 3.3.6.  Does anyone have a good explaination on how these work so I can get these straight in my head?

Thanks, 
-Vik

---

### Post by vikrant on 2006-05-04
The r128 driver does load, however I still get the no screen found error. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I](II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 4.0.4
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I](EE) No devices detected.

Fatal server error:
no screens found[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The r128 is an ATI driver I take it.  There is a TON of cards that it is trying in the log.  Rage 128 chipsets, and Radeon chipsets.  

-Vik

---

### Post by vikrant on 2006-05-04
Here is the directory listing for /usr/lib/xorg/modules/drivers.  This is were the modules for the drivers are stored right?  Anything here should be found by X correct?

-Vik

apm_drv.so
ark_drv.so
ati_drv.so
atimisc_drv.so
chips_drv.so
cirrus_alpine.so
cirrus_drv.so
cirrus_laguna.so
dummy_drv.so
fbdev_drv.so
glint_drv.so
i128_drv.so
i740_drv.so
imstt_drv.so
mga_drv.so
neomagic_drv.so
newport_drv.so
nv_drv.so
r128_drv.so
radeon_drv.so
rendition_drv.so
riva128.so
s3virge_drv.so
savage_drv.so
siliconmotion_drv.so
sunbw2_drv.so
suncg14_drv.so
suncg3_drv.so
suncg6_drv.so
sunffb_drv.so
sunleo_drv.so
suntcx_drv.so
tdfx_drv.so
tga_drv.so
trident_drv.so
v4l_drv.so
vesa_drv.so
vga_drv.so

---

### Post by vikrant on 2006-05-04
Well, according to this [web page]("http://www.xfree86.org/4.0.3/glint.4.html#toc4"), I should be using the glint drivers.  I am going to try and set these commands and see what happens. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I]The driver auto-detects the chipset type, but the following ChipSet names may optionally be specified in the config file "Device" section, and will override the auto-detection:

    "ti_pm2", "ti_pm", "pm3", "pm2v", "pm2", "pm", "500tx", "mx", "gamma". 

The driver will try to auto-detect the amount of video memory present for all chips. If it's not detected correctly, the actual amount of video memory should be specified with a VideoRam entry in the config file "Device" section.

Additionally, you may need to specify the bus ID of your card with a BusID entry in the config file "Device" section, especially with FBDev support.[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So my Device section of xorg.conf will look like this.  Anything incorrect with my changes?  I am not sure how to set 8 megs for the VideoRam setting. 

~~~~~~~~~~~~~~~~~~~~~
[I]Section "Device"
  Identifier "devname"
  Driver "glint"
  Option "Chipset" "pm2" 
  Option "UseFBDev" "true"
  Option "BusID" "128:0:0"
  Option "VideoRAM" "8"
EndSection[/I]
~~~~~~~~~~~~~~~~~~~~~

Does the BusID look crazy to anyone else besides me?  When I run a Xorg -scanpci command I get the following in the xorg.0.log. 

~~~~~~~~~~~~~~~~~~~~~
[I](II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "scanpci"
(II) Loading /usr/lib/xorg/modules/libscanpci.so
(II) Module scanpci: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 80:00:0: chip 108e,8000 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: End of PCI scan
Probing for PCI devices (Bus:Device:Function)

(128:0:0) Sun Microsystems Computer Corp. Psycho PCI Bus Module[/I]
~~~~~~~~~~~~~~~~~~~~~


Thanks, 
- Vik

---

### Post by netztier on 2006-05-04
[QUOTE=vikrant]
~~~~~~~~~~~~~~~~~~~~~
[I]Section "Device"
  Identifier "devname"
  Driver "glint"
  Option "Chipset" "pm2" 
  Option "UseFBDev" "true"
  Option "BusID" "128:0:0"
  Option "VideoRAM" "8"
EndSection[/I]
~~~~~~~~~~~~~~~~~~~~~
[/QUOTE]

Looks reasonable to me.  What are the differences between **ti_pm2** and **pm2**?

> 
Does the BusID look crazy to anyone else besides me?  When I run a Xorg -scanpci command I get the following in the xorg.0.log. 

~~~~~~~~~~~~~~~~~~~~~
[I](II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "scanpci"
(II) Loading /usr/lib/xorg/modules/libscanpci.so
(II) Module scanpci: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 80:00:0: chip 108e,8000 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: End of PCI scan
Probing for PCI devices (Bus:Device:Function)

(128:0:0) Sun Microsystems Computer Corp. Psycho PCI Bus Module[/I]
~~~~~~~~~~~~~~~~~~~~~


Is that actually a UPA or a PCI card? Could it be Linux' way of interpreting
the UPA bus?

kind regards

Marc

---

### Post by vikrant on 2006-05-04
[QUOTE=netztier]Looks reasonable to me.  What are the differences between **ti_pm2** and **pm2**?
[/QUOTE]
From what I have been reading, I think Texas Instraments has a version of this card.  I am going to try the entire lot.  See if I can get a hit with trial and error. 

[QUOTE=netztier]
Is that actually a UPA or a PCI card? Could it be Linux' way of interpreting
the UPA bus?[/QUOTE]

LOL...  To tell you the truth I have no clue.  This is the frist time I have heard of it.  Man, learning all sorts of fun stuff with this problem.  Ultra™ Port Architecture.  I gotta read up on that one. 

Thanks Netz,
-Vik

---

### Post by vikrant on 2006-05-04
It looks like it is a PCI card.  Well....  according to the [webpage]("http://www.techsource.com/products/specifications/gfx8p_spec.htm").

I did see this in the logs though too.  I think the 128:0:0 BusID is not correct.   In reading other posts for PCI the 1st spot should be a zero and for AGP it should be a 1.  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I] PCI: PCI scan (all values are in hex)
(II) PCI: 80:00:0: chip 108e,8000 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) **Bus 128: bridge is at (128:0:0)**, (128,128,128), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 128 I/O range:
	[0] -1	1	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 128 non-prefetchable memory range:
	[0] -1	1	0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Bus 128 prefetchable memory range:
	[0] -1	1	0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Host-to-PCI bridge:
(II) **Bus 0: bridge is at (0:0:0)**, (0,0,0), BCTRL: 0x0008 (VGA_EN is set)[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I really feel like I am chasing my tail right now.  I am not sure what else to try.  The "Option" "Chipset" did not work for any of them when hard set.  Makes me wonder if any of the "Option" values are being looked at, because I still see this line in the log.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I](II) GLINT: driver for 3Dlabs chipsets: gamma, gamma2, ti_pm2, ti_pm, r4,
	pm4, pm3, pm2v, pm2, pm, 300sx, 500tx, mx, delta[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Any suggestions?
-Vik

---

### Post by netztier on 2006-05-05
> (II) GLINT: driver for 3Dlabs chipsets: gamma, gamma2, 
ti_pm2, ti_pm, r4,pm4, pm3, pm2v, pm2, pm, 300sx, 500tx, mx, delta


Can you show us a bit more from Xorg.0.log, please? 

**(II)** says the module/driver/function was properly installed or activated... but where did it fail in the end (look for lines starting with **(EE)**)? Is it still "no screens found"?

Have you tried configuring **glint** as Driver, but without any further Chipset Options? A detailed study of Xorg.0.log might then reveal a few facts about the video card.

oh.. and btw... does the card show up if you do an **lspci**?

regards

Marc

---

### Post by vikrant on 2006-05-05
I'll post everything as an attachment when I get home tonight.  The error has always been "no screens found".  I would LOVE to see a new error at this point.  At least I would feel like I am getting somewhere. :p 

I have not tried the lspci command.  Not sure what it does.  I'll have to look it up.  A little busy at work today to mess around with it.  So, I'll post what I got tonight.

Thanks Marc,
-Vik

---

### Post by christhemonkey on 2006-05-05
```
lspci 
``` 
lists all pci devices the kernel has registered.

(along those lines anyway!)

---

### Post by vikrant on 2006-05-05
OK guys,
     Here are the files with nothing in the "Device" settings but the basics.  Also,  the lspci command gave me more familiar info then the previous PCI command.  I have listed it below.   Very handy command BTW.   


OH yeah...  Who names these things???  Psycho PCI Bus and a Happy Meal Ethernet controler.....    Great stuff!!!!   LOL

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[I]0000:80:00.0 Host bridge: Sun Microsystems Computer Corp. Psycho PCI Bus Module
0001:00:00.0 Host bridge: Sun Microsystems Computer Corp. Psycho PCI Bus Module
0001:00:01.0 Bridge: Sun Microsystems Computer Corp. EBUS (rev 01)
0001:00:01.1 Ethernet controller: Sun Microsystems Computer Corp. Happy Meal (rev 01)
0001:00:02.0 Display controller: 3DLabs Permedia II 2D+3D (rev 01)
0001:00:03.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 14)
0001:00:03.1 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 14)
0001:00:05.0 ATM network controller: FORE Systems Inc ForeRunner PCA-200EPC ATM[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I am going to try and set the BusID again like before and see what happens.  I xorg log does not have any other errors in it besides "No Screens Found".  Hopefully, I get a little further this weekend on this.  

-Vik

---

### Post by vikrant on 2006-05-06
OK..  Just for kicks I installed the debian distro for the SPARC last night.  It uses the XFree86 server, but I figured I might get some insight on what settings work for my box with Xorg.

I think messing around with the video card driver settings is not the problem.  I get a beautiful X window session with Debian.  I think it might have something to do with Modules that are loaded or the fonts.  I say that because I deleted the cyrillic and CID fonts because the directory was not found in the log.  I then got the LOVELY "No Screens found" message.  Maybe that was a fluke.  I will try it again later tonight.  It's yardwork time.....  

In XFree86, it probes the video card at BusID "pci:0:2:0".  So, at least I was correct there. 

-Vik

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	[I]# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
	Load	"xtt"
EndSection[/I]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by christhemonkey on 2006-05-06
So on Debian, when you delete these font directories, it gives you the same error as on ubuntu?

If so, maybe it would be wise to make them on ubuntu...

---

### Post by vikrant on 2006-05-06
I am not 100% sure about that Chris.  That was just what I remember doing to the XFree86.conf file.  I was trying to clean up the warnings in the log file to post it quick.  I am in the process of testing it, but I think it is just a fluke right now.  I have been messing with these stupid config files so much, I am not sure if there was something else I did.  I'll post the results of exactly what I do. 

<think> Now I am trying to break X.....   LOL </think>

-Vik

---

### Post by vikrant on 2006-05-06
OK...  It is NOT the fonts or the modules.  I made the XFree86.conf file look exactly like the Xorg.conf I was useing.  (One at a time of course)  The only other thing I can think of was the changes to the keyboard and mouse settings.  Looks like it is back to the drawing board.  Unless, it is the keyboard and mouse giving X greif.  Well,  off to re-install Dapper.  I think I have gotten all the info I can from the Debian install.  My desktop is filled with .conf and .log files.  HAHAHA

-Vik

---

### Post by vikrant on 2006-05-06
Nothing new here....  damn thing can not find the card and I do not think the BusID "PCI:00:02:00" option is working to set it in the conf file.  Everything keeps coming back to that.  Any suggestions????  Besides going to the Debian distro... :P

Thanks all,
-vik

---

### Post by netztier on 2006-05-09
> Any suggestions???? Besides going to the Debian distro... 

Have you tried bringing the "Modules" and "Monitor" sections als well as the Display subsections in "Screen" in Ubuntu's xorg.conf to the same content as  they are in Debian's XF86Config-4?

I can spot a few differences there, with Debian loading more modules (GLcore, speedo, record), having different values for horizontal and vertical sync in "Monitor" and specifing more detailed screen resolutions.

You'll have guessed - I am reaching my wit's end here. It's almost guesswork now, and long shot at that, but maybe it helps? 

kind regards

Marc

---

### Post by vikrant on 2006-05-09
Yeah,  I have set everything the same as in xorg.conf as the Xfree86-4.  The thing that I notice is that when using the XFree86 the PCI card is probed and found, where the xorg is not finding it by probing.  When you try to hard set the card it does not take it.  I am for a loss as well....   

Thanks Marc, 
-Vik

---

### Post by astonius on 2006-10-16
After some extensive searching I finally came across this post which mirrors my problem exactly.  I have a Sun Enterprise 250 (2x400MHz, 2GB RAM, Raptor PGX32) that is also getting the no screens found error when starting X.  I am using Xorg.  Vikrant, did you or anyone else ever find a solution to this?

---

### Post by linwin on 2007-01-13
> **vikrant said:**
> 
So my Device section of xorg.conf will look like this.  Anything incorrect with my changes?  I am not sure how to set 8 megs for the VideoRam setting. 

~~~~~~~~~~~~~~~~~~~~~
[I]Section "Device"
  Identifier "devname"
  Driver "glint"
  Option "Chipset" "pm2" 
  Option "UseFBDev" "true"
  Option "BusID" "128:0:0"
  Option "VideoRAM" "8"
EndSection[/I]
~~~~~~~~~~~~~~~~~~~~~


If specified, the VideoRam size should be given in kBytes (8192 for 8M) in
Section "Device". Possibly the autodetection did not work for this option.
 
I had similar problems with an ELSA WINNER 2000 Permedia 2 at a PC with
UBUNTU edgy erft. For the ELSA WINNER 2000 with 4M RAM, resolution of 1280x1024
works without display refresh errors after manually inserting ChipSet and VideoRam
options in /etc/X11/xorg.conf:

```
Section "Device"
  Identifier "Texas Instruments TVP4020 [Permedia 2]"
  Driver "glint"
  BusID "PCI:0:11:0"
  ChipSet "pm2" 
  VideoRam 4096
EndSection
```

Kind Regards,
LinWin

---

### Post by uatu on 2007-03-26
I have a Elsa Winner 2000/Office  with 8MB and had the same problem. Specifiyng the RAM in KB (8000) worked fine.

But now I want to connect it to a TV (this card has video in and out), but the video signal doesn't work. Do you have any advice on this issue?

---

### Post by vikrant on 2007-07-11
> **astonius said:**
>  Vikrant, did you or anyone else ever find a solution to this?


No I did not astonius.  I pretty much given up on getting X working on my E250.  I noticed that Feisty came out and perusing the forums it sparked a renewed instrest.  I am looking at the posts with the multiple PCI "domains" in the server.  

Time to start messing around with X again.  I'll let you know if I figure anything out. 

-Vik

---

