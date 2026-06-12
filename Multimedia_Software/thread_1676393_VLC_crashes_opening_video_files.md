---
title: "VLC crashes opening video files"
date: 2011-01-27
forum: Multimedia Software
---

### Post by beew on 2011-01-27
Hi,

As the title says vlc crashes when trying to open video files. I get these outputs from the terminal.

> VLC media player 1.1.6 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb735e0d4, 0xb735e048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1296432591)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:22153): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0



Please help!

---

### Post by andrew.46 on 2011-01-27
vlc 1.1.6 is only a couple of days old, can I ask where you picked this copy up from?

---

### Post by beew on 2011-01-27
Hi, you can either get it from the Maverick bleed ppa or the  vlc ppa by Ferramosca Roberto on launchpad. [https://launchpad.net/~ferramroberto/+archive/vlc]("https://launchpad.net/%7Eferramroberto/+archive/vlc")

I installed from ferramroberto, the package is fine, I installed it on other machines and it works great. 
Maybe some other updates (probably graphic driver or libraries)  in this machine has broken it, do you have any idea about the error message?

---

### Post by andrew.46 on 2011-01-27
Hmmm.... try disabling 'Accelerated Video Output (overlay), can be found in Tools --> Preferences --> Video. I attach a screenshot to demonstrate the setting.

---

### Post by beew on 2011-01-28
Hi Andrew.

Thanks for saving me again, it turns out that disabling input&codecs > use GPU accelaration works (can keep  the box "Accelerated video output overlay" checked, though it doesn't seem to do anything) What I don't understand is that the box used to be checked and there has been no problem. There was some kernal and library updates yesterday, probably that was what broke it. 

Now vainfo gives the following output:

> libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
Segmentation fault


What does it mean? (I know seg fault is no good..)

I would like to make vlc uses vdpau, is there a tutorial to do that? I know vdpau is enabled because it works flawlessly on xbmc and mplayer. Thanks once again.

---

### Post by andrew.46 on 2011-01-28
Well, looks like I just sent you in the right direction rather than found the right setting to remove :). My knowledge of acceleration with libva is small, but I am aware that it is not exactly mature yet in vlc, although others will disagree. Hopefully somebody more knowledgeable than myself can help you troubleshoot exactly what is wrong with your libva setup...

Andrew

---

### Post by drogve on 2012-07-08
Same problem. I defaulted the VLC setting and its good now

---

### Post by oldos2er on 2012-07-08
Closed. Please don't bump old threads.

---

