---
title: "ENLTV-FM rev 3.0 (saa7130, saa7134)"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Vox754 on 2009-01-17
**1. History**

I realize there are not many threads about this TV card so I start this one.

*Warning: This card is totally different from **ENLTV-FM-2**.*

This thread was created: 2009-January-17
This thread was updated: 2009-April-25
This thread was updated: 2010-April-19

**2. Encore ENLTV-FM: PCI TV Tuner Adaper with FM Tuner**

This card is manufactured by Encore Electronics Inc. with the **saa7130** chipset.

[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=17&pid=45](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=17&pid=45)

According to the manufacturer's website there are various revisions of this card. The revision number can found by physically examining the card. It should be printed in one corner.
In my case it is **Rev.3**, but there are also **Rev. 5.2**, **5.2B**, and **5.3**.

In Ubuntu 8.10
```

lspci -v

```

```

00:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: Philips Semiconductors Device 2341
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

```

It works by loading the "**saa7134**" kernel module from the "**Video 4 Linux project (v4l2)**", and optionally setting the correct "**card=number**" and "**tuner=number**" as parameters to "**modprobe**".

Unload the "**saa3174**" module and its dependency modules, if any.
```

sudo modprobe -r saa7134_alsa    <---- note the underscore
sudo modprobe -r saa7134-alsa    <---- you can use a hyphen instead
sudo modprobe -r saa7134

```

Reload the module with the correct parameters. The dependency modules should be reloaded automatically.
```

sudo modprobe saa7134 card=xxx tuner=yyy

```

You can check all modules currently loaded with
```

lsmod

```

**3. Ubuntu distributions**

**Ubuntu 6.10 (Edgy Eft)**
I started using this card in this release.

It worked by using
```

sudo modprobre saa7134 card=3

```

but it was recognized as a different card. From 
```

dmesg

```

```

saa7130[0]: subsystem: 1131:2341, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]

```

This was taken from this old thread [http://ubuntuforums.org/showthread.php?t=315379](http://ubuntuforums.org/showthread.php?t=315379)

**Ubuntu 8.10 (Intrepid Ibex)**
According to the kernel logs, this card may be set incorrectly as a GENERIC card.
```

    card=0

```

It worked correctly by using
```

sudo modprobe saa7134 card=106

```

```

saa7130[0]: subsystem: 1131:2341, board: Encore ENLTV [card=106,insmod option]

```

Actually, "**card=106**" corresponds to **ENLTV**, whereas "**card=107**" is **ENLTV-FM**, however in my PC it only works correctly with the former.

**Ubuntu 9.04 (Jaunty Jackalope)**
It worked correctly by using either of two possibilities
```

sudo modprobe saa7134 card=106
sudo modprobe saa7134 card=107 tuner=61

```

```

saa7130[0]: subsystem: 1131:0000, board: Encore ENLTV [card=106,insmod option]
tuner-simple 0-0060: type set to 69 (Tena TNF 5335 and similar models)
--- or ---
saa7130[0]: subsystem: 1131:0000, board: Encore ENLTV-FM [card=107,insmod option]
tuner-simple 0-0060: type set to 61 (Tena TNF9533-D/IF/TNF9533-B/DF)

```

When using "**card=106**" the tuner is selected automatically to "**tuner=69**" and it works.
When using "**card=107**" the "**tuner=61**" must be given explicitly.
In fact it may be possible to use different tuners, other than the ones shown here.

**4. "modprobe" configuration file**

In order to affect behaviour of modules loaded by "**modprobe**", it is possible to create files inside
```

/etc/modprobe.d/

```
as described by the manual pages
```

man modprobe
man modprobe.conf

```

To automatically pass the parameters to "**modprobe**" you can create a file named
```

/etc/modprobe.d/saa7134.conf

```
and add the following line
```

options saa7134 card=107 tuner=61

```

In Ubuntu 8.10 the modprobe configuration files were named without an extension: /etc/modprobe.d/**saa7134**
In Ubuntu 9.04 modprobe indicates that configuration files must end in **.conf**: /etc/modprobe.d/**saa7134.conf**

Next time "**modprobe**" is used with the "**saa7134**" module, for instance, when the system boots, it will use the indicated parameters.

**5. Known problems**

I have always had one problem: when using "**tvtime**" the screen is totally messed up, and **the colors are weird after the computer returns from sleep or hibernation.**

Strangely enough, "**xawtv**" does a wonderful job and never has problems with the image. Only it doesn't support full-screen and the X11 interface does not exactly blend in with the rest of the desktop.

**6. Additional information**

I use NTSC-M and US-cable frecuency table, so the options may be different for you if you are in another region.

With me, this card works better in Linux than it does in Windows.

In Windows, sometimes I get and error: "**failed to initialize hardware**" and I cannot watch TV.
According to the vendor's web page and documentation, this may occur for different reasons such as an incorrectly installed driver.
One solution to this is to reboot several times until the card is picked up. Another way is to **reset the card BIOS** by taking it off the PCI slot, and **short-circuiting jumpers labeled 2-3 in the card**. However this may not always work, and upon restart Windows may again fail to recognize the card.

On the other hand, if the "**modprobe**" parameter is set up correctly, it will always work in Linux.

If fact this procedure can be used to "turn on" the card for Windows.

Whenever the card doesn't want to show up in Windows
[LIST=1]
[*]Shutdow Windows
[*]Start Linux
[*]Open "tvtime", "xawtv" or any other program to watch TV
[*]Close it, and shutdow Linux
[*]Start Windows
[/LIST]

This almost always guarantees that Windows drivers will be able to "initialize" the hardware and I'll be able to watch TV.

I have no need for the FM tuner so I haven't even tried listening to radio stations. I have also not tried to use the remote control that comes with the card. Nevertheless, I have read that both these features work.

**In general, I do not recommend any Encore products** because they tend to be of low quality. Get one of these cards only if you are looking for something cheap that works, and don't care about fancy hardware or high definition.

This Argentinian thread makes reference to similar cards [http://ubuntuforums.org/showthread.php?t=501173](http://ubuntuforums.org/showthread.php?t=501173)

---

### Post by dealcorn on 2010-03-22
In 9.10, the card=106 (or 107), tuner=61 (or 69) parameters also permit Encore ENLTV-3 to scan channels up to 65.  With the benefit of these parameters and /usr/share/doc/linux-doc/video4linux/CARDLIST.saa7134.gz and CARDLIST.tuner, I made the baby steps to card=149 , tuner=69 which permits all channels to scan.  This success is unrelated to the 9.04 no sound in tvtime and mythtv does not scan issues which are addressed in separate threads.  For the benefit of those who search for those funny numbers with colons:
```
~$ lspci -vnn
03:04.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
	Subsystem: Device [1a7f:2208]

```

The only part of the thread which posed problems was:

```
~$ sudo modprobe -r saa7134 alsa
FATAL: Module saa7134 is in use.

```
The alternative of saa7134.conf with a reboot solved this.  A big thanks.

Lastly, while your issues with Encore are valid, this card permits reception of several channels which my Hauppauge 1600 does not receive adequately.

---

### Post by Vox754 on 2010-04-19
> **dealcorn said:**
> In 9.10, the card=106 (or 107), tuner=61 (or 69) parameters also permit **Encore ENLTV-3** to scan channels up to 65.  With the benefit of these parameters and /usr/share/doc/linux-doc/video4linux/CARDLIST.saa7134.gz and CARDLIST.tuner, I made the baby steps to **card=149** , **tuner=69** which permits all channels to scan.  This success is unrelated to the 9.04 no sound in tvtime and mythtv does not scan issues which are addressed in separate threads.  For the benefit of those who search for those funny numbers with colons:
```
~$ lspci -vnn
03:04.0 Multimedia controller [0480]: Philips Semiconductors **SAA7134/SAA7135HL** Video Broadcast Decoder [1131:7134] (rev 01)
	Subsystem: Device [**1a7f:2208**]

```

To anyone reading this, please note that the mentioned card is not the same card of the first post. Therefore, even if both use the **saa7134** kernel module, you may need to specify different **card=xxx**, and **tuner=xxx** options.

> 
The only part of the thread which posed problems was:

```
~$ sudo modprobe -r saa7134 alsa
FATAL: Module saa7134 is in use.

```


Please note that the original post is correct
```

sudo modprobe -r **saa7134_alsa**    <---- note the underscore!
sudo modprobe -r **saa7134-alsa**    <---- modprobe recognizes the hyphen and the underscore the same
~$ sudo modprobe -r saa7134

```

> 
...

Lastly, while your issues with Encore are valid, this card ...
Again, your card is not the same card mentioned in the first post, so results may be different.

---

### Post by radiobuzzer on 2012-01-31
Thanks. Any advice on how to enable the radio device would be also really great

---

