---
title: "Weird headless behaviour... (DELL GX520 Media Server)"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by ricardoph on 2010-05-29
Hi everybody,

First I'd like to say thank you for letting me participate in this community.

I've been a mac user for years as it's been pretty much the sole alternative for what I do. I'm happy with it when it comes to applications and workstations. However, with their prices, all I can afford is a single workstation, for my other needs, I've always relied on Windows PC's or old macs, such as for print servers, file servers, music libraries, etc... The use I give to this server is very simple:

-Having the same interface as my workstation, and using Screen Share or VNC, I just drag and drop files from here to there.
-I download torrents while I'm on the way
-I have 3 printers and 1 plotter connected
-I placed 2 shared folders for guests and my workgroup
-I used it as my media vault for 2 networked media players

Currently I have a mac mini doing that job, it has OSX Tiger and I control it via screen share (Apple's VNC client), and it works fine, but it has reached a point on which I cannot put more USB drives and the information flow is too big for it to operate properly.

So I got this Dell GX520 from a bid website in Chile for 180 USD, I added 2 gb of RAM, 2 x 1 TB hard drives, and of course... Ubuntu 10.04. It works like a charm as a desktop machine, torrents run great, I now can do a preview of the movies that I'm downloading, which was impossible with the Mac Mini G4, while sending jobs to all the printers and with the torrent running at its maximum.

BUT.... (and there's always a but of course)... When I attempted to disconnect the display and everything to put the machine on the closet, with just the power cord and the ethernet cable, it refused to boot... or at least I couldn't connect to it via VNC on my macbook.
Then I turned it off, did connect the display and the keyboard/mouse, and booted normally, after that, I just unplugged everything but the ethernet and the power, and voila!, it works headless.... but what if a blackout occurs while I'm not at home (which is 70% of the time).

Everything's fine, the GUI is the one that Ubuntu desktop installs by default, I configured the system to start with the VNC server on, the torrent, etc.... it's just it won't boot without a display and keyboard/mouse.... weird, isn't it????

I'm not into Linux stuff, in fact I'm scared of command lines, I'm just an engineer that enjoys exploring, and the UBUNTU concept, has caught my attention long time ago....

Don't get me wrong, I'm really happy with the machine as it is, I only need to know where to click to get it boot normally without "head and arms".

Thanks in advance and best Regards,

PS.: On my macbook I have VNC Viewer, and on the Ubuntu almost/headless machine, the client it has by default....
PS2.: Judging by the posts I've already read, I know you'll probably laugh on my background, and I'm aware of how stupid I am on this field, but who wasn't on the beginning?

---

### Post by croto on 2010-05-30
Troubleshoot mode -

1) Does it boot at all when you disconnect keyboard and monitor?
2) If it does, does it respond to pings? Can you ssh to it?

A) If you boot *with* keyboard and monitor, but you don't log in, can you connect to it with vnc?

---

### Post by ricardoph on 2010-07-24
Hey Croto....

Never received a notification of your answer, hope my late thanks still work...

Anyway, I found out that -like windows- the system won't start the GUI without detecting a monitor, the solution? easy:

1) Connect a monitor for the booting in case you're sure you won't have any power issues...
2) A little more complex, but the solution that works under any conditions, is to create a dummy monitor, with a few resistance and a female DB25 connector, you can fool the video card and tell it a SVGA monitor is hooked up. I took the instructions from this post [http://www.xtremesystems.org/forums/showthread.php?t=200444 ]("http://www.xtremesystems.org/forums/showthread.php?t=200444")

The thing works like a charm, and it only costs less than a dollar.....

:D

So, yes, the people afraid of command lines, can still have their server and manage it like a regular desktop....

---

