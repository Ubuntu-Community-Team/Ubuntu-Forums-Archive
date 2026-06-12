---
title: "Conexant Falcon II TV tuner setup help?"
date: 2008-07-14
forum: Multimedia Software
---

### Post by fliptrix on 2008-07-14
Hi, so I have a Conexant Falcon II tv tuner, in a HP media center comp. Works fine in windows, but when I boot into Ubuntu (hardy, 8.04) I can't get the tv to work. TV time and a few other tv programs tell me can't find /dev/video0 or can't open /dev/video0. I'm not sure how to setup this card in linux so any help would be great... just so i can get to watch tv in linux. I was assuming that ivtv would be the correct module to use, but I'm not sure.

---

### Post by fliptrix on 2008-07-15
No one? Anyone know anything about the Conexant Falcon II video capture chipset? Apparently it looks like it shares the same chipset as the PVR-150 if that helps..?

---

### Post by xc3RnbFO8P on 2008-07-15
Only thing I find is this:
[http://www.linuxtv.org/wiki/index.php/Reference_Designs]("http://www.linuxtv.org/wiki/index.php/Reference_Designs")

In Terminal, show the output of **lspci**.

---

### Post by fliptrix on 2008-07-15
here is the output of for **lspci**:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
02:04.0 Communication controller: Agere Systems Unknown device 0620

```

---

### Post by xc3RnbFO8P on 2008-07-15
Tvtime wont work with IVTV, so try this:
[http://ubuntuforums.org/showthread.php?t=763698]("http://ubuntuforums.org/showthread.php?t=763698")

---

### Post by fliptrix on 2008-07-15
Alright, I'll give it a try and see what I can do... if not... it looks like I'll just be looking out for a new card to use.

---

### Post by xc3RnbFO8P on 2008-07-15
Maybe you have to install V4L drivers.

---

### Post by fliptrix on 2008-07-15
not sure if this would help but here's my **dmesg | grep ivtv**
```
$ dmesg | grep ivtv
[   60.457370] ivtv:  Start initialization, version 1.1.0
[   60.457451] ivtv0: Initializing card #0
[   60.457456] ivtv0: Unknown card: vendor/device: 4444/0016
[   60.457459] ivtv0:               subsystem vendor/device: 1043/4b66
[   60.457460] ivtv0:               cx23416 based
[   60.457462] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   60.457463] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   60.457465] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   60.457467] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   60.471615] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   60.531042] ivtv0: Invalid EEPROM
[   60.882160] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   60.886560] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   60.941040] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   60.959740] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   60.959757] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   60.959772] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   60.959787] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   60.959802] ivtv0: Registered device radio0 for encoder radio
[   60.959804] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   60.959864] ivtv:  End initialization
[   81.787206] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   81.984187] ivtv0: Encoder revision: 0x02060039
[   85.583529] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   85.659571] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d
[   85.720085] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d

```

and

```
$ lspci -vv -s 02:
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 4b66
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (32000ns min, 2000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

```

---

### Post by xc3RnbFO8P on 2008-07-15
Here is what we try:
> sudo gedit /etc/modules
add this line
> wm8775
restart the computer and check **dmesg | grep ivtv** again.
Maybe its necessary add another line.

---

### Post by fliptrix on 2008-07-16
No luck so far... I'm really stumped on this. I wonder why this is so different to configure. Well here's some pics of the actual card if they give off any info possibly.

[IMG]http://farm4.static.flickr.com/3102/2672964821_40b1828289.jpg?v=0[/IMG]

[IMG]http://farm4.static.flickr.com/3109/2673783190_bbb379e646.jpg?v=0[/IMG]

[IMG]http://farm4.static.flickr.com/3181/2672964773_0a76b6c6fb.jpg?v=0[/IMG]

Any ideas about the 'Invalid EEPROM'? And how would I go about setting the tuner type? From looking at the card, I should have a Philips type tuner I think.

---

### Post by xc3RnbFO8P on 2008-07-16
Here is one thing you can try:
add in /etc/modprobe.d/ivtv: 
> options  ivtv tuner=43 cardtype=7 newi2c=1
Otherwise this card is not working.
But if someone have more information about this card, 
please add it here.

---

### Post by fliptrix on 2008-07-16
It looks like I may finally be getting somewhere... but don't really know. After adding the line, VLC is actually showing me something as in just static. As in this:

[IMG]http://farm4.static.flickr.com/3178/2674309654_a0707840f5.jpg?v=0[/IMG]

Before setting the tuner, I had just gotten a black screen. I've tried setting/changing channels but still the same static. I think I may just look for a new card to work with in linux, since I may get no where with this.

---

### Post by xc3RnbFO8P on 2008-07-16
> I think I may just look for a new card to work with in linux
Yes I agree.

---

### Post by fliptrix on 2008-07-16
Well thanks for helping out and trying. But quick question, you have and recomendations of any good tv cards that will be easy to setup in linux as well as be compatible in windows? Thanks.

---

### Post by xc3RnbFO8P on 2008-07-16
Analog or dvb-t, here is information from LinuxTv:
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")
Many countries in Europe are changing from analog to digital in air.
Some signals are ATSC others are DVB-T.
So check what is going to happened in your country

---

### Post by levif on 2008-12-24
I realize that this thread is no longer active, but I managed to (somewhat) solve the issue, and shall post my findings here so that any fellow googlers with a similar problem can get it working.  Here's what I did:

1. Install ivtv
2. Add the following to /etc/modprobe.d/ivtv:
3. > options ivtv tuner=43 cardtype=7 newi2c=1
In VLC Media Player
4. Go to Media > Open Capture Device
5. Select PVR
6. Set device name to the location of your TV card.  In most cases, this is /dev/video0
7. In advanced options, change the Channel number to the desired input.  This will select the port on the card, NOT the TV channel. The best advice I can give here is to mess with the number until it yeilds desired results.

This will get video playing in VLC.

As for audio playback, I don't know how to set this up, or if setting up is necessary, as my video device does not, at the time of writing, have audio, so I can't help there.

Hope this helps someone.

---

### Post by wolfen69 on 2008-12-24
to expand a little bit on what levif said, the following will get you set up in no time:

I have a Hauppauge pvr card, same chipset as yours and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by phil34 on 2009-04-14
Sorry to bring this thread up from forever ago...

But, does anybody know how to get this thing to work in mythtv?  I can go through these steps and see tv, but I am still unable to get myth tv to work with this.

---

### Post by phil34 on 2009-04-14
Also, when I run modprobe ivtvfb I get this error.

FATAL: Error inserting ivtvfb (/lib/modules/2.6.27-11-generic/kernel/drivers/media/video/ivtv/ivtvfb.ko): No such device

even though it is obvious I have a tuner device because I can watch tv using VLC Media Player.

Is there any way I can maybe manually show myth that I do have this device?

Thanks

---

### Post by ArielEnter on 2011-08-03
> **fliptrix said:**
> It looks like I may finally be getting somewhere... but don't really know. After adding the line, VLC is actually showing me something as in just static. As in this:

[IMG]http://farm4.static.flickr.com/3178/2674309654_a0707840f5.jpg?v=0[/IMG]

Before setting the tuner, I had just gotten a black screen. I've tried setting/changing channels but still the same static. I think I may just look for a new card to work with in linux, since I may get no where with this.

I notice that this happens every time I reboot my system. Porwer off my computer completely and Turning it back on solves the problem, but this means I can't use the reboot option for instance when performing a system update, so I turn it off and back on instead. I even followed the instructions described here to prevent restarting by mistake  [http://ubuntuforums.org/showthread.php?t=1670897&page=2](http://ubuntuforums.org/showthread.php?t=1670897&page=2) .

I notice that while this problem is occurring, mythbackend say "Probed info: Hauppauge WinTV PVR-150 [ivtv]", and then when the problem is solved it will say "Probed info: ASUS Falcon2 [ivtv]".

I'm going to see if the guys from mythtv know something about the issue but if some one knows something please share.

---

### Post by ArielEnter on 2011-08-03
For those of you just starting using mythtv, do the following in mythbackend:

[LIST]
[*]Choose IVTV MPEG-2 encoder card as the Card type.
[*]You may want to use us-cable as the channel frequency table for your video source if default doesn't work.
[*]Choose 127.0.0.1 ip address for LocalBackend and MasterBackend.
[*]Add a turner, create a video source, and define a video source to a specific input connection, and scan for channels.
[*]A listing grabber is not a must to watch tv, but a program guide is sure important.
[*]Watch out for the problem described by me in the last post.
[/LIST]
Good luck.

---

### Post by Salbono on 2012-02-07
I have been trying to get this to work in MythTv for many hours, it did work once then I had to reinstall for other reasons. The I just couldn't get it to work. 

I set to channel 2 to get the composite inputs to work. I think channel three is for the cable... that would make fm radio 1 (if logic was at work)

---

