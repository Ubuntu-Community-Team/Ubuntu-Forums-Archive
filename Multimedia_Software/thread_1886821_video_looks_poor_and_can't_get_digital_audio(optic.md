---
title: "video looks poor and can't get digital audio(optical)"
date: 2011-11-25
forum: Multimedia Software
---

### Post by ser_renely on 2011-11-25
New to linux, ubuntu 11.10.

I just bought a new HTPC - i3-2100,4gb RAM,gigabyte z68ma-d2h-b3 MOBO.

The video on it looks TERRIBLE for playback.  It is jittery and teary most of the time, using HDMI to my TV. Ideas?

I can't seem to get my audio set right, I am using an optical cable(not HDMI) to my receiver but I can only get stereo out of it.  It seems to send the signal out in analog not digital.  I look at the sound card and don't have any options that I see.

Help would be appreciated. I have installed all sorts of packages from my web research, no luck yet.

lspci

[I][COLOR=Red]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB Controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
[/COLOR][/I]
aply

[I][COLOR=Red]**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR][/I]

Thanks,
Ser

---

### Post by inobe on 2011-11-25
the integrated graphics, i cannot help with, they do not perform well for me on any platform, i filled my pci-e slot with an nvidia gtx 460.

as for the sound, i made sure hdmi was off.

[IMG]http://img821.imageshack.us/img821/3162/hdmiq.jpg[/IMG]

then made sure 958 was set as a preferred device in my kubuntu sound settings.

[IMG]http://img707.imageshack.us/img707/7049/958qs.jpg[/IMG]

surround seems to work flawless on my theater receiver.

---

### Post by inobe on 2011-11-25
rechecked, got DTS on and it sounds amazing.

---

### Post by ser_renely on 2011-11-25
> **inobe said:**
> the integrated graphics, i cannot help with, they do not perform well for me on any platform, i filled my pci-e slot with an nvidia gtx 460.

as for the sound, i made sure hdmi was off.

[IMG]http://img821.imageshack.us/img821/3162/hdmiq.jpg[/IMG]

then made sure 958 was set as a preferred device in my kubuntu sound settings.

[IMG]http://img707.imageshack.us/img707/7049/958qs.jpg[/IMG]

surround seems to work flawless on my theater receiver.

My screen looks different than yours, reg ubuntu, but I can only get digital stereo...odd. Should I just get a digital output on the 958, not stereo etc.?

I can then only listed to things via dolby pro logic - ughh.  no DTS. etc...

thanks

---

### Post by inobe on 2011-11-25
oops, i could have sworn you had kde kubuntu, my bad..

i'm sure the unity desktop has a similar ui.

but hey, i did a search and found that some things may be muted.

[http://www.bunkerhollow.com/blogs/matt/archive/2011/06/18/zotac-nd22-xbmc-hdmi-audio-configuration-in-ubuntu-11-04.aspx](http://www.bunkerhollow.com/blogs/matt/archive/2011/06/18/zotac-nd22-xbmc-hdmi-audio-configuration-in-ubuntu-11-04.aspx)

the topic is for xbmc, ignore that and notice profile settings in second image, can set hdmi to off?

---

### Post by ser_renely on 2011-11-25
Thanks.  I will take a look at that.

Just disappointed so far trying to get this to work, I did figure it would be a bit easier than this so far. Between that and the crap video, which my 7 year old windows laptop tops the quality of the i3, and the i3 is good for a HTPC.

---

### Post by inobe on 2011-11-25
yes, it really differs due to certain chipsets and the drivers provided by these vendors.

it's not really the OS is all i'm trying to explain, you can have an awesome system, and if the vendor sucks and don't provide decent multi platform driver support, then we have to question the fact that hardware vendors like nvidia are out there:)

---

### Post by ser_renely on 2011-11-26
> **inobe said:**
> yes, it really differs due to certain chipsets and the drivers provided by these vendors.

it's not really the OS is all i'm trying to explain, you can have an awesome system, and if the vendor sucks and don't provide decent multi platform driver support, then we have to question the fact that hardware vendors like nvidia are out there:)

true, makes sense.  thanks

---

### Post by ser_renely on 2011-11-30
> **inobe said:**
> yes, it really differs due to certain chipsets and the drivers provided by these vendors.

it's not really the OS is all i'm trying to explain, you can have an awesome system, and if the vendor sucks and don't provide decent multi platform driver support, then we have to question the fact that hardware vendors like nvidia are out there:)

I switched to win 7 and everything works perfectly :-/

---

