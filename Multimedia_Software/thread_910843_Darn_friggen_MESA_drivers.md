---
title: "Darn friggen MESA drivers"
date: 2008-09-04
forum: Multimedia Software
---

### Post by +1Noob on 2008-09-04
I've done searches and spent hours trying to get my ATI x1600 working correctly (that's all part of the fun right??)...unfortunately, I am still having trouble. 

I can't seem to get the ATI drivers to show up for fglrxinfo. I have the Catalyst Control Center installed, and I think my xorg.conf looks okay as well as the results of glxinfo |grep ATI. 

I try running the aticonfig commands in the terminal, but they dont seem to work like they are supposed to. 

My first goal is to get the 'big desktop' working correctly and further down the road I would like to be able to use some of the Compiz effects. 

Any help is MUCH appreciated! 

Here is what I get for fglrxinfo:

tsanterre@Ty-Desktop:~$ fglrxinfo
display: :0.1  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)



display: :0.1  screen: 1
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

and here is what I get for: glxinfo |grep ATI

tsanterre@Ty-Desktop:~$ glxinfo |grep ATI
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 


Here is what my current xorg.conf looks like:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "0"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by pytheas22 on 2008-09-05
You may want to try using [envy]("http://albertomilone.com/nvidia_scripts1.html").  It doesn't always work, but generally it does a good job of auto-configuring ATI and nvidia graphics cards to use the proprietary drivers.  Please give it a shot and see if it helps.  If not, please post:
```

lspci -nn
```

---

### Post by Yellow Pasque on 2008-09-05
Envy never worked for my X1250 or Radeon HD 3200. In fact, I can't remember the last time I actually got the proprietary driver to work at all (8.40.4?) . Either the kernel module fails to build or the driver is unusable.

Anyway, the X1k series is well supported by the radeonhd driver, so I would use that.

---

### Post by +1Noob on 2008-09-05
> **pytheas22 said:**
> You may want to try using [envy]("http://albertomilone.com/nvidia_scripts1.html").  It doesn't always work, but generally it does a good job of auto-configuring ATI and nvidia graphics cards to use the proprietary drivers.  Please give it a shot and see if it helps.  If not, please post:
```

lspci -nn
```

Thanks for the suggestion. 

I actually did try Envy...it was the first thing I did...but to no avail. I will post lspci -nn later on today when I am home from work. 

Thanks in advance,

---

### Post by +1Noob on 2008-09-05
> **Temüjin said:**
> Envy never worked for my X1250 or Radeon HD 3200. In fact, I can't remember the last time I actually got the proprietary driver to work at all (8.40.4?) . Either the kernel module fails to build or the driver is unusable.

Anyway, the X1k series is well supported by the radeonhd driver, so I would use that.

Thanks! 

So you're saying to use the radeonhd driver from the ati site instead of the x1600? Is there a certain HD model I should choose? 

Again, thanks for the help.

---

### Post by +1Noob on 2008-09-05
> **pytheas22 said:**
> You may want to try using [envy]("http://albertomilone.com/nvidia_scripts1.html").  It doesn't always work, but generally it does a good job of auto-configuring ATI and nvidia graphics cards to use the proprietary drivers.  Please give it a shot and see if it helps.  If not, please post:
```

lspci -nn
```

Here it is! 

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0261] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.2 Multimedia audio controller [0401]: nVidia Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV530LE [Radeon X1600] [1002:71ce]
03:00.1 Display controller [0380]: ATI Technologies Inc Unknown device [1002:71ee]
04:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
04:07.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
04:08.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

---

### Post by Thingymebob on 2008-09-05
```
sudo apt-get remove xserver-xgl
```

should ditch the mesa drivers

restart X (ctrl+alt+Backspace)

if it won't start you'll have to change
```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```
to
```

Section "Extensions"
	Option	    "Composite" **"Enable"**
EndSection
```

you should now have ATI Technologies listed as the opengl vendor in fglrx info

---

### Post by Yellow Pasque on 2008-09-05
> **+1Noob said:**
> So you're saying to use the radeonhd driver from the ati site instead of the x1600? Is there a certain HD model I should choose?
No, the radeonhd driver is an open-source driver: [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

```
sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool pciutils-dev libdrm-dev
cd /usr/src
sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
cd xf86-video-radeonhd/
sudo ./autogen.sh --prefix=/usr/
sudo make
sudo make install
```

After that, update xorg.conf to reference the new driver. In the Section "Device" area, change the Driver "<driver-name>" line to radeonhd.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by +1Noob on 2008-09-06
> **Thingymebob said:**
> ```
sudo apt-get remove xserver-xgl
```

should ditch the mesa drivers

restart X (ctrl+alt+Backspace)

if it won't start you'll have to change
```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```
to
```

Section "Extensions"
	Option	    "Composite" **"Enable"**
EndSection
```

you should now have ATI Technologies listed as the opengl vendor in fglrx info

I tried "apt-get remove xserver-xgl" before...I believe it comes back saying that there was nothing to remove...but I'll double check. 

I'll try changing that last line of the xorg.conf file to enable the Composite extension. 

Thanks!

---

### Post by +1Noob on 2008-09-06
> **Temüjin said:**
> No, the radeonhd driver is an open-source driver: [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

```
sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool pciutils-dev libdrm-dev
cd /usr/src
sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
cd xf86-video-radeonhd/
sudo ./autogen.sh --prefix=/usr/
sudo make
sudo make install
```

After that, update xorg.conf to reference the new driver. In the Section "Device" area, change the Driver "<driver-name>" line to radeonhd.

```
gksudo gedit /etc/X11/xorg.conf
```

Thanks! I'll let you know how I make out. 

I appreciate it.

---

### Post by +1Noob on 2008-09-09
> **Temüjin said:**
> No, the radeonhd driver is an open-source driver: [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

```
sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool pciutils-dev libdrm-dev
cd /usr/src
sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
cd xf86-video-radeonhd/
sudo ./autogen.sh --prefix=/usr/
sudo make
sudo make install
```

After that, update xorg.conf to reference the new driver. In the Section "Device" area, change the Driver "<driver-name>" line to radeonhd.

```
gksudo gedit /etc/X11/xorg.conf
```




I'm having a problem with: ```
sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
```

It creates the directory, but nothing is in it. I actually can't even connect to the website: freedesktop.org...

Any thoughts? 

Basically, when I type in the above command in the terminal...it says, "Initialized empty Git repository in /usr/src/xf86-video-radeonhd-.git/    but then it just sits there. 

Please let me know! thanks.

---

### Post by pytheas22 on 2008-09-09
I was able to git those files without a problem.  Perhaps the server was having a glitch when you tried to access it?  I'd give it another try.  If that doesn't work, I now have the radeonhd source on my computer and can always send it to you if necessary.

EDIT: actually I just uploaded the files to my site preemptively, in order to save you some time if you need to go that route.  If you replace the 'sudo git-clone...' command in the instructions with the following command:

```
wget http://burnthesorbonne.com/files/xf86-video-radeonhd.tar.gz; tar -xzvf xf86-video-radeonhd.tar.gz
```

things should work (probably still best to use the source from git, though, if possible).

---

### Post by c.pergiel on 2008-09-09
I am having problems on the same subcontinent. My story might help:

[http://pergelator.blogspot.com/2008/09/horrible-harry-linux-screen-resolution.html]("http://pergelator.blogspot.com/2008/09/horrible-harry-linux-screen-resolution.html")

---

### Post by 080711jk on 2008-09-10
[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)=&#22823;&#22909;&#21830;&#26426;=&#24040;&#22823;&#36130;&#23500; &#36148;&#33180;&#65306;&#33410;&#33021;&#20808;&#38155;&#65292;&#19968;&#36335;&#39129;&#28072;&#65292;&#22269;&#20869;&#29627;&#29827;&#36148;&#33180;&#24066;&#22330;&#36817;&#19975;&#20159;&#12290;&#22269;&#38469;&#19978;&#24212;&#29992;&#26368;&#24191;&#27867;&#30340;&#33410;&#33021;&#26041;&#24335;&#23601;&#26159;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#12290;&#22312;&#24503;&#22269;&#12289;&#32654;&#22269;&#12289;&#21152;&#25343;&#22823;&#12289;&#33521;&#22269;&#31561;&#27431;&#32654;&#21457;&#36798;&#22269;&#23478;90%&#20197;&#19978;&#30340;&#24314;&#31569;&#21033;&#29992;&#29627;&#29827;&#36148;&#33180;&#26469;&#38477;&#20302;&#24314;&#31569;&#33021;&#32791;&#65292;100%&#30340;&#27773;&#36710;&#37117;&#37319;&#29992;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#65307;&#22312;&#26032;&#35199;&#20848;&#12289;&#28595;&#22823;&#21033;&#20122;&#12289;&#26085;&#26412;&#12289;&#38889;&#22269;&#12289;&#26032;&#21152;&#22369;&#31561;&#22269;&#23478;&#65292;&#24314;&#31569;&#36148;&#33180;&#26222;&#21450;&#29575;&#36798;&#21040;80%&#20197;&#19978;&#65292;&#24212;&#29992;&#33539;&#22260;&#38750;&#24120;&#24191;&#27867;&#12290;&#32780;&#22312;&#25105;&#22269;&#65292;&#21033;&#29992;&#29627;&#29827;&#36148;&#33180;&#33410;&#33021;&#21017;&#23646;&#20110;&#26032;&#20852;&#24066;&#22330;&#65292;&#30446;&#21069;&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;&#26222;&#21450;&#29575;&#36824;&#19981;&#21040;10%&#12290;&#20294;&#21363;&#20351;&#22914;&#27492;&#65292;&#22312;&#25919;&#24220;&#12289;&#19987;&#23478;&#30340;&#33410;&#33021;&#21628;&#22768;&#24433;&#21709;&#19979;&#65292;&#29627;&#29827;&#36148;&#33180;&#24066;&#22330;&#30340;&#24180;&#22686;&#24133;&#20063;&#36229;&#36807;&#20102;20%&#65292;&#22269;&#20869;&#24066;&#22330;&#23481;&#37327;&#24050;&#36798;&#21040;&#36817;&#19975;&#20159;&#20803;&#12290; &#19968;&#21333;&#24314;&#31569;&#36148;&#33180;&#29983;&#24847;&#26377;&#22810;&#22823; &#24120;&#35268;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#24066;&#22330;&#21806;&#20215;150-300&#20803;/m2&#65292;&#19968;&#33324;&#24615;&#23478;&#24237;&#20303;&#23429;&#30340;&#29627;&#29827;&#36148;&#33180;&#38754;&#31215;&#20026;10-30m2&#65292;&#27599;&#25143;&#30340;&#38144;&#21806;&#39069;&#32422;1500&#20803;-9000&#20803;&#65292;&#37027;&#20040;&#19968;&#26635;&#20303;&#23429;&#27004;&#26377;&#22810;&#23569;&#25143;&#23478;&#24237;&#65311;&#19968;&#20010;&#23621;&#27665;&#23567;&#21306;&#21448;&#26377;&#22810;&#23569;&#26635;&#25151;&#23376;&#65311;&#39640;&#23618;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#38754;&#31215;&#26681;&#25454;&#24037;&#31243;&#22823;&#23567;&#24046;&#24322;&#36739;&#22823;&#65292;&#19968;&#33324;&#27599;&#26635;&#30340;&#24179;&#22343;&#36148;&#33180;&#38754;&#31215;&#32422;&#20026;4000m2-10000m2&#65292;&#27599;&#26635;&#30340;&#38144;&#21806;&#39069;&#32422;60&#19975;&#20803;-300&#19975;&#20803;&#12290;

---

### Post by +1Noob on 2008-09-10
> **pytheas22 said:**
> I was able to git those files without a problem.  Perhaps the server was having a glitch when you tried to access it?  I'd give it another try.  If that doesn't work, I now have the radeonhd source on my computer and can always send it to you if necessary.

EDIT: actually I just uploaded the files to my site preemptively, in order to save you some time if you need to go that route.  If you replace the 'sudo git-clone...' command in the instructions with the following command:

```
wget http://burnthesorbonne.com/files/xf86-video-radeonhd.tar.gz; tar -xzvf xf86-video-radeonhd.tar.gz
```

things should work (probably still best to use the source from git, though, if possible).


Thanks! Yea...that was my initial thought that it was a sever problem on their side. 

Anyway, I have to start from square one, because I got sick of waiting and tried a few different things...now I'm back to all defaults. 

I'll try the git first and then your site and let you know!

---

### Post by +1Noob on 2008-09-11
So I get stuck on the command ```
 sudo make 
```

I've attached the terminal output b/c it's a bit long.

---

### Post by pytheas22 on 2008-09-11
hmmm, I was able to build it without a problem (and I don't even have an ATI card).  It seems that the problem was that it couldn't find the file '/usr/include/GL/gl.h,' which exists on my system.  Maybe you're missing kernel headers or something--are you sure you ran 'sudo apt-get install build-essential'?  What is the output of:
```

ls /usr/include/GL
```

---

### Post by +1Noob on 2008-09-13
> **pytheas22 said:**
> hmmm, I was able to build it without a problem (and I don't even have an ATI card).  It seems that the problem was that it couldn't find the file '/usr/include/GL/gl.h,' which exists on my system.  Maybe you're missing kernel headers or something--are you sure you ran 'sudo apt-get install build-essential'?  What is the output of:
```

ls /usr/include/GL
```

Here is the output of "sudo apt-get install build-essential" :

tsanterre@Ty-Desktop:~$ sudo apt-get install build-essential
[sudo] password for tsanterre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 53.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110403 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib32/libGL.so.1' with
  different file `/usr/lib32/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)



And here is the output of "ls /usr/include/GL":

tsanterre@Ty-Desktop:~$ ls /usr/include/GL
glATI.h  glxATI.h  glxint.h  glxmd.h  glxproto.h  glxtokens.h  internal


???

---

### Post by pytheas22 on 2008-09-13
It looks like apt-get is broken for you, which can be a nasty problem.  You can try running this to fix it:
```

sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install -f
```

I don't know if that will work, however.  If it does, you can then try running those steps again.  But you won't be able to compile the new driver until you can install the build-essential package via apt-get.

If apt-get really won't work, you may want to think about just reinstalling, because apt-get can be a real pain to fix.

---

