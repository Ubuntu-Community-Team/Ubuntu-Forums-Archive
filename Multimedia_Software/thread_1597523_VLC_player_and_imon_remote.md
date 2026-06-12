---
title: "VLC player and imon remote"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Thiasder on 2010-10-15
Hello,

I have a Antec Veris Multimedia Station Elite together with RM200 remote. After installing Ubuntu 10.10 I was already able to move the mouse cursor with the remote "pad" - very good. I have installed also Mythbuntu Control Centre to choose the correct remote Soundgraph iMON Antec Veris. This triggered the install of lirc. Afterwards MythTV was working very well with the remote.

Now I am trying to get the remote to work with VLC player. I have activated the IR interface in VLC player preferences and set the correct path for the /.lirc/vlc file. However VLC does not react on any button except the "select" button on the remote, which is strangely mapped to the play-pause function in VLC. 

I have tried ```
vlc -I lirc
``` as suggest in another post and got the following response:

```
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x93190d4] lirc interface error: lirc initialisation failed
[0x93190d4] main interface error: no suitable interface module
[0x9267914] main libvlc error: interface "default" initialization failed
```I have checked that lircd is running.


Do you have any suggestions how to dig deeper to get VLC to work with the remote?

Best regards



PS: Another question is why i get no IR codes via irw although the remote works correct, i.e. I see the cursor moving on screen while using the "pad"?

---

### Post by Thiasder on 2010-10-16
Stopping lircd and then running irw does only show "connect: Connection refused"

---

