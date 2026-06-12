---
title: "VLC media player don't start"
date: 2010-09-14
forum: Multimedia Software
---

### Post by Shellzoy on 2010-09-14
hello
i installed VLC MediaPlayer on my ubuntu 10.04, it'l all ok and seems fine, i went to "applications", "Sound & videos" and "VLC Media Player" and nothing happened.. 
i tried to uninstall VLC Media Player and reinstall it but nothing changed..
someone can help me?

---

### Post by sikander3786 on 2010-09-14
Type vlc in a terminal and press enter. Post back the errors here.

---

### Post by Shellzoy on 2010-09-14
the error:
```
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
```

---

### Post by sikander3786 on 2010-09-14
Are you logged in as root? Is that the default account you use? If so you shouldn't...

---

### Post by Shellzoy on 2010-09-14
how i could connect to the server without to be a root??!
i connect the server with ssh (putty), and VNC.. and in the both ways i'm a root.. how does i make it work??

i'm new with linux.. can toy tell me please what to do to make VLC work??

---

### Post by sikander3786 on 2010-09-14
By using sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Logging in as root is never recommended on Ubuntu. You can use, sudo and gksu for whatever tasks and gain root privileges temporarily.

I think VLC won't be able to run under root account.

---

### Post by Shellzoy on 2010-09-14
when i connect to the server with VNC.. i'm Automatically logged in to the root user.. how can i fix this? 
i create a new user, desktop user, but i can't login to this user in the ssh.. why?
can you guide me please?

---

### Post by sikander3786 on 2010-09-14
See the link for details.

[http://ubuntuforums.org/showthread.php?t=40384](http://ubuntuforums.org/showthread.php?t=40384)

---

### Post by Shellzoy on 2010-09-14
thank you, i solved the problem.
i logged in non-root user through ssh, and start vnc, and then i logged in through vnc and it's logged into the non-root user.

---

### Post by masterman934 on 2010-10-25
Sorry to bump this old thread but I have a similar problem.
Yesterday VLC worked just fine but today when I try to start it I simply can't.
I wrote vlc in terminal and I got this:

marin@marin:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb73ba0d4, 0xb73ba048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1287840849)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2308): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[0x8d154ec] skins2 interface: skin: QuickTime UMX  author: UniverseMatrix
[0x8d154ec] skins2 interface error: video: resize policy and autoresize are not compatible

I'm net to ubuntu and I have no idea what does this means. Can you help me out please?

Thanks in advance,
Marin

---

### Post by mc4man on 2010-10-25
> Yesterday VLC worked just fine but today when I try to start it I simply can't.
Well obviously that skin you installed (QuickTime UMX), doesn't work right.
start vlc from terminal like below, then  go - tools - preferences and switch back to the native interface. ('use native style' or whatever the radio button is in 1.1.4

If trying skins out then look for ones recently built or specific to 1.1.X
(never seen any that maintained full function, though really haven't looked too hard, nor will

```
vlc -I qt4
```

---

### Post by masterman934 on 2010-10-25
Thanks a lot. That worked quite well. :)

---

