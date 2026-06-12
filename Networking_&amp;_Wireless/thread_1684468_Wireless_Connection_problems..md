---
title: "Wireless Connection problems."
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by CarltonSaysHi on 2011-02-09
This is not the common problem that's on the stickied thread. I'm able to connect to my wireless network perfectly. I switch between Windows to game and Linux for desktop, coding, and hosting, so I can tell it has something to do with ubuntu 10.10.

When I'm connected to my wireless network, at random times, my internet begins to slowdown, then I get disconnected from the internet, but the taskbar says I'm connected. This problem only happens in ubuntu and not Windows for some strange reason.

The applications that are usually open do not cause it, because it still does it even though I have little applications open (Google Chrome, gedit). When I'm on Teamspeak 3, I notice my ping rises to the 1000s randomly, and I get disconnected. Once again that only happens on Ubuntu.

How do I fix this problem?

---

### Post by CarltonSaysHi on 2011-02-09
Bump

---

### Post by moaoci on 2011-02-10
Hi Carlton !

Give us a little more info on your hardware.  Open a terminal and post the results of these 2 commands:

lspci | grep -i net
lshw -C network


The first will tell us which network card you got and the second will tell what driver it is using.

After that, someone that knows your hardware will be able to take the lead.

---

### Post by CarltonSaysHi on 2011-02-10
Thanks for a response, finally! Here's my network information.

> 
Bridge: nVidia Corporation MCP61 Ethernet (rev a2)



 description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: BLOCKED
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-25-generic firmware=N/A ip=BLOCKED multicast=yes wireless=IEEE 802.11bg

---

### Post by alinutza20 on 2011-02-10
Hey! I really get how frustrated you are, I had the same problem until today. I *think* I found a temporary solution. After trying all the fixes suggested on various forums (installing backports, using ndiswrapper, even doing a fresh install) and thinking I was going to go insane, I came across a fix. 

SO... Try uninstalling networkmanager and installing wicd instead. Keep in mind that you will need the internet working in order to download wicd. My internet has now been working for a few hours with no apparent problems. I guess I'll stick to this until they manage to find out why so many people have wireless issues.

Good luck and keep me posted!

---

### Post by CarltonSaysHi on 2011-02-17
I've tested it out, and the problem still occurs. BUMP.

---

### Post by CarltonSaysHi on 2011-02-19
BUMP once again, now I'm simply just unable to connect to my network. I have been browsing Google all day. I'm using Linksys adapter.

---

