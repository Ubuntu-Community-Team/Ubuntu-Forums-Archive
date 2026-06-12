---
title: "Sound and gconf2 problems"
date: 2010-11-12
forum: Multimedia Software
---

### Post by tpb261 on 2010-11-12
Hi:

I upgraded from 8.10 to 10.04 and now to 10.10 .After the first I had two problems: sound and USB modems. Thanks to this forum and some forgotten links, I had both working, though the modem detection was flaky. 10.10 has cleaned out the problems with the modem. But left three more (as of now):
First problem is that Sound fails.
```
tpb261@tpb261-laptop:$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset 
High Definition Audio (rev 05)
tpb261@tpb261-laptop:$ aplay -l
aplay: device_list:235: no soundcards found...

```and ```
 sudo modprobe snd<tab> 
``` gives ```

ERROR: modinfo: could not open snd_prob.txt: Exec format error

```I have tried the Comprehensive Sound problem solver or some such name on this forum, on 10.04 and it worked but hasn't with 10.10

The other problem is with login screen. With Gnome installed, there is a gcongf2.4 error. I can get the exact details when I install it again. So I had to Ctrl+Alt+F1 and login on console and start kde from there. Kde wroks fine. But firefox doesn't in kde. So I removed gnome and gconf* using apt-get and firefox worked fine. Through all this Konqueror was working fine, though.
```

tpb261@tpb261-laptop:$ firefox &
[2] 2318
tpb261@tpb261-laptop:$ Gtk-Message: Failed to load module 
"canberra-gtk-module": libcanberra-gtk-module.so: cannot open 
shared object file: No such file or directory
/usr/lib/firefox-3.6.12/firefox-bin: symbol lookup 
error: /usr/lib/libgconf-2.so.4: undefined symbol: g_bus_get_sync

[2]-  Exit 127                firefox
tpb261@tpb261-laptop:$ sudo apt-get --purge remove gconf
gconf2                  gconf2-common           gconf-defaults-service  gconf-editor            
tpb261@tpb261-laptop:$ sudo apt-get --purge remove gconf*

```System is a Acer aspire 5740 laptop.
All help appreciated.
I am not a total Linux newbie but not so familiar with it either.


PS: I am new to forums, so pls do let me know of any mess ups I might have in the post.

---

### Post by tpb261 on 2010-11-12
Sound problem is partially solved using OSS:
[https://help.ubuntu.com/community/OpenSound#Ubuntu%20Intrepid/GNOME%202.24%20%28and%20later%29](https://help.ubuntu.com/community/OpenSound#Ubuntu%20Intrepid/GNOME%202.24%20%28and%20later%29)

But as of yet only Flash is working,, other apps are yet to be configured:( :mad:

---

### Post by tpb261 on 2010-11-13
OSS looks to be working fine. Normal application sounds and Flash are working. Maybe I can ditch pulseaudio and ALSA

---

