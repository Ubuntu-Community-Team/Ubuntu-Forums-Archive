---
title: "Kworld Video Magician Tv Tuner Card"
date: 2008-10-30
forum: Multimedia Software
---

### Post by Fir3chi3f on 2008-10-30
I cant seem to get this capture card working right.

Tvtime gives the error:
```
videoinput: Cannot open capture device /dev/video0: No such file or directory

```

It looks like at least one person got it working [here]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1050249&sku=O38-1052")

Here is what I got so far:

for "dmesg":
```
 [   54.513292] Linux video capture interface: v2.00
[   54.584260] Linux agpgart interface v0.102
[   54.756658] cx8800: Unknown parameter `card'

```

and for "lspci | grep -i cx | more":
```
02:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio 
Decoder (rev 05)

```

 for "lsmod | grep "cx""
```
cx88xx                 65960  0 
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx
tveeprom               16656  1 cx88xx
videodev               29440  2 sn9c102,cx88xx
v4l2_common            18304  3 sn9c102,cx88xx,videodev
videobuf_dma_sg        14980  1 cx88xx
videobuf_core          18820  2 cx88xx,videobuf_dma_sg
btcx_risc               5896  1 cx88xx
i2c_core               24832  5 nvidia,cx88xx,i2c_algo_bit,tveeprom,i2c_nforce2
```

I have not been able to try 64bit ubuntu yet, but unless Im mistaken this should work regardless.
As always, any help, suggestions or questions are greatly appreciated

---

### Post by Fir3chi3f on 2008-11-01
desperate bump

---

### Post by xc3RnbFO8P on 2008-11-01
You can try
**lspsi -vn** and find **Subsystem ID**
you will get something like this:
> ??:??.0 ????: ????:7134 (rev 05)
	Subsystem: ????:????
Then check if your card is listed here:
[http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw]("http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw")

In /etc/modprobe.conf add this line:
> options cx88xx card=??

> sudo gedit /etc/modprobe.conf

---

### Post by Fir3chi3f on 2008-11-01
Thank you so much for your reply


"lspci -vn" gives me:
```
00:00.0 0580: 10de:005e (rev a3)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping

00:01.0 0601: 10de:0050 (rev a3)
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 0c05: 10de:0052 (rev a2)
	Subsystem: 10de:cb84
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=32]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2

00:02.0 0c03: 10de:005a (rev a2) (prog-if 10 [OHCI])
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 0c03: 10de:005b (rev a3) (prog-if 20 [EHCI])
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 0401: 10de:0059 (rev a2)
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at f000 [size=256]
	I/O ports at ec00 [size=256]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:06.0 0101: 10de:0053 (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: f0de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at e800 [size=16]
	Capabilities: [44] Power Management version 2

00:07.0 0101: 10de:0054 (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:08.0 0101: 10de:0055 (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c000 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:09.0 0604: 10de:005c (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
	I/O behind bridge: 00008000-0000afff
	Memory behind bridge: fa000000-fcffffff
	Prefetchable memory behind bridge: fdf00000-fdffffff

00:0a.0 0680: 10de:0057 (rev a3)
	Subsystem: 10de:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=8]
	Capabilities: [44] Power Management version 2

00:0b.0 0604: 10de:005d (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0c.0 0604: 10de:005d (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 0604: 10de:005d (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0e.0 0604: 10de:005d (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 0600: 1022:1100
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1101
	Flags: fast devsel

00:18.2 0600: 1022:1102
	Flags: fast devsel

00:18.3 0600: 1022:1103
	Flags: fast devsel

01:06.0 0200: 10ec:8180 (rev 20)
	Subsystem: 1186:3303
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at ac00 [size=256]
	Memory at fcfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

01:07.0 0604: 3388:0021 (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, medium devsel, latency 32
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: fdf00000-fdffffff
	Capabilities: [80] Power Management version 2
	Capabilities: [90] #06 [0080]

01:08.0 0104: 1095:3114 (rev 02)
	Subsystem: 1095:7114
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	I/O ports at a800 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9800 [size=16]
	Memory at fcffe000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at fc000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2

01:09.0 0c00: 1106:3044 (rev 80) (prog-if 10 [OHCI])
	Subsystem: 15bd:1006
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 21
	Memory at fcffd000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at 9400 [size=128]
	Capabilities: [50] Power Management version 2

01:0a.0 0200: 11ab:4320 (rev 13)
	Subsystem: 15bd:100a
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
	Memory at fcff8000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at 9000 [size=256]
	[virtual] Expansion ROM at fc080000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data

02:08.0 0400: 14f1:8800 (rev 05)
	Flags: bus master, medium devsel, latency 32, IRQ 5
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

02:09.0 0c00: 104c:8023 (prog-if 10 [OHCI])
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fbfff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

06:00.0 0300: 10de:0606 (rev a2) (prog-if 00 [VGA controller])
	Subsystem: 1682:2335
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4c00 [size=128]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

```

I might be looking at it wrong but, I just don't see anything in there about the card.

Thanks for the link and the modprobe file im going to mess with thos a little, I will post back.

---

### Post by xc3RnbFO8P on 2008-11-02
This is your card:
> 02:08.0 0400: 14f1:8800 (rev 05)
	Flags: bus master, medium devsel, latency 32, IRQ 5
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

I didn't find any solution for this card.

---

### Post by Fir3chi3f on 2008-11-03
Thank you for your help, I'm still going to mess with it. But I will look for one that I know will work.

---

### Post by Fir3chi3f on 2008-11-13
Update: I got it working!! somewhat...
[COLOR="Blue"][URL="http://bbs.archlinux.org/viewtopic.php?id=53567"]
Using the info I got here[/URL][/COLOR] on 64bit ubuntu the video-in works beatify, but the tv still doesn't... 

instead of card=38 I used card=45

And I also had to make a /etc/modprobe.conf file then put in it:
```
options cx88xx card=45
```I am still messing with it to get the Tv working and will mark this solved when it fully is, any suggestions or comments are still appreciated.

---

### Post by Fir3chi3f on 2008-11-13
Channels work perfectly, in /etc/modprobe.conf tuner had to be set to 38
```
options cx88xx card=45 tuner=38
```

Two last problems the sound for video-in is always coming out of my speakers regardless of a program viewing and no sound for tv. (video-in sound constant)

---

### Post by 081104jk on 2008-11-13
&#21488;&#28286;[**st&#38400;&#38376;**](http://WWW.yhht-valve.com/twstfm.htm)  &#21488;&#28286;[**st&#38400;&#38376;**](http://WWW.yhht-valve.com/twstfm.htm)&#20195;&#29702;&#21488;&#28286;[**st&#38400;&#38376;**](http://WWW.yhht-valve.com/twstfm.htm)&#20195;&#29702;--&#19987;&#19994;&#21488;&#28286;st&#38400;&#38376;&#20195;&#29702;&#30005;&#27668;&#21160;&#38400;&#38376;&#12289;&#26085;&#26412;&#12289;&#21271;&#27901;kitz&#12289;YOSHITAKE&#12289;&#32768;&#24076;&#36798;&#20975;&#12289;TLV&#12289;SHOWA&#65288;&#26157;&#21644;&#65289;&#12289;&#24503;&#22269;ARI&#12289;&#32654;&#22269;&#38463;&#22982;&#26031;&#22766;&#12289;ARMSTRONG&#12289;&#24847;&#22823;&#21033;ODE&#12289;&#29790;&#22763;BELIMO&#12289;&#21338;&#21147;&#35851;&#12289;&#21488;&#28286;SNW&#12289;&#21488;&#28286;ST&#12289;&#38400;&#38376;&#12289;&#30005;&#21160;&#38400;&#38376;&#12289;&#30005;&#21160;&#34678;&#38400;&#12289;&#30005;&#21160;&#29699;&#38400;&#12289;&#30005;&#21160;&#19977;&#36890;&#29699;&#38400;&#12289;&#30005;&#21160;&#35843;&#33410;&#38400;&#12289;&#27668;&#21160;&#29699;&#38400;&#12289;&#27668;&#21160;&#19977;&#36890;&#29699;&#38400;&#12289;&#27668;&#21160;&#34678;&#38400;&#12289;&#27668;&#21160;&#38400;&#38376;&#12289;&#39118;&#38400;&#25191;&#34892;&#22120;&#12289;&#38108;&#29699;&#38400;&#12289;&#38108;&#25130;&#27490;&#38400;&#12289;&#38108;&#38392;&#38400;&#12289;&#38108;&#36807;&#28388;&#22120;&#12289;&#38108;&#27490;&#22238;&#38400;&#12289;&#25163;&#26564;&#34678;&#38400;&#12289;&#34583;&#36718;&#34678;&#38400;&#12289;&#20943;&#21387;&#38400;&#12289;&#23433;&#20840;&#38400;&#12289;&#30095;&#27700;&#38400;&#12289;&#28014;&#29699;&#30095;&#27700;&#38400;&#12289;&#20498;&#21514;&#26742;&#30095;&#27700;&#27861;&#12289;&#22278;&#30424;&#30095;&#27700;&#38400;&#12289;&#28201;&#24230;&#35843;&#33410;&#38400;&#12289;&#27874;&#32441;&#31649;&#25130;&#27490;&#38400;&#12289;&#19981;&#38152;&#38050;&#23433;&#20840;&#38400;&#12289;&#38108;&#23433;&#20840;&#38400;&#12289;&#30005;&#30913;&#38400;&#12289;&#19981;&#38152;&#38050;&#30005;&#30913;&#38400;&#12289;&#36827;&#21475;&#30005;&#30913;&#38400;&#12289;&#21488;&#28286;st&#38400;&#38376;&#20195;&#29702;      &#12304;&#21488;&#28286;ST&#31995;&#21015;&#12305; |&#22797;&#21160;&#24335;&#30879;&#22411;&#38400; |&#22797;&#21160;&#24335;&#27861;&#20848;&#21475;&#29699;&#22622;&#38400; |&#22797;&#21160;&#24335;&#19977;&#36890;&#27861;&#20848;&#21475;&#29699;&#22622;&#38400; |&#22797;&#21160;&#24335;&#19977;&#36890;&#29273;&#21475;&#29699;&#22622;&#38400; |&#22797;&#21160;&#24335;&#29273;&#21475;&#29699;&#22622;&#38400;

---

### Post by Fir3chi3f on 2008-11-13
With these issues, here is the readout

```
[   25.861056] cx88[0]: TV tuner type 38, Radio tuner type -1
[   26.003969] tuner' 2-0061: chip found @ 0xc2 (cx88[0])
[   26.014194] tveeprom 2-0050: Huh, no eeprom present (err=-6)?
[   26.055283] tuner-simple 2-0061: creating new instance
[   26.055287] tuner-simple 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))

```

To my knowledge, the rest of capture card related output of dmesg is ok. 

I haven't found an option to set the radio tuner (the -1 problem); the rest of the output in that code box, I don't know what to make of it. Maybe I'll try different tuner numbers looks like 38 = Philips PAL/SECAM multi (thats not right).

---

### Post by Fir3chi3f on 2008-11-14
This does seem to be more of a journal lol. 

Anyway...

It seems like no matter what card I set is too the same outcome-
-no sound for TV
-sound all the time for video-in

Were I'm at-
I've deleted /etc/modprobe.conf and have been attempting the changes in /etc/modprobe.d/options I'm not sure the difference but here is what I am toying with in the file:

```
# capture card
options cx8800 video_nr=0 radio_nr=38
options cx88xx card=59 tuner=38
```

If I don't set the tuner the tv picture doesn't work, it seems the same as the card though- doesn't seem to matter what it is set for.

The frustrating part of setting the radio and tuner is this line in dmesg:
```
[   25.564189] cx88[0]: TV tuner type 38, Radio tuner type -1

```

---

### Post by mark-ellis on 2009-09-06
Hey! 

Thanks for posting what you've done!

It helped me allot! 

Mark

---

### Post by davis68nf on 2010-01-01
[SIZE=2]The V-STREAM VIDEO MAGICIAN capture card (VS-TV883DVR-PROII) will work fully if the **[FONT=Times New Roman]/etc/modprobe.conf[/FONT]** file has the single line:

o**[FONT=Courier New]ptions cx88xx card=16 tuner=38[/FONT]**

XawTV (TV viewer for x11) and TVtime Television Viewer work with full audio and video. XawTV is especially nice because the left and right arrow keys can be used to fine-tune each station. I have not managed to get Kaffeine or MythTV to work. Nor have I managed to capture video... yet.

I am running Linux Mint (Helena).[/SIZE]

---

