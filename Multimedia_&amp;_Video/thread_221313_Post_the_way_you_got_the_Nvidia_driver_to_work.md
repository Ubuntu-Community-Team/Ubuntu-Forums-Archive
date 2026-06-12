---
title: "Post the way you got the Nvidia driver to work"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by tseliot on 2006-07-22
The owners of an Nvidia card can post here the model (and the identifier) of their card and the tweakings they had to use in order to get it to work with the Nvidia proprietary driver. 

All the data in this thread can be accessed by other users who will save much time by looking at the solutions available here for their cards.

There is another reason to do that: I am studying Python in my spare time and I hope to start a new project (Envy 2) which should have the following features:
* Installation of the Nvidia driver
* A userfriendly GUI 
* **Automatic configuration of the graphic card  on the basis of the solutions posted on the thread I would like to start)**

[B][COLOR="Red"]What this thread IS NOT:
*a place for requesting support
*a place for asking about Envy 2 (I will make a new page for that)[/COLOR][/B]



If you are interested to help other owners of Nvidia cards please, follow this form:

**1) Post the output of this command:**
```
lspci -n | grep 0300
```

**2) Post the model of your card (if you do not know its name just post the output of "lspci | grep VGA" )**

[B]3) Post the tweakings required to get your card to work.
[/B]
For example you can say:
"I needed to get to the Section Device of my xorg.conf and add the following option:"
```
Option "RenderAccel" "True"
```

Or, if you nothing is needed for your card to work properly you can write:
No tweaking needed.



I will start posting about my card thus providing you an example:

1) 0000:01:00.0 0300: 10de:0326 (rev a1)

2) Nvidia Fx 5500 128MB

3) No tweaking needed

---

### Post by encompass on 2006-07-23
1) 0000:02:07.0 0300: 10de:0322 (rev a1)
2) nVidia Corporation NV34 [GeForce FX 5200] (PRO/660 TV/DVI Gainward FX Powerpack 128 MB PCI)
3) Needs no tweaking.
To save space... should we avoid signitures?

---

### Post by tseliot on 2006-07-23
> **encompass said:**
> To save space... should we avoid signitures?
There's no need to remove your signatures. 

Thanks for asking.

---

### Post by Sagotis on 2006-07-23
1. 0000:01:00.0 0300: 10de:0322 (rev a1)
2. NVIDIA Corporation NV34 [GeForce FX 5200] 256 meg
3. No Tweaks Needed

---

### Post by Indras on 2006-07-23
1. 0000:01:00.0 0300: 10de:0311 (rev a1)
2. NVIDIA Corporation NV31 Geforce FX 5600 Ultra 128Mb
3. No tweaks needed

---

### Post by BuffaloX on 2006-07-24
Nvidea Geforce 7600 gt 256 MB
Installed with easy ubuntu,
No tweaks required

---

### Post by m83 on 2006-07-24
1. 0000:02:00.0 0300: 10de:0181 (rev a4)
2. GeForce4 MX 440 AGP 8x
3. No tweaking needed. Followed the instructions from [http://ubuntuguide.org]("http://ubuntuguide.org").

---

### Post by jreising on 2006-07-24
0000:01:00.0 0300: 10de:0221 (rev a1)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

Made following additions to xorg.conf:

	Driver "nvidia" 
	BusID "PCI:1:0:0" 
	Option "NvAGP" "0" 
	Option "RenderAccel" "Off" 
	Option "IgnoreDisplayDevices" "DFP,TV" 
	Option "NoRenderExtension" "Off" 
	Option "AllowGLXWithComposite" "Off" 

After weeks of struggling with random hangs these changes seem to have solved the problem (12 hours up and running, google earth %100 hard hang gone!)

These settings are suggested in the nvidia HOWTO, but as a solution to the Xserver hangs.  It also solved my complete system hang.  Thanks!

---

### Post by TwistesdTexan on 2006-07-24
0000:01:00.0 0300: 10de:0326 (rev a1)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
Not tweaking made
Runnning 386 Dapper

---

### Post by cracker on 2006-07-25
0000:01:00.0 0300: 10de:00f2 (rev a2)

Card is a Chaintech GeForce 6600 256MB AGP 8x.
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

Installed nvidia-glx in Synaptic and changed driver from "nv" to "nvidia" in xorg.conf, no additional tweaking required.

---

### Post by Shay Stephens on 2006-07-25
I have an nvidia 6600.  I did the following:

```
sudo apt-get -y install nvidia-glx
sudo nvidia-glx-config enable
```

I'm not at my computer at the moment, so I will post the other info later.

---

### Post by sabredog on 2006-07-25
I let Automatix install the Nvidia drivers for my 128Mb GforceFX 5200. 

Everything works a treat.

---

### Post by TheRingmaster on 2006-07-25
1) 0000:01:00.0 0300: 10de:0113 (rev b2)

2) Quadro2 MXR/EX/GO

3) No tweaking needed (automatrix automatically set this up for me)

---

### Post by zxee on 2006-07-26
Note: This is with edgy eft knot1 alternate cd install

01:00.0 0300: 10de:0326 (rev a1)

Nvidia FX 5500 128MB

installed nvidia-glx with apt changed driver in xorg.conf to "nvidia"

---

### Post by inkapyrite on 2006-08-01
using 6.06 ubuntu64-bit.

1. 0000:03:00.0 0300: 10de:0290 (rev a1)
2. pixelView nvidia 7900 GTX

3. How i did it:

i) Installed nvidia-glx in Synaptic and changed driver from "nv" to
"nvidia" in xorg.conf.

ii) i had a 20" viewsonic vx2025wm LCD, and restarting Xserver with the
new drivers gave an 'out of range' for 1680x1050 error.

Problem was that the nvidia drivers were using a refresh rate fvert of
75.1Hz and the LCD couldn't handle it.

Long answer: nvidia drivers had the --use-edid-freq option enabled. This
options allow the drivers to query the monitor for the working refresh
rate range. My LCD can handle 75Hz at lower resolutions, but
unfortunately not at max resolution of 1680x1050. To make it work at
1680x1050 i had to set the refresh rate to ~60Hz.

This is how i solved the problem:
  1. got into xorg.conf and the added HorizSync & VertRefresh lines the
following snippet:

Section "Monitor"
    Identifier     "VX2025wm"
    HorizSync       60.0 - 70.0
    VertRefresh     60.0 - 70.0
    Option         "DPMS"
EndSection


  2. just doing that is not enough, because --use-edid-freq (when
enabled) will override whatever you put in for your VertRefresh &
HorizSync. So i disabled it by adding an extra option in the following
snippet:

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "VX2025wm"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"   # <--------- this!
    SubSection     "Display"
        Depth       1
etc..

  3. startx

Sorry for the long rant about the monitor issue (not strictly nvidia
driver problems per se :), but i thought it would be appropriate & might
save somebody's time. fyi, glxgears racks up 19500+ fps. I'm very
impressed with ubuntu. Seriously the linux distro with the least painful
installation out there! :)

---

### Post by mighty_myte on 2006-08-01
0000:01:00.0 0300: 10de:0150 (rev a4)

GeForce2 Pro

No tweaks needed. 1600 x 1200 @ 85 hz, wasn't possible in windows xp. :D

---

### Post by blitzd on 2006-08-01
1) 0000:01:00.0 0300: 10de:01dc (rev a1)
2) 0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01dc (rev a1) (It's a Quadro FX 350M)
3) No tweaks for the card, automatix did it all

As a side note, I did have issues getting my 2005FPW 20.1" widescreen set up nicely. I happened to install SLED on a machine that was hooked up to the same monitor and it built a remarkably detailed xorg.conf for me (modelines for every res/refresh rate that my monitor can handle) - I have been using that on any Linux install since. I came across this [package]("http://www.novell.com/products/linuxpackages/server10/i386/sax2-ident.html") which SaX2 uses for identifying cards/monitors just today... There may be some useful data in there for your project. You may also want to check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=224471"), there seems to be a goal in common between your efforts and the discussion there.

---

### Post by BoomerAus on 2006-08-03
Sorry just read that this is not a support thread.

---

### Post by n8hfi on 2006-08-05
1) 0000:01:00.0 0300: 10de:0177 (rev a3)

2) 0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 460 Go] (rev a3)

3) NOTHING I tried could get the "stock" Dapper nVidia driver (version 8762) to work on this machine.  I tried a lot of variations on the xorg.conf, as well as varied methods of installation (e.g. automatix, synaptic).  I tried various ways to configure it (nvidia-xconfig would build xorg.conf with a ATI card in the device section?!) dpkg-reconfigure xserver-xorg would hang the whole machine.  The usual symptom, when it didn't just hang the whole machine, was that the X log indicated that the nvidia driver couldn't find the GPU and quit.  Once I was able to recover an X log after a hang and the nvidia driver had apparently loaded, but no error message made it to the log.

Note that I had no problem at all with the non-accelerated nv driver, so I'm sure that the xorg.conf was parsing correctly, &c.  I have also had the same kernel version and nvidia driver version work fine on other chipsets, so I don't think it's a version mismatch problem.  But just changing
```
Driver "nv"
```
to```

Driver "nvidia"
```
in the "Device" section of xorg.conf would break it.  If I rebooted, it would just hang up starting X--nothing to do but cycle power and reboot in safe mode.  If I restarted X with ctrl-alt-backspace, it would generally give an error message indicating that the nvidia driver hadn't found the chipset.

What finally worked was:
```
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
*change "nv" to "nvidia" in xorg.conf*
```
Yup, the "legacy" drivers worked just fine.

I now suspect a bug in 8762 wrt this particular chipset, but I don't know how to prove it.

---

### Post by n8hfi on 2006-08-05
1) 0000:01:00.0 0300: 10de:0146 (rev a2)

2) 0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [Geforce Go 6600TE/6200TE] (rev a2)

3) No tweaking.  Automatix did the installation, worked first time.

Marked contrast to my experience with a GeForce4 460 Go, already reported.

---

### Post by zooter on 2006-08-05
I have had problems installing the nvidia driver on dapper.  I've installed the nvidia driver on mandriva and ubuntu breezy just fine, but dapper had some unusual problems.  I have a GeForce4 MX 440 AGP 8x.  On breezy I followed the instructions and it was easy.  On dapper the same instructions weren't enough.  I couldn't change the resolution from 640x480 so I ran xorgconfig (or something like that, I can't remember exactly) and I was able to get more options for resolutions (I use 1024x720).  In the end, I was able to make it work and I have tv-out working (clone).  

I think the problems might be related to the fact that xorg.conf says that I have an ATI card.  I found this out when I was trying to help someone in freenode #ubuntu with similar problems.  This person told me their xorg.conf said it was ATI when nvidia was the card.  I checked my xorg.conf and saw that mine says ATI also.  And this was AFTER I got everything working!  I added a few lines in order to get clone mode for my tv-out and I didn't even notice that it said it was ATI. 

Here are some of the lines from my xorg.conf: 

Section "Device"
    Identifier     "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver         "nvidia"



Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24


I don't know why it says this, but it may be the cause for problems other people are having.  Like I said, my acceleration and tv-out works just fine right now, but I had to run xorgconfig (or similar, as I can't remember exactly which one it was) in the console to get more resolution options.

---

### Post by zooter on 2006-08-05
Actually, I can't remember the exact order of the things i did to get my video working correctly.  I'm trying my best to remember because it was unusual compared to mandriva and breezy.  I would have to reinstall dapper in order to duplicate everything I did and everything that happened and post it here.

At one point I wasn't able to get X to work at all.  I can't remember if this was before or after I installed the nvidia driver.  The person in #ubuntu that I mentioned above was new to linux and was having a similar problem.  At one point, I only had one option for the screen resolution.  If I recall correctly, it was after I ran a command in the console that sets up the display that I was able to have different resolution options.

The instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) were sufficient in breezy but not enough on dapper.  

To sum it all up, in order get my video stuff running the way I wanted it to I had to do a combination of the instructions on the above link and I ran a command similar to 'xorgconfig' that let me manually set up the display through a console.
 
I hope this helps.

---

### Post by zooter on 2006-08-05
1.  0000:01:00.0 0300: 10de:0181 (rev a2)
2. NV18 [GeForce4 MX 440 AGP 8x]
3. combination of instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and running a command similar to 'xorgconfig'

---

### Post by TripleE on 2006-08-05
1) 0000:03:00.0 0300: 10de:01df (rev a1)
2) NVIDIA GeForce 7300 GS (G72) [FONT=Arial, Helvetica, sans-serif]256MB PCI-E x16[/FONT]
3) Needs no tweaking.

---

### Post by BoomerAus on 2006-08-06
Following Inkapyrite's example i got my Viewsonic VX2025wm up and running at 1680x1050@60

xorg.conf

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "VX2025wm"
    HorizSync       60.0 - 70.0
    VertRefresh     60.0 - 70.0
    Option         "DPMS"
    # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
     Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID	    "PCI:1:0:0"
    Option          "RenderAccel"   "true"
    Option          "AllowGLXWithComposite" "true"
    Option          "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option "UseEdidFreqs" "False"
    SubSection     "Display"
    Depth       24
    Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Thanks mate.

8)

---

### Post by aleska on 2006-08-06
1) 0000:01:00.0 0300: 10de:0221 (rev a1)
2) nVidia GeForce 6200 AGP 8x/4x 128MB DDR
3) latest drivers hosed my machine.  PC would totally hang, with no signal even being sent to the monitor.  No command line shell, nothing.  Even though I have no reason to believe I have an Intel integrated graphic card on my mother board, the symptoms sounded closest to that scenario.  So I followed tseliot's instructions on blacklisting at the Ubuntu Document Storage Facility site, article titled [Nvidia Intel Integrated]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated").  Thanks tseliot!  Card is working great now!!!  =D> 
For the full story, I have posted it at blogspot [here]("http://ska-aleska.blogspot.com/2006/08/nvidia-troubles-werent-over.html#links").

---

### Post by ubuntu_demon on 2006-08-07
1) 0000:01:00.0 0300: 10de:0201 (rev a3)
2) nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
3) no tweaking needed. 

The regular way to install the propretiary nvidia driver :
```

$sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname -r`
$sudo nvidia-xconfig

```
and do a reboot

---

### Post by ubuntu_demon on 2006-08-07
1)0000:01:00.0 0300: 10de:002d (rev 15)
2)nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
3)use the legacy driver :

```

$sudo apt-get install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
$sudo nvidia-xconfig

```

and do a reboot

---

### Post by mrazster on 2006-08-08
1.0000:01:00.0 0300: 10de:0141 (rev a2)
2.0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
3.Used latest ones from nvidia.com. No tweakings required...other then the ones used to get composite working in xorg.conf

---

### Post by shoki on 2006-08-09
0000:01:00.0 0300: 10de:0041 (rev a1)

#BFG 6800 OC AGP
NVIDIA Corporation NV40 [GeForce 6800]
#20" Dell Flat screen on DVI Port
    Monitor        "DELL 2001FP"

#Tweak I think I need
    Option         "NvAGP" "0" 
#Tweak I know I need
    Option         "ConnectedMonitor" "DFP"

---

### Post by caserio on 2006-08-09
Hi,

Custom kernel + nvidia drivers from ubuntu repos... In french, guys ! :D  [http://forum.kubuntu-fr.org/viewtopic.php?id=50214](http://forum.kubuntu-fr.org/viewtopic.php?id=50214)

---

### Post by mvoncken on 2006-08-13
sorry posted problem in wrong topic.

---

### Post by ManfredU on 2006-08-16
Adapter: Geforce4 MX Integrated GPU
Monitor: 19" Belinea 10 60 90
Driver: Nvidia 1.0-8762

At first only a resolution of 800x600 was available. 

After adding 

Option "UseEdidFreqs" "False"

to the screen section in xorg.conf 

and 

	HorizSync	30-95
	VertRefresh	50-150

to the monitor section, more modes were available. But the desired mode of 1280x1024 was only available with flickering 60 Hz. :-(
I tried a lot of settings including a custom modeline, which seemed to be completely ignored.
With some settings suddenly only 1024x768 or 1280x1024 were available.

In the end adding 

Option "ModeValidation" "NoEdidMaxPClkCheck"

made 1280x1024 available with 85 Hz and the custom modeline for 75 Hz was used as well.

---

### Post by Marvil on 2006-08-16
1. 0000:03:00.0 0300: 10de:0091 (rev a1)
   0000:08:00.0 0300: 10de:0091 (rev a1)
2. nVidia Corporation GeForce 7800 GTX (rev a1)
   nVidia Corporation GeForce 7800 GTX (rev a1)
3. No Tweaking , but haven't been able to use 1900x1200 on my Screen. Going to tweak a little bit. :-k  will tell you later.

---

### Post by KlausU on 2006-08-17
1. 0000:01:00.0 0300: 10de:0291 (rev a1)
2. Nvidia GeForce 7900 GT
3. none, used Automatix

---

### Post by p0rk on 2006-08-18
1. 0000:01:00.0 0300: 10de:00c0 (rev a2)
2. 6800 GS 256Mb
3. No tweaking needed, although am running twinview :)

---

### Post by tomplast on 2006-08-22
1. 0000:01:00.0 0300: 10de:0332 (rev a1)
2. nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)
3. No tweaking whatsoever :)

---

### Post by r4ik on 2006-08-22
0000:01:00.0 0300: 10de:0185 (rev c1)
NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]
Automatix.

---

### Post by BerlinOliver on 2006-08-23
1) 0000:02:00.0 0300: 10de:0161 (rev a1)
2) nVidia Geforce 6200TC 128MB/DDR
3) no tweating needed

---

### Post by SC_Frank on 2006-08-23
1. 0000:01:00.0 0300: 10de:0048 (rev a1)
2. Nvidia GeForce 6800 XT
3. sudo dpkg-reconfigure xserver-xorg
4. Used Nvidia NOT nv
5. Used framebuffer - 
6. All other settings were set to default during the set-up script.

---

### Post by catanzag on 2006-08-25
1. 0000:01:00.0 0300: 10de:0175 (rev a3)
2. 0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
3. nvidia-glx fully works with kernel-686; tweaked as latest nvidia dapper HOWTO for GeForce4 Go 420 black stripe issues;
note that with default kernel 386 (I don't know why) I cannot use latest nvidia-glx driver (the whole system hangs) and I used nvidia-glx-legacy.

---

### Post by dannyalberici on 2006-08-31
1. 0000:01:00.0 0300: 10de:0150 (rev a3)
2. Hercules (Guillemot) NVidia GeForce 2 GTS 128mb
3. installed nvidia-glx-legacy with synaptic
4. tweaked /etc/X11/xorg.conf as follows:

   under modules section removed the line:
   Load "dri"

   under Section Device replaced the line

   Driver "nv"

   with

   Driver "nvidia"

that's it! no need to download any drivers from nvidia!

---

### Post by CurlyBlue on 2006-09-03
1. 0000:04:00.0 0300: 10de:00cd (rev a2)
2. Nvidia Quadro FX3450 256MB

Got the card up and running eventually but in windows I can run at 2550x1600 (I have a 30" Dell 3007WFP panel) - however in Unbuntu I can only run up to 1920x1440.

I found that every time I chaged the xorg to "nvidia" from "nv" it hung the xsever.

It was only by chance that I got it to work by rebuilding the xserver-xorg and accepting all the defaults.

I am still working on it to get it running at full resolution (2550x1600) and will post once I know how its done.

Curlyblue

---

### Post by ezphilosophy on 2006-09-03
1) 0000:05:00.0 0300: 10de:00c0 (rev a2)
2) NVIDIA GeForce 6800 GS 256 MB
3) No tweaking
Maybe should be noted that "nv" driver does not work with it

---

### Post by domib on 2006-09-03
1: 0000:01:00.0 0300: 10de:0398 (rev a1)

2: GO 7600 (in an HP dv8372ea laptop)

3: none. followed method 1 in the latest nvidia dapper HOWTO

---

### Post by madmorpheus on 2006-09-04
> **cracker said:**
> 0000:01:00.0 0300: 10de:00f2 (rev a2)

Card is a Chaintech GeForce 6600 256MB AGP 8x.
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

Installed nvidia-glx in Synaptic and changed driver from "nv" to "nvidia" in xorg.conf, no additional tweaking required.

Worked liked a charm for me, and I am now loose on Americas Army.  I have a Ti4600 card.

---

### Post by skipf on 2006-09-04
0000:01:00.0 0300: 10de:0250 (rev a2)
 nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a2)
No teaks...

---

### Post by nfs510 on 2006-09-04
1) 0000:01:00.0 0300: 10de:0322 (rev a1)
2) NVIDIA CORPORATION NV34 [GeForce FX 5200]
3) No tweaking

I followed the instructions at link below and got Google earth working
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by tekrei on 2006-09-05
1. 0000:01:00.0 0300: 10de:0141 (rev a2)
2. 0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
3. No tweaking needed

---

### Post by John.Michael.Kane on 2006-09-05
[COLOR="Red"]**Output of lspci -n | grep 0300**[/COLOR]
```
**00:05.0 0300: 10de:0242 (rev a2)**
```

[COLOR="Navy"]**Output of lspci | grep VGA**[/COLOR]
```
**00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)**
```
[COLOR="DarkRed"][B]
Tweakings required to get card to work:[/B][/COLOR] [COLOR="Black"]**None**[/COLOR]

**Method-1 of tseliot guide non off-line version was used to get driver's installed.**

---

### Post by bryanchapman9999 on 2006-09-05
01:00.0 0300: 10de:0171 (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (re                    v a3)
No Tweaks needed - used the envy script to install

---

### Post by rapha on 2006-09-06
1) 0000:00:09.0 0300: 10de:0110 (rev a1)

2) Nvidia GeForce2 MX400

3) No tweaking needed [Edit: *Read: Installation of nvidia-glx with change of nv to nvidia in xorg.conf*]

---

### Post by onioneater36 on 2006-09-07
1) 0000:03:00.0 0300: 10de:0092 (rev a1)
2) eVGA 7800GT (nVidia)
3) Had to edit xorg.conf and change Driver "nv" to Driver "nvidia"

P.S. Was then able to restart system and see nVidia logo prior to Ubuntu login screen for Gnome

P.S.S. Prior to this, Ubuntu would hang about every 10 minutes or anytime using Firefox and Blender 3D would not work at all.  After this, it has been ROCK steady and Blender works great.

---

### Post by nUllSkillZ on 2006-09-08
German Ubuntu V 6.06
I've followed the how to over here:
[Nvidia_Grafikkarten](http://wiki.ubuntuusers.de/Nvidia_Grafikkarten) @ Ubuntuusers.de Wiki

[list]
[*]installation of the Ubuntu package
(in my case the "nvidia-glx" package)
[*]activation
activation with
```

sudo nvidia-glx-config enable

```
in console returned that I may have to edit "/etc/x11/xorg.conf" by hand
[*]manual editing of "/etc/x11/xorg.conf"
changed "nv" to "nvidia" manually in "/etc/x11/xorg.conf"
```

...
Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900 Ultra]"
	Driver		"**nvidia**"
	BusID		"PCI:1:0:0"
EndSection
...

```
[*]solving shutdown problems
to solve shutdown problems I've edited the "/boot/grub/menu.lst" as described in the Wiki
(adding "vga=0x31a" to the splash options)
```

...
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash **vga=0x31a**
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=0x31a**
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
...

```
[/list]

---

### Post by Izuil on 2006-09-10
1: 0000:01:00.0 0300: 10de:0312 (rev a1)

2: 0000:01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1) 

The card was made by Inno3d

3: Used method 1

---

### Post by mbmccormick on 2006-09-10
Nvidia eVGA MX4000, a cheap card I got for like $30.

This one was tough. I had to install Ubuntu by removing my card, and plugging the monitor into the motherboard. (NOTE: I did not try using "safe graphics mode, might be worth your while") Then, I downloaded and installed the driver. (following the nvidia instructions on the ubuntu wiki) Then, I installed the card again, and plugged the monitor into it. After, I booted to terminal via "rescue mode" from grub. I ran the "nvidia-glx-config enable" command. Then, I got a message that told me i needed to run a command to update md5sum of the xorg file, it gave me the command to run and i did. This configured the xorg.conf file. Only somewhat. This didnt work. I got a blue screen when i rebooted. did not get x to start. I booted to rescue mode again. ran "lspci -X" this gave me the PCI address of the card. Which was PCI:1:8:0. Then, using vi, I edited the /etc/X11/xorg.conf file and had to change this value. Rebooted into X and gnome. Problem solved. Feel free to contact me if you need further assistance with this, i've done this too many times. And the one thing I learned: ALWAYS BACKUP A FILE BEFORE YOU MAKE CHANGES TO IT.

---

### Post by sinppet on 2006-09-10
1. 0000:05:00.0 0300: 10de:0091 (rev a1)

2. Leadtek 7800GTX

3. Used Method 1 Offline :D

---

### Post by Arzin Tynon on 2006-09-14
2.6.15-26-386, GeForce2 Pro, PanaSync Pro 5G -display

1) lspci -n | grep 0300
0000:01:00.0 0300: 10de:0150 (rev a4)

2) lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)

3) followed Latest Nvidia Dapper Method 1, had to do a bit extra for the resolution & refresh-rate to 1280x1024@75Hz:
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
sudo dpkg-reconfigure xserver-xorg

UPDATE: My trusty, 10 year old PanaSync leaked out it's magic smoke, and I ended up buying a ViewSonic VX2025wm (20.1" widescreen LCD). No extra drivers needed, I just chose System->Settings->Display Resolution, and it had the display's maximum resolution of 1680x1050 (@60Hz) readily available. That was easy!

---

### Post by tmweber on 2006-09-15
0000:01:00.0 0300: 10de:0322 (rev a1)


0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


Tweaks:  I was using an old Sun monitor with a really poor refresh rate (Only using the monitor until I get the mythtv box up & running.  I had installed with method 1, or something similar to it.  I got problem 16, with sound but no screen.  I had to follow problem 10 and go in and add the EDID option and then add lower refresh rates to the Screen section.  All is working now.

---

### Post by balasarius on 2006-09-16
0000:01:00.0 0300: 10de:0322 (rev a1)

        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        128000
        Option          "NvAGP"                 "0"
        Option          "RenderAccel"           "On"
        Option          "UseFBDev"              "true"
        Option          "NoRenderExtension"     "On"
        Option          "AllowGLXWithComposite" "Off"
        Option          "IgnoreDisplayDevices"  "DFP,TV"

even tho I put all this in I think it may just be a problem with allowing GLX with composite but a working card is a working card so I ain't messing with a thing :D

---

### Post by marioquark on 2006-09-17
1) 0000:01:00.0 0300: 10de:0175 (rev a3)
2) nVidia Corporation NV17 [GeForce4 420 Go]
3) i run envy script (ask tseliot!)
4) then i modified xorg.conf adding
```
Option         "ExactModeTimingsDVI"
Option         "UseEdidDpi" "FALSE"
Option         "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
```
in Screen section
and adding a line in /etc/modprobe.d/option as told in tseliot guide.
yippi!! :D

---

### Post by sc10n on 2006-09-19
Haven't seen my video card up here yet so I thought I would post.

1) 0000:0a:00.0 0300: 10de:00ce (rev a2)
2) nVidia Corporation NV41GL [Quadro FX 1400] (rev a2) (128MB)
3) Card defaulted to 1024x768 So I had to edit xorg.conf and manually add "1280x1024" to the Section "Screen". Also one curious side effect, not sure if it came from envy or ubuntu but in the xorg.conf it sees my video card as 
```
Section "Device"
    Identifier     "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver         "nvidia"

```

When my card is a Nvidia Quadro FX 1400. It doesn't seem to have any effect on the computer though. Everything is working normally (as far as I can tell).

---

### Post by chameleon_789 on 2006-09-23
1) 0000:01:00.0 0300: 10de:00f1 (rev a2)
2) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
3) Followed the guide at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper). Just following that alone crashed X, so I had to add the following to my xorg.conf in recovery mode In Section "Device":
```

Option "NvAGP" "0"

```

---

### Post by lrrr on 2006-09-23
1: 0000:01:00.0 0300: 10de:0281 (rev a1)
2: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]
3: Had to do a couple of different things to make it work. First, got nvidia driver to work by following tseliot's instructions in [http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated), except that I needed:
```
Option "NvAGP" "0"
```
instead of:
```
Option "NvAGP" "1"
```

Then, to make it use both monitors [this video card has two outputs, a DVI and an RGB], I copied the Device, Monitor, and Screen sections as usual. In the first Device section, I needed:
```
Option "UseDisplayDevice" "DFP" # use monitor connected to the DVI output
```
And in the second Device section, I had to uncomment:
```
BusID "PCI:1:0:0"
```
and add:
```
Option "UseDisplayDevice" "CRT" # use monitor connected to the RGB output
```

In short, the BusID setting had to be in the second Device section, but not in the first.

---

### Post by KayoPs on 2006-09-23
0000:01:00.0 0300: 10de:0250 (rev a3)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti4600] (rev a3)

## Added to xorg.conf in Section "Screen"

    Option   "UseEdidFreqs"   "False"
    Option   "ModeValidation" "NoEdidMaxPClkCheck"

#Whitout this, the only res available was 800x600@60Hz.
#Also changed the "HorizSync" and "VertRefresh" acording to my monitor specification.

---

### Post by DennShin on 2006-09-26
I am at work right now but I will post what I know. 

Motherboard: Asus: P4S800X
Video: Nvidia BFGTech 6800 GS OC 8x AGP
No tweaks needed. Used both "Nv" (Automatix) and "Nvidia" (Legacy)

FujiPlus 19"LCD
NEC 15"LCD

Still working on getting duel monitor's to work. 

-Denn

---

### Post by casals on 2006-09-30
(1) lspci -n | grep 0300
0000:01:00.0 0300: 10de:0020 (rev 04)
(2) lspci |grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 0 4)

(3) no tweaks

Used envy to set up the nVidia 7184 legacy driver. Had to install nvidia-xconfig after envy ran, since it wasn't already installed. Ran that. Then 
1. backed up /etc/X11/xorg.conf
2. logout
3. ctrl-alt-F1, then log in
4. sudo -i
5. stop gnome: /etc/init.d/gdm stop
6. sudo dpkg-reconfigure xserver-xorg
      allowed this to auto detect, which it did correctly, then read all its screens, all its guesses were correct
7. restart gnome: /etc/init.d/gdm start

Everything looks good now. 

Praise/congratulations: envy rocks. I tried to install the nvidia driver manually following the directions; after 2 hours of installing missing stuff, gave up, got envy, first told it to uninstall, then told it to install, worked beautifully. Very impressed, Alberto!

Complaint: In all my life I have never had such a hard time getting a video driver set up and working !!!!! :mad:

---

### Post by jasonwstone on 2006-10-03
> **chameleon_789 said:**
> 1) 0000:01:00.0 0300: 10de:00f1 (rev a2)
2) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
3) Followed the guide at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper). Just following that alone crashed X, so I had to add the following to my xorg.conf in recovery mode In Section "Device":
```

Option "NvAGP" "0"

```

0000:05:00.0 0300: 10de:0140 (rev a2)
ME TOO! I don't know what it means but I did the same (except had to find this post first). Is Option "NvAGP" "0" because it's a PCIexpress card instead of AGP?

---

### Post by croc1 on 2006-10-07
0000:04:00.0 0300: 10de:0141 (rev a2)
nVidia Corporation NV43 [GeForce 6600]256MB
No tweaking needed. Followed the instructions from [http://ubuntuguide.org](http://ubuntuguide.org).

---

### Post by kleeman on 2006-10-07
1) 0000:08:00.0 0300: 10de:0294 (rev a1)
2) GeForce 7950 GX2 512M Memory
3) Nasty Hard Lockups with nvidia drivers 8774 and 8762. Works fine with 9625 beta and manual install.

---

### Post by Gamezguy on 2006-10-08
Card: Forsa Nvidia 6600 LE 256mb
Selected Nvidia 6800 (generic) from list and set driver to proprietary, restarted X server and 3D worked like a charm.
Since this driver is a 6800, I don't know if I'm damaging my card from doing this, so could anyone point this out please?

---

### Post by tseliot on 2006-10-08
> **Gamezguy said:**
> Card: Forsa Nvidia 6600 LE 256mb
Selected Nvidia 6800 (generic) from list and set driver to proprietary, restarted X server and 3D worked like a charm.
Since this driver is a 6800, I don't know if I'm damaging my card from doing this, so could anyone point this out please?

This is not a support thread (in which you can ask answers).

The fact that your card is being detected as a 6800 is not a problem and won't damage your card.

---

### Post by zparihar on 2006-10-14
$     lspci :

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro (rev 15)

No tweaking necessary:

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`

$sudo nvidia-xconfig

REBOOT!!!

And it booted in... Edgy-Eft

---

### Post by mozetti on 2006-10-14
1)0000:01:00.0 0300: 10de:0281 (rev a1)
2)GeForce4 Ti4200 AGB 8x (rev a1)
3)No tweaks necessary

---

### Post by priceyza on 2006-10-14
0000:01:00.0 0300: 10de:0161 (rev a1)
nVidia Corporation GeForce 6200 TurboCache
some tweaks needed for dual head display.
When using opengl apps my system can freeze needing a hard reboot. But have seen jreising xorg.conf changes in this thread and he seems have had similar problems to me so i'm going to try them. Hope it works!

---

### Post by Duggeek on 2006-10-20
1: 0000:01:00.0 0300: 10de:0322 (rev a1)

2: nVidia FX 5200 AGP 128MB DDR

3: Like "cracker" (and others, I'm sure) all I did was change the **xorg.conf**; under "Driver", changed "nv" to "nvidia"... logged out, used *[COLOR="DarkRed"]Ctrl+Alt+Bksp[/COLOR]* to restart X. 8) 

[SIZE="4"]ADDENDUM:[/SIZE] 

I, too used the Synaptic update and found difficulties after the **nvidia-glx-config enable** command. The first was the "md5 mismatch" error, but I followed the suggestion in the message first (pasting the command straight from the terminal, I might add.) It appeared to work, but X crashed with the message "No screens found". Curious thing, when I peeked around xorg.conf it seemed to identify an ATI device. (I don't, nor have ever, installed an ATI card on my machine.)

After restoring the original xorg.conf (reverts to original "nv" driver), repeating the **nvidia-glx-config enable** command, *ignoring* the "md5" message and proceeding with the "surgical strike" described above, it worked!

Go fig'.

- Doug

---

### Post by tseliot on 2006-10-20
> **Duggeek said:**
> 1: 0000:01:00.0 0300: 10de:0322 (rev a1)

2: nVidia FX 5200 AGP 128MB DDR

3: Like "cracker" (and others, I'm sure) all I did was change the **xorg.conf**; under "Driver", changed "nv" to "nvidia"... logged out, used *[COLOR="DarkRed"]Ctrl+Alt+Bksp[/COLOR]* to restart X. 8) 

[SIZE="4"]ADDENDUM:[/SIZE] 

I, too used the Synaptic update and found difficulties after the **nvidia-glx-config enable** command. The first was the "md5 mismatch" error, but I followed the suggestion in the message first (pasting the command straight from the terminal, I might add.) It appeared to work, but X crashed with the message "No screens found". Curious thing, when I peeked around xorg.conf it seemed to identify an ATI device. (I don't, nor have ever, installed an ATI card on my machine.)

After restoring the original xorg.conf (reverts to original "nv" driver), repeating the **nvidia-glx-config enable** command, *ignoring* the "md5" message and proceeding with the "surgical strike" described above, it worked!

Go fig'.

- Doug
I think you should use this command instead:
```
sudo nvidia-xconfig
```

---

### Post by Ay Deverrick on 2006-10-22
1: 0000:01:00.0 00f6

2. nVidia 6800GS Super AGP 512 MB DDR3

3.  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) <-- Method 2 on here with the newest drivers.  The old ones do not work.

Also, prior to putting in the card, I had to use the command

```
sudo update-rc.d -f gdm remove
sudo update-rc.d -f firestarter remove
```

in order to prevent it from loading X and Firestarter at boot.  If it loaded X, there would be all these little coloured lines and squares all about the screen.  Firestarter would randomly print output in the shell, ergo for ease of use I had it turned off at boot.  Restore these with 

```
sudo update-rc.d gdm defaults
sudo update-rc.d firestarter defaults
```

when you are finished fully installing the drivers.

Again, only use the 1.0-8XXX as the legacy will not work.

---

### Post by mplexus on 2006-10-24
1) 01:00.0 0300: 10de:0171 (rev a3)

2) Nvidia GeForce4 MX 440 (NV17)

3) In section "Device" of xorg.conf :
Driver "nvidia"
BusID  "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"

   In section "Screen" of xorg.conf:
Option "ExactModeTimingsDVI" "TRUE"
Option "UseEdidDpi" "FALSE"
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

   In /etc/modprobe.d/options :
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1

It works but with no GLX support.
> glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

It also worked ok (no GLX either) with the nv driver.

Resolution was ok with nv and is ok with nvidia too.

(I used nvidia-glx 1.0.8774, on Ubuntu Edgy with plenty of updates)

---

### Post by 504yaj on 2006-10-24
> **Duggeek said:**
> 1: 0000:01:00.0 0300: 10de:0322 (rev a1)

2: nVidia FX 5200 AGP 128MB DDR

3: Like "cracker" (and others, I'm sure) all I did was change the **xorg.conf**; under "Driver", changed "nv" to "nvidia"... logged out, used *[COLOR="DarkRed"]Ctrl+Alt+Bksp[/COLOR]* to restart X. 8) 

[SIZE="4"]ADDENDUM:[/SIZE] 

I, too used the Synaptic update and found difficulties after the **nvidia-glx-config enable** command. The first was the "md5 mismatch" error, but I followed the suggestion in the message first (pasting the command straight from the terminal, I might add.) It appeared to work, but X crashed with the message "No screens found". Curious thing, when I peeked around xorg.conf it seemed to identify an ATI device. (I don't, nor have ever, installed an ATI card on my machine.)

After restoring the original xorg.conf (reverts to original "nv" driver), repeating the **nvidia-glx-config enable** command, *ignoring* the "md5" message and proceeding with the "surgical strike" described above, it worked!

Go fig'.

- Doug

I have the same problem, I just installed dapper drake, installed the latest nvidia-glx, then enabled it (sudo nvidia-glx-config enable)

edited xorg.conf and saw "ATI blah blah" on the device name, what gives? I have a PCI-E GeForce 6600GT, never new ATI produced these mofos too ](*,) :-D 

I tried to restart without editing it and Xserver wont start.

---

### Post by Duggeek on 2006-10-25
> **504yaj said:**
> I have the same problem, I just installed dapper drake, installed the latest nvidia-glx, then enabled it (sudo nvidia-glx-config enable)

edited xorg.conf and saw "ATI blah blah" on the device name, what gives? I have a PCI-E GeForce 6600GT, never new ATI produced these mofos too ](*,) :-D 

I tried to restart without editing it and Xserver wont start.

I think the nvidia coders may have cheated by "borrowing" the ATI xorg.conf sample for their nvidia-glx package. Ya'think? ;) 

I've knocked it about a bit since my last post. I took the advice of [COLOR="DarkRed"]**tseliot**[/COLOR] *(thank you! BTW)* and used the tailored **nvidia-xconfig** tool. Think of it as the "nvidia-glx patch".

It simply does a swap-out of the **xorg.conf** file and places a backup in **/etc/X11**. I can't be sure, but I think it performs a simple test to discover the actual hardware, then generates the appropriate **xorg.conf** settings.

The **xorg.conf.backup** only does you good if you started with a working X config. However, you may find that X comes back after using **nvidia-xconfig**, in which case you can simply throw-out the **xorg.conf.backup** file since it's a bad config anyway.

Best of luck!

---

### Post by wilsonisme on 2006-10-27
I logged into my main account non graphically and started up aptitude. Did a update then upgrade there, fixed all my problems. On next reboot X started up fine. Then I opened synaptic and did a update and upgrade there, took like 3 cycles until there was nothing available. Everything is working perfectly now, no problems at all.

---

### Post by ginkhao on 2006-10-28
ASUS P5RD1-VM motherboard
ASUS GeForce 6600 128Mb

1. Clean Edgy Eft install
2. Installed the following using Synaptic:
dmsetup
linux-restricted-modules-2.6.17-10-386
linux-source (comes with linux-source-2.6.17)
nvidia-glx

reboot, manually edited /etc/X11/xorg.conf and changed "nv" to "nvidia"
reboot again and works fine - checked with 'glxinfo | grep direct'

Note I am a Linux noob so this may not be the best way but it works for me

---

### Post by jem7v on 2006-10-29
1. 01:00.0 0300: 10de:0110 (rev a1)

2. GeForce2 MX (manufactured by Gigabyte)

3.
Dapper: It worked fine with the method 1 instructions here (as long as the driver in my xorg.conf was nvidia instead of the generic nv): [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

Edgy: It broke during the upgrade... Edgy installed the wrong NVidia drivers but the right xorg stuff. I tried every method I could find to get it to work, including several of tseliot's. I installed and uninstalled them several times. Finally I downloaded the legacy driver file from the NVidia site rather than going through Ubuntu's repositories and, after a lot of searching, figured out how to install them. Here's the deal (and I apologize if somebody already wrote this out somewhere, but I haven't found this solution anywhere else yet). Disclaimer! I don't know exactly What some of these steps were doing - I just know that they worked. So use with caution! You should know how to use nano if you want to do it this way; if you don't know how to use nano yet, you should probably learn that before you do this.

Also, you should Probably remove any other drivers you tried to install through other methods already. (Most of the methods I've seen - particularly tseliot's - include removal instructions.)

1. Go to the NVidia site and go to the Unix/Linux kernels page: [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html"). Download the appropriate file (in this case, the Legacy one) like they tell you to. Put it in a convenient spot.
2. You gots to do this install from a terminal, so start with Ctrl+Alt+F1 to jump outta your desktop manager.NOTE that when you do this, you're essentially going to close every program you have running in your *buntu desktop right now, so you should write down the important parts of these instructions before you close them. Once you're at the command line, log in with your username and password.
3. Stop your X server with this command. The installer won't run if X is active, and if you can't kill it with telinit 1 because the installer freaks out in runtime 1 (and jumping back into runtimes 2-5 after going to 1 automatically starts your X server again). If you're in Ubuntu or Xubuntu (possibly), use gdm in the command. If you're in Kubuntu, use kdm instead.
```
sudo /etc/init.d/gdm stop
```
4. Go to the directory you saved the NVidia file in, and then type the following commands. The first one is coz we're running a 2.6 kernel, so NVidia says to use it. The second one runs the installer.
```
sudo modprobe -q agpgart
sudo sh driverfilename.run
```
5. The instructions are straightforward, but it gave me a bunch of stuff about "...unable to determine the correct X library installation path with pkg-config utility... ...install the Xorg SDK/Development kit..." Which is to say, it basically gave me the same message about 5 times. I didn't install the kit, so you might not have to worry about this.
6. When it's done you can use nano to edit your /etc/X11/xorg.conf file: just go down to the Device section and change driver from "nv" to "nvidia." 
7. To start your desktop manager back up and see if it worked or not, type
```
sudo /etc/init.d/gdm start
```
(Again, kdm if you're in Kubuntu)
8. If things just exploded and you got lots of mean, nasty error messages, just switch to a different terminal (glee! Ctrl+Alt+F2, or whatever F# you prefer) and change your xorg.conf setting back to "nv." Then I'm pretty sure you can just go through step 7 again to start your desktop manager back up and find a different solution.

This may all be rather inelegant, but hey - it's what worked for me when the simpler methods failed. (It's not actually very hard to do, really...) But again! Because I'm not particularly Linux-super, these instructions should Probably be a last resort.

---

### Post by 504yaj on 2006-10-29
> **Duggeek said:**
> I think the nvidia coders may have cheated by "borrowing" the ATI xorg.conf sample for their nvidia-glx package. Ya'think? ;) 

I've knocked it about a bit since my last post. I took the advice of [COLOR="DarkRed"]**tseliot**[/COLOR] *(thank you! BTW)* and used the tailored **nvidia-xconfig** tool. Think of it as the "nvidia-glx patch".

It simply does a swap-out of the **xorg.conf** file and places a backup in **/etc/X11**. I can't be sure, but I think it performs a simple test to discover the actual hardware, then generates the appropriate **xorg.conf** settings.

The **xorg.conf.backup** only does you good if you started with a working X config. However, you may find that X comes back after using **nvidia-xconfig**, in which case you can simply throw-out the **xorg.conf.backup** file since it's a bad config anyway.

Best of luck!

I was able to make it work by not following what the package says after it was installed, and by using this two instead

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`

$sudo nvidia-xconfig

---

### Post by blackcoatman on 2006-10-29
I installed the beta drivers from here:
[http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9625.html](http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9625.html)
I had to remove completely anything nvidia related from synaptic (nvidia-kernel as well), plus some restricted modules. By leaving the nvidia kernel and just removing nvidia-glx, i got a kernel conflict. These beta drivers have a cool nvidia utility too, with temperature monitor and stuff.

---

### Post by misterE0 on 2006-10-29
7800gtx

I used the method on ubuntuguide.org, however X wouldn't restart.  For some reason, the driver changed a line to:
	BusID		"PCI:0:5:0"

Simply setting it back to:
	BusID		"PCI:1:0:0"

worked fine.

---

### Post by jso2897 on 2006-11-01
0000:01:00.0 0300: 10de:0185 (rev c1)

Geforce4 440 agp8X  V18

No tweaks - had to use "Xconfig" command instead of "config-enable" to activate.

---

### Post by eh|oloco on 2006-11-02
01:00.0 0300: 10de:0171 (rev a3)
mx440

needed to set gcc to 4.0 (back in breezy it was 3.4 -i think)
not knowing what I'm doing but ready to hack away -the following worked 
[size=5]
[php]
cc=4.0
export CC=/usr/bin/gcc-4.0
sh your-version-here.run as usual 
[/php]
[/size]
done -bzflag works again

THANK you forums -and of Course A.Milone!
```

time wasted -about 3 nights -envy killed everything btw kdm stop doesnt do anything in gnome but u knew that anyway -didn't like the wrong compiler either // automatix2 was useless // easyubuntu -didnt work back in breezy so I didnt waste anymore time

```
I also had testing of edgy before the release so when I upgraded it wasn't pretty with "RELICS" of 2.6.17 -in my happy (working 2.6.15) that took a few days also to straighten out-silly beta release killed my wireless 

now- do I try for the eye candy or do I leave the headaches for others :rolleyes:

---

### Post by Uolirod on 2006-11-06
1) 01:00.0 0300: 10de:0222 (rev a1)

2)  EVGA Nvidia 6200 A LE

3) Just followed instructions on this page (option 2)
   [http://doc.gwos.org/index.php/BerylOnEdgy]("http://doc.gwos.org/index.php/BerylOnEdgy")

for installing the package directly from Nvidia's site.

I'm debating about the eye candy too. :twisted:

---

### Post by asasega on 2006-11-08
1)0000:01:00.0 0300: 10de:0253 (rev a3)
2)Nvidia Geforce4 Ti 4200, 128MB 
3)no tweaking

---

### Post by staib on 2006-11-10
1) 01:00.0 0300: 10de:02e1 (rev a2)
2) GeForce 7600 GS
3)  No tweaking yet - but still need to figure out how to increase resolution...

---

### Post by rikard_grankvist on 2006-11-18
1: 01:00.0 0300: 10de:0322 (rev a1)
2: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
3: No tweaking needed.

---

### Post by PartisanEntity on 2006-11-18
GeForce Go 6200
0000:01:00.0 0300: 10de:0167 (rev a1)
No tweaking. Installed through Automatix2
Ubuntu version: Dapper

---

### Post by peebly on 2006-11-18
Hello

Brand MSI.

Model PCI-E, 7600GT, 256mb.

Installed using ENVY.

No tweaking

Sorry I dont know how to get the identifier number.

Thanks for creating ENVY.

---

### Post by steveneddy on 2006-11-18
0000:01:0a.0 0300: 10de:0322 (rev a1)
0000:01:0a.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

I have the Nvidia Beta driver:
NVRM version: NVIDIA UNIX x86 Kernel Module  1.0-9742 
and the installer made my xorg.conf look like this:

Section "Device"

#    Option	   "NvAGP"  "1"	
    Identifier     "nVidia GeForce FX5200"
    Driver         "nvidia"
EndSection

Section "Screen"

#    Option	   "UseFBDev"		     "true"
    Identifier     "Default Screen"
    Device         "nVidia GeForce FX5200"
    Monitor        "P110"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "On"

which put the options I would expect to see in the "Device" section in the "Screen" section. Everything seems to be working fine for now.

Also added this line at the end on the xorg.conf file:

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by loell on 2006-11-18
01:00.0 0300: 10de:0326 (rev a1)

no tweaking

---

### Post by fnf on 2006-11-23
[LIST=1]
[*]01:00.0 0300: 10de:01d7 (rev a1)
[*]GeForce Go 7300 128MB (Turbo Cache)
[*]No tweaking needed.
[/LIST]

Additional Info:
**Driver**: 1.0.9742
**Problem**: X server crashed hard (only SysRq brought back my control) after a few minutes I tried to run any heavy 3D applications (Blender, Google Earth, Beryl...).
**Typical info logged** (in every X session):> 
NVRM: Xid (0001:00): 3, C 0000001e SC 00000002 M 00000100 Data 00000000
NVRM: Xid (0001:00): 8, Channel 00000000
NVRM: Xid (0001:00): 3, C 0000001e SC 00000002 M 00000104 Data 00000000

---

### Post by xopher on 2006-11-23
1) 02:00.0 0300: 10de:00c1 (rev a2)

2) 02:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)

3) No tweaking needed

---

### Post by budman21901 on 2006-11-23
01:00.0 0300: 10de:0326 (rev a1)

nVidia Corporation NV34 [GeForce FX 5500]

No Tweaks

---

### Post by Gustav on 2006-11-23
1) 01:00.0 0300: 10de:0110 (rev b2)
2) GeForce2 MX400 64MB
3) No tweaking needed

---

### Post by CJNyfalt on 2006-11-23
1: 01:00.0 0300: 10de:0151 (rev a4)
2: 01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a4)
3: sudo nvidia-xconfig --allow-glx-with-composite

---

### Post by rberry88 on 2006-11-25
1. 05:00.0 0300: 10de:0091 (rev a1)
2. Nvidia GeForce 7800GTX
3. added "RenderAccel" "true"

---

### Post by RockinRob2258 on 2006-11-27
0000:01:00.0 0300: 10de:0322 (rev a1)
Nvidia GeForceFX 5200, I believe manufactured by XFX.
no tweaking, used the method 1 in the HowTo that I think was written by tseliot.  
The only extra thing I had to do was add a screen resolution under the xorg.conf file so that I could get 1680x1050 widescreen, but that's not really driver related.

---

### Post by asta on 2006-11-29
1) 01:00.0 0300: 10de:0110 (rev b2)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
3) Well... Reboot the computer with the "nv" driver, start and loggin to a session. Then change the driver to "nvidia" and restart X-server with Ctrl-Alt-Backspace. Rebooting directly with "nvidia" hangs the computer after the first Kubuntu splash screen. Any hints? :D 

Same on standard edgy nvidia driver (8776) and latest 9629

---

### Post by asta on 2006-11-29
SOLVED! The BIOS setting of AGP aperture was 64M, and agpgart detected 128M. Changed BIOS setting to 128M, and it works.

---

### Post by Unterseeboot_234 on 2006-11-30
0000:03:00.0 0300: 10de:0393 (rev a1)
Graphics processor: GeForce 7300GT
PCIe 16X, 256 MB vid memory

The 64_bit ubuntu Drake install worked with a smaller screen. No desktop adjustment was possible.

Automatix immediately saw the card and fetched nVidia Driver Version 1.0-8776 and installed a control panel under Applications | System Tools

Suggestion:  some, if not most, of the new nVidia cards have built-in audio circuitry. Called MCP. Fascinating subject. Putting the audio onboard dramatically increases frame-rate for video gaming. This suggestion is just a gut feeling from all the hell I went thru in Windoze sometimes. The sound card would always in irq conflict and s/b located in the low number pci slots.

---

### Post by testbenchdude on 2006-12-02
1:

01:00.0 0300: 10de:0291 (rev a1)
03:00.0 0300: 10de:0291 (rev a1)

I'm guessing it automatically detected my SLI. Woot!

2: 

2 x 7900GT in SLI

3:

Nothing. Ran Envy Method 2. That was the only way to install it. THANK YOU SO MUCH! I was pulling my hair out trying everything else.

EDIT*

I busted my xserver somehow, and decided to do a fresh install of Ubuntu to play with anew, and this time I used Automatix2. So far so good. :)

---

### Post by twrock on 2006-12-03
Nvidia GeForce 6150 built into an ASUS motherboard.

To get Nvidia driver to work in Edgy, I used this link: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) and just followed the directions as given. Thanks for that.

There was a minor problem that 99% of the people will notice and fix, but I thought I would mention it. When I copied the "code" from the web page and pasted the contents into the NVIDIA-Settings.desktop file, it came out as one long string instead of individual lines of text (the carriage returns appeared to become individual spaces). Maybe that isn't a problem, but for what it's worth, that's what happened.

---

### Post by Footer on 2006-12-03
1. 0000:02:00.0 0300: 10de:0322 (rev a1)
2. GeForce FX 5200 128MB
3. No tweaking needed, installed using driver/installation directly from nVidia:
[INDENT]Linux Display Driver - x86
Version: 1.0-9629
[http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html)[/INDENT]

Kubuntu Dapper Drake

---

### Post by jazzgossen on 2006-12-04
1) 01:00.0 0300: 10de:0286 (rev a1)

2) GeForce4 Ti 4200 Go AGP 8x] (rev a1). This is the card in a Dell Latitude D800 laptop.

3) No tweaking needed to get the driver going, but after installing it, hibernate broke. I added 
```
Option "NvAGP" "1"
``` to get hibernate to work.

---

### Post by Bukran on 2006-12-05
1) 01:00.0 0300: 10de:0110 (rev b2)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
3) No options enabled.

After messing around with several modules, I decided to uninstall nvidia-glx, nvidia-glx-legacy and also linux-restricted-modules-2.6.17-10-generic.

Then I downloaded latest Linux Display Driver-x86 (version 1.0-9629) from [www.nvidia.com]("http://www.nvidia.com") and followed the instructions in there. The last difficulty was: "/sbin/lrm-video not found. Failed to load the nvidia kernel module", apparently impossible to work out.

But I found something about the same weird problem in [forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/50969/15/") from where I got the solution:

- Go to /etc/modprobe.d and open the file lrm-video:

```
gksudo gedit /etc/modprobe.d/lrm-video
``` or 
```
sudo vi /etc/modprobe.d/lrm-video
``` in case you prefer the classic way. ;) 

Then comment (add '#' at the beginning of the line) the lines related to fglrx adn nvidia and leave the one about nvidia-legacy uncommented. My lrm-video file now shows like this:
```

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
# install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
# install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
```

Restart X server and now everything should be working:
```
sudo /etc/init.d/gdm restart
```

I'm using Ubuntu 6.10 - Edgy Eft - and hope they eventually fix this mess to install Nvidia "old" graphic cards drivers. We all should work together to make Linux user-friendlier.

---

### Post by frogotronic on 2006-12-05
1) 0000:01:00.0 0300 10de:0112 (revb2)
2) nVIDIA Corporation NV11 [GeForce2 Go] (revb2)
3) No Tweaks needed, installed the 1.0-8776 binary driver via Automatix2

---

### Post by Mark Marple on 2006-12-09
1) 01:00.0 0300: 10de:0161 (rev a1)
2) "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]" PCIe
3) tweaking.....had to add 1440x900 resolution to xorg.config.  As I posted in another topic, the Nvidia settings from Synaptic sees all the different resolutions and will change the 1440x900, but the xorg didn't have it. Nvidia settings also sees my monitor (Viewsonic va1912wb) but the xorg.conf just has "generic monitor".....no biggie though, I just want the resolution to be correct.

I would also like to thank you for the Envy script.

Mark

---

### Post by fnf on 2006-12-10
> **fnf said:**
> [LIST=1]
[*]01:00.0 0300: 10de:01d7 (rev a1)
[*]GeForce Go 7300 128MB (Turbo Cache)
[*]No tweaking needed.
[/LIST]

Additional Info:
**Driver**: 1.0.9742
**Problem**: X server crashed hard (only SysRq brought back my control) after a few minutes I tried to run any heavy 3D applications (Blender, Google Earth, Beryl...).
**Typical info logged** (in every X session):

**[COLOR="Red"]This is neither guaranteed to work in every case nor is recommended by the nvidia team.[/COLOR]**

I got it working stably with this tweak:
```
modprobe nvdia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```
The nvidia module is usually automatically loaded on boot, if you try this, make sure you've added this option in */etc/modprobe.d/options* or start Ubuntu in console then load it manually.

It has been confirmed to work with GeForce Go 7300 and 7950 GTX. A nvnews member cleverly discovered the same tweak is applied in the downloaded Windows driver with these cards. Go **[here]("http://www.nvnews.net/vbulletin/showthread.php?t=80888")** to see the original thread and **[her]("http://www.nvnews.net/vbulletin/showthread.php?t=79503")**e for a similar case..

---

### Post by heracles on 2006-12-13
Using your script the following insatalled faultlessly. NV43 [GeForce 6600] I have to start it every time to get the dual screens but for me that is better.Thanks for your efforts

---

### Post by ZERO_SHIFT on 2006-12-15
Automatix is the best choice.

---

### Post by fnf on 2006-12-15
> **ZERO_SHIFT said:**
> Automatix is the best choice.

Does that mean automatix is able to automagically fix the stability problem ?.

---

### Post by Jenske on 2006-12-18
1/ 0000:01:00.0 0300: 10de:002c (rev 15)
2/ 0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
3/ No tweakings necessary.

Problem however: my monitor (Samsung Syncmaster 940B is able to pivot, but I can't seem to find a way to get this working in Ubuntu)

---

### Post by hoagie on 2006-12-18
> **encompass said:**
> 1) 0000:02:07.0 0300: 10de:0322 (rev a1)
2) nVidia Corporation NV34 [GeForce FX 5200] (PRO/660 TV/DVI Gainward FX Powerpack 128 MB PCI)
3) Needs no tweaking.
To save space... should we avoid signitures?

Exactly the same card, exactly the same way. Although for beryl I did a bit further tweaking.

---

### Post by tedk89 on 2006-12-18
01:00.0 0300: 10de:002c (rev 15)

01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

No tweaking Needed

---

### Post by Kalibur on 2006-12-20
01:00.0 0300: 10de:0326 (rev a1)
Nvidia Geforce NV34 FX 5500 with DVI & S-video out

tweaks to get it to work on my wide screen(1280x768_)
*Disconnected the LCD during boot up, boots up in 1024x768, if I don't do that my LCD says frequency out of range!
*Once logged in I edited the xorg.conf file to include 1280x768 as first option on all screen and display sections. And finally changed the 'nv' to 'nvidia'
*install the nvidia-settings driver
*Reboot the system -- this is where all hell breaks loose ](*,) 
Boots up and xserver-xorg cannot find display so GDM is disable and its terminal for me.
*using apt-get or aptitude I install nvidia-glx (nvidia-glx-legacy for a failsafe precaution)
 and xserver-xorg-video-nv/all
*Reboot agian -- and guess what its not over but we almost there :evil: 
Gnome login screen in 1280x768 yipee:p 
Now I login in and damn LCD says frequency out of range at this point I press ctrl+alt+backspace to return to the login screen.....
*go to options>sessions and choose failsafe terminal>then login and creat a new user give him all admin powers then login in as normal and the 1280x768 resolution works.  After that I just delete the old user and use the new one...j

Hope that helps....may ubuntu be with thee;)

---

### Post by Xanthomryr on 2006-12-21
01:00.0 0300: 10de:0200 (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3)
No tweaking needed

---

### Post by ykram on 2006-12-23
I upgraded mine from a Radeon 9250 to a Geforce 6600 so here's how I did it.

1) Before I installed the new Nvidia card, "apt-get install nvidia-glx" to install the binary nvidia driver and remove the fglrx driver ATI uses.
2) Copied my old, generic xorg.conf.old to xorg.conf and shutdown, installed the card. Easy so far.
3) Of course Xorg didn't work properly but that was okay. "dpkg-reconfigure -phigh xserver-org"
4) Boot into generic Xorg with Xorg's nv driver. Went back to command line and editted /etc/X11/xorg.conf adding the neccessary section for my Logitech MX518 mouse as well as changing the "Driver" line under Device from "nv" to "nvidia". I use a dual LCD setup so I added the TwinView options, MetaModes, TwinViewOrientation, Second monitor's vert/horiz syncs (All covered in another ubuntu-forum howto on getting dual LCDs working in linux with nvidia's driver.
5) Restarted Xorg and all was well :) While my method for setting it up may seem rather inefficient to some or even difficult to others, that's just me :P I'm used to doing things my way anyways :) Hope this helps.

*Note: In Dapper, "lspci' showed my nvidia card as "0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f6 (rev a2)", for those of you annoyed by this (as was I), "update-pciids" as root will fix it for you, assuming of course there's an ID available. "0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GS] (rev a2)"

---

### Post by mahiyar on 2006-12-28
Is it too late to reply? Installed on 27/12 through Ubuntu guide way
1)01:00.0 0300: 10de:0322 (rev a1)
2)NVIDIA GEFORCE FX 5200 -- Driver NV 34.
3)No tweaking needed

---

### Post by mattengland on 2006-12-29
Are these reports assuming a certain distro (Breezy, Dapper, Edgy, Feisty) and/or kernel revision (2.6.15.x, 17.x, 18.x, 19.x)?  I see little if any mention of this environment information.  Does it matter?  It seems to matter a lot as per my installation experience with these things today.  It would be nice for me to know the environments associated with these working reports.

-Matt

---

### Post by Andrew Smith on 2006-12-30
1)  05:00.0 0300: 10de:01d8 (rev a1)
2)  Nvidia GeForce Go 7400
3)  Even though i installed right nvidia driver, my laptop used the old ones](*,) , and crashed Xorg at each startup[-X .

:-k SO: 

Needs to remove the precompiled modules (files) from these directories:
/lib/modules/2.6.17-10-generic/volatile/nvidia.*

and also any directories named: nvidia, or nvidia-legacy from:

/lib/linux-restricted-modules/2.6.17-10-generic/

after these
it worked fine.=;

---

### Post by david_2001 on 2007-01-07
1.  02:00.0 0300: 10de:016a (rev a1)

2.  XFX GeForce 7100GS 128MB PCI-E

Install (Edgy):

sudo apt-get install nvidia-glx
sudo nvidia-xconfig
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
sudo nvidia-glx-config enable

Reboot

---

### Post by Cariboo1938 on 2007-01-07
1) 01:00.0 0300: 10de:0322 (rev a1)

2) 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

3) I run Ubuntu 6.10-AMD64 with kernel "2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux" 
   I first tried to install nVidia driver 9631 mannually following the instruction at [www.nvidia]("http://www.nvidia.com/object/linux_display_amd64_1.0-9631.html"). This installation wrecked my X window server.
   I uninstalled it following the instructions at [HERE]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy").
   Then I followed these instructions at [HERE]("http://www.ubuntuforums.org/showthread.php?t=318206") 
and installed the nvidia-glx driver.  
   I only had to edit /etc/X11/xorg.conf and replace "nv" by "nvidia":D

---

### Post by Kossilar on 2007-01-09
05:00.0 0300: 10de:00c0 (rev a2)

NVIDIA GeForce 6800 GS
The card didn't work from the LIVE CD. First I had to run:
```

sudo dpkg-reconfigure xserver-xorg
```

And use mostly the default options, only making choices where the resolution was concerned. 

```
sudo /etc/init.d/gdm restart
```

Did NOT work. I had to reboot the system and then hit f4(I think) to choose a new resolution apart from VGA. I believe I chose 1024x768 / 16bit. After that I installed Ubuntu. But of course the card still didn't work. So I downloaded the latest NVIDIA proprietary drivers from nvidia.com using 

```
wget  http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

and then: 

```
sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

To install them. However, GLX then caused a problem telling me I had the wrong NVIDIA kernel module. I believe this was because I still had references to GLX on my system. I removed references to GLX from /etc/X11/xorg.conf, reinstalled the 1.0-9746 driver and then rebooted.

There were a lot of things that I tried to get this driver running, but I believe that these were the main things that I needed to do. After commenting out references to GLX from /etc/X11/xorg.conf and reinstalling the driver. Everything seems to be working fine. If I have any more problems and I manage to fix them, I'll update this post.

I'd just like to say that I'm impressed with the Ubuntu community's willingness to help everyone get up to speed and the existance of this thread is a testimony to that.

Thank you.

---

### Post by Goth Mneph on 2007-01-09
getting the driver to work was cake, getting the 3d to work is the most difficult thing i've tried since trying to teach a Border Collie to sit still for more than 10 seconds.  does anyone have a tried and true trick that will get the 3d feature to work?:-k 

i have

NVIDIA Corporation NV34 [GeForce FX 5200] 256 meg.

any help would be tremendously appreciated.](*,)

---

### Post by old_geekster on 2007-01-15
05:00.0 0300: 10de:0290 (rev a1)

XFX GeForce 7900GTX 512 (665/1630)

I used "Automatix".  There was no tweaking necessary.  The reason that I updated the driver was "Google Earth".  It was running with emulation and poorly at that.  Now, it runs fine.

---

### Post by keet on 2007-01-15
(1.) 01:00.0 0300:  10de: 0391 (rev a1)

(2.) No responce from this line entered

But i know that i've got an nvidia xfx 7600 gt card fitted. 


(3.) Is it working? I @m not sure. Is there a standard test of function?

---

### Post by madmetal on 2007-01-15
well just the same with tseliot :)

1) 0000:01:00.0 0300: 10de:0326 (rev a1)
2) Nvidia Fx 5500 128MB
3) No tweaking needed

ubuntu 6.06.1 driver from synaptic.

---

### Post by chinocracy on 2007-01-16
As I posted in other thread, I installed the 9629 and 7184 (legacy) via shutting down X server and running the sudo sh ___.run files. I do edit the xorg.conf files as said. When I restarted X, they worked fine, but when I do a full reboot, X fails to start. I wonder if it has something to do with the driver not being able to find a precomplied kernel for nvidia when I install it? I thought I had every possibly needed module, like the linux-kernel-common, but I wonder if that interferes with the working of the driver? Or maybe I'm missing a module? I'm on 2.6.15-27-686 kernel, thanks.
Oh, Geforce2 MX 400.

---

### Post by Thar on 2007-01-18
1) 05:00.0 0300: 10de:014f (rev a2)
2) GeForce 6200
3) sudo apt-get install nvidia-glx

```
Driver "nvidia"
```
in xorg.conf

---

### Post by dermann on 2007-01-18
1) 00:05.0 0300: 10de:0244 (rev a2)
2) Geforce Go 6150
3) No tweaking needed....used tselliot's Envy script and all works perfectly so far.

---

### Post by vinboy on 2007-01-20
Because I use custom kernel, I had to do the driver install manually using
```
sudo sh sh NVIDIA-Linux-x86-1.0-9746-pkg0.run
```

then use the nvidia-settings to setup everything else including Dual Screen

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23557&stc=1&d=1169352234[/IMG]

---

### Post by Niko38752 on 2007-01-21
1) 0000:01:00.0 0300: 10de:0161 (rev a1)
2) ASUS EN6200TC (nVidia Corporation GeForce 6200 TurboCache(TM))
3) No tweaking

---

### Post by nicholas22 on 2007-01-23
1) 00:0f.0 0300: 15ad:0405
2) 00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
    (but I have Leadtek A360 TDH G-Force FX5700 256MB DDR)

3) Never have been able to properly run FX 5700 drivers on Linux. Ever. ](*,) 
    Consequently, my main issue was that I could not change resolution to a higher setting than 800x600, and I found that quite annoying, because this is a really basic requirement.

    _Half-solution:_ Deleted all 'Subsection "Display"' entries at the end of /etc/X11/xorg.conf, leaving only one as a fail-safe, the 640x480, depth 4, viewport 0 0. Then added (copy/paste) a 1024x768 entry, manually.
I am running VMWare on top of XP SP2, so (as urged by the comments in xorg.conf) I took note that my card only supports 16bit and 32bit depth (from XP auto-detected display modes), so I experimentally put down a 'depth' of 16(bpp), Note, this is what I am running on XP. I don't think it is not a good idea to mix modes if you are in my situation. 
The rest, I copied them untouched. Rebooted and I had a 1024x768 option in login screen.

I know this is not the best solution, but as I said I do not plan to accelerate 2D/3D with Ubuntu... (it's para-virtualized anyway, so performance would be sluggish)

But I finally have 1024x768 :biggrin:

---

### Post by chinocracy on 2007-01-23
OK, I think I finally got it. I decided to run the 7174 for safe measure. 

The error screen at startup when I use this driver version is something like 'cannot find ///nvidia.ko'

So what I did is to manually copy /lib/modules/2.6.15-27-686/volatile/nvidia.ko
to:
/lib/modules/2.6.15-27-686/kernal/drivers/video/nvidia.ko

That did the trick. So when the computer starts up, the Nvidia logo comes up, and X starts successfully. 

Thanks!

> **chinocracy said:**
> As I posted in other thread, I installed the 9629 and 7184 (legacy) via shutting down X server and running the sudo sh ___.run files. I do edit the xorg.conf files as said. When I restarted X, they worked fine, but when I do a full reboot, X fails to start. I wonder if it has something to do with the driver not being able to find a precomplied kernel for nvidia when I install it? I thought I had every possibly needed module, like the linux-kernel-common, but I wonder if that interferes with the working of the driver? Or maybe I'm missing a module? I'm on 2.6.15-27-686 kernel, thanks.
Oh, Geforce2 MX 400.

---

### Post by karachuonyo on 2007-01-23
1. 01:00.0 0300: 10de:0282 (rev a1)
2.GeForce4 Ti 4800 SE 128 MB
3. No tweaking needed
Used Automatix2 to install. Fantanstic

---

### Post by Cariboo1938 on 2007-01-24
1) root@BitByter:~# lspci -n | grep 0300
01:00.0 0300: 10de:0322 (rev a1)

2)root@BitByter:~# lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

3)I used "ENVY" envy_0.8.1-0ubuntu3_all.deb from [HERE]("http://albertomilone.com/nvidia_scripts1.html"). No tweaks necessary! Thanks tseliot!

---

### Post by DLinn on 2007-01-24
Linux OS:
Ubuntu Edgy v6.10

I have a PCI Express video card:
EVGA- e-GeForce 7100 GS

sudo apt-get install nvidia-glx

reboot...bingo! done!

no one was more surprised than me!

---

### Post by EvilMarshmallow on 2007-01-24
Here are my results:

Distro: Ubuntu Edgy

>lspci -n | grep 0300:
01:00.0 0300: 10de:0201 (rev a3)
02:08.0 0300: 1002:4752 (rev 27)

My card:
GeForce3 Ti 200

I got it working with nVidia-Linux-x86-1.0-9631.

---

### Post by deodatus on 2007-01-24
$ lspci -n | grep 0300
01:00.0 0300: 10de:0322 (rev a1)

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

installed with envy script!!

I have to say THANKS to tseliot!!  I install linux on a lot of machines and this has been a great help!!

---

### Post by ChrisNY on 2007-01-24
1) 02:00.0 0300: 10de:01dd (rev a1)
2)GeForce 7500LE
3) No Tweaking - Used Automatix2

---

### Post by lopoetve on 2007-01-25
1.  05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0291 (rev a1)  (it's a 7900GT)
2.  Tried the official drivers.  Tried Synaptic.  Tried Envy.  Tried the drivers from NVidia.  Nothing gets 3d acceleration.  
3.  Switched to nv to at least get something useful.  Cried.  :(

---

### Post by Arup on 2007-01-25
I came back to Linux after a long time, from SuSE 8.1 to new Ubuntu 6.10, I installed it on my older PC which is a dual P-III 850 machine with an ancient Asus GeForce 256DDR card, upon booting card was not listed on the generic kernel, tried to install it but Ubuntu would insist on installing 386kernel which is not SMP, so after going through lots of searching on net I come across ENVY, I tried the latest and it have me a md5 error so I tried the older 0.73 and it did download the driver and installed and I finally get to see the nvidia screen during boot:D 

Then came another problem, Ubuntu told me I had quite a few updates, among them Xserver etc, amounting to 156mb, I allowed the update and rebooted as per process, guess what, my nvidia driver was broken, as soon as I would try glxgears, it would blank out and come to login screen, I went into recovery mode and started Envy which reinstalled the drivers, I reboot, during boot process I get a tainted Nvidia kernel line but the nvidia screen comes up and my glxgears work fine. I am surprised because I expected the install to be smooth for a old machine but the video card install has truly left a bad taste in my mouth, I also tried recompiling with the latest Kernel 2.6.19.2 but after booting into the latest kernel, nvidia drivers would refuse to install even via Envy.

So this is my experience in a nutshell, sorry if its lengthy.

---

### Post by onlybui on 2007-01-25
1. 01:00.0 0300: 10de:0292 (rev a1)
2.  01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0292 (rev a1) "EVGA 7900GS 256MB *
3. No Tweaking needed
X. Tried ----->Synaptic Package Manager, Automatix, followed the guide Method 1&2 and I never got 3D working
Tried -----> Install Beryl on Ubuntu Edgy with nVidia using  Automatic installation and finally got 3D working followed these instructions [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation")

---

### Post by mark541 on 2007-01-25
1. Post the output of this command:

$ lspci -n | grep 0300
0000:01:00.0 0300: 10de:0322 (rev a1)

2. Video card model

$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

3. Tweaking required to get my card and monitor to work.

a. My original monitor was a Hitachi CM751. With the Hitachi, I needed zero tweaking to get the video working. Followed the standard instructions for the nvidia drivers.

b. Replaced with new monitor, a ViewSonic VP2030b. It has DVI (DVI-D and DVI-A compatible) and VGA inputs. The VGA input worked with no changes other than updating the horizontal and vertical refresh rates. 
However, the DVI input did not work. After my changes, I now get 1600x1200 @ 60Hz from the DVI-D, and the quality is fantastic. Here's what I did to get both the DVI-D and VGA to function:

xorg.conf

#===== new sections for nvidia card and viewsonic monitor =====#

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"		# "nv"
	BusID		"PCI:1:0:0"
	#
	# TwinView section
	# The following should allow the same view on both VGA (CRT-0) 
        #     and DVI (DFP-0) outputs
	Option		"TwinView"
	Option		"ConnectedMonitor" "DFP, CRT"
                           # e.g. Digital-Flat-Panel, Cathode-Ray-Tube
	Option		"HorizSync"	"CRT-0: 30-92; DFP-0: 30-92"
                           # define horiz. ranges for each output
	Option		"VertRefresh"	"CRT-0: 50-85; DFP-0: 60" 
                           # define vert. ranges for each output
	Option		"TwinViewOrientation" "Clone"	
                           # show identical output to VGA and DVI
	Option	"MetaModes" "1600x1200,1600x1200; 1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 640x480,640x480"
	# End of TwinView section
EndSection

Section "Monitor"
	Identifier	"VP2030b"
	Option		"DPMS"	"true"
	HorizSync	30.0 - 92.0 # ViewSonic VP2030b
	VertRefresh	50.0 - 85.0 # ViewSonic VP2030b
	#
	# Note: Modes I'm not using with the ViewSonic VP2030b were removed
	#	I put the 60Hz modes first for each resolution, DVI-D uses 60Hz
	#
        #  Default modes distilled from
        #      "VESA and Industry Standards and Guide for Computer Display Monitor
        #       Timing", version 1.0, revision 0.8, adopted September 17, 1998.
        #  $XFree86: xc/programs/Xserver/hw/xfree86/etc/vesamodes,v 1.4 1999/11/18 16:52:17 tsi Exp $
        #
        # 640x480 @ 60Hz (Industry standard) hsync: 31.5kHz
        ModeLine "640x480"    25.2  640  656  752  800    480  490  492  525 -hsync -vsync
        # 640x480 @ 72Hz (VESA) hsync: 37.9kHz
        ModeLine "640x480"    31.5  640  664  704  832    480  489  491  520 -hsync -vsync
        # 640x480 @ 75Hz (VESA) hsync: 37.5kHz
        ModeLine "640x480"    31.5  640  656  720  840    480  481  484  500 -hsync -vsync
        # 640x480 @ 85Hz (VESA) hsync: 43.3kHz
        ModeLine "640x480"    36.0  640  696  752  832    480  481  484  509 -hsync -vsync
        # 800x600 @ 60Hz (VESA) hsync: 37.9kHz
        ModeLine "800x600"    40.0  800  840  968 1056    600  601  605  628 +hsync +vsync
        # 800x600 @ 72Hz (VESA) hsync: 48.1kHz
        ModeLine "800x600"    50.0  800  856  976 1040    600  637  643  666 +hsync +vsync
        # 800x600 @ 75Hz (VESA) hsync: 46.9kHz
        ModeLine "800x600"    49.5  800  816  896 1056    600  601  604  625 +hsync +vsync
        # 800x600 @ 85Hz (VESA) hsync: 53.7kHz
        ModeLine "800x600"    56.3  800  832  896 1048    600  601  604  631 +hsync +vsync
        # 1024x768 @ 60Hz (VESA) hsync: 48.4kHz
        ModeLine "1024x768"   65.0 1024 1048 1184 1344    768  771  777  806 -hsync -vsync
        # 1024x768 @ 70Hz (VESA) hsync: 56.5kHz
        ModeLine "1024x768"   75.0 1024 1048 1184 1328    768  771  777  806 -hsync -vsync
        # 1024x768 @ 75Hz (VESA) hsync: 60.0kHz
        ModeLine "1024x768"   78.8 1024 1040 1136 1312    768  769  772  800 +hsync +vsync
        # 1024x768 @ 85Hz (VESA) hsync: 68.7kHz
        ModeLine "1024x768"   94.5 1024 1072 1168 1376    768  769  772  808 +hsync +vsync
        # 1280x1024 @ 75Hz (VESA) hsync: 80.0kHz
        ModeLine "1280x1024" 135.0 1280 1296 1440 1688   1024 1025 1028 1066 +hsync +vsync
        # 1280x1024 @ 85Hz (VESA) hsync: 91.1kHz
        ModeLine "1280x1024" 157.5 1280 1344 1504 1728   1024 1025 1028 1072 +hsync +vsync
        # 1600x1200 @ 60Hz (VESA) hsync: 75.0kHz
        ModeLine "1600x1200" 162.0 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 65Hz (VESA) hsync: 81.3kHz
        ModeLine "1600x1200" 175.5 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 70Hz (VESA) hsync: 87.5kHz
        ModeLine "1600x1200" 189.0 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Screen"
    Identifier	"Default Screen"
    Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor		"VP2030b"
    DefaultDepth	24
    SubSection "Display"
	Depth		1
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
	Depth		4
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
	Depth		8
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
	Depth		15
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
	Depth		16
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
	Depth		24
	Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

#===== end of sections for nvidia card and viewsonic monitor =====#

---

### Post by piponline on 2007-01-26
1) 0000:01:00.0 0300: 10de:0171 (rev a3)

2) nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

3) I had a lot of trouble to get it working: when the card was active in the bios, Ubuntu boot would always crash.

I was saved by this thread and by a reference someone made to this Howto: [http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated). I just followed the instructions on that Howto and bingo! 
One small detail not in the Howto (and for a newbie like me everything must be spelled out :D): I had to update the "Screen" section in xorg.conf because it was pointing to the onboard card.

Cheers!

---

### Post by Footer on 2007-01-27
1)  07:00.0 0300: 10de:0392 (rev a1)
2)  07:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1)

But I know it's an Albatron  7600GS 256M DDR2 PCIe card

3)  Why envy of course!  No tweaks necessary and a very SWEET script/experience after muddling along for awhile trying to install the proprietary driver myself.  Thanks tseliot!!!

Kubuntu Edgy 6.10

---

### Post by dougmoser on 2007-01-28
Could someone explain what I am supposed to do with these numbers?  I have a nvidia geforce4 mx

---

### Post by ridgeland on 2007-02-05
1. Post the output of this command:
$ lspci -n | grep 0300
01:00.0 0300: 10de:0110 (rev b2)
2. Video card model
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
3. Tweaking required to get my card and monitor to work.
At first Nvidia 3-D and ram not being used.  My test is the game KBounce.  When Nvidia doesn't work the game has serious time lags, with Nvidia it's fun.
To get Nvidia to work I followed Method 1 from:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Steps without the detail of edits required:
uname -r
sudo apt-get install linux-generic
sudo apt-get install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig --no-composite
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
:) This was a lot easier than past experiences with runlevel 3 etc.

---

### Post by #Reistlehr- on 2007-02-06
added noapic to grub. worked fine

---

### Post by Footer on 2007-02-06
Anyone know if/when envy will support Feisty?  Worked flawlessly under Edgy but says something about "Operating System not supported" under Feisty ... I'm having hit or miss luck with trying to install using the drivers straight from nVidia and I'd REALLY, REALLY like to get them to work!  I have an Albatron GeForce 7600GS with 256MB of RAM.

Thanks!

:)

---

### Post by CallsignBaron on 2007-02-07
1)  01:00.0 0300: 10de:0253 (rev a3)
2)  Nvidia GeForce4 Ti 4200 AGP/SSE2/3DNOW 128MB
3)  No Tweaks Needed. Driver installed with envy script.

Thanks tseliot :)

---

### Post by esaym on 2007-02-07
I had no problems installing [IMG]http://www.lindsay.ath.cx/pics/spacer.jpg[/IMG]

---

### Post by stromb on 2007-02-09
1.) 00:05.0 0300: 10de:0241 (rev a2)
2.) 00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
3.) Followed [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") guide.

[INDENT]a.) Had to install nvidia-glx drivers:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
```[/INDENT]

[INDENT]b.) Had to go to the Section "Device" and change "nv" to "nvidia":
```
Driver         "nvidia"
```[/INDENT]

[INDENT]c.) Had to remove all "1680x1050" resolutions (20.1" ViewSonic monitor) under all "Subsection"s under Section "Screen". This was done to prevent the login GNOME screen from defaulting to 1680x1050, and making it 1280x1024. Example:
```
SubSection     "Display"
    Depth       24
    Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x$
EndSubSection
```[/INDENT]

---

### Post by warri0r on 2007-02-10
1)01:00.0 0300: 10de:0322 (rev a1)
2)nvidia geforce FX 5200 (256MB)
3)sorry i m new to linux and after a lot of struggle, installed the driver as per your guide at some other threads and i used the method 2 (sorry if i answered bad for your question :confused: )

---

### Post by Kevf on 2007-02-10
I've used this link:

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

Post I've made in that thread:

Whoe It worked (got the fakeroot package installed)!! But when Grub loads I see two kernels (I've got a dual boot with xp). The one that loads on default works, But is there anything I should do about the other? Futhermore I have to recompile the kernel after each update. Meaning?

---

### Post by claydoh on 2007-02-10
Two different machines with (of course) two different results:

My main box:
1) 02:00.0 0300: 10de:0221 (rev a1)
2) NV44A [GeForce 6200]
3) I needed to edit xorg.conf to get correct refresh rate:

I added the line
```
Option         "DynamicTwinView" "False"
```
to the Section "Device"

I was unable to get a correct rate by specifying my crt's horiz/vert refresh rates as per usual with nvidia drivers up to 8776. Anything  newer would not give me a rate above 57hz on my 1024x768 monitor. I think I got this from a few hours pouring over nvidia's Linux forums.

My older testing box:

1) 01:00.0 0300: 10de:0326 (rev a10
2) NV34 [GeForce FX 5500]
3) nothing other than 'sudo nvidia-xconfig' no matter which driver version or install method used

---

### Post by ninjagore on 2007-02-11
0000:02:00.0 0300: 10de:02e1 (rev a2)
NVIDIA GeForce 7800GS
Just sudo aptitude install nvidia-glx. I did have to change the driver in xorg.conf from "nv" to "nvidia."

---

### Post by CowboyCoffee on 2007-02-12
1)01:00.0 0300: 10de:0161 (rev a1)

2)nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1) 256 mb

3)Ran Envy. No tweaking needed.

Running Edgy

---

### Post by 16777216 on 2007-02-13
lspci -n | grep 0300 gives me 03:00.0 0300: 10de:0161 (rev a1)
lspci | grep VGA gives me 03:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)

I used envy but it kept giving me a time out error and failed to download the driver .
I downloaded the proper driver from nVidia and as root moved the driver to /usr/share/envy.
Then I re-ran the script. 
Everything went well.
Then I hand made my xorg.conf file. ( see below )
I use dual head on one card ( I would use triple head on two cards but I only have two monitors. )
All I need to do now is figure out how to define custom refresh rates for both monitors as I use 1280x1024x1280x1024@60Hz but I know my primary will do 65Hz and the secondary will do 66Hz.
```

## Server section #############################################################
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


## File Section ###############################################################
Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection


## Modules ####################################################################
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection


## Server Flags ###############################################################
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection


## Input Devices ##############################################################
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


## Monitors ###################################################################
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMI eView 17f2"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection


## Graphics Cards #############################################################
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 TurboCache(TM)"
    Option         "TwinView" "1"
    Option         "CoolBits" "1"
    Option         "metamodes" "1280x1024,1280x1024; 1280x1024, 0; 1024x768,1024x768; 1024x768,0; 800x600, 800x600; 800x600, 0; 640x480, 640x480; 640x480, 0; 512x384, 512x384; 512x384, 0; 320x240, 320x240; 320x240, 0;"
    Option         "UseDisplayDevice" "CRT, CRT"
    Option         "TwinViewOrientation" "RightOf"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "1"
    Option         "RandRRotation" "1"
    Option         "AllowDDCCI" "1"
    Option         "HWCursor" "1"
    Option         "UseEdidFreqs" "1"
    Option         "SecondMonitorHorizSync" "30-70"
    Option         "SecondMonitorVertRefresh" "50-180"    
    Option         "AllowGLXWithComposite" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "TripleBuffer" "1"
EndSection


## Screens ####################################################################
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
  SubSection        "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480" "512x384" "320x240"
  EndSubSection
EndSection
```I would definitely like a way to configure ( make that *fine tune* ) refresh rates.

---

### Post by Snookered on 2007-02-13
Thank you, tseliot! Tried to figure out the manual install, but ended up using the Envy script. Still a noob, but learning fast!

MSI K8NGM2-FID, onboard nvidia 6150/430, amd64 (but running i386 for now)

---

### Post by Kevf on 2007-02-14
> **Kevf said:**
> I've used this link:

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

Post I've made in that thread:

Whoe It worked (got the fakeroot package installed)!! But when Grub loads I see two kernels (I've got a dual boot with xp). The one that loads on default works, But is there anything I should do about the other? Futhermore I have to recompile the kernel after each update. Meaning?

doesn't work at all. FGLRXINFO still says mesa.

---

### Post by apjone on 2007-02-14
I have a Nvidia GF 7 series and used the [Envy script]("http://albertomilone.com/")
Did nothing special and just re run it if xorg breaks. Simple and it works.

---

### Post by luke16 on 2007-02-14
1) 01:00.0 0300: 10de:0295 (rev a1)
2) 01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
*I have a 7950GT
3) Followed commands found at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) then rebooted

---

### Post by Migs on 2007-02-14
01:00.0 0300: 10de:01d8 (rev a1)
GeForce Go 7400
256 MB

VBIOS:05.72.22.26.a1

No additional tweaks needed, just manually installed the nvidia binary drivers.

Good look with your project tseliot!

---

### Post by r4ik on 2007-02-14
nVidia® GeForce™ GE 7300 SE PCI-Express + TV-out 

Hakix

---

### Post by opus_ubu on 2007-02-21
This is a new installation by a newbie.

Steps taken:
I have installed Ubuntu Server 6.10 Edgy Eft On Pentium 5
Then I have installed a desk top on it.
The graphics card I have in my machine is nVidia Riva TNT 2 64.
I have installed the nvidia drivers and rebooted my machine.
I followed the steps on this page: [http://www.ubuntuforums.org/showthread.php?t=233241](http://www.ubuntuforums.org/showthread.php?t=233241)
X windows wouldn&#8217;t load giving me the error screen with the option to view the log.
Then I remembered reading somewhere that I should change the driver name from nv to nvidia.  So I went into the new xorg.conf file placed there after running this command sudo nvidia-xconfig and looked through the parameters.
I noticed that for the graphics card driver the name was nvidia,
So I typed the value nv for this param just to try, and boom, every thing started to work.

---

### Post by majoridiot on 2007-02-21
nvidia geforce 5500FX agp, 256MB
nvidia geforce 5500FX pci, 128MB

i let alberto install the driver (thanks, man)-

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

then config'd twinview and a third mythtv screen with:

```
sudo nvidia-settings
```

couldn't be much simpler than that! :D

---

### Post by adamthompson on 2007-02-25
1) 00:05.0 0300: 10de:0242 (rev a2)

2) NVIDIA integrated graphics 6100 (on a Biostar Tforce 6100-939 mobo)

3) I had to use Method 2 from this guide: [http://albertomilone.com/latest_nvidia_udsf_edgy.html]("http://albertomilone.com/latest_nvidia_udsf_edgy.html"). Then I had to go to Main Menu > System Tools > NVIDIA X Server Settings. Once I got the settings I wanted, I had to click on the "Save to X Configuration File" button (in NVIDIA X Server Settings), then click the "Show Preview" button, then copy and paste over /etc/X11/xorg.conf. If I didn't go through that exact procedure, then the display reverted to the wrong resolution whenever I restarted. Also, I have to fix my sound, which doesn't work since installing the 9746 driver.

---

### Post by dmcdante on 2007-02-25
nvidia 7300GS, dualscreen layout

installed the driver from the nvidia page, ran nvidia-xconfig and got the whole shebang :)

i actually haven't had any easier installation than the nvidia driver in ages!

greets, dante

---

### Post by ridgeone on 2007-02-26
0000:05:00.0 0300: 10de:00c3 (rev a2)
nVidia Geforce 6800GT (Asus PCI Express x16)
tweak - edited xorg.conf  to include 1280x768 @60Hz for my 32" Viewsonic N3200W LCDTV (native res is 1366x768 - haven't tried that yet though - afraid! (edit: I actually read my manual and the max input resolution is in fact 1280x768 @ 60hz - it looks good so I'm happy.)

downloaded required packages using Synaptic and rebooted. All is well running 6.06.1 LTS Dapper Drake.

This is my first Linux distro and other than a slight leanring curve and LOTS of reading and searching How Tos to get everything to work right, I'm a very happy newcomer. These forums are priceless. Thanx to all here that are dedicated to making Linux a viable option to Windows. I plan on sticking around to learn and hopefully contribute! First post too BTW -

---

### Post by Segovia on 2007-03-01
1. 05:00.0 0300: 10de:0092 (rev a1)
2. nVidia Corporation GeForce 7800 GT (rev a1)
3. Needed to add *nvidia-settings -l* to *System > Preferences > Sessions > Startup Programs* to get changes (such as gamma adjustments) made in *nvidia-settings* to stick.

---

### Post by majoridiot on 2007-03-01
> **Segovia said:**
> 3. Needed to add *nvidia-settings -l* to *System > Preferences > Sessions > Startup Programs* to get changes (such as gamma adjustments) made in *nvidia-settings* to stick.

GREAT TIP!

that fixed a lot of little annoyances and has sped things up considerably for me.

thanks for than one, man.  i'm writing it down. :D

---

### Post by BrianK on 2007-03-05
01:00.0 0300: 10de:0338 (rev a1)
Nvidia Quadro FX 3000 (NV35GL)

- I'm running dual heads.  For some reason, with this card, the nvidia-settings program did not have the "XSerer Display Configuration Settings" section, so I copied my xorg.conf from another machine with an GeForce FX5900 running dual heads to this one, which worked.
- Also, in the "metamodes" section of the xorg.conf file, I had to remove, by hand, all resolutions larger than the one I was using or I would get a scrolling desktop (desktop that is larger than the screen area, so moving the mouse outside the visible area would move the desktop around).
- FYI: the "Method 1" method of installing the nvidia drivers as described on [this page](https://help.ubuntu.com/community/Latest_Nvidia_Dapper) simply does not work - at least it hasn't worked on the last 3 machines I've tried when installing Ubuntu 6.10. **edit:** So I just realized that the doc I linked is for 6.06 - that's Dapper, right?  RFE on the docs on the website - put version number in rather than nickname & keep it up to date with the latest release.  :p

---

### Post by entropyfoe on 2007-03-05
00:05.0 0300 10de:0240 (rev a2)  is the output from lspci -n |grep 0300

It is on a Asus m2npv-vm MB.   Running 6.10 xubuntu Edgy.

To load Nvidia driver:

Tried synaptic -did not work. 
 Installed Automatix, it did the trick.   

 Saved from seizure inducing VESA driver  for this Nvidia 6150 chip.
The Nvidia driver needed no tweaking  (so far), and seems way faster than the VESA which was unusable.

-Jay

(btw onboard sound, ethernet, USB thumbdrive work with no fussing,
 printer, text OK, pictures ?  Scanner not recognized yet.)

---

### Post by Duffy on 2007-03-10
I simply used Automatix2 to install the Nvidea driver and upon reboot, it worked perfectly. 3D games that did not work before, worked perfectly.

---

### Post by al1b1 on 2007-03-10
1)01:09.0 0300: 10de:0326 (rev a1)
2) Nvidia 5500FX
3) Used envy script
Had to edit x.org- added renderaccel, NvAGP, #BusID,
Had to add nvidia to /etc/modules
Had to add agpgart and intel_agp to /etc/modprobe.d/blacklist and /etc/hotplug/blacklist   
Mainly due to also having a onboard intel card

---

### Post by avishalom on 2007-03-11
m2npv asus,  
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)

64 bit dual core amd
64 bit version of ubuntu desktop
tried 

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

didn't work right , i didn't get the 1680x 1050 resolution just the usual 1024x768 800x600 another small one maybe x480 , and a 
VERY WEIRD 832x624

envy wouldn't work well either
auto would crash the display, and i had to revert to an old copy of the xorg file
manual install of the drivers wouldn't kick in the right driver either

then 
ii installed the latest drivers again (top link); 
then in the xorg. file, i deleted all but the 1680x1050 , from the 24 bit depth
and only then did it kick in.
(i was able to run the nvidia settings from the menu)
it is still not perfect, 
but it works.

EDIT  : 
i tried the method 2 from that link 
 all i needed was to run dpkg-reconfigure again and to clear all resolutions but the native 1680x1050

---

### Post by RedFish on 2007-03-11
1. 01:00.0 0300: 10de:0286 (rev a1)
2. nVidia GeForce 4200 Go 64 RAM
3. No tweaking needed

---

### Post by uboltun on 2007-03-13
The Hardware:
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner] (rev a4)

Xorg config:
Section "Device"
        Driver  "nvidia"
        Option  "RenderAccel"   "true"
        Option  "AllowGLXWithComposite" "true"
        Identifier "NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
        Option "DPMS" "true"
        Option "NvAGP" "1"
EndSection

How the driver was installed:
Download and install NVIDIA-Linux-x86-1.0-7184-pkg1.run form NVIDIA website

---

### Post by eggdeng on 2007-03-13
1) 01:00.0 0300: 10de:002d (rev 15)
2)"NVIDIA RIVA TNT2 Model 64/Model 64 Pro 32MB"
3) On Edgy generic kernel using legacy driver as per instructions in [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Seems that there's no way to get Compiz / Beryl working with the legacy driver though.

---

### Post by eggdeng on 2007-03-16
1) 01:00.0 0300: 10de:0176 (rev a3)

2) Nvidia GeForce4 420 Go 32M

3)Followed the howto at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to get the driver onto a default Edgy install. It doesn't work with the default generic kernel so a reboot was needed for it to start working with the i386 kernel. Followed [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) to get Beryl up and just needed to set ```
DefaultDepth    24
``` in the Screen section of xorg.conf.

---

### Post by Snookered on 2007-03-17
Nvidia PWA-G4000PRO, made for Compaq, installed on Compaq mobo, PIII 800MHz, 512 ram, worked on installation of Kubuntu.
Very old card.

---

### Post by x1a4 on 2007-03-30
MSI board with **Nvidia GeForce FX 5200** chipset.  

*lspci -n | grep 0300*
(standard input):12:01:00.0 0300: 10de:0322 (rev a1)

*lspci | grep VGA*
(standard input):12:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Had no problems during or after I installed Xubuntu (Edgy).  

Installed the latest (9755) driver from [Nvidia.com](http://www.nvidia.com/) thusly: 

1) Killed X
2) In a console executed *sudo sh ~/downloads/NVIDIA-Linux-x86-1.0-9755-pkg1.run*
    (~/downloads/ is where I downloaded the driver to)
3) Followed driver installer prompts.
4) Started X

Things worked fine, and no tweaks were necessary, but I didn't get the most of my card so I modified my _/etc/X11/xorg.conf_ like so: 
```

Section "Module"
    # Load           "GLCore"
    Load           "dbe"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
    Load           "v4l"
    # Load           "dri"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "MSI GeForce FX 5200"
    Screen          0
    Option         "NoLogo" "false"
    # AGP support
    # 0 disable AGP
    # 1 use NVAGP (Nvidia AGP module), if possible
    # 2 use AGPGART (kernel AGP module), if possible
    # 3 try AGPGART; if that fails, try NVAGP (nvidia default)
    Option         "NvAgp" "1"
    Option         "AddARGBGLXVisuals" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Accel" "true"
    Option         "RenderAccel" "true"
    Option         "DigitalVibrance" "0"
    # enable overclocking
    Option "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Sceptre"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sceptre"
    DefaultDepth    24
    Option         "metamodes" "1024x768_75 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "Overlay" "true"
    Option         "CIOverlay" "true"
    Option         "TransparentIndex" "60"
    Option         "OverlayDefaultVisual" "false"
    Option         "SWCursor" "false"
    Option         "HWCursor" "true"
    Option         "CursorShadow" "off"
    Option         "CursorShadowAlpha" "64"
    Option         "CursorShadowXOffset" "4"
    Option         "CursorShadowYOffset" "2"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

# Section "DRI"
#   Mode 0666 
# EndSection

```
I also set the following environment variables: 
```

# OpenGL settings
# Anti-aliasing mode
# 0 	FSAA disabled
# 1 	2x Bilinear Multisampling
# 2 	2x Quincunx Multisampling
# 3 	FSAA disabled
# 4 	4x Bilinear Multisampling
# 5 	4x Gaussian Multisampling
# 6 	2x Bilinear Multisampling by 4x Supersampling
# 7 	4x Bilinear Multisampling by 4x Supersampling
# 8 	4x Bilinear Multisampling by 2x Supersampling 
# (available on GeForce FX and later GPUs; not available on Quadro GPUs)
setenv __GL_FSAA_MODE 2
# Anisotropic texture filtering
# 0  No anisotropic filtering
# 1  2x anisotropic filtering
# 2  4x anisotropic filtering
# 3  8x anisotropic filtering
# 4  16x anisotropic filtering
# (4x and greater are only available on GeForce3 or newer GPUs;
# 16x is only available on GeForce 6800 or newer GPUs.)
setenv __GL_LOG_MAX_ANISO 1
# Vblank syncing
# non-zero value will force glXSwapBuffers to sync to monitor's vertical refresh
# (perform a swap only during the vertical blanking period). 
setenv __GL_SYNC_TO_VBLANK 1
# TwinView only
# setenv __GL_SYNC_DISPLAY_DEVICE
# CPU-specific features
# non-zero value inhibits use of CPU-specific features eg: MMX, SSE, 3DNOW
setenv __GL_FORCE_GENERIC_CPU 0

```

---

### Post by 16777216 on 2007-03-31
Thank you

---

### Post by x1a4 on 2007-03-31
> **16777216 said:**
> How is this done and what are all of them? ( sorry to hijack the thread ) :confused:

Check your private messages for the answer, and for future reference use private messages to ask about stuff in threads like these.

---

### Post by jbumgar on 2007-03-31
I used the Nvidia Intel Integrated doc.

Then d/l'd and used Envy.

Works like a dream.

---

### Post by hikaricore on 2007-03-31
> **x1a4 said:**
> for future reference use private messages to ask about stuff in threads like these.

Seems kinda weak if you ask me.

Now the next person who stumbles onto your setenv vars trying to get their nvida card
working/working better will ask the same question due to the answer not being in any
of your posts.  Edgy users will be even more confused as setenv no longer functions and
to the best of my knowledge commands are issued through export.

*shrug*  I just see this fueling more questions about the process.

---

### Post by avidesh on 2007-04-05
is this same as Geforce2 MX/MX 400?

---

### Post by Bachstelze on 2007-04-07
01:00.0 0300: 10de:0398 (rev a1)
GeForce Go 7600 (on Asus A6JM laptop)
No additional tweaking needed

01:00.0 0300: 10de:0179 (rev a3)
GeForce Go 440 64M (*lspci* says it's a 420 32M but that's most likely a mistake as [nvidia](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html) says otherwise, error reported - on Compaq Presario R3000 laptop)
No additional tweaking needed but is supported **only** by drivers versions up to (and including) 96xx


Ubuntu packages and installer from nvidia both worked without a problem on both laptops, I haven't tried Envy and most certainly never will.

---

### Post by abuthemagician on 2007-04-20
1. 01:00.0 0300: 10de:01d8 (rev a1)
Nvidia Quadro NVS 120m (Lists as a Geforce 7400 Go) on a Dell Latitude D820
Nothing special needed. Used Nvidia settings to get Twinview working

---

### Post by Rob Alderson on 2007-04-20
01:00.0 0300: 10de:0326 (rev a1)
Geforce FX5500 256Mb
No tweaking whatsoever, woudln't know what to tweak anyway ;)

---

### Post by mrli on 2007-04-21
1. 01:00.0 0300: 10de:0391 (rev a1)
2. eVga nVidia GeForce 7600 GT 256MB 
3. No tweaking needed

---

### Post by electronikjunkie on 2007-04-22
envy in the house. just ```
sudo envy -t
``` and  forget about it...

---

### Post by mansoniaberlin on 2007-04-23
Athlon XP 1800/256Megabyte/Gforce2 mx400

Was a tricky thing... After several differnt tries (and several crashed x-server) I finally did it. I installed the nvidia-glx-driver via synaptic, after that procedure i opened etc/default/linux-restricted-modules-common. At the end of the page i edit Diasbled Modules "nv" to  Disabeld Modules "". Then I openend  etc/X11/xorg.conf. Under Section "Device" I added      Option         "AllowGLXWithComposite" "true". Never activate the Driver with that trashy restricted driver Manager!!!
Just reboot and there you are!

(takes me the whole weekend to figure it out - I am no programmer....)
Bye 
Andreas

---

### Post by jollemeyer on 2007-04-24
01:00.0 0300: 10de:0182 (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440SE AGP 8x] (rev a2)
No tweaking needed. It was as easy as it could be. I was using the Howto here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

---

### Post by craigyjack on 2007-04-24
Is this only for Edgy users, or are you now incorporating Feisty Fawn users?
And is this only referring to the nvidia drivers from nvidia's website, or also the nvidia drivers installed through Feisty Fawn's new "restricted drivers manager".

Because I originally used the nvidia drivers through the restricted manager, had a few problems, so I thought I'd try the drivers from the nvidia website [the nvidia drivers from their website worked like a charm on Edgy, and not to criticize, but the Envy program messed up X on my old Edgy, and I found the using the .run from the nvidia website worked much easier from me]. Well now, the nvidia drivers from their website do not work in Feisty Fawn and had to compile a module for the new kernel, and ended up just farkling up the X server.

So I went back the nvidia drivers from the restricted manager, and set about fixing the flaws that came with it. I ended up fixing everything [the problems were with resolution, refresh rate, and then visual corruption add my desired resolution]. I got it all fixed and I can now have it at my desired resolution (which was 1440x900) and with no visual corruption.

I would like to post what I did to get the nvidia drivers form the restricted manager to work properly as I have seen many people with the same problems, and I thought it should be stickyed. Wondering if this thread is the right thread at all to post steps for Feisty Fawn nvidia driver in the restricted driver manager.

Let me know if this is the right place and I can post, or direct me to a place where I can post, I'd like to help people with the nvidia driver in Feisty Fawn, since Feisty added in the new manager.
Thanks,
Craig

---

### Post by smsmith050 on 2007-04-24
Monitor Samsung 906BW
Video GeForce4 MX 4000
Using Synaptic installed 
nvidia-glx
nvidia-settings
nvidia-xconfig

ran nvidia-xconfig 
rebooted
xserver crashed, could not find module 'nvidia'

edited /etc/X11/sorg.conf commented out Driver   "nvidia" added Driver  "nv"

ran startx

task bar showed a PCI card 

I clicked it and was informed that I had to accept the non-free restricted driver which I did

Ubuntu downloaded something, driver module?

I rebooted

I could not select my monitors native resolution 1440x900

I edited /etc/X11/xorg.conf.

I changed the 1440x1440 resolution selections to 1440x900

I killed x and restarted it.

I selected 1440x900

Only remaining issue is the V refresh  is 50Hz.

I might need to create a custome modeline to make that work but I am happy with 50Hz for now

---

### Post by sleepyjon on 2007-04-25
I have an NVIDIA Geforce 6200.

I followed this guide to step 3:

[http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/)

Then went to telinit 1, and ran the nvidia driver install from there. I had to edit the xorg.conf for the display settings.

---

### Post by dansolo on 2007-04-25
GeforceGo 7400 on a HP Pavillion dv6299

- 01:00.0 0300: 10de:01d8 (rev a1)
- 01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
- After installing the driver I had to change the driver section of xorg.conf changing the line BusId in this way:

   BusID		"PCI:1:0:0"

After that I user the nvidia-settings to choose the correct resolution 1280 * 800 and it all works fine

---

### Post by rumli on 2007-04-25
1. 02:00.0 0300: 10de:01df (rev a1)
2. 02:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
3. I used the steps listed [here]("http://www.cs.cornell.edu/~djm/ubuntu/index.html#nvidia-driver").
Basically I first reconfiguring my x server config from scratch:
```
sudo dpkg-reconfigure xserver-xorg
```
During the reconfiguring, I chose the Vesa driver, I chose the "Medium" method for selecting the monitor characteristics, and I chose "1024x768 @ 60Hz" for the monitor's best video mode.
Then I installed and enabled the nVidia driver:
```
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
```
Then I restarted X by pressing CTRL-ALT-BACKSPACE.
Then I configured my dual monitor and screen resolution setting using:
```
sudo nvidia-settings
```

---

### Post by medya on 2007-04-25
I have Nvidia Rivia TNT2  32 MB
and I installed it  [this way]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")

---

### Post by DeadPlanet on 2007-04-25
greetings,

Ive gotten my 6600 nvidia to work, I followed the many posted howtos and found that at first glance they didn't work.  Upon restarting x, the x-server would crash.
The NEW step I took was interesting.  
After doing all the right steps like normal, turn off and unplug the computer for about 10 minutes.
Upon restarting, the x-server ran flawlwssly and glxgears, x-plane, etc all seem to work very well.
I tried the above methods for about two days to my complete frustration, and found that simply letting the hardware "reset" did the trick.  
I hope this less-than-technical idea helps, It totally worked for me.  
Ken

---

### Post by flade on 2007-04-27
0000:01:00.0 0300: 10de:002d (rev 15)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

I did everything like rumli did but nvidia driver just doesn't work (api mismatch nvidia and kernel driver wrong version or something like that)

What to do ?

22:00 - It's alive.
What i did was installing through apt nvidia legacy driver and nvidia driver works. 

First problem solved.
Second is screen resolution. For some reason 1440x900 could not be selected from GUI Screen resolution. in xorg.conf everything ok.


regards

---

### Post by ridgeland on 2007-04-29
This is my second post.
For 6.10 I posted four steps or so and they worked.
This time for 7.04 I tried the Add/Remove for nvidia and the command line
X crashed.  I copied back the original settings.
Then I downloaded Envy 0.9.2
This installed and from the GUI from the menu worked great!
Thank you tseliot.

Oh yeah:
01:00.0 0300: 10de:0110 (rev b2)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
(GeForce2 MX400 - AGP card)

---

### Post by pkslot on 2007-04-29
1)    01:00.0 0300: 10de:0110 (rev a1)

2)    Nvidia geforce 2 mx/mx 400

3)    Fresh installed ubuntu 7.04. Used Envy GUI mode. Restricted driver manager does not install "deep" enough!

---

### Post by stchman on 2007-05-01
I have a procedure to get Nvidia drivers working here:

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Geforce FX 5700 Ultra AGP 8X
Geforce 7600GT PCI-E

Or I use Envy.

---

### Post by GoBieN on 2007-05-02
Nvidia geforce 7200 GO 128 in HP pavilion dv6017ea:
Download script from nvidia site and run (everytime you get a kernel upgrade).

Envy won't install, missing dependency xserver-xorg-dev :s

---

### Post by NewDisciple on 2007-05-03
1. 01:00.0 0300: 10de:0098 (rev a1)
2. 01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7800 (rev a1)

apt-get install nvidia-glx

Changed in x-org "nv" to "nvidia" and added "1920x1200" to screen mode.

Current driver 9631
Just now updated to 9755 via Synaptic.  Required complete shutdown and restart.

---

### Post by quail-linux on 2007-05-04
lspci -n | grep 0300
01:00.0 0300: 10de:0185 (rev c1)

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

cat /etc/X11/xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        65536
        Option          "AddARGBGLXVisuals"     "True"
        Option          "TripleBuffer"          "True"
        Option          "UseEDID"               "False"
EndSection

Section "Monitor"
        Identifier      "IBM G96"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
        Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
        Modeline        "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
        Modeline        "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "IBM G96"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024_75.00" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by RockinRob2258 on 2007-05-06
0000:01:00.0 0300: 10de:0322 (rev a1)
model:  Nvidia GeForceFX 5200

tweakings and notes:  Everything worked at first in early spring, then something changed, I think perhaps when I installed VMware Workstation 6.0 Beta.  Anyway, afterward, acceleration and screensavers caused X to reset.  I changed the section in the xorg.conf file
     load module "glx"
to 
    load module "opengl"


Everything seems to work again.  I'm still somewhat new to Linux, so if I made any mistakes on what section I changed, feel free to comment.  I know the editing I did was "glx" to "opengl"

---

### Post by Pollywoggy on 2007-05-16
I have a Geforce 7600 GS and the Nvidia driver would not load after I upgraded from Edgy to Feisty.
The way I got it to work is by first removing all the nvidia packages.  I purged them to be more precise.

Then I did 'apt-get install nvidia-glx-new' and that fixed things, since I already had a working configuration.
Now I have just two Nvidia packages installed:

ii  nvidia-glx-new                             1.0.9755+2.6.20.5-15.20 
ii  nvidia-kernel-common                       20051028+1ubuntu7       


I installed xfce4 today and I did get some sort of error concerning Nvidia drivers after I did that, but everything still works and I have not seen that error since.

---

### Post by moopere on 2007-05-19
> **mansoniaberlin said:**
> i opened etc/default/linux-restricted-modules-common. At the end of the page i edit Diasbled Modules "nv" to  Disabeld Modules "". 

Thankyou thankyou thankyou!  This is it.  


> **mansoniaberlin said:**
>  Never activate the Driver with that trashy restricted driver Manager!!!

Yep, good advice.  I've managed to munge up all my nvidia machines here!  Thanks very much for your pointers above.

Cheers,
Craig

---

### Post by dannyboy79 on 2007-05-21
> **GoBieN said:**
> Nvidia geforce 7200 GO 128 in HP pavilion dv6017ea:
Download script from nvidia site and run (everytime you get a kernel upgrade).

Envy won't install, missing dependency xserver-xorg-dev :s

You know, I told him this awhile ago but apparently he didn't fix that issue. Anyway, all you would have had to do is:
sudo aptitude install xserver-xorg-dev
and then run envy.

---

### Post by dannyboy79 on 2007-05-21
Just so you are aware, I believe there is a bug in the newest Envy Unstable script (i think it's 0.9.4).

 I troubleshot the API mismatch for about 2 hours with the help of a forum user that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim (IM). 

He tried to have me add blacklist nvidia_new to the /etc/modprobe.d/blacklist file, BUT that still didn't work, NO module was loading when we tried that and that fix DID work for psyke83 so we weren't sure why it didn't work on my machine? I also ensure that my /etc/defaults/linux-blah-blah-blah-common DID have the Disabled MOdules = "nv" within it and it STILL DIDN'T WORKL.

It turned out that the Envy unstable program had a bug and didn't do somethign correctly (if this is an untrue statement, I am only conveying the message that psyke83 informed me of. He said that he tried telling the author of Envy but the author of Envy said there was no bug. Then psyke83 even tried the unstable version on his own computer and tried to install 100.xx.xx and he got the same API mismatch error). 

So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable.

---

### Post by Pumalite on 2007-05-28
> **dannyboy79 said:**
> Just so you are aware, I believe there is a bug in the newest Envy Unstable script (i think it's 0.9.4).

 I troubleshot the API mismatch for about 2 hours with the help of a forum user that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim (IM). 

He tried to have me add blacklist nvidia_new to the /etc/modprobe.d/blacklist file, BUT that still didn't work, NO module was loading when we tried that and that fix DID work for psyke83 so we weren't sure why it didn't work on my machine? I also ensure that my /etc/defaults/linux-blah-blah-blah-common DID have the Disabled MOdules = "nv" within it and it STILL DIDN'T WORKL.

It turned out that the Envy unstable program had a bug and didn't do somethign correctly (if this is an untrue statement, I am only conveying the message that psyke83 informed me of. He said that he tried telling the author of Envy but the author of Envy said there was no bug. Then psyke83 even tried the unstable version on his own computer and tried to install 100.xx.xx and he got the same API mismatch error). 

So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable.

I removed the generic driver, made sure I had 'make', 'autoconf', kernel-headers, gcc, etc. Downloaded latest NVIDIA Driver 9755, went to init 3, became root, and coded sh /Path/To/Driver/NVIDIA-Linux-x86-1.0-9755-pkg1.run; answer all the questions and had my driver installed.

01:00.0 0300: 10de:02e1 (rev a2)
N7600GS GeForce
No tweaking

BTW, I installed Ubuntu yesterday.

---

### Post by dannyboy79 on 2007-05-29
well if you were just going to use the 9755 than all you had to do was use the built in Fiesty Restricted Module Manager than which is under System, Admin, Restricted Modules pull down. THen just check Nvidia driver and it should install the correct driver for your card which is the 9755. I was trying to the latest unstable Envy because I wanted to try out the latest Nvidia 100.xx.xx driver  due to random freezes I was having when doing a gksudo gedit. So, I just reinstalled after trying everything in power to troubleshoot this issue and all is well now. I used the restricted module manager to install 9755 and I using Desktop Effects and Mythtv which is awesome so all is well. One thing I have not done like I did with the other install which went bad was to use Automatix2, I DIDN'T use it this time and am just installing stufgf as I go instead of use Automatix2 to do everything in one swoop. It's slower and taking longer but I am learning and don't have the freeze issue as of yet, knock on wood!
So it must be a library issue or software conflicts because hardware didn't change.

---

### Post by Genecks on 2007-05-29
After reformating and reinstalling Kubuntu various times because of irrelevant, unhelpful, hurting, crappy threads, I found this nice thread.

My graphics card: NVidia GeForce 6150 LE
Tweaking: Plenty involved
Method for installation: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

I used Method 1, which is actually the method that uses the Internet.
Someone should really clean that page up, by the way.

1) I made sure my Internet connection was active.
2) I followed the directions.
3) I checked the linked pages during "3) Install the Nvidia driver:" to make sure I was getting the right driver.
4) I eventually installed it all and hit "ctrl+alt+backspace"

I ran into a problem after this, however.
I began to notice the mouse cursor was gone.

I looked for some quick way to solve this.
I had to make sure I was in the konsole. I made sure I was in sudo, and I made sure I would be able to edit the xorg.conf 

I edited the section "Device" within xorg.conf. I'm not talking about the inputdevice section. I'm talking about the section "Device."

I added the line

Option "HWCursor" "off"

Afterwards, I saved the file.
I hit ctrl+alt+backspace

Make sure you edit the xorg.conf file with the added line to fix the cursor before restarting the GUI!!!

And whalah, I finally had a nice screen size and corrected mouse.

==update==
I'm actually doing this the second time, but it doesn't seem to work. I'm playing with a different method of doing this, and I'll report back later today.

Alright, for some odd reason, Method 1 isn't working again. However, I'm starting to understand Linux, so I switch methods to complete the task of editing xorg.conf
Apparently, for some odd reason, I wasn't able to create the "NVIDIA-Settings.desktop" file using KATE.
Therefore, I decided to use sudo nano, which reminds me of edit back in the days of windows.

From there, I created the file with "sudo nano -w /usr/share/applications/NVIDIA-Settings.desktop"
That created the file. Afterwards, I had to input the information as I would have done in method 1.
Afterwards I hit the control key, which is represented by the ^ symbols. And I saved the stuff.
I remembered to edit xorg.conf and fix the cursor problem. Afterwards, I hit ctrl+alt+backspace.
Everything looks fine once more.

Apparently, there are a variety of ways to solve this problem, but one often works in the end.

---

### Post by SkyNet2029 on 2007-06-12
03:09.0 0300: 10de:0185 (rev c1)
NVidia GeForce MX4000(AGP8x) 128MB GPU
No tweaking needed.

*Beryl required not using any translucency, otherwise composite manager crashes. Weird but no biggie.

Kudos on the excellent thread.

---

### Post by gorankallqvist on 2007-06-12
Hi!
Here's how I managed to get the nvidia (proprietary) driver to work
1) lspci: 02:00.0 0300: 10de:0393 (rev a1)
2) nvidia 7300 GT 256 MB
3) I had to disable APCI in BIOS (MoBo: Asus M2N, AMD 64 x2 4600+)
Now the card works like a charm.:-)
BTW: I installed the nvidia drivers using the envy tool. Excellent tool!
Greetings, Göran K

---

### Post by dannyboy79 on 2007-06-12
> **gorankallqvist said:**
> Hi!
Here's how I managed to get the nvidia (proprietary) driver to work
1) lspci: 02:00.0 0300: 10de:0393 (rev a1)
2) nvidia 7300 GT 256 MB
3) I had to disable APCI in BIOS (MoBo: Asus M2N, AMD 64 x2 4600+)
Now the card works like a charm.:-)
BTW: I installed the nvidia drivers using the envy tool. Excellent tool!
Greetings, Göran K

did you mean acpi or apic???  I don't believe there is such a thing as apci.

---

### Post by C.S.Cameron on 2007-06-13
I've tried Linux several times in the past, almost got Acad R14 working with wine.
When Dell started installing Ubuntu I thought I would give it another try.
I was trying to figure out what to do with a 4GB Kingston USB traveler I had bought.
Installed Ubuntu on it, I was impressed. 
Managed to get the Nvidia restricted drivers working on the living room computer which uses a Nvidia 7800? card with a 50" 1080P monitor, but then got the X failed screens on my office computer with an 8800 GTS.
I tried everything, reformatted then learned "sudo co /etc/X11/xorg.conf_backup ...". This helped alot.
This morning I again tried Envy. This time I read the instructions thoroughly.
I again got  X failure on boot, but this time I had made a note to use "sudo envy -t".
I tried option 2 remove. 
The computer did a bunch of stuff, looking like it was trying to install the drivers again, instead of removing them. 
I was again trying to get prepared to reformat my thumbdrive.
Went to have a smoke, when I got back the Ubuntu desktop was asking for my user name. i was so exited I flubbed 3 times.
Wow, next I tried Nvidia settings, double Wow. 
Then I tried Acad 2000 running under wine. 
Yesterday I was getting 3 fps rotating a complex shaded model degrading to flat shaded. Now it is like magic.
I figured out how to copy the new xorg.conf to desktop then to X11.
Everything is working beyond my dreams.
Cork

---

### Post by nyanga on 2007-06-24
01:00.0 0300: 10de:0140 (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
No tweaking needed

---

### Post by mpneerkaje on 2007-06-25
1) 00:0d.0 0300: 10de:03d0 (rev a2)

2) GeForce 6100 nForce 430

3) No tweaking needed, but had to install drivers from repository, and run nvidia-settings after that to get a good screen resolution.

---

### Post by sab0403 on 2007-07-02
1) 01:00.0 0300: 10de:0171 (rev a3)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
3) I'll post what I did in order:

[INDENT]i) Followed [the guide]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") (method 1).
[INDENT]ia) After step 5, I went to the "Problems" section and followed step 7 as indicated; then continued with method 1.[/INDENT]
ii) Since I could ONLY get 800x600, I followed step 10 of the "Problems" section. This only enabled 800x600 and 640x480 for me, though, so then I modified the "Monitor" section on the xorg.conf file by adding these lines:

```
HorizSync      28-61
VertRefresh    48-75
```

Which specify what's my monitor Horizontal Sync and Vertical Refresh range. These would change according to the monitor, of course... google for your monitor's model and "vertical refresh", and/or "horizontal sync". That's how I found them (my monitor is a Sony SDM-S51, btw).

I had also added a custom modeline using [this tutorial]("http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline"), but I think it isn't necessary. However, I put the information so if someone needs it, they have it.

iii) BERYL. As I tried to run the basic desktop effects already installed in Ubuntu, I ran into the following error:

```
Cannot enable desktop effects. The Composite extension is not available.
```

Which really threw me off. Why would it tell me this *after* I installed the updated drivers?

Well, it turns out the guide sets these off by default. So I went right ahead and found this section on my xorg.conf:

```
Section "Extensions"
     Option "Composite" "**Disabled**"
EndSection
```

and simply changed the "Disabled" (in bold) for a "1". I also added this to the "Screen" section:

```
Option "addARGBGLXVisuals" "True"
```

And all set! I followed the [guide to install Beryl]("http://ubuntuforums.org/showthread.php?t=263851"), and (this is very important) **skipped the section on installing the nVidia drivers** (since I had just installed them). This is important because if you follow the instructions there with this particular model of card, you'll trash all your previous effort. Trust me. I know.

Any questions at all with this particular model of card, feel free to PM/e-mail me. Cheers! :popcorn:

[/INDENT]

I hope this helps. I had a lot of problems with the resolution (which is solved in step ii) but I finally resolved it.

EDIT: Props to [this thread]("http://ubuntuforums.org/showthread.php?t=487372&highlight=desktop+effects+composite") and [this post]("http://ubuntuforums.org/showpost.php?p=2514042&postcount=2"), where I got the info on the "Composite not available" problem.

---

### Post by bsawler on 2007-07-03
1. 01:00.0 0300: 10de:01d6 (rev a1)
2. nVidia Corporation GeForce Go 7200
3. No tweaking required

The maximum resolution that I can get is 1280x800 at 50Hz.  I think the resolution needs to be bigger cause the fonts/sizes are too big, fuzzy and awful.  So bad that I put my winxp CD in, but it now does not recognize my harddrive so thankfully I am left with Ubuntu.  I hope I can fix it to my likings.

---

### Post by skrimpy on 2007-07-04
1. 01:00.0 0300: 10de:0326 (rev a1)
2. e-GeForce FX 5500 DDR 256mb AGP 8x/4x
3. My tweaking:

I got my card working initially with this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

I used the Envy script to clean out and reinstall the Nvidia driver once I had the card working initially.  I do think this helped - my graphics rendering improved a lot after running the script.  More info on Envy:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

I used this thread to get desktop effects working - using the terminal command in post #21:
[http://ubuntuforums.org/showthread.php?t=419058&highlight=desktop+effects&page=3](http://ubuntuforums.org/showthread.php?t=419058&highlight=desktop+effects&page=3)

I then tinkered in Firefox using this thread (post #2 was most helpful):

[http://ubuntuforums.org/showthread.php?t=439357&highlight=firefox+font+looks+bad](http://ubuntuforums.org/showthread.php?t=439357&highlight=firefox+font+looks+bad)

My desktop "wobbly windows" effects are working, My fonts are rendering smoothly, and my graphics look very smooth.  Overall, I am pleased thus far.

---

### Post by mattyrigby00 on 2007-07-05
1) 00:05.0 0300: 10de:0240 (rev a2)
2) nvidia 6150 (onboard to m2npv-mx)
3) i installed it using normal instructions and it was fine, but i got an xorg.conf error every reboot and said to read the readme common error section. the readme it said to boot the kernel with noapic turned on, and another site said other nvidia-related packages being installed can cause it - so i did this:

used adept manager to remove all nvidia packages, then installed the driver and selected NO to changing xorg.conf (staying at the "nv" driver), then edited /boot/grub/menu.lst, went to this section:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8a820cc1-4775-452e-820d-797d7b9f65f0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
then added noapic onto the end of the root= line so it was:
```
root=UUID=8a820cc1-4775-452e-820d-797d7b9f65f0 ro quiet splash noapic
```
,  then did  sudo dpkg-reconfigure -phigh xserver-xorg , picked nvidia as the graphics driver, restarted and it worked ;p happily using beryl now, with 1280x1024 res. also the dpkg thing let me change the resolution it boots with, with the every reboot having to reinstall drivers thing it also reset my res to 800x600.
[img]http://img377.imageshack.us/img377/6084/screenshot1xv0.png[/img] :p

---

### Post by Johnged on 2007-07-06
Hi, My computer is an Optima P3, has 256mbr and the processor is 900+ something, the card in question is an nVidia Corp. M64 Riva TNT2 32 mbr I think! I cannot set my screen res. above 800X600 and need to run Google Earth.How do I get me screen res. to at least 1024X740 or whatever I need?

---

### Post by themainliner on 2007-07-06
1)1.0-9755, Installed with the Automatix GUI!

2) Nvidia GeForce 7950 GT

3) NVIDIA X Server Settings fiddling to get my two Viewsonic VX724's working, displaying at 1280 x 1024 in TwinView refreshing at 75 Hz.

It was so easy I almost wept.  All GUI!

---

### Post by azc on 2007-07-09
GeForce 6200

$ lspci -n | grep 0300
01:00.0 0300: 10de:0221 (rev a1)

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

Ubuntu 7.04 Feisty Fawn

$ uname -r
2.6.20-16-generic

---------------------------------------
Followed this thread:
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
---------------------------------------

Needed to install these packages:

linux-source-2.6.20
version: 2.6.20-16.29

build-essential

---------------------------------------
These packages were already installed by default, and so I just left them:
---------------------------------------

linux-headers-2.6.20-16-generic
version: 2.6.20-16.29

nvidia-kernel-common
version: 20051028+1ubuntu7

linux-restricted-modules-2.6.20-16-generic
version: 2.6.20.5-16.29

linux-restricted-modules-common
version: 2.6.20.5-16.29

linux-restricted-modules-generic
version: 2.6.20.16.28.1

restricted-manager
version: 0.20

gcc

---------------------------------------

Next I logged out, ALT+CONTROL+F1

$ sudo /etc/init.d/gdm stop

$ sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

$ sudo reboot

---------------------------------------
Tweaks: Needed to modify xorg.conf
---------------------------------------

Modified:
Section "Screen"

Modes "1024x768" "800x600" "640x480"

To:
Section "Screen"

Modes "1280x1024" "1024x768" "800x600" "640x480"

---------------------------------------
Additional info that may be useful:
(This is what is currently on my box, and the Nvidia driver seems to be working ok.)
---------------------------------------
```

$ dpkg --list linux-headers*

||/ Name                              Version                           
+++-=================================-=================================
un  linux-headers                     <none>                           
un  linux-headers-2.6                 <none>                           
ii  linux-headers-2.6.20-15           2.6.20-15.27                     
ii  linux-headers-2.6.20-15-generic   2.6.20-15.27                     
ii  linux-headers-2.6.20-16           2.6.20-16.29                     
ii  linux-headers-2.6.20-16-generic   2.6.20-16.29                     
ii  linux-headers-generic             2.6.20.16.28.1                   
$ 



$ dpkg --list linux-source*

||/ Name                              Version                          
+++-=================================-=================================
un  linux-source                      <none>                           
un  linux-source-2.6                  <none>                           
ii  linux-source-2.6.20               2.6.20-16.29                     
$ 



$ dpkg --list *nvidia*

||/ Name                              Version                          
+++-=================================-=================================
un  nvidia-glx                        <none>                           
un  nvidia-glx-legacy                 <none>                           
un  nvidia-glx-new                    <none>                           
un  nvidia-kernel-1.0.7184            <none>                           
un  nvidia-kernel-1.0.9631            <none>                           
un  nvidia-kernel-1.0.9755            <none>                           
ii  nvidia-kernel-common              20051028+1ubuntu7                
$ 



$ dpkg --list *restricted*

||/ Name                              Version                          
+++-=================================-=================================
ii  linux-restricted-modules-2.6.20-1 2.6.20.5-15.20                   
ii  linux-restricted-modules-2.6.20-1 2.6.20.5-16.29                   
ii  linux-restricted-modules-common   2.6.20.5-16.29                   
ii  linux-restricted-modules-generic  2.6.20.16.28.1                   
ii  restricted-manager                0.20                             
$ 

```

---

### Post by Meogeo on 2007-07-09
(1) 03:00.0 0300: 10de:02e0 (rev a2)
(2) Nvidia 7600GT
(3) Tweaked

I used envy to uninstall original drivers then reinstalled.

Rebooted

code:-
sudo nvidia-xconfig --add-argb-glx-visuals --depth=24

restarted the x server with Ctrl+Alt+Backspace

Then readjusted settings in Applications/System Tools/Nvidia Settings

Viewsonic VX924 @ 1280x1024 75 Hz

Thanks to tseliot and Yuzem

---

### Post by drytear on 2007-07-13
02:00.0 0300: 10de:0322 (rev a1)
FX5200 128MB
No tweaking needed.

---

### Post by dvenardos on 2007-07-14
nVidia GeForce 7300GT and Samsung Synchmaster 225BW 22inch widescreen via DVI

In order to get correct widescreen native resolution 1680x1050 ran:
sudo dpkg-reconfigure xserver-xorg add 1680x1050 when choosing available resolutions and when setting up monitor choose advanced mode and enter the correct horizontal and vertical refresh ranges. If you do not choose advanced mode the 1680x1050 settings are not saved to the xorg.conf file.

---

### Post by Ralob on 2007-07-14
1. 01:00.0 0300: 10de:0045 (rev a1)
2. 01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)
3. no tweaking necessary :)

---

### Post by Boricua on 2007-07-15
Hi, first time posting here.:)
I have a fairly new machine (intel motherboard with core-duo, 4GB RAM and two maxtor diamondmax HDs) with the GForce 8500 GT. My monitor is a Viewsonic VX2235wm.
After failing in finding other success stories making the nvidia driver working with my 8500 card, I took the route of removing all nvidia files from my system and then installing the new one with Envy. It worked perfectly.
However, on one occasion when I logout the xorg.conf file stopped working, not sure why. I rebooted the machine, killed the x server and then copied my xorg.conf.backup file into xorg.conf. Then, I reinstalled the driver back with Envy and everything went back to normal.
If you need further info just let me know.

---

### Post by spur on 2007-07-22
01:00.0 0300: 10de:0221 (rev a1)
nvidia geforce 6200 with 256mg ram
downloaded drivers using automatix.
64bit ubuntu no probs.
With 32 bit kubuntu on 64bit system a pile of probs not resolved by me.

---

### Post by mrazster on 2007-07-22
1. 01:00.0 0300: 10de:0291 (rev a1)
2. MSI 7900 GTO
3. Installed with ***Envy*** script

Did a clean install, then compiled a custom 2.6.22 kernel and then installed the drivers with envy.

---

### Post by Bob Unitt on 2007-07-22
1. 01:00.0 0300: 10de:00f5 (rev a2)
2. 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
3. Installed with ***Envy*** script

Tried to use 'nvidia-settings' to set the default resolution to 1280*1024 but it kept reverting to 1024*768 after a reboot. Also tried modding '/etc/X11/xorg.conf' with same result. Doing these logged-on as sudo user made no difference.

Eventually found the file 
'*(user-home)*/.gconf/ desktop/gnome/screen/default/0/%gconf.xml', containing :-
[INDENT]
<?xml version="1.0"?>
<gconf>
        <entry name="rate" mtime="1182701462" type="int" value="50">
        </entry>
        <entry name="resolution" mtime="1182701462" type="string">
               <stringvalue>1024*768</stringvalue>
        </entry>
</gconf>
[/INDENT]

Changing the '1024*768' to '1280*1024' in this file solved my problem.

---

### Post by denar on 2007-07-22
01:00.0 0300: 10de:0111 (rev b2)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
No tweaking needed

---

### Post by Salpiche on 2007-07-25
> **ubuntu_demon said:**
> 1)0000:01:00.0 0300: 10de:002d (rev 15)
2)nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
3)use the legacy driver :

```

$sudo apt-get install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
$sudo nvidia-xconfig

```

and do a reboot

Are you able to use desktop effects or beryl with TNT2? I did the same thing, yet I can't use desktop effects nor beryl, for that matter I thing that the kernel is the one controlling the video instead of the video card (32mb waisted). I do not really care that much about beryl but it would benice tobe able to use desktop effects at the very least.

---

### Post by TKIII on 2007-07-25
07:00.0 0300: 10de:0421 (rev a1)
MSI 8500GT OC Edition
Fresh Installed Kubuntu and purged the nvidia-kernel-common package. Then I installed the driver from Nvidia's site.

---

### Post by DeltaZero on 2007-07-27
10de:0047 (rev a1)
EVGA GeForce 6800GS OC AGP 256Mb

Ubuntu 6.06

Must use [Method 2]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2_2"). OpenGL works OK.

---

### Post by NT4usB on 2007-07-28
(I also posted this under the * Please Help us TESTING the Latest ATI and NVIDIA Driver *)

Awright... enough fighting the ATi card and Mythtv. fglrx works fine but MythTV hates it.
Out with the ATi and in with a GeForce 7600 GS.
Here's what I did:

Remove purged envy and installed the latest.
Swap the cards.
Ctrl+Alt+F1
```
sudo apt-get install -f
``` wanted to remove ~400 packages so I said no thanks to that.
```
sudo envy -t
```
First selected the option to remove all the ATi stuff.
Then selected #6 clean install, but it threw all kind of complaints at me and didn't install anything.
Selected #5 and the options to install the latest.
Looks like it worked...
```
ct@wimp:/etc/X11$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 02e1 (rev a2)
ct@wimp:/etc/X11$ lspci -n | grep 0300
01:00.0 0300: 10de:02e1 (rev a2)
ct@wimp:/etc/X11$ glxinfo
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11
```
Don't know why it's a 'Unknown device' but as long as it works...

envy rocks!
Thanks again tseliot.

---

### Post by bwallum on 2007-07-29
nVidia GeForce 7300 GS, worked out the box. Absolutely no settings to be made. Then downloaded proprietory driver with the tick box in System>Administration>Restricted Packages Manager. This ran with Movie Player and gstreamer plus some codecs and stuff from the Medibuntu repository, but had restricted resolution. 

I then downloaded Envy and had full range of resolutions (which all worked). The only downside is that when I reset the resolution it changes back to the default setting established before Envy was installed when I boot up. No idea why but if you know please let me know.

I just followed defaults or recommended settings when offered. No conscious tweaking involved (wouldn't know how to do it anyway).

Graphics is certainly improving quickly, well done to all active on the job. I am also becoming better at some of the simpler terminal stuff, like recognising the prompt when I see it! So that may be helping as well. 

For anyone having trouble with setting up graphics I would say be confident that it can be done and trust the community to get you out of any backwaters you might find yourself in.

Regards
Bob

---

### Post by NT4usB on 2007-07-29
> **bwallum said:**
> ...The only downside is that when I reset the resolution it changes back to the default setting established before Envy was installed when I boot up. No idea why but if you know please let me know...
I read somewhere that if you run nvidia-settings as root```
sudo nvidia-settings
``` the changes will stick. I dunno. 
I edited my xorg.conf directly.

---

### Post by bwallum on 2007-07-30
Hi NT4..

Thanks for the suggestion.  It doesn't fix it for me I'm afraid. Just thought I'd report back in case others were following the thread.

The last time I messed about with the x-server i got a black screen. That's the level of my knowledge showing. With that in mind could you walk me through changing the configuration so that it does stick?

Kind Regards
Bob

---

### Post by bwallum on 2007-07-30
1) 05:00.0 0300: 10de:01df (rev a1)
2) nVidia GeForce 7300 GS
3) no tweaking

---

### Post by Phloston on 2007-07-30
1. 07:00.0 0300: 10de:0393 (rev a1)
2. 07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
3. No tweaking required (using twinvew)

---

### Post by NT4usB on 2007-07-30
> **bwallum said:**
> Hi NT4..

Thanks for the suggestion.  It doesn't fix it for me I'm afraid. Just thought I'd report back in case others were following the thread.

The last time I messed about with the x-server i got a black screen. That's the level of my knowledge showing. With that in mind could you walk me through changing the configuration so that it does stick?...

Are you familiar with editing using a non graphical editor like vi? That's what I use and the only one I know. I'm assuming you know how to cd into X11 directory...
Anyway, before you start messing with xorg, back it up.```
sudo cp xorg.conf bkup.xorg.conf
``` then when you hose it and get a black screen, you can Ctrl+Alt+F1, login, cd to X11, and  restore by```
sudo cp bkup.xorg.conf xorg.conf
```

I went into xorg and changed:```
Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
``` to add the resolution (in red):```
Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes   [COLOR="Red"] "1680x1050"[/COLOR] "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
Insert a resolution supported by your monitor.
Also, be sure you have the correct Fh and Fv settings for your monitor.

I've removed all the other 'Depth' SubSection and other unused clap from my xorg so I'm assuming you'd make the change for every SubSection you have. My entire xorg is below. Note: It's an old copy from before I got the big LCD and it's for a dual monitor/TV setup so much of it doesn't apply.```

Section    "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"
    # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

Section "Monitor"
 #LCD
    Identifier     "Monitor[0]"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci EndSection
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO" #or Composite etc
    Option         "TVStandard" "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60"
    EndSubSection
EndSection 
```

ed: you might search and google around for 'modelines' (or, something). No idea what they are but I recall seeing posts about having to use them to get some wide monitors to work...

---

### Post by veli on 2007-07-31
1. 03:00.0 0300: 10de:0167 (rev a1)
2. nVidia Corporation GeForce Go 6200 TurboCache (rev a1)
3. Manually change the driver in xorg.conf from "nv" to "nvidia".

proprietary driver "nvidia-glx-new" installed via synaptic.

---

### Post by buckrodgers on 2007-08-09
01:00.0 0300: 10de:0402 (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)
nv8600GT from ASUS on a Dual core AMD64 

envy did not work, I tried many others things with out success 

However with the Nvidia drivers and the following method it runs perfect with no options
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

I would definitively welcome an automatic & clean installation of the graphic card driver from the  start.

Cheers

---

### Post by jso2897 on 2007-08-10
THe restricted drivers manager worked for me - and according to the Wiki, it shouldn't have. I have an old GeForxe MX4000, and it is not supported - but it worked with no complications. It tests out on Grep rendering, and I played TR2 in wine, and in the setup was able to use all features, including triple buffering - so it's working. I dunno.:confused:

---

### Post by Onay on 2007-08-12
Nvidia GeForce 6200

Envy

Thanks so much for Envy; It was a HUGE help when it came to installing the driver. It's amazing!

---

### Post by Alexander2007 on 2007-08-12
The "Restricted Drivers Manager" installed it fine for me. :)

---

### Post by Falcorian on 2007-08-12
1) 01:00.0 0300: 10de:0193 (rev a2)
2) EVGA nVidia e-GeForce 8800GTS 640MB (01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2))
3) Installed latest nVidia drviers from their site, answered 'yes' to all the questions it brings up, and rebooted. Worked fine (and X even started without crashing).

---

### Post by bulletboy on 2007-08-12
1. 01:05.0 0300: 10de:0322 (rev a1)

2. 01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


3. I used the nvidia-settings application that came with the ubuntu 7.04 nvidia restricted driver to configure twinview on my 19" LCD's

---

### Post by bricksen on 2007-08-12
1) 01:00.0 0300: 10de:00f2 (rev a2)
2) Nvidia GeForce 6600
3) No tweak

---

### Post by gigahz on 2007-08-13
1) 0000:01:00.0 10de:0028 (rev 15)
2)  nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro
3) Installed nvidia-glx, nvidia-glx-legacy, nvidia-kernel-common with Synaptic.

The nvidia driver loaded (nvidia splashscreen) but GLX did NOT work. Fix: added to THE END OF xorg.conf:
```
Section "Extensions"
Option "Composite" "Disable"
EndSection
[COLOR="SeaGreen"]
``` Maybe this should be added by default to xorg.conf regarding the cards 10de:0028? my 2c.[/COLOR]

(Tried just adding the option in the [Device] section, together with driver=nvidia, but that did NOT work. ) see also [http://ubuntuforums.org/showpost.php?p=3178287&postcount=10](http://ubuntuforums.org/showpost.php?p=3178287&postcount=10)

---

### Post by jso2897 on 2007-08-14
Output:01:00.0 0300: 10de:0185 (rev c1)

5oomhz PIII
512mb Ram
Nvidia Geforce 4 MX440

Installed with the Restricted Drivers Manager utility. The first time, I had already tried other methods, and the install I ended up with kept hard freezing on unanswered calls, like when surfing the net. So I deleted and re-installed all the modules and then ran the Manager. Seems to be working so far - haven't had any problems. I'm keeping my fingers crossed.

---

### Post by Phase1 on 2007-08-16
1.01:00.0 0300: 10de:0295 (rev a1)

2.EVGA 7950 GT KO (nVidia) ([http://www.evga.com/products/moreinfo.asp?pn=512-P2-N637-AR&family=22](http://www.evga.com/products/moreinfo.asp?pn=512-P2-N637-AR&family=22))

3. no tweaking

i used Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) and got lucky cause a new version of Envy came out today, and i stumbled upon it today, it worked first try.

---

### Post by Opiatr on 2007-08-16
1) 04:00.0 0300: 10de:0140 (rev a2), 05:00.0 0300: 10de:0140 (rev a2)

2) 2xChainWreck 6600GTs

3) Reading, reading reading, and creating the proper xorg.conf to enable the use of a Sony Wega televison as a secondary desktop. Found all the info I needed here: [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html")

P.S. First Post
P.P.S. Thanks everyone for maintaining a superior forum!

---

### Post by rberry88 on 2007-08-17
F'n sweet tutorial, I used Method 1:
1) 01:00.0 0300: 10de:0091 (rev a1)
2) Nvidia 7800GTX
3) No tweaking needed, it just works and WoW runs fantastic

---

### Post by nikkkko on 2007-08-22
1. 02:00.0 0300: 10de:01f0 (rev a3)
2. GeForce4 MX - nForce GPU
3. Fresh feisty install, downloaded envy, installed nvidia - black screen and flashing cursor.  Uninstalled nvidia with envy and tried automatix2 - same result. Manually deleted/purged everything nvidia related, then re-installed nvidia via envy.  This time it worked.

( If a man successfully installs nvidia drivers and ndiswrapper wifi in the middle of a forest and noone is around to see him cry with joy, did it really happen? )

---

### Post by migulic on 2007-08-22
1. 01:00.0 0300: 10de:0175 (rev a3)
2. GeForce 4 420 Go
3. First, Option "ConnectedMonitor" "DFP" to the Screen section of my xorg.conf, to be able to see anything at all. This left me with a black bar on the right side of the screen and a maximum resolution of 800x600 (I wanted 1024x768 as that was my LCD's native resolution). To fix this I had to modify the EDID (actually, I used the ready file from this site: [http://www.nvnews.net/vbulletin/showthread.php?t=84773](http://www.nvnews.net/vbulletin/showthread.php?t=84773)). Then I had to add 'Option "CustomEDID" "/path/to/patched/EDID.file"' to the Device section of xorg.conf.

I don't know if that matters, but this card is in a Toshiba Satellite 1410-604 laptop.

---

### Post by dr_agon on 2007-08-23
1)  00:05.0 0300: 10de:0240 (rev a2)
2)  00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
(this is integrated video chipset on MSI K8NGM2 mainboard)
3) I needed to add proper [FONT="Courier New"]HorizSync[/FONT] and [FONT="Courier New"]VertRefresh[/FONT] lines to [FONT="Courier New"]Section "Monitor"[/FONT].  There were none after default instalation. Without them my monitor was discovered as 
```

Xorg.0.log:
(...)
(II) NV(0): SyncMaster: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): SyncMaster: Using default vrefresh range of 50.00-70.00 Hz

```
and such low frequencies prevented using higher resolutions than 800x600. 
I am using "nv" driver.

I had the same problem with old TNT2 card on another machine with "nvidia" (legacy) driver , and the same solution worked (I ran [FONT="Courier New"]dpkg-reconfigure xserver-xorg[/FONT] and only important change were proper lines with HorizSync and VertRefresh).

The most funny thing is that I found this forum ***after*** couple of hours of internet searching and making all required changes :cool:

---

### Post by ozzyprv on 2007-08-26
1) 01:00.0 0300: 10de:0322 (rev a1)
2) Nvidia FX 5200 128 MB
3) No tweaking

 --EDIT
3) Had to run "sudo dpkg-reconfigure -phigh xserver-xorg" and make sure resolution 1440x900 was checked.
Run "sudo nvidia-xconfig --no-composite" right after that.

---

### Post by xpod on 2007-08-29
1) 00:0a.0 0300: 10de:0185 (rev c1)
2)  nVidia Corporation NV18 GeForce4 64Mb MX 4000 

Never really had to do anything other than use the restricted drivers manager,synaptic or indeed Automatix ..........as i used to use of course:???:
Used envy a couple of times too but never recently.
I  usually have to enter a particular monitors refresh rates but everything always works fine regardless.

Never really had any issues in that department  but since recently changing monitors(and re-installing) i`m having minor issues with TVout via Svideo and a [Stubborn Mouse Pointer](http://ubuntuforums.org/showthread.php?t=533317) that will no longer move screens over to the TV??

It`s neither here nor there though as the MX4000 is now going in another machine we have just as soon as the slightly better FX5500 i`ve ordered arrives.(PCI):(

I was always quite surprised by just how much this old thing is actually capable of to tell the truth.
Vistas bells & whistles just laughed me out of the building during the short time i tried it with the MX4000 but apart from the water effects in Compiz/Beryl  the rest of the effects have always worked just fine.

---

### Post by man_bash on 2007-09-11
Nvidia 6800XT AGP on a ASUS K8N (Ai) board with Feisty 64-bit

All actions

<Alt> + <Ctrl> + <F1>

-login

in command line

sudo /etc/init.d/gdm stop

cd Destop (this is where Firefox put the proprietary driver download)

sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run

run the installer, when finished

sudo /etc/init.d/gdm start

/done/

---

### Post by jbuc89 on 2007-09-27
1) 01:00.0 0300: 10de:0111 (rev b2)

2) GeForce2 MX-200 64MB

3) Installed Ubuntu repos nvidia-glx 9631 driver but it fixed screen @ 800x600x50Hz using Method 1. Installed and got it working  @ 1024x768x85Hz using Method 2. Must be problem with repository driver as similar posts had same problem.

One other thing that was kind of wierd. I'm using a circo 1999 BIOS and I had to disable the Video RAM and Video BIOS cache in my computer's BIOS to have my computer recognize the 9631 driver.  Without disabling the cache it would only see the 7184 driver.

---

### Post by Rorscharch on 2007-09-27
**1.**  03:00.0 0300: 10de:0391 (rev a1)
**2.** nVidia GeForce 7600GT 256mb
**3.** Default resolutions only went up to 1024x720, had to change my xorg.conf to include higher resolutions

---

### Post by buckykat on 2007-09-28
1)01:00.0 0300: 10de:0174 (rev a3)
2)nVidia GeForce4 400 Go 64MB
3)fresh install of feisty, enabled it on restricted drivers manager, then rebooted. well, the usplash showed fine, but when i got the login screen, i got the noise but nothing on the screen. i did a hard shutdown, and used GRUB to choose recovery mode. in recovery terminal, i did "sudo nano /etc/X11/xorg.conf" then under section "display" i changed "nvidia" to "nv", then rebooted. i downloaded the envy deb, then ran it as "envy -t". i chose "install nVidia drivers". it couldn't install the following packages: "libqt3-mt-dev kernel-wedge rpm sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev" i ran "sudo apt-get install libqt3-mt-dev kernel-wedge rpm sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev",then ran "envy -t" again and rebooted. works fine now with glxgears running at around 2000fps. hope this helps someone.

---

### Post by gwoodard on 2007-09-28
I used envy but now my xorg.conf cant save my settings

file:///home/gwoodard/Desktop/Screenshot.png

due to a backup issue

---

### Post by jackcy on 2007-09-29
If anybode is interested - I wrote a shell script that compares the nvidia chip id with a driver list provided on the nvidia webpage. The script installes the right nvidia module from repositories and modifies the xorg.conf (nv to nvidia).

For more information visit [http://doku.liedler.at/doku.php/update_scripts:0_update_scripts](http://doku.liedler.at/doku.php/update_scripts:0_update_scripts)
The relevant script is 4_nvidia.cyb

Your feedback is welcome.

---

### Post by gwoodard on 2007-09-30
Oh and if anyone is wondering I own a Nvidia 6200a I can get smaller resolutions but it wont save in xorg.conf plz help

---

### Post by CulleyS on 2007-10-08
I used this method:

[http://paste.ubuntu-nl.org/39098/](http://paste.ubuntu-nl.org/39098/)

Only thing I've noticed is when I used that method and a new "kernel" release of Ubuntu comes out, I have to do it all over again. :-?

I've made several posts about drivers and video today as it is the last frontier I need to traverse in terms of fully migrating to Linux.  Using this method, I have finally managed to get dual monitors working.  However, am experiencing problems with video playback.  After reading some posts, I think it may be connected to OpenGL 3D graphics that come with Gutsy.

---

### Post by riotnumber9 on 2007-10-08
Hi everyone - supern00b here...   first post and getting frustrated.

just set up a dual boot with Ubuntu Feisty - I'm running an nVidia 8600GTS card - but for the life of me can't get it to work dual screen.  i can't even get it to use a restricted driver.  I've tried manual install, [clumsily] editing my xorg.conf, and tried Envy and that didn't work either.

Would someone mind shedding some light as to how to get this working?


Much appreciated.

---

### Post by marmiteOlz on 2007-10-08
riotnumber9   it says at the start no requests for help
but if some kind fellow posts a solution i have a 8600gts  and symptom i get is  upon boot up all goes well but when the ubuntu progress bar fills my monitor seems to go into sleep, green light turns orange

anyway.. posted  cus i tried envy and had the above problem
resinatlled and manually installed nvidia driver and exact same problem .. is this card supported?

---

### Post by marmiteOlz on 2007-10-10
ok i got mine to work...
i noticed if i installed nvidia drivers
and teh xorg.conf showed "nvidia" as teh drivers i would get teh blank screen
however if i changed it to vesa it worked but on standard resoution and i couldnt change it even if i edited the xorg.conf
i also tried teh "nv" as the driver in the xorg.conf and now it works and detects teh resolutions i put in  the xorg.conf manually
and also the refresh rate
only thing i get is an error about HAL. but ill try and look for that one

---

### Post by Ngiri on 2007-10-11
1) 01:00.0 0300: 10de:0421 (rev a1)
2) 8500 GT 256 DDR2  (Vendor: EVGA)
3) Installed with Envy but had trouble where I couldn't save xorg.conf when attempting to change resolutions.  Looked at the properties of the Envy shortcut and then ran Envy from a terminal with sudo and there was no problem saving the file.  (Made a backup first... always do that...)

---

### Post by Shannon_VanWagner on 2007-10-21
Hi there,

I installed Ubuntu 7.10 on my Dell Inspiron 2650 and enabled Nvidia GeForce2 Go (lspci shows nVidia Corporation NV11 [GeForce2 Go] (rev b2)) proprietary drivers and after rebooting the screen either was blank, frozen, or sometimes would show some garbled output.

Here's what I did to fix it:

On bootup, hit F2 to enter the Dell BIOS
For the section marked "Video Display Device", switched the setting from "Simul Mode" to "LCD Mode"

Saved the setting with F10 and then exited and rebooted.


On reboot everything came up normal.

Go Linux!!

Hope this helps!

Shannon VanWagner

---

### Post by pmorton on 2007-10-21
1)  01:00.0 0300: 10de:0322 (rev a1)
2) Nvidia geforce FX 5200 (256MB)
3) Gutsy
4) I had terrible problems with  a MSI card  based on this chipset until I read this post and downloaded Alberto Milone's Envy GUI installer  from  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). Some problem with openGL files and old symlinks, I think. Envy sorted it for me. But I'm wondering what's wrong with MSI   and NVidia fixing  it and saving owners of this card hours of hassle.

---

### Post by Cariboo1938 on 2007-10-23
1) 01:00.0 0300: 10de:0322 (rev a1)
2) 01:00.0 VGA compatible controller: 
   nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
3) I couldn't get my card running up today. 

I followed the instructions [HERE]("http://www.psychocats.net/ubuntu/nvidia"),
I tried [ENVY]("http://albertomilone.com/nvidia_scripts1.html"),
I tried [THIS]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") and nothing worked yet.

I found this message in the "nvidia-bug-report.log"
Quote:
26.150026] AGP bridge at 00:00:00
[ 26.150030] Aperture from AGP @ f0000000 size 4096 MB (APSIZE 0)
[ 26.150032] Aperture too small (0 MB)
[ 26.150033] Your BIOS doesn't leave a aperture memory hole
[ 26.150035] Please enable the IOMMU option in the BIOS setup
[ 26.150037] This costs you 64 MB of RAM

---

### Post by kyledevans on 2007-10-23
GeForce Go 7900 GS
01:00.0 0300: 10de:0298 (rev a1)

I had to enable RenderAccel in my xorg.conf:
Option          "RenderAccel"   "True"

---

### Post by VON_CAPO on 2007-10-23
Envy works good for me.
Running at 1920x1200 without any problem so far. :)

---

### Post by potnoodles on 2007-10-23
Using Geforce 8600GTS

Envy worked well for me in 7.04 and survived the upgrade to 7.10 as well.
Viewing 1680x1050 on a Belinea monitor.(Maxdata (RogenTech) Bel2225S1W (CRT-0))

regards,

potnoodles

---

### Post by bwallum on 2007-10-23
It might be best starting a new thread, a lot of changes have happened since this one started. Could you also put your rig specs in your signature please. Some laptops have more problems than others. I note from your links that they too are a bit behind the times although if you email tseliot I'm sure he will bring you up to date regarding Envy (which has worked well for most people). 

There are two drivers in restricted packages; 'nv' and 'nvidia'. These correspond to the nvidia-glx and nvidia-glx-new as far as I can make out. Use the latter for accelerated graphics (compiz needs this).

I get the same warning about AGP aperture too small and I have a pcie card. I just ignore it. Try setting up on a vesa driver then completely remove nvidia-glx (-new) Reboot and reinstall using the nvidia-glx-new driver.

I'm running on the restricted nvidia-glx-new, full compiz, streaming news etc, etc without any problems at all so there must be a way. I did the above shimmy a couple of times I recall to get it working properly. I was also using the beta at the time so maybe an update fixed it. Make sure you have all the boxes ticked in System>Administration>Software Sources (except perhaps the source code one) and then use Update Manager to make sure you are getting the latest.

Good luck.
Bob

---

### Post by handy on 2007-10-23
***nv*** is open source ***nvidia*** is nVidia's *binary* linux driver (closed source - restricted).  Use the appropriate nvidia *binary* driver if you want 3D.

The 3 binary drivers are for 3 different nVidia technologies:

nVidia Binary X.Org "Legacy" Driver =  ***Old*** - is for TNT, TNT2, GeForce, GeForce2.

nVidia Binary X.Org Driver = ***Newer*** - GeForce, nForce and Quadro families of NVIDIA chipsets.

nVidia Binary X.Org Driver = ***Latest*** - GeForce, nForce and Quadro families of NVIDIA chipsets.

The nVidia site has all the information regarding which chip-sets are supported by which drivers.

---

### Post by xjoshx9 on 2007-10-23
I installed the newest Nvidia driver in ENVY, and that driver updated itself in the "Screens and Graphics" manager.  Then I just opened a terminal and typed "sudo nvidia-settings."  I set my resolution and refresh rate and saved it to the xorg.conf file.  Tah dah!

---

### Post by handy on 2007-10-24
> **xjoshx9 said:**
> I installed the newest Nvidia driver in ENVY, and that driver updated itself in the "Screens and Graphics" manager.  Then I just opened a terminal and typed "sudo nvidia-settings."  I set my resolution and refresh rate and saved it to the xorg.conf file.  Tah dah!

I wish I could use my expensive bit of hardware, not matter which way I try it will not run under kubuntu 7.10. :(

***[Edit:]** I've taken this box back to Sabayon 3.4f, it set everything up perfectly, card, monitor the lot...*

---

### Post by Cariboo1938 on 2007-10-24
1) 01:00.0 0300: 10de:0322 (rev a1)
2) 01:00.0 VGA compatible controller:
nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

3) I had to edit /boot/grub/menu.lst: .
Find this section and add "iommu=noaperture":> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e4af70f0-d555-49ab-8dd0-687cc3e7f81c ro [COLOR="Magenta"]iommu=noaperture[/COLOR]

Save the file and type:
```
sudo update-grub
```
and then 'restart'  your computer!

BTW: 
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly.

---

### Post by handy on 2007-10-24
> **Cariboo1938 said:**
> 
BTW: 
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly.

That is really interesting, I am running a GA-K8NS Ultra-939 motherboard too!

I was stopped by an inability to install any kind of X in my attempt to install Gentoo as well.  This motherboard also causes keyboard timing problems with any of the Ubuntu versions after Dapper, & on Sabayon as well, unless I turn off the on-board USB. (I use a PCI card now.)

I will have a look into the depths of my just installed Sabayon system & see what they do to get past this AGP problem.  I'll post what I find.

---

### Post by handy on 2007-10-24
Sabayon doesn't use ***iommu=noaperture*** in menu.lst:

[I]# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /kernel-genkernel real_root=/dev/sda2
#          initrd /initramfs-genkernel
#boot=sda
default=0
timeout=6
splashimage=(hd0,0)/grub/splash.xpm.gz
title Sabayon Linux x86 3.4 Standard Edition 
	root (hd0,0)
	kernel /kernel-genkernel-x86-2.6.22-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/sda2  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi 
	initrd /initramfs-genkernel-x86-2.6.22-sabayon
 [/I]

---

### Post by handy on 2007-10-24
Interestingly the Sabayon xorg.conf does not identify my Sony CPD G400 monitor, nor does it have the correct refresh rate range for it, but the monitor IS identified correctly & runs the appropriate refresh rates when checked in the nVidia X Server Settings, also I'm running a screen resolution of 1280x1024 @ 85hz both of which are not even mentioned in my xorg.conf?  I surely do have a lot to learn. :-)

***Sabayon 3.4f xorg.conf:***

[I]Section "Files"


    #FontPath	"/usr/share/fonts/local/"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath 	"/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
    Load	"type1"
    Load	"freetype"
    Load	"extmod"
    Load	"synaptics"
    Load	"vbe"
#   Load        "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option 	"AllowMouseOpenFail" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier		"Synaptics1"
    Driver		"synaptics"
    Option		"SendCoreEvents"	"true"
    Option		"Device"		"/dev/psaux"
    Option		"Protocol"		"auto-dev"
    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS/MacBook TouchPads
    #Option		"MaxSpeed"		"0.7"
    #Option		"MinSpeed"		"0.18"
    #Option		"AccelFactor"		"0.08"
    #Option		"TopEdge"		"120"
    #Option		"LeftEdge"		"120"
    #Option		"BottomEdge"		"830"
    #Option		"RightEdge"		"650"
    #Option		"FingerLow"		"25"
    #Option		"FingerHigh"		"30"
    # MacBook touchpad
    #Option		"MaxTapTime"		"180"
    #Option		"MaxTapMove"		"220"
    #Option		"MaxDoubleTapTime"	"180"
    #Option		"VertScrollDelta"	"20"
    #Option		"HorizScrollDelta"	"50" 
    #Option		"TapButton2"		"3"
    #Option		"TapButton3"		"2"
    #Option		"VertTwoFingerScroll"	"1"

    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    
    Option	"AutoRepeat"	"500 5"
    Option      "XkbModel"	"pc105"
    Option	"XkbLayout"	"us"
    Option      "XkbRules"      "xorg"
    # Macintosh keyboard
    #Option	"XkbOptions"	"lv3:rwin_switch"

EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom1"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom2"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom3"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"

    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"ImPS/2"
    Option	"ZAxisMapping"	"4 5"
     
EndSection

Section "InputDevice"
    Identifier	"Mouse2"
    Driver	"mouse"
    Option	"Protocol"	"ImPS/2"
    Option	"Device"	"/dev/input/mice"
    Option 	"ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 43 - 60
    HorizSync	28 - 80
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "nvidia" # do not remove vesa
    #Option "RenderAccel" "on"
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier	"Screen 1"
    Device	"VESA"
    Monitor	"Generic Monitor"
    #Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth		8
        ViewPort	0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier	"Main Layout"
    Screen 0 	"Screen 1"
    InputDevice	"Mouse1" "CorePointer"
    InputDevice	"Mouse2" "SendCoreEvents"
    #InputDevice "Synaptics1" "SendCoreEvents"
    #InputDevice "wacom1" "SendCoreEvents"
    #InputDevice "wacom2" "SendCoreEvents"
    #InputDevice "wacom3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection

Section "Files"


    #FontPath	"/usr/share/fonts/local/"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath 	"/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
    Load	"type1"
    Load	"freetype"
    Load	"extmod"
    Load	"synaptics"
    Load	"vbe"
#   Load        "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option 	"AllowMouseOpenFail" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier		"Synaptics1"
    Driver		"synaptics"
    Option		"SendCoreEvents"	"true"
    Option		"Device"		"/dev/psaux"
    Option		"Protocol"		"auto-dev"
    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS/MacBook TouchPads
    #Option		"MaxSpeed"		"0.7"
    #Option		"MinSpeed"		"0.18"
    #Option		"AccelFactor"		"0.08"
    #Option		"TopEdge"		"120"
    #Option		"LeftEdge"		"120"
    #Option		"BottomEdge"		"830"
    #Option		"RightEdge"		"650"
    #Option		"FingerLow"		"25"
    #Option		"FingerHigh"		"30"
    # MacBook touchpad
    #Option		"MaxTapTime"		"180"
    #Option		"MaxTapMove"		"220"
    #Option		"MaxDoubleTapTime"	"180"
    #Option		"VertScrollDelta"	"20"
    #Option		"HorizScrollDelta"	"50" 
    #Option		"TapButton2"		"3"
    #Option		"TapButton3"		"2"
    #Option		"VertTwoFingerScroll"	"1"

    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    
    Option	"AutoRepeat"	"500 5"
    Option      "XkbModel"	"pc105"
    Option	"XkbLayout"	"us"
    Option      "XkbRules"      "xorg"
    # Macintosh keyboard
    #Option	"XkbOptions"	"lv3:rwin_switch"

EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom1"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom2"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom3"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"

    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"ImPS/2"
    Option	"ZAxisMapping"	"4 5"
     
EndSection

Section "InputDevice"
    Identifier	"Mouse2"
    Driver	"mouse"
    Option	"Protocol"	"ImPS/2"
    Option	"Device"	"/dev/input/mice"
    Option 	"ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 43 - 60
    HorizSync	28 - 80
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "nvidia" # do not remove vesa
    #Option "RenderAccel" "on"
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier	"Screen 1"
    Device	"VESA"
    Monitor	"Generic Monitor"
    #Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth		8
        ViewPort	0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        #Modes		"1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier	"Main Layout"
    Screen 0 	"Screen 1"
    InputDevice	"Mouse1" "CorePointer"
    InputDevice	"Mouse2" "SendCoreEvents"
    #InputDevice "Synaptics1" "SendCoreEvents"
    #InputDevice "wacom1" "SendCoreEvents"
    #InputDevice "wacom2" "SendCoreEvents"
    #InputDevice "wacom3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection

[/I]

---

### Post by Wollongong on 2007-10-25
02:00.0 0300: 10de:01a0 (rev b1)

integrated GF2 (Asus AN266 mainboard)

1: apt-get install nvidia-glx-legacy
2: sudo nvidia-glx-config   (which just changes driver from "nv" to "nvidia" in /etc/X11/xorg.conf)
3: reboot

It worked fine. For this device, do not use the regular 'nvidia-glx' package.

---

### Post by dartmusic on 2007-10-25
After using Upgrade Manager to upgrade from Feisty to Gutsy and using an old ATI 9600 (because  I couldn't get either a GeForce 5200 or 6200 to work in Feisty), the 9600 worked (barely) with the Restricted Drivers Manager.  

For the hell of it, I tried replacing the ATI 9600 with the Nvidia 6200 to see what would happen.  It was detected immediately, though the resolution was a wrong.  X booted into low-graphics mode and gave me choices to set up the card manually, though none of them worked.  As soon as I cancelled out of it, I was taken to an X session that looked fine other than the resolution being wrong.  The Restricted Drivers Manager popup popped up (!) and I enabled the driver there.  Upon reboot, everything worked perfectly.  

Yea Ubuntu!!

Though I do still have the jittery video and screen blanking problem when watching video.  Any ideas?

---

### Post by mshaaban on 2007-10-26
1. 01:00.0 0300: 10de:0175 (rev a3)
2. 0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
3. Tweaking: First, my graphic card is listed in the [list of cards known by ubuntu 7.10 nVidia binary drivers]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") so as to be enabled using nvidia-glx package but nvidia-glx will not work. nvidia-glx-legacy will work fine.

Please follow these steps in order for specifically this type of card:

- replace your /etc/X11/xorg.conf file with the one from [Latest nvidia dapper HOWTO for GeForce4 420 Go]("http://ubuntuforums.org/showthread.php?t=139264"). The file is attached.
- you need to add the line 'options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1' to /etc/modprobe.d/options file. The options file is attached as an example. (Thanks to Tseliot and Joffe)
- Install nvidia-glx-legacy
```
sudo apt-get install nvidia-glx-legacy
``` or use synaptic package manager. If you did not find this package you might want to enable main, universe, restricted and multiverse in System > Administration > Software Sources and disable installation from Cdrom.
- restart your computer and you should see the nvidia logo and driver should be working.

That's it. :)

BTW, I did these steps from a clean ubuntu installation, if you have been trying to make your card enabled using many ways and other packages, you might want you reinstall ubuntu or make sure that you do not have any conflicting nvidia drivers installed before you go on with the above steps.

It took me a lot of time and effort to be able to enable my card :mad:. Everything was posted here in ubuntu forums but not togather in one place. This thread is really a very good idea, thanks to Tseliot. All I needed is to be able to use desktop effects on Utuntu Gusty 7.10. After enabling your card, you can simply install xerver-xgl package, compizconfig settings manager and restart your computer and you are in. Good Luck.

If someone has the same card and have any questions please reply to me.
Regards,
Mohsen Shaaban

---

### Post by moschops on 2007-10-26
With a Feisty to Gutsy upgrade no amount of install-uninstall-reinstall hack, hack, hack could get my Ti4200 to work - the nv driver was fine but nvidia (regular or "new") just wouldn't recognize it complaining of an incompaitibility (from /var/log/gdm files):
[I]
Error: API mismatch: the NVIDIA kernel module has the version 1.0-7185, but
this X module has the version 1.0-9639.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.[/I]

While researching that I followed a few more uninstall/reinstall type ideas but none worked so I bit the bullet and used Envy that many had said worked for them.  It seemed like a sledgehammer solution and it seemed to do a million uninstalls, installs and compiles but you know IT WORKED.

So, if all else fails and you're tired of trying why not go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and get:

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb)

No modifications are required for Gutsy - it just works as is and now I can use the glorious screen effects.  Mmm desktop cube....

Thanks Alberto!

---

### Post by handy on 2007-10-26
Envy doesn't work for everyone's problem.

---

### Post by Frak on 2007-10-26
Envy on Linux Mint Daryna.

---

### Post by gp95ac on 2007-10-29
01:00.0 0300: 10de:0150 (rev a4)

01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)

compiz wouldnt work until I downloaded xgl and added 

Option		"AllowGLXWithComposite"	"True" to xorg

---

### Post by gp95ac on 2007-10-29
and the screens and graphics gui was needed to properly display on my widescreen (1440x900)

---

### Post by sochbat on 2007-10-29
I've run across this problem a few times in the past, always trying the nvidia-glx-legacy route, only to find it too complicated.

Most recent Nvidia fix:

sudo dpkg-reconfigure xserver-xorg

Learned it off Splitpaw @ YouTube.  He made a cool video about xserver crashing.

---

### Post by slyboots on 2007-10-29
01:00.0 0300: 10de:042b (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
When i use Emerald (compis fusion) or GTK window decorator then i have the CPU used on 100% usage by Xorg precess. It is occuring when i change the tabs on firefox it get very slowly and usage of CPU get to top by xorg. I changet the setting by the efects and i found that by some themes it occuring more, becouse they need more performance from VGA. Same occured by gnome-terminal tabs.  Other efects are going normaly. I have reinstalled firefox, compiz fusion but it still the same. I thing it is the driver, or some setting by the driver I am using driver 100.14.19


My lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)


```

---

### Post by RWC on 2007-10-29
01:00.0 0300: 10de:0392 (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
Installed 7.10 via Alternate Install CD while connected to a wired network, once installed - enabled the Nvidia Driver in Restricted Drivers Manager - latest driver was downloaded and installed.  Upon restart the Nvidia Driver was installed - no problems.

---

### Post by J44xm on 2007-10-29
> **sochbat said:**
> Most recent Nvidia fix:

sudo dpkg-reconfigure xserver-xorg

I just thought that should post this worked for me. After days of struggling with this and almost reinstalling from scratch, this did it for me. I have a Toshiba Satellite 1415-S173 with a GeForce4 420 Go card. However, I don't have the advanced effects and, frankly, I'm scared to try to obtain, though I'm a little too curious.

Thank you much, Sochbat, and everyone who's posted information about this issue.

---

### Post by sochbat on 2007-10-30
I actually have a GeForce4 440.  I've tried going bigger in terms of resolution, but no dice.

When i was still using Feisty, i could use 1280x1024, no prob.  But with Gutsy, i tried to reconfigure it, no dice.

The effects are nice and all, but i've always been more of a Function > Form kinda guy.

Its nice to show off the buddies tho.  Otherwise, not worth my time sadly.

---

### Post by stevie_velvet on 2007-10-30
10de:0429 Rev A1
nVidia quadro NVS 140M 256M (A.k.a., 8400GS + 100MHZ+128MB))
No Tweaks, - using nvidia-glx 100-.14.19 via restricted drivers manager

Almost used envy on previous Ubuntu version, but 'vesa' worked OK

---

### Post by KenMac on 2007-10-30
1) 00:05.0 0300: 10de:0247 (rev a2)
2) NVIDIA go 6100
3) clicked 'enable' under Restricted Drivers Manager and rebooted.
     -no tweaking necessary! :)

---

### Post by cotcot on 2007-11-01
1.   02:00.0 0300: 10de:01df (rev a1)
2.   nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
3.   no tweaks

---

### Post by mickey57 on 2007-11-01
....Gforce 5500
.....System/Admin/restricted drivers manager:guitar:

---

### Post by couzin2000 on 2007-11-01
1. 05:00.0 0300: 10de:0393 (rev a1)
2. 05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
3. No tweaks at all.

Problem: I cannot get Nvtv TV Out to work, and I cannot clone my screen through the SVideo port.

Please see my post at [http://ubuntuforums.org/showthread.php?t=595363]("http://ubuntuforums.org/showthread.php?t=595363")

Thanks

---

### Post by carlinuxlearner on 2007-11-01
1. 01:0b.0 0300: 10de:0172 (rev a3)
2. 01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
3. I Had to install it manually, Envy wouldn't work.

C@RL

---

### Post by mathiasv on 2007-11-01
1) 01:00.0 0300: 10de:0179 (rev a3)
2) nVidia Corporation NV17 [GeForce4 420 Go 32M]
3) Option "ConnectedMonitor" "DFP"
2.6.20.3-ubuntu1 on a Medion laptop (FID 2010 MD6081)

---

### Post by snkmad on 2007-11-01
1) 00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
2) installed the restricted drivers, reboot. Flawless Victory!
3) no tweaks needed.

Gutsy AMD64.

---

### Post by mmcmonster on 2007-11-02
1) 01:00.0 0300: 10de:0221 (rev a1)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
3) None!  Works beautifully with either nv or nvidia drivers on Gutsy.

System:
[HP Pavilion a645c]("http://tinyurl.com/2yzxv5") AthlonXP 3200+, [ASUS A7V8X-LA]("http://tinyurl.com/ynth8b"), [GeForce 6200LE]("http://tinyurl.com/yo2erl") (AGP)

---

### Post by Ranguvar on 2007-11-05
1.) '01:00.0 0300: 10de:0322 (rev a1)
2.) nVidia GeForce FX 5200 128MB AGP
3,) Just used the latest (envy_0.9.8-0ubuntu10_all.deb) version of Envy. I'm running Gutsy 64bit. Fixed black X crash!

---

### Post by Anlace on 2007-11-07
They don't work.

See [http://ubuntuforums.org/showthread.php?t=605460](http://ubuntuforums.org/showthread.php?t=605460)

Opps, forgot to add this info from lspci -n | grep 0300:
1)  01:00.0 0300: 10de:00f6 (rev a2)
2)  Nvidia GeForce 6800 GS/XT 256MB AGP
3)  Nothing worked, not even Envy

---

### Post by mmcmonster on 2007-11-07
1) 03:00.0 0300: 10de:0402 (rev a1)
2) 03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
3) Works perfectly with a fresh installation of Ubuntu Gutsy.

System:  ACER Aspire E360 Athlon 64 3500+, [ACER FC51GM/Foxconn 6150K8MA-8EKRS]("http://tinyurl.com/2h8yja"), [GeForce 8600GT]("http://tinyurl.com/2c48dz") (PCI-e)

---

### Post by enternalsoul on 2007-11-11
> **RWC said:**
> 01:00.0 0300: 10de:0392 (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
Installed 7.10 via Alternate Install CD while connected to a wired network, once installed - enabled the Nvidia Driver in Restricted Drivers Manager - latest driver was downloaded and installed.  Upon restart the Nvidia Driver was installed - no problems.


I am having no luck.  I do not have the corporate verison of the card nor am i on 64bit.

here is my situation.
PNY  NVIDIA GeForce 7600 GS
UBUNTU 7.10 GUTSY   upgraded from 7.04   (32 bit intel cpu)

here is a copy of the post i did on NVIDIA's site  it should explain every tyhing:

[QUOTE=pvdeynse]under Ubuntu 7.10, use the "synaptic package manager" and install package "nvidia-glx-new" afterwards, to enable the driver, run "sudo nvidia-glx-config enable" from a terminal window. Restart your PC 
this above procedure did install nvidia 100.14.19[/QUOTE]

I did the above and when i go to Screens and Graphics it still says I am using the VESA Driver.  Also my xorg.conf has to use VESA driver.

any time I change it to use the NVIDIA driver it will not use it at all.  I get a screen on reboot that says in low graphics mode selet correct driver.

If i can get it to use the NV or NVIDA driver then i only get 800x600 resolution.

I am on UBUNTU 7.10  and have a PNY GeForce 7600 GS.


any suggestions on how to make it use the NVIDIA drivers?

yes i enabled the restricted driver via the GUI (system, admin, restricted drivers)


I would appreciate any help.

BTW  I have dual monitors.  the VESA works for one monitor but not TWO.

---

### Post by enternalsoul on 2007-11-11
I got the driver to work  now i am just having troubles getting both monitors to work.

btw i got it to work by using [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

is there any special option setting or something that goe sin the xorg.conf files with this driver and acrd that i need to make sue i put in?

---

### Post by stevethefiddle on 2007-11-16
1) 01:00.0 0300: 10de:0020 (rev 03)

2) NVidia TNT2

3) Basic functionality without tweaking, but no graphics acceleration.

To enable 3D acceleration ( Xubuntu 7.1 )
     Applications => System => Restricted Drivers Manager
     Selected to enable "NVIDIA accelerated graphics driver (legacy cards)"
     Followed on screen instructions
     Reboot.

This enabled graphics acceleration, but NOT OpenGL.

To test for OpenGL:
     In Terminal, type: ```
glxinfo | grep rendering
```

To enable OpenGL:
     First back up Xorg.conf with the following:
          in Terminal enter: 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

I then tried entering this, but it did not seem to work:```
sudo nvidia-glx-config enable
```

So I typed: ```
sudo mousepad /etc/X11/xorg.conf
```
This opens xorg.conf in mousepad with root (sudo) access.
Add the following line to the "Screen" section of xorg.config
```
Option "AllowGLXWithComposite" "1"
```
Save xorg.conf
Reboot

Test with ```
glxinfo | grep rendering
``` produces:
```
direct rendering: Yes
```

Testing with ```
glxgears
``` produces:
```
1728 frames in 5.0 seconds = 345.549 FPS
1753 frames in 5.0 seconds = 350.448 FPS
1791 frames in 5.0 seconds = 358.129 FPS
```

(Not bad at all for a 500MHz Pentium with a TNT2 :)

---

### Post by MegaJim on 2007-11-21
1) 03:00.0 0300: 10de:0391 (rev a1) 
    06:00.0 0300: 10de:0391 (rev a1)

2)  These are **dual 7600GTs** running over SLI PCIe x16 Bridge on ASUS A8N32-SLI Deluxe mobo, **both of 256mb**, but different manufacturers.

03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
06:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

3) No tweaking

---

### Post by drub on 2007-11-22
[LIST]
[*]Gutsy Gibon
[*]01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
[*]HP Pavillion a1150y
[/LIST]

No tweaks required.  Installed easily.  Functional.  Ubuntu is beautiful!

However ... highest resolution offered is 1280x1024 ... not nearly high enough on a CRT.  Am looking to get a newer driver, or modify the X config, or something, to get it higher.  Would like 1600x1280 or similar.

Drub

---

### Post by drub on 2007-11-22
BTW ..

glxgears produced the following

8177 frames in 5.0 seconds = 1635.308 FPS
7861 frames in 5.0 seconds = 1572.153 FPS
8358 frames in 5.0 seconds = 1671.447 FPS
8380 frames in 5.0 seconds = 1675.953 FPS

---

### Post by pedro_cesar on 2007-11-23
nVidia GeForce 8600GT 256MB DDR3

After letting "Envy" download and install the drivers no twek were needed.

---

### Post by yanks0616 on 2007-11-27
05:00.0 0300: 10de:00ce (rev a2)
05:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2)
no tweaking needed

---

### Post by navaburo on 2007-11-30
```

cmerck@alderan:~$ lspci -n | grep 0300
01:00.0 0300: 10de:0391 (rev a1)

```

```

cmerck@alderan:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

```

The contents of my xorg.conf file, which I modified to do multihead and allow for using compiz:

It took conciderable xorg.conf tweaking to get the whole mess working togeather.

The only unsolved sort-of-problem I have is that the keyboard doesn't talk to applications on the alternate monitor.

```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 640 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "18 TFTLCD MN"
    DisplaySize     328    246
    HorizSync       31.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "DEC"
    HorizSync       15.4 - 56.5
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    DisplaySize     328    246
    ModelName      "CRT-0"
    HorizSync       31.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "18 TFTLCD MN"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Alternate Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "DEC"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0; CRT-0: 1280x960 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 832x624 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

```

---

### Post by immolat3 on 2007-12-01
02:00.0 0300: 10de:0422 (rev a1)
geforce 8600 Ultra here

used Envy, worked perfect. only thing is ubuntu says im refreshing at 50hz, but i tested it using some other software AND the nvidia config says its at 75, which is what i have it set to. sooooo oh well.

13176 frames in 5.0 seconds = 2635.130 FPS
13211 frames in 5.0 seconds = 2642.109 FPS
12925 frames in 5.0 seconds = 2584.854 FPS
13096 frames in 5.0 seconds = 2619.096 FPS
13097 frames in 5.0 seconds = 2619.220 FPS
13160 frames in 5.0 seconds = 2631.973 FPS
12419 frames in 5.0 seconds = 2483.662 FPS

---

### Post by Khyber on 2007-12-05
Dell 1907fpt LCD & Dell M990 CRT w/ EVGA 7800 GT CO.

I tried a bunch of different ways to get the Nvidia drivers and dual monitors to work. Nothing went right until I did the following:
1)I used Envy to uninstall any drivers I had. Then I used Envy to install the drivers.
2)After rebooting my CRT was acting as the main display. I launched the nvidia control panel with sudo and then enabled the LCD with TwinView.
3)After rebooting both monitors came on 

I did everything within Envy and the Nvidia control panel. I didn't directly edit anything with the xorg.conf file. All that is left for me to do is set my LCD as the main display and extend the desktop to the right.

---

### Post by wizochelle on 2007-12-07
01:00.0 0300: 10de:0402 (rev a1)
GeForce 8600 GT
No tweaking needed Yay!:guitar:

---

### Post by capella on 2007-12-08
1) 00:05.0 0300: 10de:0240 (rev a2)
2) 00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
3) no tweaking needed

---

### Post by satx on 2007-12-13
1.  01:00.0 0300: 10de:01d1 (rev a1)
2.  nVidia GeForce 7300/256MB
3.  Used Envy script. Resolution at 1280 x 1024/24 60Hz
4.  Monitor HP vs19d
5.  Using Compiz

---

### Post by galvheim on 2007-12-14
Asus EN8800GTS 320MB nVidia
Used Envy w/o problems
Using dualmonitors @ 1280 x 1024
Running Compiz with most anims working.

---

### Post by Myglaren on 2007-12-14
1) 01:00.0 0300: 10de:0322 (rev a1)

2) 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

3)  No tweaking as such, just needed to let the system know what sort of monitor I was using to be able to increase screen resolution.

---

### Post by randywilharm on 2007-12-16
I have an Nvidia 8500 gt 512meg on an Acer E380 Amd64 dual-core 2.6ghz.
Ubuntu 7.10
All I did was install ENVY and I even had the luxury of increasing my screen
resolution to 900 x 1440.

sometimes while watching youtube or turning on the javascript on the NOAA
website the picture will fade but I don't care as perfection is too expensive.

The Italian dude who created ENVY saved me a lot of trouble.

---

### Post by -grubby on 2007-12-16
1 : 00:05.0 0300: 10de:0242 (rev a2)
2 : NVIDIA Geforce 6200
3 : to boot into the live-CD (that is, not with a resolution of only 640x480) , I had to add the word inred  under section "input device" on "option        "CorePointer" [COLOR="Red"]"true"

[/COLOR] and also under section "Device"  with the "identifier" line saying "nVidia Corporation C51G [GeForce 6100]" I had to add (in red) :

[COLOR="Red"]Option "HWCursor" "off"[/COLOR] and then ctrl-alt-backspace.
 After I installed, I had to erase those lines, and to get to a proper Screen Resolution (above 50HZ) I had to (in red):
 "[COLOR="Red"]```
gksudo nvidia-settings
```[/COLOR]"
 in the terminal and change it there and then I had to ctrl-alt-backspace

---

### Post by superaktieboy on 2007-12-18
not sure what that weird number is and where i can get it but here goes:
nVidia Geforce 6200
no need to tweak..

the drivers i got from the official nvidia site ;) ([http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html))

greeetzz

---

### Post by odiseo77 on 2007-12-18
1) lspci -n | grep 0300
01:00.0 0300: 10de:01df (rev a1)

2) lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

3) No tweaking needed

---

### Post by Mr Wrath on 2007-12-18
1) 000:01:00.0 0300 10de:0110 (reb b2)

2) 0000:01:00.0 VGA compatible controller: nVidia corporation NV11 [GeForce 2 MX/MX 400] (rev b2)

3)  No tweaks needed using Automatix (use at your own risk)

---

### Post by popch on 2007-12-18
1: 00.0 0300: 10de:0176 (rev a3)

2: 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

3:  tweaks:
[LIST]
[*]changed ***software sources/Download From*** from ***<local> server*** to ***main server***
[*]enabled proprietary driver
[*]done[/LIST]System is Ubuntu 7.10

Changing the server to 'main' proved necessary because the driver apparently could not be found on the Swiss server.

---

### Post by jtprince on 2007-12-19
1.   01:00.0 0300: 10de:0324 (rev a1)
2.   nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
3.    
[LIST]
[*][For 7.10] enabled restricted drivers [turns on nvidia-glx-new, I believe]
[*]'nv' -> 'nvidia' (in xorg.conf)
[*]if you don't care to hibernate/suspend: add nvAGP "0" to xorg.conf
[*]if you want to hibernate/suspend and don't mind random 'freezes' (described [here]("http://xlife.zuavra.net/index.php/41/")): nvAGP "1"
[*]To hibernate/suspend with no freezes, I did this (taken from  [here]("http://en.opensuse.org/index.php?tit..._Suspend_HOWTO")):
[LIST=1]
[*]add NvAGP "1" to xorg.conf
[*]add the phrase 'agp=off' to your /boot/grub/menu.lst file (yes, the line is preceded with a pound key). The line now looks like this:
# kopt=root=UUID=e4d79a31-027c-4f2f-abbb-604bab112a1c agp=off ro
[*]notice that 'lsmod | grep agp' gives the intel_agp module and agpgart. Go into /etc/modprobe.d/blacklist and add the line:
blacklist intel_agp
and then restart the machine.
:) Hibernation + AGP + No Freezing!  :)
[/LIST]
[/LIST]

---

### Post by ubutufan on 2007-12-23
1. 01:00.0 0300: 10de:01d8 (rev a1)
2. nVidia 7400 Go
3. No tweaking needed

---

### Post by aonegodman on 2007-12-27
1) 01:00.0 0300: 10de:0171 (rev a3)

2) nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

3) No tweaks - yet.

Once I added the restricted and med lists Ubuntu did some updates and automatically installed added driver update for my card.

I'm having some occasional problems especially on boot and restarts. Monitor shuts down before desktop comes up like going into hibernation. Have to soft touch the power switch on computer or turn the monitor on/off to come up.

Locks up sometimes when switching to desktop two - goes full screen no icons and I can't get back to desktop one. Have to restart.

Tried to use compiz and tweak up to 4 desktops but had more problems so backed out settings  down to just 2 desktops. Still have wavey windows and theme running.

On Boot diagnostics I notice the comment:  NO VRAM -  just above the RAM check.

Does this mean it can't see the 64MB on my video card and is not using it or what?

Great forum here, the best I've ever seen - bar none.

---

### Post by Vesslan on 2007-12-30
1.  01:00.0 0300: 10de:0611 (rev a2)
2.  XFX Geforce 8800GT (overclocked version)
3. had to use the nvclock CVS to reduce fan speed with 169.07 driver.

---

### Post by magozoom on 2008-01-08
01:00.0 0300: 10de:0398 (rev a1)

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

Tweaks needed: added maximum laptop  resolution 1280 x 800 in xorg.conf

---

### Post by Shazaam on 2008-01-09
Fresh install of Gutsy.
0000:01:00.0 0300: 10de:00f5 (rev a2)
BFG GeForce 7800GS agp.
Tweaks- nvidia-xconfig didn't work, copied over my xorg.conf from Dapper. Works perfectly.

---

### Post by GSF1200S on 2008-01-10
1) 01:00.0 0300: 10de:0398 (rev a1)
2) Nvidia GeForce 7600 Go
3) Restricted Driver Manager (all that worked)
Had to remove nvidia-common-kernel to prevent API mismatch when using website drivers. Synaptic wouldnt work..

---

### Post by jespdj on 2008-01-10
1. Downloaded driver 169.07 from nVidia website
2. Switch to a text console with Ctrl + Alt + F1 and login
3. Make myself root with sudo -i
4. Copy the NVIDIA...run file to /root
5. Kill GDM (ps -ef | grep gdm to find the process number, then kill it)
6. Run the installer: sh ./NVIDIA...run
7. When it's finished, reboot

Problem: It starts X in low-graphics mode.
After a lot of puzzling, I discovered that I had to edit /etc/default/linux-restricted-modules-common: added "nv" to DISABLED_MODULES
I also uninstalled the Ubuntu nvidia driver: sudo apt-get purge nvidia-glx-new

After doing that and rebooting it works fine.

This works both on my desktop (8600 GTS) and laptop (8400M GS).

---

### Post by Kevbert on 2008-01-12
1) 05:00.0 0300: 10de:0392 (rev a1)

2) NVidia Corporation G70 [GeForce 7600 GS](rev a1) 512Mb

3) No tweaking needed.  Just went to System - Preferences - Appearance - Visual Effects - Changed to Normal from None and the updates were downloaded automatically.

---

### Post by KillerSponge on 2008-01-12
1) 01:00.0 0300: 10de:00f1 (rev a2)

2) XFX Geforce 6600GT 128mb

3) I used Envy to install the nvidia driver :)

---

### Post by jhetrick62 on 2008-01-12
1)  00:12.0 0300: 10de:053e (rev a2)
2)  00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053e (rev a2)  (onboard Nvidia on Biostar TForce TF7025-M2)
3)   Downloaded and installed latest Nvidia driver from Nvidia website and it ran out of the box after that.

---

### Post by wearekosh on 2008-01-18
01:00.0 0300: 10de:0400
Gigabyte  Ge8600gts - with 2 asus VW192t LCD's
driver downloaded with "Restricted Drivers Manager"
setup with "gksudo nvidia-settings" command
works great..........

---

### Post by pucenavel on 2008-01-20
Once I had 7.10 updated and had it already recognizing the need for the restricted driver (all by itself), the only thing I really had to to was run:

dpkg-reconfigure xserver-xorg

to manually apply the resolutions supported by my monitor.  The problem I was having was with the system only thinking that I could go to 800x600.

Everything is working OK now.

---

### Post by kodak on 2008-01-20
01:00.0 0300: 10de:0173 (rev a3)

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440-SE] (rev a3)


No tweaking needed

---

### Post by SZF2001 on 2008-01-20
01:00.0 0300: 10de:0110 (rev b2)

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

...Should I tweak something? I used to be able to run Beryl in Feisty just fine, but I upgraded to Gutsy and suddenly aren't allowed to run Compiz-Fusion or any fancy extra stuff...

---

### Post by Artemis3 on 2008-01-21
[list]
[*]03:00.0 0300: 10de:0611 (rev a2)
[*]03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
[*]I did [this](http://ubuntuforums.org/showpost.php?p=4131809&postcount=9) to make it work, and [this](http://ubuntuforums.org/showpost.php?p=4181624&postcount=21) to lower the fan noise.
[/list]
PNY Geforce 8800GT 512m

Output of NVClock 0.8 (Beta3):
```

artemis3@artemis3-desktop:~$ /usr/local/bin/nvclock -i
-- General info --
Card:           nVidia Geforce 8800GT
Architecture:   G92 A2
PCI id:         0x611
GPU clock:      601.712 MHz
Bustype:        PCI-Express

-- Shader info --
Clock: 1512.000 MHz
Stream units: 112 (0b)
ROP units: 16 (1b)
-- Memory info --
Amount:         512 MB
Type:           128 bit DDR3
Clock:          899.996 MHz

-- PCI-Express info --
Current Rate:   16X
Maximum rate:   16X

-- Sensor info --
Sensor: Analog Devices ADT7473
Board temperature: 49C
GPU temperature: 50C
Fanspeed: 3202 RPM
Fanspeed mode: auto
PWM duty cycle: 56.9%

-- VideoBios information --
Version: 62.92.16.00.04
Signon message: GeForce 8800 GT VGA BIOS
Performance level 0: gpu 600MHz/shader 1500MHz/memory 900MHz/0.00V/100%
VID mask: 3
Voltage level 0: 0.95V, VID: 0
Voltage level 1: 1.00V, VID: 1
Voltage level 2: 1.05V, VID: 2
Voltage level 3: 1.10V, VID: 3

```

---

### Post by Artemis3 on 2008-01-21
> **SZF2001 said:**
> 01:00.0 0300: 10de:0110 (rev b2)

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

...Should I tweak something? I used to be able to run Beryl in Feisty just fine, but I upgraded to Gutsy and suddenly aren't allowed to run Compiz-Fusion or any fancy extra stuff...

Try installing nvidia-glx-legacy package. geforce2 used to be in nvidia-glx.

---

### Post by SZF2001 on 2008-01-21
> **Artemis3 said:**
> Try installing nvidia-glx-legacy package. geforce2 used to be in nvidia-glx.

That didn't work.

Neither did the Restricted Drivers manager.

I tried Envy. Had little results... My card is found better off than it was before but I can't do anything.

```
(me)@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 18
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
```

---

### Post by malfist on 2008-01-22
02:00.0 0300: 10de:0043 (rev a1)
GeForce 6200 (setup was performed on FX 5200)

Neither the repo drivers worked nor nvidia's. Nvidia's didn't stick after reboot, repo couldn't handle the resolution of anything after 800x600 at 54Hz refresh.

Used Envy, worked since.

---

### Post by talbain on 2008-01-23
**lspci -n | grep 0300**:
01:00.0 0300: 10de:0611 (rev a2)

**lspci | grep VGA**:
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)

**Card**: Asus EN8800GT (nVidia GeForce 8800 GT 512MB)

**No tweaking needed**.

Installed with envy, over the default restricted driver (Also worked fine).
Actual driver version: 169.07

---

### Post by bkelly on 2008-01-25
I did not see how to post a URL in the FAQs, but Eracks (who sold me the conmputer with Gutsy installed) resolved my problem. I now have an ASUS card with NVIDIA chips running in dual monitor mode. (It was working when they sent it, but I messed with it and blew the config.)  The  procedure is documented in this thread:

[http://ubuntuforums.org/showthread.php?t=666034](http://ubuntuforums.org/showthread.php?t=666034)

---

### Post by seanreynoldscs on 2008-01-29
I have Nvidia 6600 with 512.

When Install the ubuntu Nvidia new restricted drivers, i have no luck.

When i go to Nvidia and get their updated driver, i get one screen working. 
When I use the Screen And Resolution in ubuntu, i get the Low Resolution error. 
I had alot of trouble getting Compiz and Dual Screens. This is what i did.


Process:
Get new ubuntu 7.10 with updates: DONT INSTALL RESTRICTED DRIVER. 
Go to Nvidia and get their driver and install it.
Install Nvidia Settings through Synaptic Manager. (STAY AWAY FROM [Screen and Resolutions] It breaks the xorg.conf file)
Go to the Nvidia Settings and set Seperate X Screens with xinerama. Reboot (make sure to save the xorg.conf file each time) ( I had to cut and paste it because the Nvidia settings did not elevate when trying to save the xorg.conf file)
Go back to Nvidia Settings and set TwinView and merge the settings.(make sure to save the xorg.conf file each time)

and its all better.

To make it work, i had to get: ```
sudo apt-get install nvidia-settings
```
which uninstalled the restricted nvidia new drivers (if you had them installed).

Using Nvidia settings I was able to get both monitors with good resolution and Compiz using seperate x screens or Using TwinView. BUT I did not want either of those settings. Seperate X Screens wouldnt let me drag a window from one screen to another, and twin view gave me one big cube and when i maximized a window it went to both monitors full screen!

So i found out that if you go to Seperate X Screens and tick xinerama and restart, it sets that flag in your xorg.conf file but disables 3D! Then if you switch settings to Twinview once xinerama was already ticked, you get the 3d with the ability to drag windows from one screen to another, Two separate cubes, and Maximize to one screen only. Exactly what i wanted. 

Im sure there is a better way to do this, Im quite new to linux: but i got it to work, and that was how.

---

### Post by cptnff on 2008-01-30
Nvidia quadro fx 1400

I just used th nvidia-glx driver in the synaptic package manger, and then in the terminal i put the following "sudo nvidia-glx-config enable" after that I restarted my computer, and everything seems to be working fine.

---

### Post by Michl on 2008-01-31
1)  01:00.0 0300: 10de:0028 (rev 11)
2) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 11)
3)  I installed it in two different ways, first
enabling the driver in the restricted drivers manager, and
then after disabling I used envy.  Both times everything 
worked, including 3D acceleration except that the highest
resolution was 800x600.  I tried lowering the depth to
16 in xorg, but that did not help.

---

### Post by perixx on 2008-02-02
Hello!

**I'm having big trouble** getting new Ati drivers to work, ever since I've had a Nvidia 6800XT with 169.09 driver in my system temporarily - some parts of that remained on my system, somehow **seeming to block ATI drivers** from installing properly... at first, I wanted to install the 8.01 drivers with my X1950 GT, but I'm not sure anymore, if they'll install on Feisty at all (due to DKMS) - but also 7.11 won't install now!

I'm afraid I've misplaced my initial thread; since it concerns both Nvidia and Ati issues, I'll link to my more detailed problem-thread (it's not too long - yet); according to a post in this thread, ATI 8.01 drivers are not made for the 'X'-series cards, so not for me... I dunno, if 8.01 is supposed to install under Feisty at all:
[http://ubuntuforums.org/showthread.php?t=685476]("http://ubuntuforums.org/showthread.php?t=685476")

**ADD: **As far as I can tell, I've removed all Nvidia crap that has obviously totally borked my symlinks before:
[http://ubuntuforums.org/showthread.php?t=679086]("http://ubuntuforums.org/showthread.php?t=679086")

perixx

---

### Post by Sockerdrickan on 2008-02-03
```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

---

### Post by perixx on 2008-02-04
Hello Tux0r...

> sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
 I already have those packages.

> sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules* Of the 'nvidia' components, only 'nvidia-kernel-common' is still there; removing it would also remove 'linux-restricted-modules*' (as you suggested). But this would also remove any other restricted modules, such as for sound, printer and so on, wouldn't it?). Apart from that - AFAIK, 'restricted modules' are only loaded, if they're not blacklisted in /etc/default/linux-restricted-modules-common, so they shouldn't at the moment.

I'm not sure what happened, if those were removed and I guess those wouldn't be automatically reinstalled during the driver-setup - besides, I've reinstalled the 'linux-restricted-modules*' via Synaptic before...
Supposedly, some symlinks are amiss, so already installed ATI-driver parts won't work, that otherwise would. Do you think that going through those steps really would make any difference for missing symlinks?

From what I can tell, in your proposal, the only steps other from what I've done so far are:> sudo apt-get --purge nvidia-kernel-common linux-restricted-modules* of which I did the latter one separately from all other steps (more specifically: reinstalled it). Also, /etc/init.d/nvidia-kernel is still on my system.

**ADD:** guess I've disposed of Nvidia, finally - **here's... HOW**:
[http://ubuntuforums.org/showpost.php?p=4266586&postcount=7]("http://ubuntuforums.org/showpost.php?p=4266586&postcount=7")

perixx

---

### Post by wabbalee on 2008-02-08
the problem i got with my card was to do with resolution being too low (800x600) and could not get it higher in gutsy.  

nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

what i did:

installed headers for my kernel (ubuntu studio) and another file (development?) which i forgot but nvidia installer tells what to do/get.

downloaded latest driver for my card:
[http://www.nvidia.com/object/linux_display_x86_71.86.04.html](http://www.nvidia.com/object/linux_display_x86_71.86.04.html)

theN to kill x in ubuntu (as this must be done from a commandline without x running) i issued command: 

sudo /etc/init.d/gdm stop


cd to directory with nvidia script file in it and ran (as root):

sh NVIDIA-Linux-x86-71.86.04-pkg1.run

answered questions accordingly (this is where i bumped in the files that were missing but all was in ubuntu repo's)

remember where installer places a readme file! find it later and read 'sec 3' about editing xorg.conf (comment out: 'dri')

after running Nvidia script do: startx

in a terminal run (or still from commandline) run: 
dpkg-reconfigure xserver-xorg
answer questions correctly, especially the one about resolutions (choose 'medium' if you are not too savvy about ins and outs of vertical/horizontal refresh rates and choose available resolutions for your monitor. do not pick too high refresh rate or risk frying your monitor)

edit xorg.conf according to previously mentioned readme file and restart x

imho: ubuntu restricted driver manager loads wrong driver (saw it in synaptic!) for this card: the 96xx driver instead of 71xx, which is for even older cards like mine.

as far as i know (read it somewhere) this card may not work properly with compiz fusion, but one can find that out through trial and...

good luck!
ron

---

### Post by herbster on 2008-02-09
sh NVIDIA-Linux-x86-169.09-pkg1.run

Hit ENTER a few times, done.

---

### Post by yizuman on 2008-02-09
I am using a Nvidia Riva, Riva TNT, Geoforce,,,,(something, cuts off at the 800x600 resolution), it's an integrated video card (generic)

It doesn't work at all when it's installed. I'm using a Nec Multisync A500 monitor.

---

### Post by PaJoe on 2008-02-13
1. 02:00.0 0300: 10de:0421 (rev a1)
2. 02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
3. Used  Envy to install drivers with no additional tweeking

---

### Post by Christmas on 2008-02-13
On Debian Testing 'Lenny':
1. I installed the Linux headers linux-headers-2.6.22-3
2. I installed the NVIDIA binary driver (RUN package from their official website)
3. Changed 'nv' to 'nvidia' in /etc/X11/xorg.conf

I know this is not the recommended way but it's the simplest for me and whenever a kernel update occurs I reinstall the driver.

On Ubuntu, I used to only do a:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
And restart the X server.

---

### Post by texasjim on 2008-02-16
01:00.0 0300: 10de:0181 (rev a2)

Card is:  VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

No tweaks, just ran ENVY.

  Good job,thanks

---

### Post by Moog Moogle on 2008-02-17
Apologies posted in the wrong thread. If there are mods on this forum please delete this post.

Thank you.

---

### Post by K.Mandla on 2008-02-23
Moved to Multimedia and Video. I'm not sure why it was in the Cafe. :-k

---

### Post by BXA121 on 2008-02-24
i dont have an NVIDIA video card- i have an ATI 9800 pro card. 

on my searches, i found  a really simple way to install proprietry drivers! install Envy and it will complie and install the right driver!
here it is!

[http://www.ubuntu1501.com/2007/12/in...ti-driver.html](http://www.ubuntu1501.com/2007/12/in...ti-driver.html)

So simple! i tried to use the guides to manually activate my driver to no end - i failed - i searched around and foudn this dell guide ( i dont have a dell) and it worked fine. 

hope this helps.

---

### Post by HHelsinger on 2008-02-24
People should be made aware that not all failures can be fixed by tweaking the xorg.conf. file.  Various monitors produced several years ago have faulty EDID software in the monitor with which the nVidia drivers react badly.   One result is that the monitor goes into power save mode, and then freezes.  The result is a black screen, but it has nothing to do with refresh rates, modelines, or anything else in the xorg.conf file.   If that is your situation you may have to modify the monitor software.     The xorg.conf file can't deal with it.   Here are links to the relevant information, in the hope that it will save someone lots of time and frustration.


[http://forums.us.dell.com/supportforums/board/message?board.id=dim_monitor&message.id=33721]("http://forums.us.dell.com/supportforums/board/message?board.id=dim_monitor&message.id=33721")

[http://www.geocities.com/jgeneedid/]("http://www.geocities.com/jgeneedid/")

the Dell files aren't available from Dell -- no one there (wherever there may be) knows anything about it all.   But you can find the files available for download here:

[http://www.jeffgeiger.com/Stuff/DVI_Recover.htm]("http://www.jeffgeiger.com/Stuff/DVI_Recover.htm")

---

### Post by -random on 2008-02-26
foxconn 8600gt on both ubuntu 32 and 64 bit:

1. package manager for:
 * nvidia-glx
 * libc6-dev
(also but, most probably installed)
 * gcc
 * make.
2.go to nvidia.com and download your driver, then put in in root directory (easy accesible).
2.restart with nvidia graphix card
3,ctrl + 4
4.init 3
5./etc/init.d/gdm stop
6.cd /
7.sudo sh /N (press tab to complete the rest of the sentence, adding something like nvidia..
8.sayd yes to all instructions (compile kernel, configure x).
9.startx

There you go! Hope this helpd!

p.s.

32bit is smooth as vanilla... but the 64bit is giving me some shiz which i'm too tired to tinker out futher now, I'll try ENVY on it asap..

---

### Post by bred on 2008-03-04
Hi guys,

01:00.0 0300: 10de:0177 (rev a3)
nvidia 440

I tried Envy- did not work good...
i had a black monitor, reinstalled ubuntu 7.10 again...tried to install manual all 3 drivers with envy- and got nothing
have no ideea what to do?
thx

---

### Post by nativehound on 2008-03-07
[LIST=1]
[*]01:00.0 0300: 10de:00f1 (rev a2)
[*]Nvidia 6600GT AGP
[*]sudo nvidia-xconfig[LIST]
[*]Synaptic Package Manager to uninstall  xserver-xgl to get direct rendering to work properly with full desktop effects 
[*]no further tweaking
[/LIST]

---

### Post by bred on 2008-03-08
my nvidia driver doesn't work, have no idea what to do...

---

### Post by denny1105 on 2008-03-10
01:00.0 0300: 10de:0140 (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
No Tweaking needed

---

### Post by AMD64_N_Linux on 2008-03-14
1)  02:00.0 0300: 10de:0391 (rev a1)
     04:00.0 0300: 10de:0391 (rev a1)

2)  02:00.0 nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
      04:00.0 nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

TWEAKING....

When I first installed Ubuntu 7.10  x64 with one of the 2 cards, it was listed on PCI bus 3.

After I installed 2nd card, first card was at PCI 4 the 2nd at PCI 2. This confused me to no end, and SLI mode would work until a "2nd" reboot,

I have spend a week, installing the drivers with different methods, from using the restricted drivers, automatix, the drivers from nvidia. and envy.

I tried tweaking xorg.conf with a number of methods, including trying to hack it by hand. 

Had many errors after many attempts. The error that I got most frequently and usually started after 2nd reboot, was a complaint in the /var/log/Xorg.0.log. was a statement which varied, but talked about a "parent device".

A few hours ago, I remembered a discussion, on a non-linux forum, about using different graphics cards in SLI mode, and how it would supposedly work, as long as the card in the primary PCIE slot was the slowest of the 2 cards.

Although my cards were ordered at the same time from newegg, are both the same exact model, etc... etc .... 

I thought maybe.....

I switched the cards, removed all the drivers, rebooted into recovery mode, ran ENVY in text mode ( envy -t ) and installed the drivers.


What do you know, both cards are in SLI mode, and working beautifully.

I have rebooted at least 30 times, booted into Windows XP several times, and the config is holding and working. 

I guess that the auto detect function of the nvidia drivers even works on exact models of the same card.

the only weird thing is that the parent card is STILL on the PCI 4 bus instead of 2, but as long as it works.......

Just thought I would share this, maybe someone else is having the same problem.

---

### Post by WileyHunter on 2008-03-16
OK, so I just picked up the Nvidia GeForce FX5500 (256 MB) from the local Wally World.  And before anyone says it...  I know it's not top end, but it'll do for me.

Install on an OLD Compaq Presario 5284 that is laying around the closet.  AMD 6 450MHz if I remember right.  Can't remember the memory (think there's a name for that).

So I pull the cover, stick it in avail slot and fire up the Ubuntu Install 7.10.  Wham! it's locked on.  I haven't tested it fully yet but it sure seems PnP.  Got me all fired up, I'm planning on using this as a test bed for a homemade DVR and the S-video on the card caught my eye.  I will eventually build something with more gusto to it but for now, alas I settle.

Not shabby for about $75.:guitar:

WH

---

### Post by mgysgthath on 2008-03-22
01:00.0 0300: 10de:0191 (rev a2)
BFG 8800 GTX 768 MB

I simply used the "Envy" script provided on another page, and it went off without a hitch.  Ubuntu's resolution changer (gnome?) shows wonky refresh rates, but Nvidia's utility works just fine.

---

### Post by cozmicharlie on 2008-03-22
I just installed the beta Hardy and this is what I had to do.  Initially after install I booted only to get the screen that says the resolution is not supported.  I booted to safe mode and this is what I did:

Install the nvidia driver using the hardware drivers proprietary drivers.
opened applciations>screens and Graphics - found my monitor listed under model and set it up.
Rebooted and adjusted the resolution

Thats it - really improved in Hardy.  The xorg.conf file really looks different in Hardy though.  

**My xorg.conf in Gutsy**

Section "Device"
	Identifier	"nVidia Corporation NV41.1 [GeForce 6800]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-40
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV41.1 [GeForce 6800]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"


**My xorg.conf in Hardy**

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E196FP"
	Horizsync	31.0-83.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@75"	"1792x1344@60"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection

---

### Post by richardh9936 on 2008-03-22
lspci -n | grep 0300
NVIDIA geforce 7600 gt
NEC Multisync FP2141SB
:KS
technically, it worked immediately.  However, I had ghosting, which for quite a while I blamed on the driver, until I realised that, if it was a TV, ghosting would be caused by poor quality signals or interference effects.  I changed the video cable from a long thin one to a short fat one, and that resolved all the ghosting issues.

Finding information about faults with the Nvidia cards or drivers, or the NEC multisync screens, was very difficult.  In hindsight, I believe this is because they work so well.  ie most people ask for help with incidents.  They don't tell us about their successes.  Good products get very few incidents, so they appear less in web searches.

So, I must remember my physics.  Not all "ict" problems are software or the usual hardware issues.  Sometimes, they are old-fashioned physics like interference.

And thanks for creating ENVY.

---

### Post by SnakeHips on 2008-03-24
pete@desk:~$ lspci -n | grep 0300
01:00.0 0300: 10de:0221 (rev a1)

pete@desk:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

No Tweaking

---

### Post by vlaar on 2008-03-29
1. 01:00.0 0300: 10de:0402 (rev a1)
2. Nvidia (asus) 8600gt
3. Worked with without tweaks

---

### Post by dmatej on 2008-03-30
GigaByte GeForce 8800 GT 

Kubuntu hardy 32bit:
Download the driver package from nvidia (169.12 in my case) and run it as root after console login. 
Didn't find any problem, but hardy wasn't yet ready for me ;)

Kubuntu gutsy 32bit
1) Download driver the package from nvidia (169.12 in my case) 
2) Restart and login to console as root
4) copy /etc/X11/xorg.conf /etc/X11/xorg.conf.arc - package archives cfg still to the same name, so if you run it twice, old configuration is lost.
3) sh pathtopackage - it will fail, but tell what you need to download
4) run aptitude and download missing things (kernel headers, libc, ...). Exit aptitude.
5) sh pathtopackage - install the driver, but don't let it write configuration (last question) - it breaks it.
6) Run dpkg-reconfigure xserver-xorg - ... when selecting a graphic driver, select nvidia, not nv. And after answering all the questions, save it and restart the computer.

I have tried many variants of this, but the last point was missing on every "howto" :D
I'm not sure with point 5), I have tried also this: [http://ubuntuforums.org/showthread.php?t=458930](http://ubuntuforums.org/showthread.php?t=458930) and now don't know which one is working now ...

---

### Post by mattchew on 2008-03-30
results of lspci -n | grep 0300

```
01:00.0 0300: 10de:0407 (rev a1)
```

Nvidia 8600M GT - laptop is an Asus C90S (if you want to look up specific 8600M GT type)

Ubuntu Gutsy 32bit

Since I am a complete ubuntu noob, what I had to do was install XGL. Prior to XGL I was getting the ```
The error was 'RenderBadPicture (invalid Picture parameter)'.
```  message.

I've still yet to find what I have to change in the config to separate the screens, working on that.

---

### Post by hooflung64 on 2008-03-30
```
michael@Bluebomber:~$ lspci -n | grep 0300
05:00.0 0300: 10de:0606 (rev a2)
```

eVGA 8800GS Superclock 384mb Ram | 192bit Memory Bus

Ubuntu 7.10 AMD64 Edition

I found that I couldn't just install the Nvidia official drivers after installing Ubuntu 7.10 and doing the updates through Update Manager. What would happen is that it would work fine until I rebooted. Then I would be forced into the failsafe. So this is what I did after doing another fresh install ( about the 4th time overall mind you so I was about to just gentoo this box if this hadn't worked ) and ran another system update through Update Manager.

I removed anything Nvidia related already on the system through synaptic.

Then I went into a terminal  after exiting the window manager by CTRL+ALT+F2 and did:

```

sudo /etc/init.d/gdm stop

sudo apt-get install ia32-libs
sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev

sudo sh NVIDIA-Linux-x86_64-169-12-pkg1.run

sudo modprobe nvidia

sudo vim /etc/X11/xorg.conf

sudo /etc/init.d/gdm start

```

When the Nvidia Installer asked to make xorg.conf file I said no. I then manually replaced 'vesa' with 'nvidia' in the original.

I found if I didn't do the ia32-libs the OpenGL 32 compatibility sanity check would fail. I then went into the Nvidia X Server Settings page and exported the new xorg.conf file into my Documents as xorg.conf.new and coped the original to /etc/X11/xorg.conf.old and then copied my new one over as the main xorg.conf file.

Restarted and BAM. All is good after I rebooted. Hopefully some others might find this helpful. Basically what was happening is that there were conflicting files on the system AND the Nvidia Installer wasn't inserting the module into the kernel except for the current session.

---

### Post by vercan on 2008-04-04
Thinkpad T61 with nVidia Quadro NVS 140M:

I installed the propietary drivers from the Restricted Drivers Manager, ran nvidia-settings (easy to use graphical utility) from the command line, enabled my ViewSonic 1680x1050 widescreen external monitor and wow!

When I use the laptop standalone, I get 1400x1050 on the LCD.  When I dock the laptop I get 1680x1050 on my external monitor.  No need to switch resolutions, everything works automatically.  I am really impressed.

---

### Post by RollingFred on 2008-04-09
Thinkpad T61 with nVidia Corporation Quadro NVS 140M (Same computer as above obviously)

Installed nvidia proprietary drivers through Envy after some struggling with TwinView.
Used Nvidia-settings to configure.

Got two xorg.conf:

* One enabling dual external monitors (one DVI, one VGA) with TwinView. Compiz Cube is working great (Although doesn't look like a cube, more like an octagon). Ctrl + Alt + left/right Changes both monitors desktops. Both monitors are 1600x1200 (that's not mine, that's work).

* One enabling the laptop panel only (1440x900).

> lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

> lspci -n | grep 0300
01:00.0 0300: 10de:0429 (rev a1)

Hope this helps

---

### Post by Johnnny on 2008-04-12
1. 01:00.0 0300: 10de:00f5 (rev a2)
2. 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
3. Installed with ***Envy Legacy*** script (Thanks for your script **tseliot**)

**NOTES:** Downloaded and installed ***Envy Legacy,*** followed the GUI, and selected the first option "Install nVidia Driver," rebooted for changes to take effect.

**TWEAKS:** Witnessed a problem after every reboot. The desktop screen would change to lower resolutions than desired. Altering the xorg.conf file did not help. I left it at default. Someone else **[SIZE="4"][here]("http://ubuntuforums.org/showthread.php?p=3060834&highlight=7800#post3060834")[/SIZE]** also had the same problem. If you read his post, he mentioned that he found the %gconf.xml located in the following directory:

(user-home)/.gconf/desktop/gnome/screen/default/0/%gconf.xml

But unfortunately for me I didn't have the files and all of it's directories and sub-folders until I rebooted a few times. Then right after the reboots I went and checked again and everything was there(weird). Somehow the %gconf.xml file was automatically created including other files and it's directories and sub-folders. In the %gconf.xml file it included the following:
```
<?xml version="1.0"?>
<gconf>
        <entry name="rate" mtime="1208233546" type="int" value="50">
        </entry>
        <entry name="resolution" mtime="1208233546" type="string">
                <stringvalue>640*680</stringvalue>
        </entry>
</gconf>
```
To fix my problem all I had to do was change 640*680 to my desired resolution which is 1280*1024, saved it and rebooted the computer and all was fine.

To be specific I broke everything down to get a better picture. Here is how it looks like for me at the moment.

	Open up terminal

	cd /home/username/.gconf/desktop/gnome

	cd screen

	ls    <===should return a folder called 'default' and an empty file called %gconf.xml

	cd default

	ls    <===should return a folder called '0' without quotes and an empty file called %gconf.xml

	cd 0

	ls    <===should contain a file called %gconf.xml containing code.

	%gconf.xml  <===This file should not be empty and it should contain code. In my case the above and similarly to this **[SIZE="4"][one]("http://ubuntuforums.org/showthread.php?p=3060834&highlight=7800#post3060834")[/SIZE]**

 - Linux 1 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
 - Current Driver Version: 169.12
 - Resolution: 1280x1024

Default xorg.conf file at /etc/X11/xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"17Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"17Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
Section "Module"
	Load		"glx"
EndSection
```
[SIZE="5"]**UPDATE**[/SIZE]

 - OS x86
 - 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
 - 01:00.0 0300: 10de:00f5 (rev a2)
 - Ubuntu Hardy 8.04 LTS 2.6.24-16-generic
 - Nvidia Driver Version: 169.12
 - Installed with EnvyNG

I just recently upgraded to **Ubuntu Hardy 8.04 LTS** without uninstalling my old video card drivers inluding Envy. The upgrade was perfect except that it had a problem with my old driver. To fix the problem I uninstalled Envy completely by issuing the following commands:
```
sudo apt-get remove envy

sudo aptitude purge envy

sudo rm -R /usr/share/envy
```
Then I installed EnvyNG:
```
sudo apt-get install envyng-gtk
```
Installation was successful. I opened up EnvyNG GUI over at "Applications/System Tools" and did an automatic installation of the Nvidia drivers. Rebooted and everything was fine.

Default xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"17Monitor"
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"17Monitor"
	Option		"DPMS"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by Ed Parlette on 2008-04-22
01:00.0 0300: 10de:0611 (rev a2)
MSI (NVidia) GeForce 8800GT 512MB
No tweaks needed

I installed hardy heron, and everything worked. I installed the third-party driver (in Ubuntu) and everything worked fine.

Ed Parlette

---

### Post by dage on 2008-04-23
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e4 (rev a1)

Card is nvidia 8400GS

I've downloaded and install the binary driver downloaded from official website of nvidia.
To be able to install the file, i've to boot in "rescue mode".

---

### Post by Jsk2003 on 2008-04-26
Nvidia Geforce 6200

dalton@kids-computer:~$ lspci -n | grep 0300
01:06.0 0300: 10de:0221 (rev a1)

I just had to enable the driver in
System>Administration>Hardware Drivers

Then I restarted using Ctrl+Alt+Backspace

Then it worked fine.

---

### Post by Nathan.Flow on 2008-04-26
00:12.0 0300: 10de:0531 (rev a2)
Nvidia 7150M on mother board
had to reset the resuliton from 800X600 to 1280X800
also get weird message about xorg.conf when switching to alt+ctrl+f2, something about using the wrong bussid.  will post it when I see it agin.  
all esle works fine.
no futher tweaks

---

### Post by lantana on 2008-04-27
Nvidia GeForce 7800 GTX with 512 ram
Ubuntu Heron on a 64 bit AMD dual core ---& I'm also dual booting with XP
Had problems on install with max resolution at 600X400

Simple fix that worked for me:

1)Go to Synaptic manager; download & install envyng [core,glf,qt & associated packages] Takes about 15 minutes to download & install all the packages

2) Go to system tools and run envy program.....does it all, just pick what you want

3) Go to terminal screen & type. 
     sudo displayconfig-gtk

Bingo for me & good luck
lantana

---

### Post by bjbosch on 2008-04-29
GeForce Ti-4400
01:00.0 0300: 10de:0251 (rev a2)
Had the low resolution screen
Installed NVidia-settings
Changed the resolution and applied
Tried to save X conf with this message (still getting it)
"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."
Saved the xorg.conf to /home
Copied and pasted contents to /etc/X11/xorg.conf

---

### Post by brigadoon on 2008-04-29
My fix can be found at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

By the way, Thanks for writing the envy program in the first place. Your work saved me hours of pain. ](*,)

---

### Post by nineowls on 2008-05-02
1.) wa01:00.0 0300: 10de:01dc (rev a1)
2.) 01:00.0 VGA compatible controller: nVidia Corporation G72GL [Quadro FX 350M] (rev a1)
3.) I tried many things--but the Envy install reboot uninstall reboot 
Followed by enabling "Restricted Drivers" was the last thing I did and now everything works
this is my xorg.conf section
```


Section "Device"
        Identifier      "nVidia Corporation G72GL [Quadro FX 350M]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-96
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G72GL [Quadro FX 350M]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1920x1200"
        EndSubSection
EndSection


Section "Module"
        Load            "glx"
EndSection




```
if this is not helpful--send me a message and i will shorten it up

---

### Post by gslo on 2008-05-04
> **cracker said:**
> 0000:01:00.0 0300: 10de:00f2 (rev a2)

Card is a Chaintech GeForce 6600 256MB AGP 8x.
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

Installed nvidia-glx in Synaptic and changed driver from "nv" to "nvidia" in xorg.conf, no additional tweaking required.
Thanks for your post,it worked perfectly.I have been fooling around with other methods for a week with limited success. Thanks again!

gslo

---

### Post by tnt533 on 2008-05-04
Ubuntu 7.04 Feisty Fawn *fully updated*
nVidia 8800 GTX 768mb  x2 in SLI

No SLI as of yet 

installed using nVidia's downloaded installer from outside of X with no issues. 

Edited /etc/X11/xorg.conf to enable composite and beryl works out of the box also.

Cheers!

---

### Post by Zanshin on 2008-05-07
1)  01:00.0 0300: 10de:0622 (rev a1)
2)  01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1) [


3)  Not simple install - nvidia drivers not ready for prime time

Details:
New install Ubuntu 8.04 LTS Hardy
Started with nVidia 7300LE - after new install, used Synaptic to download nvidia proprietary driver from repos using glx-new pkg (iirc) - was same ver as most recent on nvidia site - yay.

However, glxgears on that card only 2000 fps tops.  Weak for ETQW.  Got new card nvidia 9600GT OC from BFG.  Generic driver works, but need nvidia proprietary driver for good glxgears.  glx-new no good for 9600, unusable video.  Other posts have stated the production nvidia driver doesn't work for the newest cards and the BETA drivers from nvidia site must be used.  However, some forum posters state the most recent 173.08 beta driver (April 10 2008) is unstable, so the March 2008 171.06 beta must be used.  I used 171.06.

Here were my key references, although separately they were not complete for a noob like me (continuing my climb up the learning curve).

[http://ubuntuforums.org/showpost.php?p=4873656&postcount=15]("http://ubuntuforums.org/showpost.php?p=4873656&postcount=15")

[http://ubuntuforums.org/showpost.php?p=4863356&postcount=8]("http://ubuntuforums.org/showpost.php?p=4863356&postcount=8")

Here are the steps I took:

    * find the file here:    [http://us.download.nvidia.com/XFree8...71.06-pkg1.run]("http://us.download.nvidia.com/XFree8...71.06-pkg1.run")
    * download file
    * go to the download directory and add permission to execute using "chmod +x [filename.run.Here]"
    * alt+ctrl+F1 [to get to tty screen]
    * sudo /etc/init.d/gdm stop [to shutdown gnome gui shell]
    * type "uname -r" to get the correct info to replace in "linux-headers" line in next step
    * sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
    * note: above step was tried with just the gcc lib and didn't work.  had to add the gcc-3.4 also to get the right libc header files installed.
    * press: y if done
    * sudo sh NVIDIA-Linux-x86-171.06-pkg1.run
    * accept agreement, say No to next question, OK to build linux headers, YES to autoconfigure xconfig

I've read that these beta drivers aren't fully cooked yet.  Problems have been noted by others.  There are soooo many 8xxx and 9xxx series cards out there that you'd think nvidia would be spending more time on it or delivering faster.  But, 171.06 was from 3/7/08 and 173.08 is from 4/10/08 - maybe we'll see the new beta driver soon. 

GLX gears went to 10000 fps on the new card (once the drivers were loaded).  

Then added the following to my xorg.conf:

Section "Device"
       Option          "TripleBuffer" "true"
       Option          "RenderAccel"   "true"
       Option          "AddARGBGLXVisuals" "true"
       Option          "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
       Mode    0666
EndSection

This took glxgears to about 11000.

Waiting now for the final driver release from nvidia...tick tock tick tock...

---

### Post by cybercookie72 on 2008-05-07
1.  01:00.0 0300: 10de:01df (rev a1)
2.  Nvidia 7300gs lowprofile (it's in a optiplex gx280)
3.  no tweak just d/l & used EnvyNG when I didn't get the prompt..

---

### Post by briandu on 2008-05-08
SOLVED!!! :popcorn:

I used Envyng this did not work - I tried various installs but ....

So this is what I did:
open terminal:
cd /lib/linux-restricted-modules

sudo rm .nvidia*

[U][B]UPDATE - due to another install on another PC
from here
[/B][/U]use Synaptic and remove all nvidia files such as :
linux-restricted-drivers
xserver-xorg-video-nv
nvidia-xconfig
nvidia-settings
nvidia-kernel-common
[U][B]to here

[/B][/U] then:
downloaded the NVIDIA driver - I used 173.08.
sudo chmod +x NVIDIA-Linux-x86_64-173.08-pkg2.run (   note this is for 64 mode)
(note place this in you home directory - easy access)

press Ctrl+Alt+F1
log in 

enter:
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run (say yes to all prompts)
sudo reboot

then:
Done!!!!:popcorn:

Goodluck!

---

### Post by Cauda_Draconis on 2008-05-08
I love Envy.

1. 01:00.0 0300: 10de:0100 (rev 10)
2. lspci -n | grep VGA doesn't return anything for some reason, but I have an old GeForce 256.
3. When I upgraded to Hardy, my comp would only run at 800x600, so I used Envyng to install the drivers, and now it works! :D running at 1400x1050, Compaq 7550 colour monitor. Thank you muchly, Envy writer :D.

---

### Post by Bari on 2008-05-08
Hi, running Hardy
01:00.0 0300: 10de:0221 (rev a1)
Geforce 6200 256mb
no tweaks needed just used nvidia-glx new and everything worked fine.

---

### Post by vaxius on 2008-05-09
My computer is an HP pavilion dv2116wm with a GeForce Go 6150.  The driver installed without any problems.  I had to do a few things to make suspend work on this system (see link below).

[LIST]
[*][Howto: Install nVidia driver]("http://blog.vaxius.net/?p=42")
[*][Howto: Get suspend working]("http://blog.vaxius.net/?p=43")
[/LIST]

Edit: Changed card from 1650 to 6150 (typo).

---

### Post by draxbear on 2008-05-10
Card Details:
$ lspci -n | grep 0300
01:00.0 0300: 10de:0044 (rev a1)

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 XT] (rev a1)

~$ uname -m
x86_64

Problem(s):
The base Ubuntu install of this card with open drivers works great.
However I want to run eve-online so need to get OpenGL support working.

Ages ago I had issues getting things working on Fiesty and finally resolved that after trying each Nvidia driver and manually modifiying my /etc/X11/xorg.conf file after each attempt to find a working combination.

After upgrading from Fiesty to Gibbon using the built in option everything worked ok. Unfortunately the jump from Gibbon to Heron was not so easy.

I tried (with synaptic) each of the 3 Nvidia drivers without success.

After reading around on here it seemed I would need the "ia32-libs" packages. I couldn't get them to appear no matter how I modified my apt sources. The problem was the non AMD64 version of Ubuntu I was running (results from uname -m mentioned i686). So I reinstalled Heron from scratch with the AMD64 ubuntu cd.

Still had problems and tried my luck with envyng, a great tool, that's probably put in many of the other undocumented packages I needed to get the Nvidia driver working. Unfortunately it didn't quite get me there. 

On startup I kept getting either a black screen (169.12 latest Nvidia driver) or that annoying "configure your screen menu" (the other 2 Nvidia drivers) which I just hit continue to get past.

The key in my case was to use:
A) The 96.43.05 (new legacy) Nvidia driver.
B) Correct settings in my /etc/X11/xorg.conf file for my monitor

Everything was good to go, but my monitor settings were stuffing me up. Specifically the resolutions it was capable of. Some more reading allowed me to concoct a working xorg.conf file (attached) for my LG L222W (Analog) monitor. I am now able to run eve-online and pass every test with it's config tool.

Way too much hassle, but it's not Ubuntu's fault that the Nvidia drivers (ok at least they provide some!) are not playing nice by identifying their dependencies properly. We'll just get the package maintainer to fix it up...oh hang on there isn't one cause Nvidia isn't! :)

---

### Post by ali999 on 2008-05-11
I have an NVIDIA 9600GT installed with version 8.04. I've posted how I got everything working for it here: [http://ubuntuforums.org/showthread.php?p=4892694#post4892694](http://ubuntuforums.org/showthread.php?p=4892694#post4892694)

---

### Post by Johan_A_N on 2008-05-11
1: 01:00.0 0300: 10de:0402 (rev a1)
2: GeForce 8600 GT
3: No simple change. This was after several other attempts to get the system to work.
Note that during the process my x-server was totally non-functional and xfix could not get it to work.

I Download NVIDIA-Linux-x86-173.08-pkg1.run from nvidia and Changed kernel from 386i to generic.
Then I removed all nvidia files I could find among others:
* xserver-xorg-video-nv
* nvidia-xconfig
* nvidia-settings
* nvidia-kernel-common

After I restarted the system the x-server was not working. 
I ran xfix and restarted. And the x-server still did not work
Then I Installed the new nvidia driver (NVIDIA-Linux-x86-173.08-pkg1.run) allowing it to change my xorg.conf file and restarted the system.

After this the system worked.

---

### Post by rsidle on 2008-05-11
01:00.0 0300: 10de:0622 (rev a1)
EVGA Geforce 9600GT 512mb
Installed from nvidia's binary version 171.05, minor modifications of xorg.conf as it did not auto-detect resolutions.

---

### Post by Lucky LIX on 2008-05-13
1) 01:00.0 0300: 10de:0253 (rev a3)

2) Chaintech GeForce 4 Ti 4200 128MB
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

3) No tweaking needed

---

### Post by fsckedagain on 2008-05-21
mike@darkstar:~$ lspci -n | grep 0300
01:00.0 0300: 10de:042d (rev a1)

mike@darkstar:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 360M (rev a1)

had to get my EDID of my video card to make it not be stupid.
mike@darkstar:~$ cat /etc/X11/xorg.conf | grep EDID
    Option         "CustomEDID" "DFP-0:/home/mike/edid.bin"

mike@darkstar:~$ glxgears
15553 frames in 5.0 seconds = 3110.597 FPS
15485 frames in 5.0 seconds = 3096.854 FPS
15593 frames in 5.0 seconds = 3118.451 FPS

---

### Post by Not Sure on 2008-05-22
1.) 01:00.0 0300: 10de:0402 (rev a1)
2.) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT -DDR3 (rev a1) 256 Meg 
3.)  Ubuntu 10.4 64-bit required three steps: Download 64-bit Linux driver from NVIDIA website. Attempted to install and received error message that libc header files were missing. Used the Synaptic Package Manager to download and install all libc dev packages since I didn't know which one was needed. Ran the 64-bit Linux driver again.  This compiled code specifically for this pc. Now, it works fine. See attached screen capture.  :popcorn:

---

### Post by butterman on 2008-05-23
1.  01:00.0 0300: 10de:01d8 (rev a1)

2. 01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)

3. X server failed to start on first restart after upgrade to Hardy.  Based on this [post]("http://ubuntuforums.org/showthread.php?t=198480"), I did the following:

```
sudo dpk-reconfigure xserver-xorg
```

I took the default for every answer

```
sudo /etc/init.d/gdm restart
```

It worked!

---

### Post by smarks on 2008-05-24
Hey everyone,

I am having a problem with my 9600GT card. I have been trying to solve this for days and can't find any help. I have 8.04 installed. when I try to run the file in F1 all i get back is:
sh: Can't open /nvidia-linux-x86-173.08-pkg1.run

I disabled gnome, idk if im missing something. the file is saved to my desktop.
Please HELP!!

---

### Post by phillywize on 2008-05-24
> **PaJoe said:**
> 1. 02:00.0 0300: 10de:0421 (rev a1)
2. 02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
3. Used  Envy to install drivers with no additional tweeking

Similar setup; no such luck:

(1) 01:00.0 0300: 10de:0421 (rev a1)
(2) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
(3) Envy failed; repo packages failed.  Had to manually install the nvidia beta drivers, using the info [here]("https://bugs.launchpad.net/ubuntu/+bug/222407") (bug report).

Criminy...widespread breakage of nvidia drivers is no way to start out an LTS.

---

### Post by adamthompson on 2008-05-24
Hardy, NVIDIA GeForce 6100, 64-bit AMD processor.

I tried several things, starting with repository driver installation. When that didn't work, I tried EnvyNG, which didn't work either. Eventually I tried nbayiha's advice in this thread ([http://ubuntuforums.org/showthread.php?t=765985&highlight=nvidia+hardy+modules&page=3]("http://ubuntuforums.org/showthread.php?t=765985&highlight=nvidia+hardy+modules&page=3")), which worked. Yay!!!!!

---

### Post by briandu on 2008-05-28
SOLVED!!! :popcorn:

I used Envyng this did not work - I tried various installs but ....

So this is what I did:
open terminal:
cd /lib/linux-restricted-modules

sudo rm .nvidia*

use Synaptic and remove all nvidia files such as :
linux-restricted-drivers
xserver-xorg-video-nv
nvidia-xconfig
nvidia-settings
nvidia-kernel-common
 then:
downloaded the NVIDIA driver - I used 173.14.05
sudo chmod +x NVIDIA-Linux-x86_64-173.14.05-pkg2.run (   note this is for 64 mode)
(note place this in you home directory - easy access)

press Ctrl+Alt+F1
log in 

enter:
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run (say yes to all prompts)
sudo reboot

then:
Done!!!!:popcorn:

Goodluck!

---

### Post by Daminator on 2008-05-28
I'm glad everyone else is getting there with this, but I can't use the 173 driver as my CPU doesn't have SSE (as I'm repeatedly told when I try one of these newer drivers).

Is there any hope for me or do I just need to upgrade?

Cheers
Damian

---

### Post by superbiskit on 2008-05-30
I'm composing at work, so I have to do this from memory. It shouldn't be too horrible -- the incident was only last night.

Card: FX5200 AGP
Kernel: 2.6.24
I have all the linux-restricted-modules, linux-ubuntu-modules, etc. and the darned thing was working before last night's updates.

Under "normal" conditions, gdm fails to start with an utterly useless message about the "failsafe" session having been used less than 30-sec previously.  If I delete enough /tmp/.X--- and /var/log/gdm/... so that it doesn't think it's already been tried, I find that the X11.20.log says:

Primary Default "2:00:00"
No device found at default device
*fatal* no usable screens

All my older, working, backups of xorg.conf predate having the video card on AGP. But my older nVidia card died a horrible death.

---

### Post by robertchahine on 2008-05-30
1-01:00.0 0300: 10de:0322 (rev a1)
2-[GeForce FX 5200]
3-no tweaking needed

---

### Post by doobrain on 2008-05-31
1-04:00.0 0300: 10de:0393 (rev a1)
2-GeForce 7300GT
3-no tweaking needed

---

### Post by oldsoundguy on 2008-05-31
3 nVida cards (varies) on three machines all installed using Envy.  All work flawlessly.

---

### Post by superbiskit on 2008-06-06
**FIRST** This forum needs a link to: [nVidia's README,]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/index.html") containing all configuration labels.

**Second, Thank you, Thank you, to tseliot for Envy.**  I spent several days with only a console after a kernel-packages upgrade broke my video.  After fixing all the dependencies of Envy, everything was dandy.

However, even then I discovered I wasn't really using the AGP port.  To do that required that I blacklist the "nvidia-agp" backend module:
```
/etc/modprobe.d/blacklist-agp <= "blacklist nvidia-agp"
```

Here is all my info:
```

02:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1) (prog-if 00 [VGA])

cat files in /proc/driver/nvidia/
**************************
/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
**************************
/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
GCC version:  gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
**************************
/proc/driver/nvidia/agp/card
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f000e1b:0x1f004302
**************************
/proc/driver/nvidia/agp/host-bridge
Host Bridge: 	 PCI device 10de:01e0
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f00421b:0x00000302
**************************
/proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled
**************************
/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.
**************************
/proc/driver/nvidia/cards/0
Model: 		 GeForce FX 5200
IRQ:   		 19
Video BIOS: 	 04.34.20.18.07
Card Type: 	 AGP
DMA Size: 	 32 bits
DMA Mask: 	 0xffffffff
Bus Location: 	 02.00.0



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#### $Id,/etc/X11/xorg-conf-2.6.22-14-generic [nvidia]
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"False"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"stylus"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"eraser"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"cursor"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
#-	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200] (rev a1)"
	Vendorname	"nVidia Corporation"
	Driver		"nvidia"
#-	Busid		"PCI:1:6:0"
	Busid		"PCI:2:0:0"
#+ {
	Option		"NvAGP"		"3"	## 3= Use AGPART if you can, else nVidia AGP
	Option		"RenderAccel"	"On"
	Option		"NoLogo"	"False"
## nVidia considers the following "*At Your Own Risk*" -- sticking to default
	Option		"AllowGLXWithComposite"	"True"
	Option		"AddRGBGLXVisuals"	"True"
	Option		"TripleBuffer"		"True"
	Option		"UseEvents"		"True"
## CoolBits IS VERY RISKY -- Don't enable this
	Option		"CoolBits"		"0"
	Option		"UseFBDevice"		"True" # Try some time
	Option		"NoRenderExtension"	"False"
	Option		"NoFlip"		"False"
	Option		"AllowDDCCI"		"True"
	Option		"IgnoreDisplayDevices"	"TV,DFP"
#  }
EndSection

Section "Monitor"
	Identifier	"PAVILION M50"
	Vendorname	"Hewlett-Packard"
	Modelname	"Pavilion M50"
#       HorizSync and VertRefresh from HP User Guide.
#       Require(?) Option "UseEdidFreqs" "False" in Screen section
	Horizsync	30-54
	Vertrefresh	50-100
	Displaysize	280	210
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
#-	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Device		"nVidia Corporation NV34 [GeForce FX 5200] (rev a1)"
	Monitor		"PAVILION M50"
	Option		"UseEDIDFreqs"		"False"
	Option		"UseEDIDDpi"		"True"
	Defaultdepth	24
## Note: The depth "1" - "15" are just absurd, deleted them
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	#	Inputdevice	"stylus"	"SendCoreEvents"
	#	Inputdevice	"cursor"	"SendCoreEvents"
	#	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by VoodooPHX on 2008-06-06
1-1-04:00.0 0300: 10de:0393 (rev a1)
2- nVidia Corporation NV18GL [Quadro NVS 280 SD]
3-no tweaking needed

---

### Post by dnairb on 2008-06-06
lspci -n | grep 0300: **02:00.0 0300: 10de:0421 (rev a1)**
lspci | grep VGA: **02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)**
(Card is an Asus EN8500GT SILENT/HTP/512M)
No tweaks required.

---

### Post by wolf354 on 2008-06-06
Thanks for your help...
:guitar:

---

### Post by Cherrybark on 2008-06-09
A big thanks to Briandu in message #430.

My nvidia driver was humming happily along until I installed NVIDIA X Server Settings.  I went through the "you're not using NVIDIA drivers, please run nvidia-xconfig..." several times.  Repeatedly restored my configuration file and tried various other suggestions.

Following Briandu's suggestions cleaned up my drivers and corrected whatever was stopping the X Server Settings.

I don't mind the struggle so much but it reminded me of one of the main reasons why Linux isn't more popular among home users.

---

### Post by john.nicholls on 2008-06-09
01:00.0 0300:10de:0422 (rev a1)
nVidia Corporation GeForce 8400 GS
No tweaking needed

---

### Post by michael_mallett on 2008-06-12
1) 05:00.0 0300: 10de:0611 (rev a2)
2) 05:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
3) Used guide located here ( [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270) ). No tweaking needed. Works with multiple displays @ different resolutions on 64bit AMD Hardy system

---

### Post by crane on 2008-06-14
02:00.0 0300: 10de:0622 (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
No tweaking needed after manual install of driver.

I downloaded beta driver from nvidia.
ctrl+alt_f2
Typed : /etc/init.d/gmd stop
ran the the driver install using
Sudo sh /home/jason/(Name.of.driver)
 when it finished I typed
Sudo reboot
(I know I could have just used Sudo /etc/init.d/gdm start)

 and was done.


I just noticed there is another driver out. I may need to update!

---

### Post by Norwal on 2008-06-14
03:00.0 0300: 10de:00f2 (rev a2)
Asus N6600 256 MB
No Tweaks required. I used EnvyNG.

:)

---

### Post by Victormd on 2008-06-14
01:00.0 0300: 10de:0611 (rev a2)

Used EnvyNG, no tweaks required... :)

---

### Post by ad_267 on 2008-06-14
I went System - Administration - Hardware Drivers.
Ticked next to nvidia drivers.
Restarted.

Everything worked great with my 6600GT.

---

### Post by AnomalyDetected on 2008-06-16
1. 01:00.0 0300: 10de:0600 (rev a2)
2. nVidia Corporation GeForce 8800 GTS 512 (rev a2)
(BFGtech nVidia 8800 GTS 512 Overclocked)
3. Downloaded 173.14.05 from nvidia.com and followed the normal install instructions. It worked fine when I started X back up, but after rebooting I would get the "low resolution mode" warning and the drivers wouldn't load.

To remedy, I first made sure all other (older) nVidia drivers were removed, installed the new 173.14.05 ones normally, and then ran nvidia-settings to set my desired display resolution and selected Merge with xorg.conf file.

Evidently the default xorg.conf wasn't working for some reason, no matter how much I tried to manually hack at it. I now have two monitor sections in there, but am afraid to touch it since it finally survives a reboot! 

Working great now.

---

### Post by rocketangel on 2008-06-18
1) 01:00.0 0300: 10de:0326 (rev a1)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
3) No tweaking needed.

---

### Post by Insti on 2008-06-19
1) 01:00.0 0300: 10de:0185 (rev c1)
2) 01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
3) 

Stop the x server that is running. 
```
sudo /etc/init.d/gdm stop
```

Made sure all packaged nvidia drivers were removed:
```
sudo apt-get remove --purge nvidia*
```

Downloaded the latest **legacy** nvidia drivers from the [nvidia website]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and install them:
```
sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run
```

Follow the onscreen prompts and say ok a lot.

I also had to make sure the Monitor section of my xorg.conf had the right things in it, otherwise I could only see the top left corner of the gdm login screen.
[COLOR="Red"]WARNING:[/COLOR] Only copy this section if you have this exact monitor!
```

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 240T (Analog)"
    HorizSync       30.0 - 93.0
    VertRefresh     50.0 - 60.0
    ModeLine       "1600x1200" 162.3 1600 1672 1864 2160 1200 1201 1204 1250 +hsync +vsync
    Option         "DPMS"
EndSection

```

Start the x server again.
```
sudo /etc/init.d/gdm start
```

---

### Post by gwillem on 2008-06-23
1) 01:00.0 0300: 10de:0402 (rev a1)
2) nVidia GeForce 8600 GT
3) It worked with the nvidia-glx-new driver, however, since "new is usually better", I downloaded 173.14.05 from nvidia.com. X wouldn't boot or display gibberish afterwards. After removing the old drivers, it worked!

```
mv /lib/modules/`uname -r`/nvidia* /root
```

Apparently the new drivers are under /lib/modules/`uname -r`/kernel/drivers/video/nvidia*

---

### Post by sorolop on 2008-06-23
1)01:00.0 0300: 10de:0425 (rev a1)
2)Nvidia 8600 GS 256 MB
3)(Its my first day on ubuntu)

---

### Post by soloman498 on 2008-06-24
NVIDEA 7300 GT 512mb
no tweaking needed
just followed ubuntu 8.04 instructions

---

### Post by wh0rd on 2008-06-24
This is from Nvidia website, using their binary drivers on **Hardy Heron**.
[COLOR="Red"]
*Should be done after upgrading to the latest kernel to avoid re-installations.[/COLOR]

[INDENT]```
sudo aptitude update && sudo aptitude safe-upgrade
```[/INDENT]

	Open a new commandline tty login & then login by pressing: **Ctrl+Alt+F5**
	```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
[INDENT]-this backs up your xorg.[/INDENT]
	```
sudo /etc/init.d/gdm stop
```
	```
sudo aptitude install linux-headers-`uname -r` build-essential
```
	```
sudo sh NVIDIA-[COLOR="Red"]driver-version[/COLOR].sh
```
[INDENT]            *-note change [COLOR="Red"]driver-version[/COLOR] to your Nvidia driver you downloaded to whatever directory you saved to.*[/INDENT]

	```
glxinfo | grep direct
```
[INDENT]-this should return **Yes**
[/INDENT]


Now reboot your pc with:
[INDENT]```
sudo reboot
```[/INDENT]


[SIZE="3"]**If you're not getting the right resolutions then you need to specify your Xorg Display refresh rates:**[/SIZE]
	
	```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_4display
```
	Edit the following Section in red with your displays refresh rates:

> 		Section "Monitor"
[INDENT]            Identifier     "Monitor0"
		    VendorName     "Unknown"
		    ModelName      "Unknown"
		    [COLOR="Red"]HorizSync       28.0 - 80.0
		    VertRefresh     48.0 - 75.0[/COLOR]
		    Option         "DPMS"[/INDENT]
		EndSection
Save & close. Press **Ctrl+Alt+Backspace** to restart xorg.

---

### Post by tanso on 2008-07-10
05:00.0 0300: 10de:0421 (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

Have dual monitors and I am limited to digital output and the other analog, ran the xserver settings that loaded by EnvyNG.
This will not save configurations, as my limited knowledge of Linux will prove obvious here, I am clicking "Save to X Configuration File" and it just complains "Unable to remove old X config backup file 'etc/X11/xorg.conf.backup'.

So I entered the system as root, copied the xorg.conf generated by 'Nvidia-settings Configuration' program I saved in my documents directory to /etc/X11/
No more tweaking after that.

---

### Post by mwgnz on 2008-07-12
01:00.0 0300: 10de:0622 (rev a1)

XFX NVIDIA GeForce 9600GT 

Just needed to purge system of nvidia-glx drivers, run dpkg-reconfigure xserver-xorg, then run the NVIDIA installer. 

Works great :)

---

### Post by kioftes on 2008-07-13
00:05.0 0300: 10de:0247 (rev a2)
nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

On Hardy 8.04.1, no tweaks, using the default restricted drivers application.

---

### Post by nwubie on 2008-07-16
01:00.0 0300: 10de:0391 (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
(XFX 7600GT XXX)
no tweaking needed

---

### Post by sjbaugh on 2008-07-18
Being new to Ubuntu, I have installed Hardy Heron on an old system with an NVIDIA MX 440 card in an AGP 4X slot.

When installing the distro there was a lot of flickering on the display. At the end of the install I took the option to install the "nvidia-glx" Restricted driver. This has curred the flickering but now I get random lockups. I think this is when it is displaying 3D content. I have edited xorg.conf and added the following (as suggested in another post above for a different NVIDIA card):
Option "RenderAccel" "Off"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
It has not locked up (yet!) with this setting but I get no 3D

I downloaded and installed the nvidia-glx-legacy driver.

This ran OK but I only got 800X600 and still no 3D.

So I have reverted to the nvidia-glx driver with the above settings as at least I can get the 1280X1024 resolution of my monitor.

Steve

---

### Post by stanley82 on 2008-07-20
Ubuntu Hardy Herron AMD64 version with 8500GT video card.
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
The first fix did it.

---

### Post by JMcClane on 2008-07-23
Well, long story short: I've installed Ubuntu 8.04 and everything was ok, then with the kernel update the drivers got screwed up, and I was stuck with a 640x480 resolution. The workaround that solved the problem:

**1)** Typed
```
gksudo displayconfig-gtk 
```

**2)** On the window that showed up I could choose Screen1 > Generic > LCD 1280x1024 (in my case). It then asks to logoff, and so did I. Once the logon was done, the resolution was the correct one: 1280x1024. 

**4)** Typed
```
nvidia-settings
```
(obviously this nvidia tool has to be previously installed). Once the nvidia control panel shows up I was able to pick up the correct resolution and refresh rate on "X Server Display Configuration" menu.

**5)** Then pressed "Save to X configuration file", **unchecked** "Merge with existing file", and press "show preview". Then I just copied the content of the preview to the xorg.conf file itself (I was getting an error if I pressed the "save" button directly). Obviously, to edit the xorg.conf one needs to be in sudo mode, so one option is to start gedit with gksudo.


Well, while I was trying to solve this annoying problem (don't know if it is a OS or drivers' fault), I haven't done exactly what I've wrote here (there was a lot more "trial and error"), but after all the mess up, this exact steps ended up being correct ones, hope it might be useful for someone with the same problem.

Btw, I have a nvidia 6600GT and a Asus 19' LCD


ps - sorry for the bad english

---

