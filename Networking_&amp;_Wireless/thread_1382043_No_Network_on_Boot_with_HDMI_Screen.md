---
title: "No Network on Boot with HDMI Screen?"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Azureon2 on 2010-01-15
Hi,

I've been experiencing a really strange issue regarding networking.  I just installed Ubuntu 9.10 for use as a server/media box, which is connected via HDMI to a TV.  Everything seems to be working fine, but there's one peculiarity: the machine doesn't connect to the network (so I can't SSH to it or anything) until it loads on the HDMI display.  While it's not a big deal to turn on the HDMI display and wait for Ubuntu to show GDM, I was wondering if anyone knows why I'd have to start up GDM for the machine to connect to the network, and if there's a way to fix it.

I did notice after unplugging the HDMI cable and rebooting that networking started without any trouble after boot.  But it's also not very convenient to have to unplug the HDMI cable every time booting!

Not sure if it's relevant, but the graphics card is an ATI Radeon HD 4350, and I'm using the binary ATI driver (otherwise HDMI doesn't work).

Thanks for your help.

---

### Post by KarlIvan on 2010-01-15
i dont know for a fact, so dont quote me on this...but i assume it has something to the boot process from what it sounds like if i hear you correctly

most likely, the processes involving display start up before the ethernet card. i assume that when hdmi is hooked up, it creates a larger overhead to start, and it just takes a little longer to finish than regular vga (assuming thats what it is otherwise). after its finished starting up, the rest of the processes finish. as you did say, the network eventually comes up, it just takes longer with the hdmi hooked up

---

### Post by Azureon2 on 2010-01-15
> **KarlIvan said:**
> i dont know for a fact, so dont quote me on this...but i assume it has something to the boot process from what it sounds like if i hear you correctly

most likely, the processes involving display start up before the ethernet card. i assume that when hdmi is hooked up, it creates a larger overhead to start, and it just takes a little longer to finish than regular vga (assuming thats what it is otherwise). after its finished starting up, the rest of the processes finish. as you did say, the network eventually comes up, it just takes longer with the hdmi hooked up

I think you are right that the HDMI display is in the boot sequence before networking, but the networking does not ever start until the display is turned on.  I waited for quite a while and still was not able to connect over the network, then turned on the HDMI display and immediately was able to connect.  So the HDMI is hanging the startup process, it looks like.

Is there a way to change the startup sequence so that networking is before whatever might be managing the HDMI?

---

### Post by KarlIvan on 2010-01-15
there is, but you have to be careful what you modify. i dont have a linux machine at home to look at (i only like to use linux at work, at home its windows all the way!), but if memory serves, its the rc.1, rc.2...rc.n files that you would need to modify, as those are scripts that are run when your machine starts up. in order for me to look and see for myself what would need to be done, youd have to wait until monday though lol

---

