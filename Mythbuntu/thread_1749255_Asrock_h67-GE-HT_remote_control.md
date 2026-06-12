---
title: "Asrock h67-GE-HT remote control"
date: 2011-05-04
forum: Mythbuntu
---

### Post by dawez on 2011-05-04
HI all,

I have an Asrock h67-GE/HT which came bundled with a remote control and a usb receiver [the receiver is marked just Asrock]. I tried without any luck to have lirc working with this remote control. The USB receiver is not appearing in the

lsusb

which is already a bad sign. I tried plenty of combinations of receiver/remote in the Lirc setup without any progress.

The remote control looks like this one : 
[URL="http://www.phoronix.com/scan.php?page=article&item=asrock_vision3d&num=1"]
http://www.phoronix.com/scan.php?page=article&item=asrock_vision3d&num=1[/URL]

at the bottom of the page. In that page is written "The MCE remote control ASRock includes with the Vision 3D is decent and can be configured to work under Linux with LIRC." which seems to be encouraging. 

I looked around but I cannot find anything specific.

Does anyone have any [hopefully] success story to share about this remote control / receiver combination ?

---

### Post by dawez on 2011-05-06
Maybe it's just a matter of days to see this supported. I think that the other devices [the boxed HT systems] are using the same remote control/receiver.

Here is the combo receiver + remote that I got.

[http://www.asrock.com/mb/spec/Card.asp?Model=Smart%20Remote](http://www.asrock.com/mb/spec/Card.asp?Model=Smart%20Remote)

another picture of the receiver / remote combo

[http://www.overclockzone.com/tor_za/year_2011/02/asrock_h67m_ge_ht/pic/IMG_7653.jpg](http://www.overclockzone.com/tor_za/year_2011/02/asrock_h67m_ge_ht/pic/IMG_7653.jpg)

---

### Post by phroman on 2011-05-09
Not sure where you're at with this but did you check the link provided by dawez?  They appear to be the same remote.  The description of the usb ir receiver says: 

> The MCE Remote Controller operates with this exclusive Multi-Angle CIR Remote Receiver. The CIR Remote Receiver is able to receive the multi-direction infrared signal (top, down and front), which is compatible with most of the chassis on the market.  

And a bit farther down it says:

> Note: The ASRock Smart Remote in only supported by some of ASRock motherboards.  ( they're typo, not mine )

If the usb ir receiver is not showing up on your system in lsusb, that's your first issue.  Did you try any other usb ports on your system?  If you do get it to show up, the Lirc wiki page will be your friend.  

[http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)

I know this is a side step from your question, but I'm so impressed with this I just wanted to throw it out there.  There is a remote control for android that I put on my Android phone, an HTC G2, that is so easy and so awesome I'll never mess around with lirc again.  I'm going to get a cheap Android tablet to use as my whole home remote control, so it's perfect for my situation, it may work for you as well.  Here's a video of it and how to install it.  Just remember to restart your frontend and backend for this to work.  

[http://www.youtube.com/watch?v=Xr1cljto3OE&feature=related](http://www.youtube.com/watch?v=Xr1cljto3OE&feature=related)

---

### Post by dawez on 2011-05-10
Hi phroman,

Thank you for the reply. I think that the receiver is not a standard USB stick. Here it is how to connect

[http://www.asrock.com/support/faq.asp?id=275](http://www.asrock.com/support/faq.asp?id=275)

and if you look at this picure

[http://images.anandtech.com/doci/4241/H67M-GE_HT.jpg](http://images.anandtech.com/doci/4241/H67M-GE_HT.jpg)

You can see on the left nearby the LPT1 connector a USB connector that has below another set of pins. USB6_7 and CIR1.

The story is better explained in the MB manual is that you have to connect a USB plug to the CIR1 and the lower part of the USB.

On this page: [http://www.asrock.com/mb/manual.asp?Model=H67M-GE/HT](http://www.asrock.com/mb/manual.asp?Model=H67M-GE/HT)
there is the PDF manual [http://europe.asrock.com/downloadsite/manual/H67M-GEHT.pdf](http://europe.asrock.com/downloadsite/manual/H67M-GEHT.pdf)

On page 26 there is the explanation on ow to connect the USB plug.

I tried to put in other ports but with lsusb nothing comes up. The remote is working flawlessly with Windows7 [even in this case it should be put in a specific USB port]

And it is also working to powerup the machine! So the Bios is some kind of wakemeup interrupt.

Will check the link for Android, it sounds intriguing

---

### Post by tatou_smaj75 on 2011-06-08
Hello,

I have the same motherboard and I have followed the instructions for the assembly.
I have tested the remote by making the computer booting with the power button of the remote... so it should work fine.

But I also was unable to find it with the lsusb command.



I have found this line with a  lspci  command :
> 
04:00.0 USB Controller: Device 1b6f:7023 (rev 01)
Could it be the remote receiver ?
If so, how can we call it with LIRC ??

Thank you for your help!

for the record, the complete lspci below :
> 
tatoug@tatoug-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
04:00.0 USB Controller: Device 1b6f:7023 (rev 01)lsusb :
> tatoug@tatoug-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by dawez on 2011-06-21
Good to know that there is another user with the same issue :)

This is my output of lspci:


```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 USB Controller: Device 1b6f:7023 (rev 01)
03:00.0 USB Controller: Device 1b6f:7023 (rev 01)
04:00.0 PCI bridge: Device 1b21:1080 (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

Hope that this can be of any help.

I sent a mail to Asrock asking if they are planning to support ubuntu/linux remote but they did not bother caring at all. no good.

As they have already working remote controls on linux for other boxes that may use the same hardware, it should not be such big thing to release a bit of info so we can write some drivers... [good rant.. before going to bed :) ]

---

### Post by dawez on 2011-06-29
Hey tatou_smaj75

Did you try to contact the ASRock Support ? I guess if they will get more requests they will be more likely to help ! ;)

---

### Post by nickrout on 2011-06-29
You gutys might get better answers on the mythtv mailing list, at least one lirc dev hangs out there.

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

---

### Post by maxfire2020 on 2011-09-18
also i have the same problem

---

### Post by weirdweekend on 2011-10-26
Dawez/tatou_smaj75

I've just ordered one of these thinking it would be perfect for a HTPC. Have either of you had any luck getting the remote working or have I just wasted a load of money?

---

### Post by dawez on 2011-10-27
Hey weirdweekend,

I played for 1 day 6 months ago, looking for various option but none worked in linux. Do not know if anything is working now. I guess that there should be some hope as the system is recognizing the receiver/remote on bootup [you can start the system  with the remote-power button] so there should be already something in the BIOS.

In one message one guy suggested to ask a question in a mailing list: 

> 
You guys might get better answers on the mythtv mailing list, at least one lirc dev hangs out there.

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

And best luck of course!

---

### Post by weirdweekend on 2011-10-27
Hi Dawez

My board has not arrived yet but when it does I'll let you know how I get on trying to get everything to work. In the meantime I've been doing some research and have found that Asrock include the same remote with some of their other products and people seem to have got it to work.

This is from someone using XBMC/Ubuntu on an ASRock Ion 330

[http://forum.xbmc.org/showpost.php?p=658379&postcount=384](http://forum.xbmc.org/showpost.php?p=658379&postcount=384)

This is from someone using openelec on an ASRock Z68M-ITX-HT mobo. They make no mention of problems with the remote.

[http://www.openelec.tv/forum/41-supported-hardware/12460-asrock-z68m-itx-ht-motherboard-with-cir-remote-control-device](http://www.openelec.tv/forum/41-supported-hardware/12460-asrock-z68m-itx-ht-motherboard-with-cir-remote-control-device)

Not sure if any of that will be useful but if you have any luck let me know. Failing that the XBMC forums seem to be the place to look for help. Have you tried it with 11.10?

---

### Post by cyberdiamond on 2011-10-29
> **weirdweekend said:**
> 
This is from someone using openelec on an ASRock Z68M-ITX-HT mobo. They make no mention of problems with the remote.

[http://www.openelec.tv/forum/41-supported-hardware/12460-asrock-z68m-itx-ht-motherboard-with-cir-remote-control-device](http://www.openelec.tv/forum/41-supported-hardware/12460-asrock-z68m-itx-ht-motherboard-with-cir-remote-control-device)

Not sure if any of that will be useful but if you have any luck let me know. Failing that the XBMC forums seem to be the place to look for help. Have you tried it with 11.10?

This would be me and I can confirm that it works fine in 11.10
I have yet to try and remap any buttons as the defaults are ok for now.

---

### Post by dawez on 2011-10-29
So good news it seems. I will have a go next weekend [I have 11.04 installed so I can check].

Would be good if I could use the remove control directly in the OS [e.g. increasing the volume and so on.]

Will keep you updated after some more tests on my side.

---

### Post by weirdweekend on 2011-10-31
Wonderful. I'll look forward to hearing about how you get on.

---

### Post by dawez on 2011-11-06
Hi all,

I made some tests and I managed to have a working remote :cool:!

I have 11.04 ubuntu version and from what I understood the modules to accessing the chip are already in the kernel However my specific chip revision is not supported.

```
$ dmesg | grep nuvoton -i

[    8.436279] nuvoton_cir: w836x7hg: unsupported chip, id: 0xc3 0x33
[    8.436399] nuvoton-cir 00:05: disabled

```
this with kernel 2.6.38-12-generic.  In my case there was no point of installing the nuvoton driver patch as this is working for earlier version of kernel [also it's  a bit of struggle to remove it if you install by mistake].

It seems that I have a version of chip that is not supported by kernel 2.6.x. Here you can find more details on the chip version story : [http://forum.xbmc.org/showthread.php?t=100772](http://forum.xbmc.org/showthread.php?t=100772)

Follow also this one with more details : [http://forum.xbmc.org/showthread.php?t=102159](http://forum.xbmc.org/showthread.php?t=102159)

I then installed a newer version of the kernel [3.0.0-0300-generic] and 

```
$ dmesg | grep nuvoton -i

[   18.473341] input: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:05/rc/rc0/input5
[   18.473395] rc0: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:05/rc/rc0
[   18.473470] nuvoton_cir: driver has been successfully loaded
[   18.534436] rc rc0: lirc_dev: driver ir-lirc-codec (nuvoton-cir) registered at minor = 0
```

Which is quite reassuring. And actually with kernel 3 the remote is finally working [no need to install lirc and commands and up/down volume is working straight in Gnome].

Finally it seems that OpenELEC is using a patched version of kernel as described in one forum: [I]OpenELEC uses 2.6.39 with patches to support this chips.
[/I]
[so probably is using the same patch that makes the remote working in my case]

---

