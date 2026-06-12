---
title: "VLC doesn't like Lirc - errors"
date: 2010-12-26
forum: Multimedia Software
---

### Post by martygeek on 2010-12-26
[B]no one had answers in general help, so maybe you multimedia types know something...
[/B] 			
 			 			 		   		 		 		I just recently switched over from Fedora to Ubuntu. I am very pleased with Ubuntu with the exception of the VLC ant Lirc operation.

I have Lirc working and can control RythmBox well with my remote.  When I try to do the same with VLC I get nothing.  I get errors when trying to run VLC with the lirc interface :[INDENT] vlc -I lirc movie.avi 
VLC media player 1.1.4 The Luggage (revision exported)
Remote control interface initialized. Type `help' for help.
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8c0a224] lirc interface error: lirc initialisation failed
[0x8c0a224] main interface error: no suitable interface module
[0x8b5b914] main libvlc error: interface "default" initialization failed
status change: ( stop state: 0 )
status change: ( quit )
[/INDENT]If I try the extraintf, I can similar errors, but then locaization fails (I use korean fonts for subtitles)
[INDENT]marty@koreaboy:~$ vlc --extraintf lirc Desktop/Movies/5.0-Eat\ Pray\ Love.2010.R5.LiNE.Xvid\ \{1337x\}-Noir/Eat\ Pray\ Love.2010.R5.LiNE.Xvid\ \{1337x\}-Noir.avi 
VLC media player 1.1.4 The Luggage (revision exported)
[0x9423e44] lirc interface error: lirc initialisation failed
[0x9423e44] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x938c914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb5e6b0d4, 0xb5e6b04:cool:
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1293739734)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:30661): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
[/INDENT]I can run it without errors if I use vlc -I rc, but the remote still doesn't work.

Any ideas what I should be doing differently?

Thanks,
Marty

---

### Post by mastapat11 on 2011-11-01
[SIZE=4]BUMP![/SIZE]

I'm having the exact same issue.  Ever since i upgraded from 10.04 to 10.10, lirc hasn't worked.  since then i've gone from 10.10 -> 11.04 -> 11.10 and it is STILL broke!! :mad:

The only thing i noticed that might help is that there is no */dev/lirc* but there is

[I]crw-------   1 root root 248, 0 2011-10-31 23:25 /dev/lirc0
lrwxrwxrwx 1 root root     19 2011-11-01 05:43 /dev/lircd -> /var/run/lirc/lircd=[/I]

i tried ```
sudo ln -s /dev/lirc0 /dev/lirc
``` But that does nothing but allow *irrecord* to work.
vlc still fails to start w/ lirc, rhythmbox has 5 buttons working.

also, _irw_ & _irexec_ show nothing on the **cli** when i press buttons, but they did in Lucid.

Anybody know how to fix this, or at least has it working in Onciric??  :confused:

---

### Post by ult_avatar on 2012-01-26
hi I just stumbled on this topic while looking for something else..

Well I've had a similar problem this weekend when I upgraded my Ubuntu to a kernel version past 2.6.35. So I thought I might share my revelations with you :) 
After a couple of hours I found out the following: almost all the LIRC modules are now part of the kernel and do not present themselves as devices but as events (eg. keyboard, mouse). LIRC itself is not needed anymore - nor is it functional. The "new" way now is to use things like inputlirc, ir-keytable and similar to provide the functionality that LIRC has done before. Also, the package lirc-modules-sources is completely obsolete and might even break something.

Since I upgraded a working (though out of date) Karmic system to Lucid LTS(+ backports and updates) I had to revert back to a lower Kernel (2.6.32) since I did not want to be bothered to work out exactly how iniputlirc, ir-keytable and the whole "events" thing works.

But since this is now upstream (2.6.35+) I will have to figure out how this works, but not with my Meadiacenter. I will use an old laptop with an IR Port to figure it out.

---

