---
title: "Remote Desktop Viewer doesn't work"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by lb4406 on 2010-09-18
Hello everyone,

I have Lynx, trying to connect to a tightvnc server on a Win7 box on my LAN.

Server IP: 192.168.1.42:5900

The remote desktop window just goes black and pops up a dialog saying connection closed every time.

However VNC works fine as I installed xtightvncviewer as an alternative and that connects, and I can view the Win7 desktop and control it and do everything you would expect.

I've also tried connecting using Android VNC viewer from my phone on my LAN and that also works fine so it appears to be an issue with Remote Desktop Viewer.

Incidentally using R.D.V. on Intrepid into a tightvnc server on my old XP box worked fine.

Anyone any ideas?

---

### Post by lb4406 on 2010-09-20
bump

---

### Post by perspectoff on 2010-09-20
I think I had the same problem with the TightVNC server on Linux.

(I also prefer UltraVNC server on Windows machines because UltraVNC's file-transfer capability is superior to TightVNC's).

I now use X11VNC server on (K)Ubuntu Linux, which I find to be superb. It is fast, reliable, and clean. It supports compression (for faster transmission times) and can be set up to run as a single-use server or can stay running in the background.

Of course, I always use VNC through an SSH tunnel, but that is independent of the server (or client) software.

I can use any client to connect to X11VNC server. Since I happen to be a Kubuntu user, I use KRDC as a VNC client (although I have also used Vinagre in Ubuntu). From Windows machines I use either TightVNC or UltraVNC as the client.

---

### Post by perspectoff on 2010-09-20
It seems I have misunderstood your question. You are looking for support for the app Lynx, which I have never heard of.

Clearly you identified a VNC client that works for you (XTightVNCViewer) and now you just want support for Lynx. Doesn't Lynx have its own support?

---

### Post by lb4406 on 2010-09-20
My fault I abbreviated incorrectly, I meant Lucid - as in "Lucid Lynx" - Ubuntu 10.04LTS the version I had before I upgraded to 10.10 Maverick Meercat.

Remote Desktop in 10.04 connected to TightVNC in XP fine with no problem, as it did in every version going back to intrepid.

After replacing my XP machine with Win 7 machine and installing the latest tight VNC and upgrading all my other ubuntu boxes to 10.10, the remote desktop app in 10.10 no longer connects. I originally thought it was a Windows 7 problem or firewall problem within Windows, until I realised I could actually connect using other VNC clients.

The Windows Machine is always the VNC server in my setup and I'm using Ubuntu machines as clients and its only in a LAN enviroment, not worried about external net access yet.


Cheers!

---

### Post by lb4406 on 2010-09-21
Bumping again

---

### Post by polarbear10 on 2010-09-21
You're not the only one to see this - I'm having the same problem.  I've verified that I can connect to the win7 client from screensharing on a mac so I know tightvnc on the pc is setup correctly.

Using the remote desktop view with tightvnc on win7 results in an immediate disconnect before requesting the password.

Oh well - onto another vnc client for now - bug report please!

---

### Post by bruno.braga on 2010-09-24
Just to leave my experience on this... with the 10.10 still in beta, it is unfortunate that Remote Desktop Viewer (a.k.a. vinagre) is not working... I really like it.

To workaround the problem, for now, I am using the:
```

# install
sudo apt-get install xtightvncviewer

# execute
vncviewer 192.168.1.1::5900

```

This one works great, but with additional settings (like, I wanted to create a desktop icon and click on it without password), you will need the whole vnc package:

```

# install
sudo apt-get install vnc4server

```

with this you will have access to applications like vncpasswd, used to store passwords for automating the connection from interface level.

But I would say that the official release promises to be fixed... let's wait and see.

---

### Post by lb4406 on 2010-09-24
Thanks I'll try that until I wait for the fix - At least I know its a bug and not something I'm doing now!

---

### Post by comthre3 on 2010-10-11
I've recently upgraded from 10.04, but unfortunately the issue isnt fixed as of yet. any workarounds. couldnt get vnc4server nor tightvnc to work either. any help would be appreciated
thanks

---

### Post by ckkoba on 2010-10-11
Delete

---

### Post by luvshines on 2010-10-13
See if this helps:
[http://ubuntuforums.org/showthread.php?t=1593398](http://ubuntuforums.org/showthread.php?t=1593398)

---

