---
title: "Unable to see any network interface except lo after power failure"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by squigish on 2010-10-25
My laptop lost power in my bag this afternoon; I told it to suspend but it must have gotten hung up somewhere, because an hour later the battery was totally dead, and the computer was quite hot.  

After reconnecting to AC power and rebooting into linux (10.04.1 Lucid LTS), I noticed that I didn't have any internet connectivity.  I ran ifconfig, which only listed my loopback controller.  It did not see either my ethernet interface on eth0 or my wifi card on eth1.  

I tried the usual suspects for getting it running again, including (all run as root)

[LIST]
[*]/etc/init.d/networking restart
[*]service network-manager restart
[*]ifconfig eth0 up
[/LIST] 

I may have mis-remembered the exact commands I ran (I'm posting from windoze), but I did something to the effect of restarting both the networking and network-manager services.  Neither of the restart commands had any noticeable effect, and when I ran ifconfig eth0 up, the eth0 interface started to display when I ran ifconfig.  However, it displayed an ipv6 address (I'm on an ipv4 network), and I still couldn't connect to anything.

Rebooting ubuntu multiple times didn't fix anything.

The real kicker though, is that if I go into recovery mode, and choose the root prompt with networking, I am able to connect to the network as usual, and even browse the web using lynx.  

Also, networking works fine in windows XP.

System info:
Dell Latitude D610 Laptop (32-bit system), running Ubuntu 10.04.1 Lucid Lynx LTS
80GB hard drive with a large ext4 partition mounted as root, and a smaller NTFS partition with windows.
I can get the make/model of my ethernet and wifi cards if necessary, but they were both working great this morning.

I'm totally baffled as to what caused this, and how I might fix it.  Thank you in advance for your help.

---

### Post by squigish on 2010-10-25
I'm now posting from ubuntu, as I found a recommendation to rebuild my /etc/network/interfaces file in another thread, which did the trick, sort of.  

My ethernet connection (eth0) now works, but I still can't connect to wifi.  I imagine the problem is in the settings in the /etc/network/interfaces file, but I don't know what a "normal" version of that file should look like.  

Here's my /etc/network/interfaces file: 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

When I first looked at it after the problem, all that was there was the first two lines, which  I left intact.  

Also, even after rebooting, the icon on the right-hand side of my gnome-panel, where I would normally choose a wifi network to connect to, says "networking disabled" when I mouse over it.

---

