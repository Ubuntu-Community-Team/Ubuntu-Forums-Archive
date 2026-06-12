---
title: "Fix that slow VNC Connection!"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by ricojonah on 2009-10-29
**BACKGROUND: **
Every Ubuntu 9.04 Jaunty and 9.10 Karmic system comes with a VNC server and Client (vino for the server, and both vinagre and tsclient for the client). The problem I've noticed is that every VNC session I've used with Ubuntu's default VNC server/client tools has had a noticeable amount of sluggishness. The slowness is extremely noticeable when a VNC server is connected to over low-bandwith connections (weak wireless LANs, ISP plans with less than 512kbps for upload bandwidth). This has been an ongoing issue for several months, and I've seen many, many users reporting the same problem.

**DISCLAIMER: **
This is a *possible* workaround/solution for the problem. (I say [I]possible[I] because I'm no expert with the guts & entrails that make vnc function on Ubuntu, but this solution worked for me).

**POSSIBLE CAUSE: **
By default, Ubuntu uses **vino** for the VNC server, and two different clients for connecting to it: **vinagre**and **tsclient (Terminal Server Client)**.

Unfortunately, the default VNC clients appear to use a lot of bandwidth during VNC sessions. The primary reason for this is that neither**tsclient** nor **vinagre**, provide a means to configure the compression levels of the VNC session (at least not on the GUI). By default, both clients appear to assume a very low (or no) compression, causing the VNC sessions to eat up a lot of bandwidth.

Vino, as the vnc server, is capable of serving a low-bandwidth/high compession vnc session, so replacing vino with something like tightvncserver is NOT necessary.
[B]
POSSIBLE SOLUTION:[/B]
I just tested this on two of my home computers: Try using a different vnc client instead of tsclient or vinagre. 

1) I installed xtightvncviewer, which is installable using apt-get or synaptic. It is command-line based, but it supports the ability to set the compression level of the VNC connection. (If anyone knows of a GUI-based VNC client for Ubuntu that allows you to set compression levels, please post! :D ).

2) I connected to my VNC server (from my client, using xtightvncviewer) using this command in a terminal window:

```
xtightvncviewer -compresslevel 9 192.168.1.20
```

Note: the *-compresslevel 9* option specifies the maximum level of compression (it's a noticeably lower quality, but uses MUCH less bandwidth and is still decent & very useable). Of course, you'll want to replace *192.168.1.20* with the actual IP address or hostname of the VNC server you're wanting to connect to.

You may be prompted for your VNC password within the terminal, if configured for one on your VNC server.

3) That's it!

Please post if this resolves anyone's issue with the slow VNC connection. It worked for me, and I'd love to know if it helped someone else too.

As an afterthought, this problem seems like a pretty silly one to me. Why does neither tsclient nor vinagre provide a GUI option to set the compression levels? Almost every other VNC client I've seen allows this, and this is absolutely essential for anyone wanting to remote over a low-bandwidth or WAN connection). 

Also, I've noticed some threads and tutorials suggesting that the vino VNC server needs to be replaced with a different VNC server to get better low-bandwidth performance. I'm not sure why anyone would think that's necessary--Vino's very well-integrated and supports low-bandwidth/high-compression sessions; it's the clients that appear to be the problem.

Please post your thoughts, results, and suggestions. Thanks!

---

### Post by Darkmoon_UK on 2010-01-05
...good advice on improving a bandwidth-limited VNC connection; **ricojonah** is definitely right to say that not all VNC clients are built the same, and **xtightvncviewer** seems by far the quickest, even before adjusting the compression. Unfortunately it also suffers from a bit of a weird user interface (scroll bars) and I've recently settled on **xvnc4viewer** as a more usable, close second in performance.

I think its very important to mention another potential problem with VNC which rarely gets mentioned but can catch users out. VNC operates by observing your screens [framebuffer]("http://en.wikipedia.org/wiki/Framebuffer"), then transmitting the differences since the last frame. This means it has to read data back from your graphics cards video RAM - observing the screen almost at the same level as the user. The problem is that many older/cheaper video cards are poorly designed for 'reading back' from video RAM as this is a relatively uncommon task, resulting in appallingly slow VNC performance which is bottlenecked by the graphics card itself, no matter how good a network connection you throw at it. This is discussed, along with instructions for discovering your graphics cards read speed, in [this thread]("http://ubuntuforums.org/showthread.php?t=1097683").

The solution in these cases is one of two things, in my experience:

a) Use **Terminal Server** based software such as NX. This operates in a different and more efficient way, creating a Desktop session with software 'hooks' which observe screen draw commands and transmit these to the client machine. This is the same way that Microsofts RDP works, and no longer involves the graphics card at all. **FreeNX** is [a free implementation]("http://freenx.berlios.de/") of this and has server and client for Windows and Linux. Mac doesn't have server at this time, only client.

b) If you really want to use VNC still, you may just have to replace the graphics card. There is a possible method to speed up VNC on a poor graphics card by using an X server option called **ShadowFB** ([Shadow Framebuffer]("http://www.xfree86.org/current/apm5.html")) where faster system RAM is used to buffer all reads and writes to the graphics card, meaning the VNC server will automatically rely on faster RAM instead. I failed to get this to work and went with NX instead, but that doesn't mean you will. **Note:** I've seen a suggestion in [this post]("http://lists.x.org/archives/xorg/2007-June/024955.html") that the ShadowFB option is deprecated, but Google reveals nothing about the 'miext/shadow' module of which the poster writes.

Good luck in getting that VNC connection how you want it; commanding multiple systems without having to leave your chair allows all of us never-before seen levels of laziness/efficiency :-)

---

