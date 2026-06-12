---
title: "How Can I Activate Wireless Network Interface in Terminal?"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Uber-n00b on 2010-02-26
running 9.10 server, have SSH access through LAN, but I'd like to move box out of my neighbor's (shared internet & the router's in his place) and into my own space. Would have done so already, but I can't get the wireless working. Details below:

[FONT="Courier New"]**lshw -C network**[/FONT] gives:
```
  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       ...
```
and here's my [FONT="Courier New"]/etc/network/interfaces[/FONT] file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
This is a fresh install btw. I'm pretty sure the problem is with [FONT="Courier New"]*-network:0 DISABLED[/FONT] as there's a similar entry for my ethernet card (eth0) that looks the same except missing for a big honking [FONT="Courier New"]DISABLED[/FONT] behind it. How can I enable the wireless network interface? I'm sure I could figure this out on my own if I had X windows running, but I'd like to keep this box GUI-free. I need to jump onto my WPA TKIP wireless network ASAP before complaining from upstairs starts. Thanks in advance.

---

### Post by Uber-n00b on 2010-02-26
After dragging my box downstairs and hooking monitor, I realized that what I had thought was a non-related issue of spotty SSH connectivity appeared to be intertwined with my network problems. Every few minutes (aperiodically) I'd see this message: **[FONT="Courier New"]* Reloading /etc/samba/smb.conf smbd only[/FONT]**. This in turn was restarting OpenSSH service and I was loosing my session. This *related* issue is discussed in [[COLOR="Green"][SIZE="4"]this[/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1140094&page=3") thread. As I use DHCP (with reserved IP addy assigned from router,) Looks like there's a whole mess of diagnosing and troubleshooting I'll have to do.

*Shucks. Well for the time being, I think I'll snake a hard line downstairs. I'd really like to get wireless up and going if anybody has some hot ideas. I fitted a few 120mm fans in the storage part of my TV stand down there and that's where I'd like to eventually put this box. *sigh*

---

### Post by Uber-n00b on 2010-02-27
I think I've found a way to totally circumnavigate this issue. I was just digging through my PC odds and ends, and came across my old wrt54g linksys router. We've moved 2x since I last used it. Anyway, I remember swapping out the linksys firmware for dd-wrt (linux-based opensource alternative) ages ago and recall there being a wireless bridge operation mode. Booted teh thing up, and still works like a charm. 

Guess I'll just plug in via eth0 and pull the wireless card out altogether. Not an ideal sol'n but hey, it'll work. Plus I'll have some spare cat5 jacks and an extra pci wireless card in the end. :D

---

