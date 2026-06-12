---
title: "Dvico Dual Digital 4 Rev2 Failing"
date: 2008-12-05
forum: Mythbuntu
---

### Post by theyallexist on 2008-12-05
Hi All,

I'm Very new to all this, so I will try to be as concise as possible.

Some time ago I purchased this HDTV card and have been unable to get it to work.
I have followed the instructions @ [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)

But am still unable to get it working.

I am using 8.10 with kernal 2.6.27-9

The specific error I get when testing the card is:
matthew@media:/etc/init.d$ mplayer /dev/dvb/adapter/dvr0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) Dual Core Processor 4850e (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: Connection refused
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvb/adapter/dvr0.
File not found: '/dev/dvb/adapter/dvr0'
Failed to open /dev/dvb/adapter/dvr0.


Below is the result of further commands which may assist:
matthew@media:/$ dmesg | grep TV
[   11.322848] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[   11.354110] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[   11.710052] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[   11.710069] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[   11.741308] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[   12.068663] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
matthew@media:/$ 


matthew@media:~$ lsusb
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0fe9:db98 DVICO 
Bus 008 Device 002: ID 0fe9:db98 DVICO 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I really hope someone can point me in the right direction.

Cheers
Matthew

---

### Post by ian dobson on 2008-12-05
Hi,

What device files do you have in /dev/dvb? They should be called something like /dev/dvb/adapter0, /dev/dvb/adapter1.

What permissions do you have for the devices in for example /dev/dvb/adapter0? Do a ls /dev/dvb/adapter0 -o should produce something like:-

@alpha2:~# ls /dev/dvb/adapter0 -o
total 0
crw-rw---- 1 root 212, 4 2008-11-14 11:15 ca0
crw-rw---- 1 root 212, 0 2008-11-14 11:15 demux0
crw-rw---- 1 root 212, 1 2008-11-14 11:15 dvr0
crw-rw---- 1 root 212, 3 2008-11-14 11:15 frontend0
crw-rw---- 1 root 212, 2 2008-11-14 11:15 net0

Regards
Ian Dobson

maybe you just need to try:- mplayer /dev/dvb/adapter0

---

### Post by theyallexist on 2008-12-05
Hi Ian, Thanks for your response.

I tried mplayer /dev/dvb/adapter0 - no luck, the dump is below along with the other suggestion.

Thanks for your quick response.

matthew@media:/dev/dvb$ ls
adapter0  adapter1
matthew@media:/dev/dvb$ ls /dev/dvb/adapter0 -o
total 0
crw-rw----+ 1 root 212, 0 2008-12-05 21:29 demux0
crw-rw----+ 1 root 212, 1 2008-12-05 21:29 dvr0
crw-rw----+ 1 root 212, 3 2008-12-05 21:29 frontend0
crw-rw----+ 1 root 212, 2 2008-12-05 21:29 net0
matthew@media:/dev/dvb$ ls /dev/dvb/adapter1 -o
total 0
crw-rw----+ 1 root 212, 4 2008-12-05 21:29 demux0
crw-rw----+ 1 root 212, 5 2008-12-05 21:29 dvr0
crw-rw----+ 1 root 212, 7 2008-12-05 21:29 frontend0
crw-rw----+ 1 root 212, 6 2008-12-05 21:29 net0
matthew@media:/dev/dvb$ 


matthew@media:/dev/dvb$ mplayer /dev/dvb/adapter0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) Dual Core Processor 4850e (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: Connection refused
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvb/adapter0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)

---

### Post by ian dobson on 2008-12-05
Hi,

But now we've got a step further. Mplayer used to say "file not found" now it can't find "Playing /dev/dvb/adapter0.
Win32 LoadLibrary failed to load: **avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll**"

So it's now finding a video stream but can't play it. I think you now ned to install the win32 codecs. Not 100% sure but that sounds about right.

Regards
Ian Dobson

---

### Post by theyallexist on 2008-12-07
Hi Ian,

Thanks for the response.
I installed the win32 codecs per the instructions here:
[http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html](http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html)

But still no luck, I am still getting the same error.

Cheers
Matthew

---

### Post by ian dobson on 2008-12-07
Hi,

Can you just try enabling the w32codecs in myth control center, install the w32codecs or w64codecs if your running 64bit, reboot then do:-

dpkg -l | grep codec

from the terminal and include the results here. If your getting the same error then it means that the dlls are not being found.

Regards
Ian Dobson

---

### Post by theyallexist on 2008-12-08
Hi,
Still no luck.

root@media:~# dpkg -l | grep codec
ii  libavcodec51                              3:0.svn20080206-12ubuntu3             ffmpeg codec library
ii  libspeex1                                 1.2~beta4-2                           The Speex codec runtime library
ii  libwavpack1                               4.50.0-1                              an audio codec (lossy and lossless) - librar
ii  libxvidcore4                              2:1.1.2-0.1ubuntu3                    High quality ISO MPEG4 codec library
ii  w32codecs                                 20071007-0medibuntu3                  Win32 codec binaries


Cheers
Matthew

---

### Post by ian dobson on 2008-12-09
Hi,

Can you do a 

cat /dev/dvb/adapter0/dvr0 > file.ts and after about 10-15 seconds press control C. This will create a video stream called file.ts. Can you then upload this file to some web space and post a link here. So I can have a look at the file it creates.

Regards
Ian Dobson

---

### Post by theyallexist on 2008-12-09
Hi Ian,
Please find the file here:
[http://users.bigpond.com/thepolsons/file.ts](http://users.bigpond.com/thepolsons/file.ts)

However it doesn't appear to have written any date, I did it twice to makesure of the filesize.

Cheers
Matthew

---

### Post by ian dobson on 2008-12-09
Hi Matthew,

Your right the file is empty. I'm starting to get to the end of my knowledge. Do you have a windows box that you could try the card on (I'm starting to think there's a hardware problem or the linux driver isn't 100% OK.)

Maybe if no one else can help you, we should arrange for me to get ssh access to your box so I can have alook myself if I can see whats wrong. I don't really want to do this but it might be the only solution.

Regards
Ian Dobson

---

### Post by theyallexist on 2008-12-09
Hi Ian,

I have taken a old 40gb HDD out of retirement and installed XP, tonight after work I will install mediaportal and let you know how I go with it.

Thanks for your help,

Matthew

---

### Post by theyallexist on 2008-12-15
Hi all,
Have installed XP with media portal, and after a little playing around with the drivers the card certainly works.
I am re-installing Ubuntu and will have another go this week.

thanks for the assistance Ian.

Matthew

---

