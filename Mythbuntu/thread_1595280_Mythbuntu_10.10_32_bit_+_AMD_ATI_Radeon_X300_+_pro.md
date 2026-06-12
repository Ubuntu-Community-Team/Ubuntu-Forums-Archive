---
title: "Mythbuntu 10.10 32 bit + AMD ATI Radeon X300 + proprietary driver = blank/error"
date: 2010-10-13
forum: Mythbuntu
---

### Post by JordanRieger on 2010-10-13
Dear MythBuntu/Linux experts,

I'm having trouble getting my PVR build working. Everything is OK if I  stick to the default open source ATI Radeon driver for my old Foxconn  Radeon X300SE PCI-Express card. But the only output my Sony 34" CRT will  support is S-Video, and as I understand it, I need to use the  proprietary AMD driver to enable that.

However, if I select the AMD driver during installation and enable  S-Video, I get a blank screen as soon as the installer reboots the  system for the first time. I know the system isn't hung because I can  press Ctrl-Alt-Del, there is a couple seconds of hard drive access  before it reboots gracefully. Now, I should say that I'm not yet running  the PC in my living room where it will eventually live, so I currently  have it connected to my Acer LCD via the DVI-out. Could it be that the proprietary driver is enabling S-Video and simultaneously disabling DVI, and I just can't tell because I don't have the TV hooked up yet? I would prefer not haul it all into the living room before I have everything installed properly.

So I reinstalled using the default driver, and then I tried downloading  the latest version of the appropriate proprietary driver from AMD's site  directly: [ati-driver-installer-9-3-x86.x86_64.run]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"), but when I install it, I get the following error: 
 
[B]Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro[/B]

Another thing I tried is to install the fglrx driver through Synaptics Package Manager. Now that I've done that, I seem to have an ATI Catalyst Control Center available under Applications > Settings in Xfce. However, when I try to open it, it says:

**There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.**
  **No ATI graphics driver is installed, or the ATI driver is not functioning properly.**
 **Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.**
 
 

If I run aticonfig from a terminal, I get:

**No supported adapters detected**

Any ideas?

My hardware:


[LIST]
[*]Apevia 500W Power Supply
[*]Foxconn A74ML-K 3.0 AM3 AMD 740G Micro ATX AMD Motherboard
[*]Foxconn ATI Radeon X300SE PCI-Express (DVI, S-Video)
[*]Hauppage WinTV PVR-250 PCI w/ remote (pleasantly surprised that the remote worked so easily!)
[*]AMD Phenom II X2 550 Callisto 3.1GHz Socket AM3 80W Dual-Core Desktop Processor HDX550WFGMBOX
[*]A-DATA Gaming Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model AX3U1600GB2G9-2G
[*]Seagate 7200.12 500G SATA II Hard Drive
[/LIST]

Thanks in advance,

Jordan Rieger

---

### Post by JordanRieger on 2010-10-14
Well, I brought the system to my living room and hooked everything up. I reinstalled Mythbuntu and picked the proprietary AMD driver option during installation, enabling the S-Video output in NTSC-M format (North America I presume.) But there was no signal going to the S-Video on my TV.

So I'm back to square one.

I should add that I switched back to Mythbuntu x64 as that was the version I first tried. (I had switched to 32 bit to see if the driver would behave better.)

---

### Post by novellahub on 2010-10-14
Try reinstalling without selecting any S-Video options.  I had a similar issue in the past with a Nvidia card having issues selecting S-Video during the initial install. The screen would come up blank after the first reboot.  By not selecting the s-video option, I let the Nvidia card automatically detect the display output.

Also try doing the initial install with the open source driver and not the proprietary one.  Then switch to the closed source driver after you verify the machine is working (System > Administration > Hardware Drivers)

---

### Post by LowSky on 2010-10-14
Welcome to the forums.

AMD does not supports video cards older than the HD2xxx series. your only option is the open source driver.

Im sorry to be the one telling you this.

---

### Post by JordanRieger on 2010-10-14
> AMD does not supports video cards older than the HD2xxx series. your only option is the open source driver.

That may be true going forward, but the proprietary Catalyst 9.3 driver that I am trying to install does indeed support the X300. See [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English).

> Try reinstalling without selecting any S-Video options.  I had a similar  issue in the past with a Nvidia card having issues selecting S-Video  during the initial install. The screen would come up blank after the  first reboot.  By not selecting the s-video option, I let the Nvidia  card automatically detect the display output.

Yes, that allows me to get the system up and running, but how would I enable S-Video out at that point? And why would that be any different than enabling it immediately during the install? It seems that the proprietary AMD driver bundled with MythBuntu 10.10 simply doesn't support S-Video out for the X300, otherwise it would have worked they way I tried it. That's why I'm trying to install the Catalyst 9.3 driver.

> Also try doing the initial install with the open source driver and not  the proprietary one.  Then switch to the closed source driver after you  verify the machine is working (System > Administration > Hardware  Drivers)

Yes, I've been able to install successfully using the open source driver. However, I'm unable to switch to the closed source one afterward. There seems to be no option for it in the MythTV UI -- I don't see any System > Administration > Hardware Drivers menu item like you suggest. When I try to do it from outside MythTV, in the Xfce UI, the proprietary drivers section says "No third-party drivers found" or something to that effect. Running "aticonfig" from the command line says"No supported adapters detected." And running Catalyst Control Center tells me essentially the same thing. Trying to install the AMD Catalyst 9.3 drivers yields the error message in my original post.

---

### Post by LowSky on 2010-10-14
yes I understand that 9.3 does support your card, but that driver doesn't work with the current version of Xserver

Your product is considered legacy to ATI/AMD, and they say they are not supporting legacy products for Linux


[http://blogs.computerworld.com/the_ubuntu_and_ati_blues](http://blogs.computerworld.com/the_ubuntu_and_ati_blues)

---

### Post by novellahub on 2010-10-14
I would either pick up a  Nvidia video card or get one of these VGA to S-Video converters:

[http://www.monoprice.com/products/search.asp?keyword=4724](http://www.monoprice.com/products/search.asp?keyword=4724)

---

### Post by JordanRieger on 2010-10-14
Thanks for your advice novellahub and LowSky.

I did some more research and it sounds like the only way I can get S-Video output on this card is to revert to an old version of X-Server, but apparently that could cause conflicts with other stuff.

So I'm now scouring the local Craigslist ads for a cheap nVidia PCI-Express card with S-Video Out. There are quite a few out there under $20, so I should be OK.

And thanks for that link to the VGA to S-Video converter! At $27 it's the cheapest one I've found online, and according to the customer reviews, the picture quality is very good. I might order one even if I can find an nVidia card.

---

