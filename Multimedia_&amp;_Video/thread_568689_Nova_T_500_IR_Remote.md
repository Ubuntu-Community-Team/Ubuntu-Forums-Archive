---
title: "Nova T 500 IR Remote"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by gareththered on 2007-10-06
I've read all the forums that I can find and googled so much that I've ended up in a full circle, but still can't resolve my issue with the IR Remote on my Hauppauge Nova T 500 tv card.
I can get MythTV to scan, display and record TV with not too many issues, but I can't for the life of me get the remote to work.  Many forums state that it works with newer kernels (I'm on 2.6.22-12-386) and show 'dmesg' output to that fact.  Each one shows the 'input' device.  Here are a few 'dmesg' of mine :-```

[   60.042778] MT2060: successfully identified (IF1 = 1220)
[   60.111586] wlan0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x1 status=0 aid=1)
[   60.111589] wlan0: associated
[   60.112208] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.299298] NET: Registered protocol family 17
[   60.521423] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   60.521772] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[   60.530043] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   60.534784] MT2060: successfully identified (IF1 = 1220)
[   61.090854] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   61.090906] usbcore: registered new interface driver dvb_usb_dib0700
[   61.098881] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input2
[   61.098935] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:03.2-1.1
[   61.130634] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input3
[   61.130716] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:03.2-1.1
[   61.130743] usbcore: registered new interface driver usbhid
[   61.130747] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   61.194815] usbcore: registered new interface driver snd-usb-audio

```There is no input device for the IR Remote, along the lines of:-```
[   32.959607] input: IR-receiver inside an USB DVB receiver as /class/input/input4
```(which I copied from a forum; hence the different timestamp).
I've piped 'dmesg' through 'grep' looking for 'input' but the remote doesn't appear.  In desperation I compiled the latest v4l-dvb code and that didn't help!
In even more desparation I installed WinXP and the remote worked on that but I couldn't get it to tune to many channels or display any video! GB-PVR looks promising on Windows (similar to MythTV) but with hardly any channels and no video, it's rather pointless.  Linux is closer to the winning post so far!!
Has anyone had any success with this?
Thanks in advance.

---

### Post by sygin on 2007-10-07
Hi Gareththered,

I have got everything working, my only problem is that I have to power
down my box every few days (some issue with usb disconnect bug I think).

I followed this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI) 

To get the modules to compile I had to install the linux-headers-2.6.22-13-386 
package, the exact version depends on the kernel you are using. 

To find my Linux Kernel version. I used:
uname -r

I also had to use the command:
sudo ln -s /usr/src/linux-headers-2.6.22-13-386 /lib/modules/2.6.22-13-386/source

to get the v4l modles to compile, replace 2.6.22-13-386 with your kernel version.

This was the only way I got the remote to work. :)

Another tip, the firmware only loads when you power cycle your box. So do that 
before giving up.

Cheers
Sygin

PS: I am using gutsy beta but feisty will work.

---

### Post by gareththered on 2007-10-09
Thanks Sygin,
I tried this on a previous install which was Ubuntu 7.04 that had been upgraded to 7.10 and basically played with for ages - it didn't work.
Since then I've installed Mythbuntu from fresh so will try this again.  I'm not convinced it will work as I don't get any messages about the remote when I grep through the output of 'dmesg'.
I just hope I'm wrong!

---

### Post by gareththered on 2007-10-09
Well that will teach me to be such a cynic!  It worked.  Well, it worked to an extent, and I can move up and down using the menus but the OK button doesn't work.
That though is just a matter of adjusting the conf flies as per the document you linked to in your previous post.
Thanks very much for your help.

---

### Post by Lem on 2007-10-09
> **sygin said:**
> Hi Gareththered,

I have got everything working, my only problem is that I have to power
down my box every few days (some issue with usb disconnect bug I think).


Have you tried the new firmware? [http://www.linuxtv.org/pipermail/linux-dvb/2007-September/020348.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-September/020348.html)

---

### Post by sygin on 2007-10-14
Thanks Lem,

The new firmware 1.10 seems to fix the problem. I have just broken 
my uptime record and am very happy.

Cheers
Sygin

---

### Post by Nightwalker07 on 2007-10-15
That sounds promising to me regards the firmware update! I've been suffering harshly from this 'USB Disconnect' issue, more frequent that most are reporting, so it would be nice to get it fixed. :)

---

### Post by theak on 2007-11-17
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")

This looks promising for getting my remote up and running but how do I

> Disable ACI mixer in Audio devices for Multimedia ?

---

### Post by dmelliot on 2007-11-18
Hi Theak,
I struggled on this one for a bit.  You need to disable the ACI mixer in the menu interface you are given after running the "make menuconfig" command.

Hope this helps

---

