---
title: "VLC won't launch"
date: 2010-08-30
forum: Multimedia Software
---

### Post by JoeGoalie on 2010-08-30
When I click on VLC nothing happens.  When I try to run vlc from the terminal I get this:
```
joseph@joseph-desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x1dea808] main interface: creating httpd
[0x1dea808] http interface error: cannot find any file in directory /usr/share/VLC/http
[0x1dea808] main interface error: no suitable interface module
[0x1cef4b8] main libvlc error: interface "http,none" initialization failed
[0x1e0e568] main interface: creating httpd
[0x1e0e568] http interface error: cannot find any file in directory /usr/share/VLC/http
[0x1e0e568] main interface error: no suitable interface module
[0x1cef4b8] main libvlc error: interface "default" initialization failed
```
I changed some http options trying to get VLC remote to work but, somehow I broke it all together.  It still works if I go to actually play a video if I browse to the video itself and launch it.

---

### Post by mc4man on 2010-08-30
Either start vlc in the qt4 interface and adjust your settings (tools - preferences
```
vlc -I qt4
```
or start and reset

```
vlc --reset-config
```

---

### Post by JoeGoalie on 2010-08-30
Excellent.  Thanks, I reset my config and now I can start messing up my VLC all over. :D

---

### Post by mc4man on 2010-08-30
> now I can start messing up my VLC all over

I've always found one of the best almost free tools is good old 'trial & error'

---

### Post by JoeGoalie on 2010-08-30
> **mc4man said:**
> I've always found one of the best almost free tools is good old 'trial & error'

Absolutely.  It's how I've learned nearly everything I've done on computers.  It's usually tough to screw something up to the point of no return.  Thanks for the help.

---

