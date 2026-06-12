---
title: "Strange problem with VLC"
date: 2011-01-24
forum: Multimedia Software
---

### Post by maiandros on 2011-01-24
Hello mates and many Wishes for the New Year!
I`d like to start with an apology for disturbing you with my question to come and thank u in advance regardless the fact if u find some time to answer or not!
Anyway,i m short  of a newbie in the Linux World but i`m really an enthusiast of the kind! The problem is that i still tend to think of Linux as if it was Windows and there is where i mess everything up.
I`d like your opinion on something that i`ve screwed up in my Ubuntu Maverick (64bit). I was trying to reconfigure -for no reason- my VLC and now it just will not open. I`ve tried to complete remove and reinstall it in case that resolves it but in vain! When i m trying to run VLC in a terminal this is what i get : 

VLC media player 1.1.4 The Luggage (revision exported)
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/maiandros/.dvdnav/.map'
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav: DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to srand(1294245719)
Warning: call to srand(-837263553)
Warning: call to srand(-953759192)
Warning: call to srand(-973534609)
Warning: call to srand(-981927247)
[flv @ 0x253b640]Estimating duration from bitrate, this may be inaccurate
[flv @ 0x7f2ac8016960]Estimating duration from bitrate, this may be inaccurate
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f2abaeccb20, 0x7f2abaecca80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5580): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[0x2597ea0] skins2 interface: skin: subX  author: Martin Poehlmann
[0x17e8120] main libvlc: Esecuzione di vlc con l'interfaccia predefinita. Usa 'cvlc' per utilizzare vlc senza interfaccia.
[0x1aabff0] qt4 interface error: cannot start Qt4 multiple times
[0x1ad68a0] qt4 generic error: cannot start Qt4 multiple times
[0x1aabff0] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x1aabff0] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x18d4440] main playlist: end of playlist, exiting
Blocked: call to sigaction(17, 0x7fff85f95b90, 0x7fff85f95af0)
Blocked: call to sigaction(17, 0x7fff85f95af0, (nil))
 
Do you guys have any idea what`s wrong and how can i fix it???

Thank you so much again and sorry for being such a pain !!!!

---

### Post by Yellow Pasque on 2011-01-24
> [0x1aabff0] qt4 interface error: cannot start Qt4 multiple times
VLC seems to think it's already running. If you log out, does it help?

---

### Post by maiandros on 2011-01-24
> **Temüjin said:**
> VLC seems to think it's already running. If you log out, does it help? 

It`s not something that just happened...i`m trying to deal with this problem more than one month or so...whatever,yes,i`ve tried to log out,i have tried to uninstall and then to complete remove anything that has to do with VLC and then install it back...but nothing!!!! I admit that i haven`t touched at all the QT4...it seems too complicated and it gives me the creeps;)!

---

### Post by ajgreeny on 2011-01-24
Delete the vlc configuration folders from your home, which are possibly in three places.  You may or may not have all of them, but search around and delete any you find.  Mine are in:-

/home/user/.cache/vlc
/home/user/.config/vlc
/home/user/.local/share/vlc

These folders are all in hidden folders so hit Ctrl+H if you can't see any of them, then reinstall vlc if you have it still removed.

---

### Post by Claus7 on 2011-01-24
Hello,

searching a little bit on the net, from the errors you are getting I came up with this:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

check this out, install what it proposes and see what you can get... No personal experience on that I should say...

&#922;&#945;&#955;&#942; &#967;&#961;&#959;&#957;&#953;&#940; &#954;&#945;&#953; &#963;&#949; &#963;&#941;&#957;&#945;,
Regards!

---

### Post by mc4man on 2011-01-24
you may have set vlc to use the skins2 interface w/ a skin that won't work.
You can either remove the vlcrc file in ~/.config/vlc or simply from the terminal
```
vlc -Iqt4
```
when vlc opens Tools > Preferences >  Interface  and enable the 'Use native ..' (qt4

Edit: if not the above than try removing the complete vlc folder in 
~/.config
(home folder > View > show hidden files, scroll down and you'll find the .config folder

---

### Post by maiandros on 2011-01-24
Ok! I just had to uninstall it and erase every folder of vlc. 
Now it seems to be working just fine...
A huge thank u to all of ya guys!!!! :KS

ps: i think u ll be hearing from soon again...i feel i ll mess something up  again!;)

---

