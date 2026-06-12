---
title: "Anyone using Hauppauge WinTV-quadHD?"
date: 2016-08-02
forum: Mythbuntu
---

### Post by gga96 on 2016-08-02
I have upgraded to Mythbuntu 16.04 and MythTV  0.28.
 
 Unfortunately my tuner has now failed (after 3 years) and  I am hoping to replace it with a new tuner, possibly a “Hauppauge WinTV-quadHD  (DVB-T/T2/C)”. Refer [http://www.hauppauge.com/site/products/data_quadhd.html]("http://www.hauppauge.com/site/products/data_quadhd.html") for details.

I think the WinTV–quadHD is a  new release that is supported by Linux [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)]("https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)") .
 Both the driver and firmware need to be install to use  the hardware on MythTV. The linux reference above provides the data required but  no instructions on what to do to install the data. 
 
 I am missing myth and would like to get it online again,  but...
 The technical implications of the installation sounds  some what daunting and a new release may imply initial bugs, I am not a  MythBuntu expert and would appreciate comment and/or help from those in the  know.
  

 Hope to hear from you soon.
 
 Cheers
 Glen
 
 P.S. how does one pronounce “Hauppauge “?

---

### Post by wildmanne39 on 2016-08-02
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by bhee on 2016-08-20
I bought this card in hopes of getting it working with a headless [MythTV]("https://help.ubuntu.com/community/MythTV/Install/Server/Backend"). I have some success namely installing the new 4.8 kernel with Ubuntu 16.04 Server using the details found [here]("http://www.ubuntumaniac.com/2016/08/linux-kernel-48-rc2-ubuntu.html"). The kernel recognises this card and I am able to capture the 4 tuners but during the channel scanning I get 'Failed to open card' and that's where I am now.

Any help appreciated..

Barry

---

### Post by bhee on 2016-08-20
Just noticed in the capture setup, the Frontend ID shows 'Could not get card info for card'.

Barry

---

### Post by bhee on 2016-08-20
Well I went back to basics and installed the traditional way, i.e. setup the backend on a desktop as opposed to a server and not remotely. Mostly everything works, the only thing I want to get working now is KODI frontends which have been working in other setups and sort out why the headless method does not work, probably permissions. All in all the Hauppauge QuadHD is great if you want to be at the bleeding edge.

Just to sum up, I have a Ubuntu Desktop 16.04 and installed the 4.8 Kernel, have Hauppauge WinTV-QuadHD tuner card with firmware from the OpenElec site and MythTV 28.

Barry

---

### Post by shspvr on 2016-10-18
> **bhee said:**
> Well I went back to basics and installed the traditional way, i.e. setup the backend on a desktop as opposed to a server and not remotely. Mostly everything works, the only thing I want to get working now is KODI frontends which have been working in other setups and sort out why the headless method does not work, probably permissions. All in all the Hauppauge QuadHD is great if you want to be at the bleeding edge.

Just to sum up, I have a Ubuntu Desktop 16.04 and installed the 4.8 Kernel, have Hauppauge WinTV-QuadHD tuner card with firmware from the OpenElec site and MythTV 28.

Barry
Hauppauge quadHD DVB should all ready be supported with kernel 4.7
Hauppauge quadHD ATSC will add in kernel 4.9 last I heard
Hauppauge dualHD DVB should all ready be supported with kernel 4.8
Hauppauge dualHD ATSC no time frame as to when but let hope it get add to kernel 4.9 other that just email Hauppauge and put in a req the linux driver patch
No news on HD-PVR Rocket nor HD-PVR 60 when I last check the other day

---

### Post by gga96 on 2016-10-30
Thank you all for your interest and replies.

My Hauppauge Quad tuner finely arrived after a 3 month wait.


Installed Hauppauge WinTV-quadHD (DVB-T/T2/C) PCIe board to a HP i5 Compaq 8100.


Installed ISO mythbuntu 0.28/16.04 64bit.


Used reference [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-quadHD_(DVB-T/T2/C)) to specify the required firmware and driver.


Installed kernel 4.8 to get the correct driver.


Copied firmware dvb-demod-si2168-b40-01.fw to /lib/firmware.    


I expected to see the following HW identification: 
> lspci -v
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
Subsystem: Hauppauge computer works Inc. Device 6a18
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at fd200000 (64-bit, non-prefetchable) [size=2M]
Capabilities: <access denied>
Kernel driver in use: cx23885


05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
Subsystem: Hauppauge computer works Inc. Device 6a18
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at fd000000 (64-bit, non-prefetchable) [size=2M]
Capabilities: <access denied>
Kernel driver in use: cx23885

But what I got follows: 
> lspci -v
1a:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
    Subsystem: Hauppauge computer works Inc. CX23885 PCI Video and Audio Decoder
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885


1b:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
    Subsystem: Hauppauge computer works Inc. CX23885 PCI Video and Audio Decoder
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0600000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885


I expected version (rev 04) but I got (rev 03).


MythTV does not work with this setup.


What version of kernel and driver did you use and what lspci -v output did you get on your working installation?


Is there something else I should be doing?


Hope to hear from you soon.


Regards
Glen

---

### Post by ray2u99 on 2016-12-13
[COLOR=#000000][FONT=Arial]Just to let you know that you&#8217;re not the only one experiencing problems.  Maybe there&#8217;s someone out there who has had success can let us know their secret.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]My scenario:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]WinTV-quadHD hardware works fine within the Windows 10 operating system[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Running Ubuntu:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]16.04 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Upgraded to kernel:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]4.9.0-040900-generic to get the latest drivers.  Note; I understand that you must have at least v 4.8 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Installed dvb-demod-si2168-b40-01.fw firmware[/FONT][/COLOR]




[COLOR=#000000][FONT=Arial]Used [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ dmesg | grep -i dvb-demod[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]to confirm that the firmware was operating okay[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Used [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ w_scan -ft -cAU -X[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]to test but got (at the end of all the appropriate and long frequency scan)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ERROR: Sorry - i couldn't get any working frequency/transponder[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial] Nothing to scan!![/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]And trying to get TVHeadend to work gives similar problems.  That is a lack of connection to the TV channels.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]So, I&#8217;m guessing there&#8217;s a yet to be resolved problem between the driver and the firmware.  Or maybe it's just a problem to us from 'the land down under' (Australia).

Cheers
Ray[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by bhee on 2017-01-24
Sorry not been monitoring this thread since I moved my test system to CentOS 7, the 4.8 kernel and MythTV 0.28. I am also from down under, specifically Sydney, no problems with MythTV 0.28 and Hauppauge WinTV-quadHD. I am not sure whether I still have Ubuntu 16.04 installed on a spare disk but will check when I get home this evening. From memory there is a problem with the firmware out there from different sources. I had success from this source version 25,

[http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/Si2168-B40/](http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/Si2168-B40/)

Tell me how you go, if still unsuccessful I will try another test with Ubuntu 16.10 as this has the 4.8 kernel built-in and post the results.

regards,
Barry

---

### Post by bhee on 2017-01-25
An lspci -v produced the following,

> [COLOR=#000000][FONT=Monaco]08:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Subsystem: Hauppauge computer works Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Flags: bus master, fast devsel, latency 0, IRQ 17[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Memory at eb400000 (64-bit, non-prefetchable) [size=2M][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Kernel driver in use: cx23885[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Kernel modules: cx23885[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]09:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Subsystem: Hauppauge computer works Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Flags: bus master, fast devsel, latency 0, IRQ 18[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Memory at eb200000 (64-bit, non-prefetchable) [size=2M][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Kernel driver in use: cx23885[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Kernel modules: cx23885[/FONT][/COLOR]
This is from a fresh updated install of 16.10, with firmware installed from the above address and a
[FONT=Monaco][COLOR=#000000]
dmesg | grep -I DVB produced[/COLOR][/FONT]

> [COLOR=#000000][FONT=Monaco][ 7.954545] CORE cx23885[0]: subsystem: 0070:6a28, board: Hauppauge WinTV-QuadHD-[COLOR=#c33720]DVB[/COLOR] [card=56,autodetected][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.296237] tveeprom 12-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/[COLOR=#c33720]DVB[/COLOR] Digital (eeprom 0xf4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.296244] cx23885_[COLOR=#c33720]dvb[/COLOR]_register() allocating 1 frontend(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.296413] cx23885[0]: cx23885 based [COLOR=#c33720]dvb[/COLOR] card[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.371883] [COLOR=#c33720]DVB[/COLOR]: registering new adapter (cx23885[0])[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.371887] cx23885 0000:08:00.0: [COLOR=#c33720]DVB[/COLOR]: registering adapter 0 frontend 0 (Silicon Labs Si2168)...[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.380364] cx23885_[COLOR=#c33720]dvb[/COLOR]_register() allocating 1 frontend(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.380367] cx23885[0]: cx23885 based [COLOR=#c33720]dvb[/COLOR] card[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.431113] [COLOR=#c33720]DVB[/COLOR]: registering new adapter (cx23885[0])[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.431116] cx23885 0000:08:00.0: [COLOR=#c33720]DVB[/COLOR]: registering adapter 1 frontend 0 (Silicon Labs Si2168)...[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.433363] CORE cx23885[1]: subsystem: 0070:6b28, board: Hauppauge WinTV-QuadHD-[COLOR=#c33720]DVB[/COLOR] [card=56,autodetected][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.777767] tveeprom 17-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/[COLOR=#c33720]DVB[/COLOR] Digital (eeprom 0xf4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.777774] cx23885_[COLOR=#c33720]dvb[/COLOR]_register() allocating 1 frontend(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.782613] cx23885[1]: cx23885 based [COLOR=#c33720]dvb[/COLOR] card[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.797319] [COLOR=#c33720]DVB[/COLOR]: registering new adapter (cx23885[1])[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.797323] cx23885 0000:09:00.0: [COLOR=#c33720]DVB[/COLOR]: registering adapter 2 frontend 0 (Silicon Labs Si2168)...[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.801097] cx23885_[COLOR=#c33720]dvb[/COLOR]_register() allocating 1 frontend(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.801100] cx23885[1]: cx23885 based [COLOR=#c33720]dvb[/COLOR] card[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.839053] [COLOR=#c33720]DVB[/COLOR]: registering new adapter (cx23885[1])[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][ 8.839056] cx23885 0000:09:00.0: [COLOR=#c33720]DVB[/COLOR]: registering adapter 3 frontend 0 (Silicon Labs Si2168)...[/FONT][/COLOR]

Hopefully this helps but maybe pointless now that Mythbuntu is no longer, have you tried CentOS 7?

regards,
Barry

---

### Post by moehaidar-k on 2017-01-29
Hi,
I've installed Ubuntu 16.10 with kernel 4.8 and copied the FW but have not been able to get mythtv to recognize the card.
What step have I missed? 

Thanks,
Moe

---

### Post by Zenon_Skuza on 2017-01-30
Hi Ray, I'm having exactly the same issue as you in Australia (Melb) - Channels are getting picked up when the card is used in Windows, but tvheadend, while getting an SNR in the mid-30s and Signal Strength in mid -30 dBm is giving a Fail scan result for channels. However when channels are picked up the picture is rock-solid. I'll look on linuxtv.org for more info, but it's really frustrating.

Let me know if you've had any more luck with the card, and I'll post any of my findings here if I make progress.

---

### Post by Chad_Wagner on 2017-02-22
I am using a similar setup, Ubuntu 16.04, MythTV 0.28, and just purchased the WinTV-QuadHD (ATSC).  I had to backport the patches from the Linux media tree.  As someone mentioned in this thread, ATSC support for this card will not be available until Linux 4.9.

These are the two patches you would need to backport to an earlier version (so far it works on 4.4):
[https://git.linuxtv.org/media_tree.git/commit/drivers/media/pci/cx23885?id=10a5210ed40cb13c1645969ac4307dfa3f3d5a00](https://git.linuxtv.org/media_tree.git/commit/drivers/media/pci/cx23885?id=10a5210ed40cb13c1645969ac4307dfa3f3d5a00)
[https://git.linuxtv.org/media_tree.git/commit/drivers/media/pci/cx23885?id=dd9ad4fbf0cecfe9a823d6a18707af394eb9af21](https://git.linuxtv.org/media_tree.git/commit/drivers/media/pci/cx23885?id=dd9ad4fbf0cecfe9a823d6a18707af394eb9af21)

Here is lspci and kernel output for the module backported to 4.4:
[http://paste.ubuntu.com/24049780/](http://paste.ubuntu.com/24049780/)


I am using dkms to rebuild the module for any kernel updates.  So far so good.

---

### Post by jimmyjimjim on 2017-03-06
> **Chad_Wagner said:**
> 
I am using dkms to rebuild the module for any kernel updates.  So far so good.

Chad,

Would you share how you setup dkms for rebuilding the module?
What does your dkms.conf look like?

---

### Post by Chad_Wagner on 2017-03-11
Here is the DKMS build that I am using, this is based on the 4.4 kernel tree with the two patches I mentioned earlier.  There is a deb in there which could be installed, and a dsc if you want to build it, share it on launchpad or something like that, etc.

[URL="https://drive.google.com/open?id=0Bzqixi91Zl5lTjhZVmpJWjNhTVk"]https://drive.google.com/open?id=0Bzqixi91Zl5lTjhZVmpJWjNhTVk


[/URL]

---

### Post by bhee on 2017-03-16
> **moehaidar-k said:**
> Hi,
I've installed Ubuntu 16.10 with kernel 4.8 and copied the FW but have not been able to get mythtv to recognize the card.
What step have I missed? 

Thanks,
Moe

Hi Moe,

Please post your lspci and a dmesg.

Barry

---

### Post by jimmyjimjim on 2017-03-18
> **Chad_Wagner said:**
> Here is the DKMS build that I am using, this is based on the 4.4 kernel tree with the two patches I mentioned earlier.  There is a deb in there which could be installed, and a dsc if you want to build it, share it on launchpad or something like that, etc.

[URL="https://drive.google.com/open?id=0Bzqixi91Zl5lTjhZVmpJWjNhTVk"]https://drive.google.com/open?id=0Bzqixi91Zl5lTjhZVmpJWjNhTVk


[/URL]

Thanks Chad.  Looks like you created a snapshot of driver source from the kernel tree and created a separate package you can compile separately from the kernel build.  What happens if the kernel updates the driver source that makes it incompatible with the snapshot?

I've tried a different approach where I created a Makefile that unpacks the kernel sources, applies patches, builds the module, and then copies the target to a suitable location for dkms install to pickup.  So far there has been only one update which didn't go off without some manual intervention so I'll see how it goes next update.

---

### Post by ray2u99 on 2017-04-25
I'd just like to say thank you to Barry (bhee) for redirecting my to a later driver for the Hauppauge WinTV-quadHD.  It fixed the main problem I was having.  For those that may come across this thread, and in the future;
As at the time of writing, the driver found on github.com is not the correct diriver.  One that I found worked is located on [http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/Si2168-B40/](http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/Si2168-B40/) and get the latest version (again, thanks to Barry for this).
Below I've shown the difference in sizes between the two drivers.  The (much) larger driver is the better one.
The correct firmware size ought to be about 16K```
-rw-rw-r-- 1 ray ray 15827 Apr 24 07:23 dvb-demod-si2168-b40-01.fw
-rw-rw-r-- 1 ray ray  6919 Dec 14 11:18 dvb-demod-si2168-b40-01.fw
```

Ray

---

### Post by reubenbrown13 on 2017-05-07
I just got the WinTV-quadHD card (rev04) setup and running on LTS 14.04 with the dkms package you shared.  THANK YOU for sharing that.  It is working great with kernel 4.4.0-75.

---

### Post by moehaidar-k on 2017-07-27
I was able to get everything working on 16.10 using [this]("http://www.hauppauge.com/site/support/linux.html") guide.

---

