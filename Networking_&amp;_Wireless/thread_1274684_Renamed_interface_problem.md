---
title: "Renamed interface problem"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2009-09-24
This may be a simple question with an obvious answer, but I've not been able to find a solution by searching the forum and the documentation...

First, the background. I have a small LAN in my home office, and for about 10 years it's been running under control of an ancient Pentium 2 box with Mandrake Linux 8.1, serving as the firewall, router, gateway, and mail-FTP-web server. Last Saturday night a capacitor in the power supply gave up the ghost. Because of the box's age, repair isn't feasible, so I decided to move a somewhat newer box that served as my DNS server into its position. That box was running Mandriva 10.2 (2005 edition) so I thought the replacement would be fairly easy. However when I tried to configure it for connection sharing, it asked for the installation CD which was nowhere to be found. I decided to upgrade it to the current Mandriva 2009 version, downloaded the ISO, burned the CD, and began the upgrade. Six hours and two kernel panics later I gave up on Mandriva, and installed my reliable Xubuntu 8.04.3 LTS! It installed with no problem, in a total of an hour and 10 minutes.

And that brings me to the problem and question. Because this box will be serving as the gateway and router for my LAN, it has two NICs. Dmesg shows that both are detected, but for some reason the original eth0 gets its name swapped with eth1 during the boot process. I wind up with three eth* interfaces listed in the "interfaces" file; the third is "eth0_rename" and since it has the same ip values as the original eth0, it takes over the connection and somehow makes eth0 invisible to the "ifup -a" script, which complains about a non-existent device. Also the XFCE net monitor panel applet is unable to see eth0, and "eth0-rename" is one character too long to be entered in its configuration edit box!

Here at last is my question(s): What is causing the unnecessary renaming? How can I stop it, or alternatively how can I force a shorter name for the temp copy? Finally, how can I get rid of the left-over interface, which reappears each time I power up the system?

---

### Post by JKyleOKC on 2009-09-25
Well, I did a bit more digging, removed all traces of Network Manager, and now the rename doesn't happen. Instead, eth0 vanishes! Here's a capture of my CLI attempting to bring it up:
```
jim@Mehitabel:~$ sudo ifconfig eth0 66.143.22.33
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
jim@Mehitabel:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.2

auto eth0

iface eth1 inet static
address 66.143.22.33
netmask 255.255.255.248
gateway 66.143.22.38

auto eth1

jim@Mehitabel:~$ 

```
I don't mind showing my IP in public since it has to be accessible to my customers anyway. Anybody have any idea why ifconfig cannot find it although it's there in the interfaces list?

---

### Post by Iowan on 2009-09-25
I'm probably diagnosing the wrong problem, but you called ifconfig for eth0 with the address you assigned to eth1?

---

### Post by JKyleOKC on 2009-09-25
At that point I was grasping at straws and attempting to swap the addresses back rather than simply switching the cables.

I've since disabled the "avahi" service, and that ended the disappearing act -- but now the box won't find the ISP name servers that were working fine before the reboot!

I'm a bit slow in replying because I have to use my laptop and its wireless connection (I have five static IPs and use one for Mehitabel, one for a wireless router, and a third for my wife's machine that won't talk to my LAN) to get back to the forum, while I keep trying to troubleshoot Mehitabel's problem(s). Thanks for the response!

---

### Post by spd106 on 2009-09-25
As you're going with static configuration your box won't be receiving the DNS server address, so you'll have to set that too.

You can add a line in the /etc/resolv.conf file or put it in the interfaces file with a dns-nameservers line.

This wiki page might prove useful.
[http://wiki.debian.org/NetworkConfiguration](http://wiki.debian.org/NetworkConfiguration)

---

### Post by JKyleOKC on 2009-09-25
I have them added in the /etc/resolv.conf file; for a few hours this afternoon everything seemed to be working. Then I re-booted to verify that I had things fixed, and the renaming problem popped back up. I'm almost ready to switch things over to a Red Hat derivative such as Centos; seems as if the *buntu efforts have gone a bit overboard in the search for simplicity and made it extremely difficult to do anything complex! I still like them best at the workstation level, but this box will primarily be a server...

---

### Post by kerry_s on 2009-09-25
have a look in /etc/udev/rules.d/70-persistent-net.rules

that is where your net devices get assinged there name, look on the end. see pic

---

### Post by JKyleOKC on 2009-09-26
Thank you very much, kerry_s! Manually adding another line to handle the second NIC, and changing the existing line's KERNEL= attribute from "eth*" to "eth0" seems to have fixed it. I still get an "eth1 - link not up" error in the dmesg report but the box is now able to connect to the internet.

Thanks also to spd106 for pointing me to the Debian page on the interfaces file; adding the dns servers to this file certainly makes maintenance easier!

EDIT: The "link not up" error turned out to be a loosely plugged in connector that had worked itself out! Firmly seating it cured that problem, but another one appeared the next time I re-booted. Looking again at the "70-persistent-net.rules" file showed that another rename had been automatically inserted, which brought back the original trouble. I deleted the added rule, then went to the "75-persistent-net-generator.rules" file and erased "eth*|" from its whitelisting stanza, to prevent generation of any more spurious rules. It seems to be working properly again after a test re-boot, and I'm posting this edit through the machine! Fingers crossed, but I've changed the thread title to indicate it's solved.

---

