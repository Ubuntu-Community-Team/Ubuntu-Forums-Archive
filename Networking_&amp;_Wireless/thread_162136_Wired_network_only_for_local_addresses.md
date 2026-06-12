---
title: "Wired network only for local addresses"
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by superami on 2006-04-18
I have the strangest problem at the moment.  I just got a new laptop from work and so I setup a multi-boot with WinXP, Ubuntu, Fedora and OpenSuse.  At home I have access to two networks:

1.  My wired network (eth1) with DSL over a router, and several local computers.

2.  A wireless network (eth0) from a neighbor.

My attempts to use the wired network produce the following results:

1.  I can access the local computers and samba server without a problem.
2.  I can type "ping www.google.com" and get valid responses.  This also works for other www addresss.   It also works for if I enter thi IP address directly, wether its local or out on the internet.
3.  The router properly assigns a IP address and I show up in the routers DHCP client table.

so far so good, however:

4.  I cannot actually open any websites.  This means that attempts to open [www.google.com](www.google.com) or [www.ubuntu.com](www.ubuntu.com) only get as far as waiting for a reply from server and then eventually failure.  What is also odd is that I am unable to access my router's setup page either.

The wireless network works fine as long as eth1 (wired) is deactivated.  Activating the wired network also cause the wireless network to behave the exact same way.

Does anyone have any idea what might be causing the problem here?

EXTRA Info:
WinXP has no trouble with either network.
Fedore can't seem to access either network.
Suse can't seem to access the wireless, but has no trouble with wired internet.

---

### Post by ranf on 2006-04-20
Collect all available info from XP regarding networking:
```
ipconfig /all
```

In Suse look at the output from:
```
ifconfig
```

and compare it with ifconfig in Ubuntu.

---

### Post by mips on 2006-04-22
[QUOTE=superami]I have the strangest problem at the moment.  I just got a new laptop from work and so I setup a multi-boot with WinXP, Ubuntu, Fedora and OpenSuse.  At home I have access to two networks:

1.  My wired network (eth1) with DSL over a router, and several local computers.

2.  A wireless network (eth0) from a neighbor.

My attempts to use the wired network produce the following results:

1.  I can access the local computers and samba server without a problem.
2.  I can type "ping www.google.com" and get valid responses.  This also works for other www addresss.   It also works for if I enter thi IP address directly, wether its local or out on the internet.
3.  The router properly assigns a IP address and I show up in the routers DHCP client table.

so far so good, however:

4.  I cannot actually open any websites.  This means that attempts to open [www.google.com](www.google.com) or [www.ubuntu.com](www.ubuntu.com) only get as far as waiting for a reply from server and then eventually failure.  What is also odd is that I am unable to access my router's setup page either.

The wireless network works fine as long as eth1 (wired) is deactivated.  Activating the wired network also cause the wireless network to behave the exact same way.

Does anyone have any idea what might be causing the problem here?
[/QUOTE]

I suspect both interfaces are being allocated an ip address in the same subnet which is no-no. You should not have two interface on the same machine within the same IP subnet. Thus the unplugging makes it work.

Can you ping IP addresses on the net with success ?
Try disabling IPv6.
Try booting with either APCI or APIC =off

---

### Post by superami on 2006-04-23
[QUOTE=mips]I suspect both interfaces are being allocated an ip address in the same subnet which is no-no. You should not have two interface on the same machine within the same IP subnet. Thus the unplugging makes it work.

Can you ping IP addresses on the net with success ?
Try disabling IPv6.
Try booting with either APCI or APIC =off[/QUOTE]

Well both networks use the exact same addressing space.  At the same time though, Windows has no problems doing this.  I will try reconfiguring my wired network to a slightly different address space and see if that helps.

Jacob

---

### Post by mips on 2006-04-23
[QUOTE=superami]Well both networks use the exact same addressing space.  At the same time though, Windows has no problems doing this.  I will try reconfiguring my wired network to a slightly different address space and see if that helps.

Jacob[/QUOTE]

Windows is breaking TCP/IP rules...but then again it is MS

---

