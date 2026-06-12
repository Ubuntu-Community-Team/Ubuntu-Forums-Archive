---
title: "tvtime pvr-350 ivtv help needed"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by gotmonkey on 2006-07-01
I have been trying to get both my pvr-350 working with tvtime. Could someone help?

This is what I have so far. I followed the guide on ivtv's site to get the card working.
ivtv install and dmesg is returning this:

> 
[17179586.684000] ivtv:  ==================== START INIT IVTV ================== ==
[17179586.684000] ivtv:  version 0.4.6 (tagged release) loading
[17179586.684000] ivtv:  Linux version: 2.6.15-25-k7 SMP preempt K7 gcc-4.0
[17179586.684000] ivtv:  In case of problems please include the debug info betwe en
[17179586.684000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179586.684000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179586.684000] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[17179586.684000] **** SET: Misaligned resource pointer: f7b55b42 Type 07 Len 0
[17179586.684000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179586.684000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 ( level, high) -> IRQ 209
[17179586.684000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179586.736000] tveeprom: ivtv version
[17179586.736000] tveeprom: Hauppauge: model = 32552, rev = B233, serial# = 6511 438
[17179586.736000] tveeprom: tuner = Temic 4039FR5 (idx = 33, type = 21)
[17179586.736000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x0000100 0)
[17179586.736000] tveeprom: audio processor = MSP4448 (type = 1b)
[17179586.736000] tveeprom: decoder processor = SAA7115 (type = 13)
[17179586.736000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179586.756000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179586.756000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61 ]
[17179586.900000] eth0: link up.
[17179586.956000] saa7115 2-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179587.112000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179587.160000] msp3400 2-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radi o mode=simpler
[17179587.160000] msp3400 2-0040: msp34xxg daemon started
[17179587.188000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[17179587.656000] NET: Registered protocol family 17
[17179587.956000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179588.184000] ivtv0: Encoder revision: 0x02050032
[17179588.184000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers ( 4096KB total)
[17179588.184000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2 048KB total)
[17179588.184000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2 048KB total)
[17179588.184000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffe rs (2048KB total)
[17179588.184000] ivtv0: Create encoder radio stream
[17179588.184000] tuner: type set to 21 (Temic NTSC (4039 FR5)) by ivtv i2c driv er #0
[17179588.364000] ivtv0: Initialized WinTV PVR 250, card #0
[17179588.364000] ivtv:  ====================  END INIT IVTV  ================== 


and when I try to run tvtime I get this:

> 
simian@shuttle-ubuntu:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/simian/.tvtime/tvtime.xml"
videoinput: Card failed to allocate capture buffers: Invalid argument
I/O warning : failed to load external entity "/home/simian/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
Thank you for using tvtime.


When I try running the program from the start menu, I get this

ivtv: invalid argument
Cannot open capture device /dev/video0

---

### Post by fragos on 2006-07-01
tvtime site says it doesn't support ivtv.

---

### Post by gotmonkey on 2006-07-02
From what I am seeing, unless I want to configure mythtv, my pvr-350 is best suited in my windows machine for now.

I did find a wintv card in an old system that seems to be working with tvtime. 
It is a wintv card and device manager is listing it as a Bt878 Video Capture card.

The video is a little grainy, maybe I will find something in the forum to address that. Not getting sound from the card, I enabled sound by connecting an audio cable from the card to the aux connector on my system board.

---

### Post by User_Program on 2006-07-03
I also have a pvr 350 and didn't want to install mythtv either.  The closest thing I've found that does the trick is karaivtv ( [http://www.kde-look.org/content/show.php?content=29661](http://www.kde-look.org/content/show.php?content=29661) )

Now this is if you have kde, not sure if there is anything like it in Gnome.

If you want to do it manually there are media players that can play the pvr's 
VLC,Mplayer, Kaffeine

In terminal
> mplayer -vo xv /dev/video0
you can also change "mplayer"  to whatever media player you want to use

Now in a new terminal
> ivtv-tune -c xx -d /dev/video0

Replace xx with the channel you want to tune into.

Listen to radio
> ivtv-radio -f xx.x
xx.x being the station you want to tune into.

Does anyone know if there is anything like the Wintv app that you get in windows...like a click of the mouse channel changing, recording ect in Linux?
Maybe a plugin for VLC or Kaffeine ?  One click mouse to change the channel being the most important for me though.  You would think there would be one out there !?!?

---

### Post by crispy_420 on 2006-07-03
If you plan on using Windows with this card, try SageTV. I use it on my windows box and it works great.

Also look at this offering from the makers of SageTV:    [SageTV Linux]("http://www.sagetv.com/linuxOEMedition.html")

I saw a demo of it at DLS in San Diego and it looked good. Apparently you can control it from anywhere in the world, assuming highspeed internet. We watched the guy showing it's home tv(DirectTV) in San Diego when his home was in Northern California. Also it is a whole distro with this purpose in mind. The down side is it will cost you. As of right know it is $79.95 (US). I have been considering it myself, my Windows Media Center computer is gathering dust. And the system requirements are pretty basic, so if you have the extra hardware sitting around...

Just a thought. When I get time I will probally give it a try. If it is as good as the Windows version I will be happy.

---

