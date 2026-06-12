---
title: "Getting a ATI video card tv tuner to work"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by kgreiner on 2006-08-17
I have an ATI tv video card but i can not get the tv tuner option to work in dapper. When i try to run a tv veiwing program it just tells me that /dev/video0 is not detected.

when i do a lspci it shows my tv card as:
0000:00:0f.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

I tried the faq on using gatos but still nothing worked, now that it is part of X.org, i tried to look on that site and could not find anything to help. 

If some one could please help me out or provide Links or suggestions would be great!
Thank you
Kurt

---

### Post by mordi on 2006-08-17
I tried to make the tv tuner on an ati aiw 9800pro work, but no luck so far. reading ati web site and gatos web site, I don't think it is even supported. you can try sudo modprobe tuner, since there are a bunch of modules related to tv tuners in /lib/modules/2.6.yourversion/kernel/drivers/media. however, it does not look good if you cannot see your tv tuner listed under media, with lspci.
then, I think we are supposed to confiqure the tv tuner with sudo gatos-conf or sudo xatitv. However be very careful, gatos-conf tries to make a backup of your X11 under X11.old and then create a new link or file or something, called X11. since my card is not supported, the new X11 created on my system is just an empty file, so I have no clue what it should be. if you want to play with sudo gatos-config and the xserver does not work anymore, just delete the new X11 and mv X11.old to X11. make sure it exists first. also, for ubuntu, the path to your xorg.conf has to be provided to gatos-conf, so the correct command should be sudo gatos-conf -X /etc/x11/xorg.conf. 
that is all I know about configuring an ati tv tuner, sure hope somebody knows more.

---

### Post by Hal58 on 2006-08-18
I also have the ATI AIW 7500 and it works just fine in Dapper, but you must use 'xawtv' to view TV.  The gatos drivers are included in xorg 7.0, but no /dev/video0 is set up and I have not found a way to use 'tvtime' (which by the way seems to chew up much more CPU power than xawtv).

You might need to manually generate the config file since the 'scantv' utility seems to also fail.

---

### Post by kgreiner on 2006-08-18
thanks for your reply.

which data files do i need to change? 
what does your xorg.conf file look like? 
which drivers are needed to be loaded?

---

### Post by Hal58 on 2006-08-18
> **kgreiner said:**
> thanks for your reply.

which data files do i need to change? 
what does your xorg.conf file look like? 
which drivers are needed to be loaded?

Don't change any data files, if you have usable video then xorg.conf is probably Ok, and you don't need to load any drivers.  Just get xawtv with:

 apt-get install xawtv

The application will then be installed under Multimedia, and when you select it, you will probably have a garbage display, so right click with the cursor in the window and you will have the xawtv control panel.  Select NTSC/PAL, mono/stereo, video source (tuner) and anything else that looks wrong, crank up the audio level and use the up/down arrows to step the channels.

Read up on xawtvrc (or whatever the config file is called in the man page) to set up the settings in your home directory (mine is '.xawtv') so that you don't have to set it up each time.

---

### Post by kgreiner on 2006-08-18
when i select xatitv from the menu nothing happens. when i open a terminal and then 'xatitv' i get:
GATOS: No ATI PCI/AGP Cards ?
GATOS: gatos_inita(): Invalid argument
xatitv: gatos_init(): Invalid argument


when i try tvtime or scantv it complains it can not find /dev/video0, which there is no a device video0 in /dev

any ideas?

---

### Post by kgreiner on 2006-08-21
which driver do i need to use in my xorg.conf file? I have tried radeon and ati.

which modules should be loaded? i currently have:
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

---

### Post by kgreiner on 2006-08-22
when using the ati driver and then looked at my Xorg.0.log file and it shows that it detects the tuner

(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia/fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
(II) RADEON(0): Detected FI1236W device at 0xc6

then later i see an error
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): Device 1 on VIP bus ids as 0x4d4a1002
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d4a1002
(II) RADEON(0): Detected Rage Theatre revision 00000001
(II) RADEON(0): video decoder type is 0x61a8 (BIOS value) versus 0x61a8 (current PLL setting)
(II) RADEON(0): Tuner is on port 0
(II) RADEON(0): Composite connector is port 1
(II) RADEON(0): SVideo connector is port 5
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=1, svideo=5
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=1, svideo=5
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre200"
(II) LoadModule: "theatre200"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre200_drv.so
(II) Module theatre200: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): Microcode: Use default microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use default microcode type: BINARY
(EE) RADEON(0): Microcode: cannot load microcode
(II) RADEON(0): Rage Theatre disabled

is this the reason why things are not working? what could i do to fix this?

---

### Post by kgreiner on 2006-08-22
ok, i got past the rt2_pmem.bin issue, i had to grab the ativm20.cod file off the ati install cd and put it into place. 

but that still has not solved my problem. 

/dev/video0 is still not created

I ran 'MAKEDEV video' and it does not dev created in /dev. 
But i did a search for video0 and it looks like everything is getting created in /dev/.static/dev/ - it looks like it is done because it is using udev

I tried to run xatitv using the /dev/.static/video0 specifically,it still states that it can not locate it.
scantv -c /dev/.static/dev/video0
v4l2: open /dev/.static/dev/video0: No such device or address
v4l2: open /dev/.static/dev/video0: No such device or address
v4l: open /dev/.static/dev/video0: No such device or address
no grabber device available

hmm... more thoughts?

---

### Post by kgreiner on 2006-08-24
i still get the same errors when i run xawitv, but when i run xawtv   , the application starts and i see static on the screen. I change the defaults to NTSC/US-BROADCAST and change the input method to the tuner. 

Once I start to change channels and fine tune i start to see a picture, but it is too fuzzy and jumpy and can not get anything noticable. I do have a tv antena hooked up, I know it works because I took it off the tv i have near by.

I am trying to get things working one thing at a time, but i also, do not have sound. :( 

Any ideas how to get any other tv program to work?
What could i do to get a decent picture?
What could i do to get sound to work?

if you need more info i will share it with you

---

### Post by leeper69 on 2006-08-27
I am using XAWTV and all I had to do was right click inside the tv display window which popes up the options menu then place your mouse pointer on the box next to the volume collum and click with the left button to increse the sound or the right to decrese the sound. ( if there isen't a bar in the box or it is on the extreme left hand side this is all that is wrong.) You can also try MOTV it has a better set of controls and a save configuration option that will keep your settings in XAWTV as well. As far as I know these two programs are the easyest to get working with an ATI card.

---

### Post by leeper69 on 2006-08-30
Hi I am using xawtv with a Radon 7500 all in wonder card to get it working properly I set the settings in the popup window for xawtv to these values.

tv norm: ntsc
vidio source: composite
frequency table: us-cable
capture:overlay

  I am using a dish and only use channel 4 on the card tuner so you may need to change the frequency table setting for your setup. The one that is giving you a snowy screen is most likly the capture setting it should be on overlay!

Hope this helps

---

### Post by hulet on 2006-09-04
Hi, I am so happy because I finally got this working under ubuntu after so many tries with other distros. The only other linux distro that I could watch TV using my legacy ati all-in-wonder rage 128 card (r128 ) was on Gentoo. Here is what I did in Ubuntu 6.06 LTS:

sudo apt-get install gatos
xatitv

The quality is not that great; when you close xatitv, the sound wouldn't die; and, video capture doesn't seem to be working but atleast I could see something on it. :)

Btw, I was getting /dev/video0 is not found message when I tried to run using xawtv or tvtime.
)
Edit: I just realized this software is written long time ago (1999) so might not work for newest driver cards mentioned in this thread.

---

### Post by watson540 on 2006-11-10
You will never get a /dev/video using this card, its a hack at best. Only xawtv, avview (best one cause you can tweak), or mplayer/xibne will work. Support for the theatre200 chip sucks in linux and its probably best to buy a hardware card instead. I get a picture only after much playing around and nothing stays the samme, also i get no soiund, as i said in another post, maybe its possible to get vmware to recognize your card and you could use vmware to run x with ati's software?? I say just buy a  hardware tuner

---

### Post by blueboy4 on 2007-05-28
I have an external ATI Tv Wonder USB 2.0 Tuner Card. Will XAWTV work with it as well?

---

### Post by Siegfried on 2007-06-17
> **blueboy4 said:**
> I have an external ATI Tv Wonder USB 2.0 Tuner Card. Will XAWTV work with it as well?
It will work as long as there is a V4L driver for that card.  Unfortunately, at this time there is no driver for the TV Wonder USB 2.0.


Hope this helps.

---

### Post by blueboy4 on 2007-06-17
Well will there be a driver available sometime soon? It would be great if that happens.

---

### Post by blueboy4 on 2007-06-18
If there won't be a driver available, can someone recommend me an alternative way to get it to work?

---

### Post by Siegfried on 2007-06-19
> Well will there be a driver available sometime soon? It would be great if that happens.
There will be one when and if someone writes a driver.  You can help developers make a driver by posting in the associated mailing lists with detailed information on the hardware (as much as you can).  For example, what chipset is used, what tuner, etc.

> If there won't be a driver available, can someone recommend me an alternative way to get it to work?
If there is no driver available for Linux, you'll have to use an operating system that has one, either directly or through emulation/virtualization.  This could be Windows, Mac OS X, etc.  You could give VMWare Server a try, and see if it runs under that.

---

### Post by blueboy4 on 2007-06-19
If I know how to find this information out I will. But apparently I don't, so can you tell me how I can?

---

### Post by blueboy4 on 2007-06-19
Apparently these are the only ATI tv tuner cards that ATI seems to support for linux at the moment:

Radeon
All-In-Wonder
FireMV
FireGL
Mobility Radeon
Integrated/Motherboard

---

