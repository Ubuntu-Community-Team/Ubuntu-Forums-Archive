---
title: "Karmic can't play mpg, wmv only sound plays, no video."
date: 2009-11-13
forum: Multimedia Software
---

### Post by Erik765 on 2009-11-13
I've recently installed Karmic 64 bit after using Jaunty 32 and since have noticed it doesn't like to play media files.

When using kaffeine or dragon player, it opens the file, but I only hear sound and no video plays.


When using VLC, I get this output for a .mpg file:

> erik@Desktop:~/Desktop$ vlc 1.mpg
VLC media player 1.0.2 Goldeneye 
[0x1909b88] main interface error: no interface module matched "globalhotkeys,none"                                              
[0x1909b88] main interface error: no suitable interface module  
[0x16b8888] main libvlc error: interface "globalhotkeys,none" initialization failed                                             
[0x16b8888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                       
[0x1b83008] pulse audio output: No. of Audio Channels: 1        
[0x1b83008] pulse audio output error: Failed to connect to server: Connection refused                                           
[0x1b83008] pulse audio output error: Pulse initialization failed                                                               
QPainter::begin: Paint device returned engine == 0, type: 1     
QPainter::setClipRegion: Painter not active                     
QPainter::setClipping: Painter not active, state will be reset by begin                                                         
QPainter::begin: Paint device returned engine == 0, type: 1     
QPainter::begin: Paint device returned engine == 0, type: 1     
QPainter::setClipRegion: Painter not active                     
QPainter::setClipping: Painter not active, state will be reset by begin                                                         
QPainter::begin: Paint device returned engine == 0, type: 1     
[????????] x11 video output error: X11 request 132.19 failed with error code 8:                                                 
 BadMatch (invalid parameter attributes)                        
X Error of failed request:  BadMatch (invalid parameter attributes)                                                             
  Major opcode of failed request:  132 (XVideo)                 
  Minor opcode of failed request:  19 ()                        
  Serial number of failed request:  101                         
  Current serial number in output stream:  102                  
Cannot find libdbus-1 in your system to resolve symbol 'dbus_connection_close'.                                                 
Aborted


and this output from a .wmv

> erik@Desktop:~/Desktop$ vlc 2.wmv
VLC media player 1.0.2 Goldeneye 
[0x12d0a98] main interface error: no interface module matched "globalhotkeys,none"                                              
[0x12d0a98] main interface error: no suitable interface module  
[0x107f888] main libvlc error: interface "globalhotkeys,none" initialization failed                                             
[0x107f888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                       
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
[0x7f1204237bd8] pulse audio output: No. of Audio Channels: 2
[0x7f1204237bd8] pulse audio output error: Failed to connect to server: Connection refused
[0x7f1204237bd8] pulse audio output error: Pulse initialization failed
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

Haven't tried other media types, but am guessing it will do something similar.

Any ideas here? Is it pulse audio? Haven't had much satisfying results from pulse audio, but can't seem to uninstall it as easily as I could in Jaunty.

So far this is about the only thing I've had problems with in Karmic.

Please let me know ;)

---

### Post by andrew.46 on 2009-11-13
Hi Erik765,

You seem to have a problem with your selected video out in both cases:


```
[????????] x11 video output error: X11 request 132.19 failed with error code 8: 
```

Have you tried selecting a different setting for this? Available options should be seen from:

Tools --> Preferences --> Video --> Output

All the best,

Andrew

---

### Post by Erik765 on 2009-11-13
Thank you.
I chose OpenGL as the output mode and it worked fine... wonder why Xine doesn't work though?

---

### Post by andrew.46 on 2009-11-13
Hi Eril,

> **Erik765 said:**
> I chose OpenGL as the output mode and it worked fine... wonder why Xine doesn't work though?

Great news. I am not familiar with Xine unfortunately, but you will be able to adjust MPlayer/SMPlayer in the same way. Any Xine users here?

All the best,

Andrew

---

### Post by benvantende on 2009-11-16
I have absolutely no video in no application (miro, vlc, kaffeine). It seems to have something to do with the nvidia 190 driver. I can't seem to solve this. I have 64bit Kubuntu if that makes any difference. This is the closest post I can find. The problem does not seem to be very common. I installed every package with xine in it but still no go.

Any help would be greatly appreciated. Would not want to do a new install. That just does not make sense.

tHNx

ben

---

### Post by yozgoesdigital on 2009-11-20
As far as I understand you now overrule the default setting of the systems in every program separate.(correct me if I am wrong)
If that is the case isn't there a way to change the systems default so you do not have to change it for every program separate?

Because I encountered a similar problem (kubuntu-netbook 9.10) If I change the output for the programs to x11 they work fine.

@benvantende Did you try different outputs for the programs (eg. for vlc --> tools --> preferences --> video output) as describe earlier?
Which file formats did you try?

Thanks, YOz

---

