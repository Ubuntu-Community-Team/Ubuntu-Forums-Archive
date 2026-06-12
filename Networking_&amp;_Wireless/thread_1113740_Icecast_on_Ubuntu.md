---
title: "Icecast on Ubuntu"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Plasma_Snake on 2009-04-01
Hi everybody, I'm new to the forum and n00b to OSS stuff, been a M$ slave till Ubuntu liberated me. ;) Now as I'm an Engineering student, in my last semester, as my minor project, I installed and configured various servers in R.H.E.L 5 This year in addition to those servers, I also want to setup an Icecast based web radio server, all in Ubuntu. For this I was referring to the Linux Toys 2 e-book and there the author hasn't mentioned anything much about needed packages except that they are all available in his CD.:mad:
I want your help guys, in installing and configuring this server so please start by telling me as to what all the packages I'll be needing for this?

---

### Post by freonchill on 2009-04-02
dont know if there is a ubuntu deb package, but there is this

[http://www.icecast.org/](http://www.icecast.org/)

---

### Post by pieisgood4589 on 2009-04-02
You could download the .exe for Windows computers, and then run it in Wine from Ubuntu. Wine is simply a Windows emulator, and works very well.

1. Click on Applications
2. Click on Add/Remove
3. Next to the top, it says "Show" and options, click on "All available applications"
4. Search "Wine" and download/install it
5. Right click on the .exe to install Icecast you downloaded earlier and select Open With--> Wine Windows Emulator.

Hope this helped :guitar:

---

### Post by freonchill on 2009-04-02
why not compile the souce for linux ?

from the link i posted before
[http://downloads.xiph.org/releases/icecast/icecast-2.3.2.tar.gz](http://downloads.xiph.org/releases/icecast/icecast-2.3.2.tar.gz)

and compile it.

---

### Post by Plasma_Snake on 2009-04-02
Thank u all for quick replies BUT going the Wine way is not the true Linux way so will have to compile the source code but then again How? I dunno jack about this stuff, hell I've few tarballs containing themes of Ubuntu, I dunno how to install them, how can I do such high level tasks like compiling the source code?:confused:
I also found [this link]("http://www.howtoforge.com/linux_webradio_with_icecast2_ices2"), please see it and tell me whether this apt-get method will work for Ubuntu too? :-?

---

### Post by Plasma_Snake on 2009-04-20
OK, now when I run the Icecast2 using /etc/init.d/icecast2 start it runs but when I try to run the Ices2 Source client, it doesn't runs. The error as recorded in the log file is as below:
```

[2009-04-20  19:53:46] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  19:53:46] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  19:53:46] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  19:53:46] WARN playlist-builtin/playlist_read Error opening file "/etc/ices2/music/Guns N' Roses-Paradise City.ogg": No such file or directory
[2009-04-20  19:53:46] EROR playlist-builtin/playlist_read Cannot play same file twice in a row, skipping
[2009-04-20  19:53:46] EROR playlist-builtin/playlist_read Cannot play same file twice in a row, skipping
[2009-04-20  19:53:46] EROR playlist-builtin/playlist_read Cannot play same file twice in a row, skipping
[2009-04-20  19:53:46] EROR playlist-builtin/playlist_read Cannot play same file twice in a row, skipping
[2009-04-20  19:53:46] EROR playlist-builtin/playlist_read Cannot play same file twice in a row, skipping
[2009-04-20  19:53:46] WARN playlist-builtin/playlist_read Too many consecutive errors - exiting
[2009-04-20  19:53:46] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)
[2009-04-20  19:53:46] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  19:53:46] DBUG input/input_loop An instance died, removing it
[2009-04-20  19:53:46] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  19:53:46] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  19:53:46] INFO ices-core/main Shutdown complete
[2009-04-20  19:56:13] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  19:56:13] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  19:56:13] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  19:56:13] INFO playlist-builtin/playlist_read Currently playing "/etc/ices2/music/City.ogg"
[2009-04-20  19:56:14] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)
[2009-04-20  19:56:14] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  19:56:14] DBUG input/input_loop An instance died, removing it
[2009-04-20  19:56:14] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  19:56:14] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  19:56:14] INFO ices-core/main Shutdown complete
[2009-04-20  20:01:00] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  20:01:00] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  20:01:00] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  20:01:00] INFO playlist-builtin/playlist_read Currently playing "/etc/ices2/music/City.ogg"
[2009-04-20  20:01:01] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)
[2009-04-20  20:01:01] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  20:01:01] DBUG input/input_loop An instance died, removing it
[2009-04-20  20:01:01] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  20:01:01] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  20:01:01] INFO ices-core/main Shutdown complete
[2009-04-20  20:02:37] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  20:02:37] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  20:02:37] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  20:02:37] INFO playlist-builtin/playlist_read Currently playing "/etc/ices2/music/City.ogg"
[2009-04-20  20:02:37] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)
[2009-04-20  20:02:37] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  20:02:38] DBUG input/input_loop An instance died, removing it
[2009-04-20  20:02:38] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  20:02:38] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  20:02:38] INFO ices-core/main Shutdown complete
[2009-04-20  20:03:28] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  20:03:28] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  20:03:28] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  20:03:28] INFO playlist-builtin/playlist_read Currently playing "/etc/ices2/music/City.ogg"
[2009-04-20  20:03:28] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)
[2009-04-20  20:03:28] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  20:03:28] DBUG input/input_loop An instance died, removing it
[2009-04-20  20:03:28] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  20:03:28] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  20:03:28] INFO ices-core/main Shutdown complete
[2009-04-20  20:06:28] INFO ices-core/main IceS 2.0.1 started...
[2009-04-20  20:06:28] INFO signals/signal_usr1_handler Metadata update requested
[2009-04-20  20:06:28] INFO playlist-basic/playlist_basic_get_next_filename Loading playlist from file "/etc/ices2/playlist.txt"
[2009-04-20  20:06:28] INFO playlist-builtin/playlist_read Currently playing "/etc/ices2/music/City.ogg"
[COLOR="Red"][2009-04-20  20:06:29] EROR stream/ices_instance_stream Failed initial connect to localhost:8000 (Login failed: Success)[/COLOR]
[2009-04-20  20:06:29] DBUG reencode/reencode_clear Clearing reencoder
[2009-04-20  20:06:29] DBUG input/input_loop An instance died, removing it
[2009-04-20  20:06:29] DBUG input/input_flush_queue Input queue flush requested
[2009-04-20  20:06:29] INFO input/input_loop All instances removed, shutting down...
[2009-04-20  20:06:29] INFO ices-core/main Shutdown complete
```
What is wrong with it and how to rectify it? Please help! :(

---

### Post by Plasma_Snake on 2009-04-21
OK, now the Icecast2 is running, Ices2 is running and Ezstream is also running, now what remains is to provide live feed. I wanted to go the MuSE way but in place of MuSE, APT installed muse, some MIDI thingy. If MuSE can't be installed in Ubuntu then p;ease tell e some other software which can allow me to provide live feed?
The other problem is that, in Windows too, using Oddcast if I try to provide the live feed via Winamp, it keeps on disconnecting. :(
Please help me guys. This is supposed to THE Ubuntu forum and for my last 2 posts I've received no reply. :(

---

### Post by Plasma_Snake on 2009-04-22
No Answers??? :(

---

### Post by stupid_browner on 2009-04-25
I don't believe MuSE is in the default repository. However, they have a deb on their site which you should be able to use. First, uninstall MusE (the "MIDI thingy"), then download and run the deb from [http://muse.dyne.org/?info=download]("http://muse.dyne.org/?info=download").

---

### Post by Plasma_Snake on 2009-05-08
Well thanx for the help, I got it up and running, thank u all. :guitar:

---

### Post by andrewthed on 2011-10-01
> **Plasma_Snake said:**
> Well thanx for the help, I got it up and running, thank u all. :guitar:

HOW DID YOU DO IT?? i still got troubles trying to braodcast live using ices2 i mean both pw are just the same i do not know where i am mistaking....(sorry for my english)
if u can help i would really apreciate it!! :)

---

### Post by OneMixDJ on 2011-12-13
> **andrewthed said:**
> HOW DID YOU DO IT?? i still got troubles trying to braodcast live using ices2 i mean both pw are just the same i do not know where i am mistaking....(sorry for my english)
if u can help i would really apreciate it!! :)


^^^^ Agreed ^^^^

If this is *_supposed to be **THE** Ubuntu forum_* and you got your problem solved, why don't you share your findings with the rest of the community?

---

