---
title: "Capture ext PVR to harddrive - PCI AVC – 2010 - mmap"
date: 2008-06-11
forum: Multimedia Software
---

### Post by lizzie2 on 2008-06-11
Hi all, 9 month silver haired newbe here. 
Have been using 7.4 / 7.10 and now on 8.4. Hardy, Ubuntu, what a great OS. 
Have been having a great time trying to learn about ubuntu. and solving problem with the help of the posts here, (thank you all for your hard work) but, have a problem I have got nowhere with. Am trying to transfer programmes from external PVR via ¨Videoh! PCI AVC-2010¨ capture card to hard drive to watch/record. Apart from ¨suspend¨, this is the last big problem I have.
It works in XP via Sonic MyDVD,(video composite in NTSC/PAL & Secam) so hardware OK. Linux recognizes pci card: 

Processor	2x Intel(R) Core(TM)2 CPU 6320 @ 1.86GHz 
Memory	1034MB (362MB used) 
Operating System	Ubuntu 8.04    
Resolution	1280x960 pixels 
OpenGL Renderer	GeForce 7300 LE/PCI/SSE2 
X11 Vendor	The X.Org Foundation 
Audio Adapter	HDA-Intel - HDA Intel 
Multimedia video controller	Internext Compression Inc iTVC16 

Jun  6 05:42:57 les kernel: [   37.247818] Linux video capture interface: v2.00 
Jun  6 05:42:57 les kernel: [   37.453114] ivtv:  Start initialization, version 1.1.0 
Jun  6 05:42:57 les kernel: [   37.453185] ivtv0: Initializing card #0 
Jun  6 05:42:57 les kernel: [   37.453188] ivtv0: [COLOR="Red"]Autodetected Adaptec VideOh! AVC-2010 card (cx23416 based) [/COLOR]
Jun  6 05:42:57 les kernel: [   37.527187] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 21 
Jun  6 05:42:57 les kernel: [   37.527199] ivtv0: Unreasonably low latency timer, setting to 64 (was 32) 
Jun  6 05:42:57 les kernel: [   37.606862] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22 
Jun  6 05:42:57 les kernel: [   37.681463] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0) 
Jun  6 05:42:57 les kernel: [   37.731915] input: PC Speaker as /devices/platform/pcspkr/input/input6 
Jun  6 05:42:57 les kernel: [   37.951810] parport_pc 00:08: reported by Plug and Play ACPI 
Jun  6 05:42:57 les kernel: [   37.951855] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
Jun  6 05:42:57 les kernel: [   38.025036] cs53l32a 0-0011: chip found @ 0x22 (ivtv i2c driver #0) 
Jun  6 05:42:57 les kernel: [   38.041854] ivtv0: Registered device video0 for encoder MPG (4096 kB) 
Jun  6 05:42:57 les kernel: [   38.041873] ivtv0: Registered device video32 for encoder YUV (2048 kB) 
Jun  6 05:42:57 les kernel: [   38.041890] ivtv0: Registered device vbi0 for encoder VBI (1024 kB) 
Jun  6 05:42:57 les kernel: [   38.041906] ivtv0: Registered device video24 for encoder PCM (320 kB) 
Jun  6 05:42:57 les kernel: [   38.041908] ivtv0: Initialized card #0: Adaptec VideOh! AVC-2010 
Jun  6 05:42:57 les kernel: [   38.041923] ivtv:  End initialization 

Under system/preferences/Multimedia-system-selector/video - ¨Output works¨ - ¨Input¨ - lists Adaptec Videoh! PCI AVC-2010 .
Under input/plugin ¨Test¨ = [COLOR="Red"]test card works[/COLOR] - Under Video for Linux (v4l) gives ¨[COLOR="Blue"][COLOR="Red"]Video for Linux (v4l): Could not read from resource[/COLOR][/COLOR]¨

Have spent many days over the last 9 months trying to find an answer but post are about TV cards or movie cameras. 
From these I have installed (ivtv-sourde/ivtv-utils/libvideo-ivtv-perl/xserver-xorg-video-ivtv/ogmtools/dvgrab/Draw 1394 + raw1394dev) Still does not work but has reduced errors about (¨[COLOR="Red"]stream_out_transcode error: cannot create chain[/COLOR]¨) In VLC message log using /dev/video0. Now reads:- 

[COLOR="Red"]v4l error: mmap unsupported[/COLOR] 
main warning: resampling stopped after 8784363 usec (drift: 46) 
main warning: output date isn't PTS date, requesting resampling (46380) 
main warning: buffer is 45585 late, triggering upsampling 
main warning: re sampling stopped after 6132431 usec (drift: -57) 

From what I have read (a lot of it goes right over my head at the moment) mmap (what ever that is!) is not surported in VLC, that being the case can anyone suggest how I can make use of my ¨Videoh! PCI AVC-2010¨ or another way of transferring the files from my PVR.

Would very much appreciate any help you can give me, only thing keeping XP on hard drive. 
May the penguin be with you, Les

---

### Post by xc3RnbFO8P on 2008-06-11
Try Tvtime in Add/Remove (All Available Application)
This card is supported:
[http://www.ivtvdriver.org/index.php/Supported_hardware]("http://www.ivtvdriver.org/index.php/Supported_hardware")

---

### Post by lizzie2 on 2008-06-11
> **Ringi said:**
> Try Tvtime in Add/Remove (All Available Application)
This card is supported:
[http://www.ivtvdriver.org/index.php/Supported_hardware]("http://www.ivtvdriver.org/index.php/Supported_hardware")
Hi Ringi,
Thanks for your reply.Will give it a try and get back to you.
Les

---

### Post by lizzie2 on 2008-06-11
Hi Ringi,
Installed Tvtime but get error message:-

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
[COLOR="Red"]videoinput: Card failed to allocate capture buffers: Invalid argument[/COLOR]
Les

---

### Post by xc3RnbFO8P on 2008-06-11
My mistake:
> Tvtime
The ivtv driver supports cards that provide high quality MPEG2 encoded video. This cards are ideal for PVR systems. However, tvtime has no MPEG2 decoding capabilities or audio playback code, and therefore cannot be used to watch live TV from these cards.

---

### Post by lizzie2 on 2008-06-11
Hi Ringi,
Thanks for the post.
No problem,gives me somthing else to look into.
What searching brings up is TV cards in the main, where as this is just a capture card (no tv). On the other hand it maybe that one of the TV software will work.
Les

---

### Post by xc3RnbFO8P on 2008-06-11
You can try Mythtv.

---

### Post by lizzie2 on 2008-06-12
Hi Ringi,
Thanks for that, will into it.
Mythtv does list the ¨Videoh! PCI AVC-2010¨ capture card¨
but will take me a few days to check it out.
Les

---

### Post by terry_opie on 2008-12-09
Any luck finding a way to capture video on this card??  I've had this card for several years now, used it in Windows when I first got it, and moved it to my new machine, and then never used it.  Been using Ubuntu for a while now, and just remembered it was in my machine... It would be nice to be able to convert some old VHS to DVD before the tapes fall apart.  :)

---

### Post by lizzie2 on 2008-12-15
Hi Terry,
I still have had no luck with this.I tied Mythtv but it reconized the card but because it was not a TV signal would not record.
I did find a post with a command line code but it only recorded the sound. ( I have been unable to find the command, sorry.)
Les

---

### Post by sdowney717 on 2009-10-11
you can capture video to this card with vlc or mplayer.
it is just a v4l device usually video0

from terminal type vlc /dev/video0

i can also record to mpg with vlc. enable by clicking view advanced controls
it will give you a red record button.

the card works well, nice picture and sound. the default is svideo in. anyone know how to change it?

in xp, the default is composite in.

---

