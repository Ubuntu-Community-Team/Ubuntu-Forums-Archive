---
title: "Vlc Crash"
date: 2010-11-26
forum: Multimedia Software
---

### Post by Mr.Exc3llent on 2010-11-26
i have just changed something in preferences for Skins.
then i restarted my vlc media player and now i cant run vlc !
i removed and reinstalled vlc Thousand times but it didnt work !
when i type vlc in Terminal :

exc3llent@exc3llent:~$ vlc
VLC media player 1.1.5 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb752a0d4, 0xb752a048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1289860942)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:13965): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[**[COLOR=Lime]0x86ee1b4[/COLOR]**] vcdx access error: **[COLOR=Red]fread (): Is a directory[/COLOR]**
[**[COLOR=Lime]0x85a4aac[/COLOR]**] xml xml error: **[COLOR=Red]XML parser error (line 2) : Validation failed: no DTD found ![/COLOR]**
[**[COLOR=Lime]0x858db84[/COLOR]**] skins2 interface error: [COLOR=Red]**no skins found : exiting**[/COLOR]
Blocked: call to sigaction(17, 0xbfbfb4d8, 0xbfbfb44c)
Blocked: call to sigaction(17, 0xbfbfb44c, (nil))

pls help me!
sry for bad english :x

---

### Post by mc4man on 2010-11-26
use this to start vlc and then swicth back to 'native' interface
```
vlc -Iqt4
```
or 
vlc --reset-config

Most skins are hit or miss, many features aren't available in them and you'd need a skin(s) installed to use in the first place

---

### Post by Mr.Exc3llent on 2010-11-26
> **mc4man said:**
> use this to start vlc and then swicth back to 'native' interface
```
vlc -Iqt4
```or 
vlc --reset-config

Most skins are hit or miss, many features aren't available in them and you'd need a skin(s) installed to use in the first place

Oh ! : x
Thank u, Fixed ! :D

---

