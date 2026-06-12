---
title: "Detecting tv tuner"
date: 2008-05-05
forum: Multimedia Software
---

### Post by moshy on 2008-05-05
I have what I think is a Leadtek Winfast DTV 1000T tuner, but I don't think it is being detected by the system (hardy) - I have no /dev/dvb.

 Think this is the card from lspci -v, but it looks like it's not being detected properly.
```
05:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Unknown device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fb002000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
```

What are the steps I have to do to troubleshoot the card and figure out what exactly is going wrong?

---

### Post by Jussi Kukkonen on 2008-05-05
That lspci output looks fine to me. *dmesg* may tell you something new, this is what I have:
```

[17179578.528000] saa7146: register extension 'budget_ci dvb'.
[17179578.528000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179578.528000] saa7146: found saa7146 @ mem e0872000 (revision 1, irq 193) (0x13c2,0x1010).
[17179578.528000] saa7146 (0): dma buffer size 192512
[17179578.528000] DVB: registering new adapter (TT-Budget-C-CI PCI).
[17179578.564000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179578.572000] adapter has MAC addr = 00:d0:5c:04:7a:6f
[17179578.572000] input: Budget-CI dvb ir receiver saa7146 (0) as /class/input/input0
[17179578.572000] DVB: registering frontend 0 (ST STV0297 DVB-C)...
```
For troubleshooting info, see [linuxtv.org](http://www.linuxtv.org/wiki/index.php/Main_Page), especially [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

---

### Post by moshy on 2008-05-05
If I do dmesg I get:
registered device video0 [v4l2]
But I was under the impression this was for analog cards, and I think my card is only digital, and hence I want something like /dev/dvb/adapter* to show up.
doing 'dmesg | grep dvb' shows literally nothing.
I looked at linuxtv.org, and under my card it says, 'Conexant based system see LR6650', which led me to believe I need the ex88* module instead of SAA7130, but I don't know how to use modprobe.

How would I go about getting the system to load a different module, or am I completely wrong?

---

### Post by Mze on 2008-05-05
I have a Compro VideoMate TV PVR/FM. 

lspci -v:
00:13.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: Compro Technology, Inc. Compro VideoMate TV PVR/FM
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at db000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

I followed instructions to modify modprobe using this [thread]("http://ubuntuforums.org/showthread.php?t=725431") but I modified my modprobe saa7134 file thus; with instructions from another site to get my card working:

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=37

I then installed TVtime and was able to scan channels after a reboot.

Hope this helps.

---

### Post by steefjeqv on 2008-05-06
Hi,

As quick test you can try in terminal :

sudo modprobe saa7134

Kaffeine is a nice and easy app to use and test your DVB card.
It's available in Synaptic or in terminal :

sudo apt-get install kaffeine

Greetings,
Steven

---

### Post by moshy on 2008-05-06
No, its still not working.
Kaffeine says 'can't bind info socket'
MeTV says 'no tuner device'

I've been reading some more and I really think the problem is it should be using cx88-dvb instead of saa7134, i.e. lspci -v should read something along the lines of:

Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

Instead of what I get:

Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

I can load the cx88-dvb module by adding it to /etc/modules, and it loads fine, but its not registering with the device.

```

$ dmesg | grep dvb
[   34.129703] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   34.129705] cx88/2: registering cx8802 driver, type: dvb access: shared

```

It's not creating /dev/dvb either.

Thanks for all your help so far.

---

### Post by steefjeqv on 2008-05-06
Hi,

This Leadtek DVB card normally uses the cx88 driver.
It should have a conexant chipset.. strange ?

I'm going to try and find some more info.

I'll keep you posted.

Greetings,
Steven

---

### Post by steefjeqv on 2008-05-06
Hi,

Try in terminal :

sudo modprobe cx88-dvb card=35

Greetings,
Steven

---

### Post by moshy on 2008-05-06
This is what I get:
```

$ sudo modprobe cx88-dvb card=35
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.24-16-generic/ubuntu/media/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$ dmesg | tail
[ 5678.317284] wlan0: RX authentication from 00:04:ed:05:2a:d9 (alg=0 transaction=2 status=0)
[ 5678.317287] wlan0: authenticated
[ 5678.317289] wlan0: associate with AP 00:04:ed:05:2a:d9
[ 5678.319273] wlan0: RX ReassocResp from 00:04:ed:05:2a:d9 (capab=0x11 status=0 aid=4)
[ 5678.319275] wlan0: associated
[ 5691.002216] cx88_dvb: Unknown parameter `card'
[ 5713.902598] WEP decrypt failed (ICV)
[ 5714.313083] WEP decrypt failed (ICV)
[ 5723.969439] cx88_dvb: Unknown parameter `card'
[ 5728.220854] wlan0: No ProbeResp from current AP 00:04:ed:05:2a:d9 - assume out of range

```

---

### Post by steefjeqv on 2008-05-06
Sorry, my mistake.

The cx88 driver isn't able to load a certain card reference this way.

We can try this (terminal) :

sudo gedit /etc/modprobe.d/options

Now add the following line :

options cx88xx card=35

Save the file.

Then (terminal) :

sudo modprobe cx88-dvb

Give Kaffeine a try. If it doesn't work immediattelly, try a reboot.

Greetings,
Steven

---

### Post by moshy on 2008-05-07
This still does not work. Am I doing something wrong with Kaffeine? I'm just opening it up and going to the DVB client tab, I can't find anything to do with scanning channels etc.

Also I've now tried blacklisting the saa7130 module, and putting cx88-dvb in /etc/modules.
There's still no /dev/dvb but I found /dev/.static/dev/dvb/adaptor*
lspci still shows the card as SAA7134 instead of Conexant

I really don't know what to do, lots of the forums suggest compiling new drivers or new kernels, but I'm using hardy heron, so I think I should have the latest of everything anyway.

---

### Post by steefjeqv on 2008-05-08
Hi,

Did you buy this card recently?

There seems to be a new version called the Leadtek Winfast DTV 1000-S.

See this thread :

[http://ubuntuforums.org/showthread.php?t=597244&page=3]("http://ubuntuforums.org/showthread.php?t=597244&page=3")

Greetings,
Steven

---

### Post by moshy on 2008-05-16
I already know of this card and that it is not supported under linux before I bought the new computer, so I specifically tried not to get it. But now for unrelated reasons I opened up the box and while I was there slipped a mirror under the pci slot, and alas it's a DTV 1000-S. It seems there was a misunderstanding with the retailer.

I'll probably just 'sell' this to my brother and and get a new one. Thanks for all your help.

---

