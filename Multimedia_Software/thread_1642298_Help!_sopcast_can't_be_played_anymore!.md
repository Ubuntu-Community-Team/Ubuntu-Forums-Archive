---
title: "Help! sopcast can't be played anymore!"
date: 2010-12-10
forum: Multimedia Software
---

### Post by davy.johns on 2010-12-10
Hi everyone,

I got a problem with the sopcast for Linux. I'm using the Ubuntu10.10. I was able to watch the channels this morning but in the afternoon it just didn't work any more. 

The below command ran as normal:

sp-sc sop://117.135.141.178:3920/4841 10000 20000

but I just can't play the content with my vlc:

$ vlc [http://localhost:20000](http://localhost:20000)
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb73dd0d4, 0xb73dd048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1291927838)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2375): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x9851494] main access error: connection failed: Connection refused

and it just stuck in there and not play anything.

I tried to play sth else local and the vlc can play them well. I tried to open the stream by Totem2.32.0 but it also failed. Again the Totem can play other local files successfully. This make me guess that may be it not the player's problem. What make me feel more strange is that it work in the morning then down in the afternoon and during that time no one is using the PC I just left it play the channel. When I came back I found that the screen of the vlc is freezed and after I close the vlc and restart it again the problem came.


Is there anyone can help me with this? Thanks in advance!

---

