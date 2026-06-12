---
title: "Network Manager fails, but dhclient works"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by projectshave on 2009-07-09
The NetworkManager applet fails to connect via dhcp, but "dhclient" on the command line sets it up fine. How can I get the NetworkManager app to work correctly? 

The setup for NetworkManager is the default: Wired connection named Auto eth1, IPv4 method is automatic dhcp. When I select this, the icon lights up for a while, then it says I'm disconnected.

dhclient works fine. Here's the output: 

[INDENT]Listening on LPF/eth1/00:0c:29:af:02:ff
Sending on   LPF/eth1/00:0c:29:af:02:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.113 from 192.168.1.1
DHCPREQUEST of 192.168.1.113 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.113 from 192.168.1.1
bound to 192.168.1.113[/INDENT]

Details: Ubuntu 9.04 running in vmware player on Windows host. NetworkManager 0.7.0.100. dhclient v3.1.1.

Thanks.

---

### Post by slugmax on 2009-07-09
In a console window, run 'tail -f /var/log/syslog | grep NetworkManager' while you try and connect. That may give you a clue as to what is going wrong.

---

### Post by projectshave on 2009-07-09
Thanks for the suggestion. I trimmed the output, here are the important lines. Elsewhere, someone said apparmor might be preventing execution. I attached my apparmor_status below. 

[INDENT]Jul  9 13:46:52 ubuntu dhclient: execve (/usr/lib/NetworkManager/nm-dhcp-client.action, ...): Permission denied
Jul  9 13:46:52 ubuntu kernel: [ 6619.834009] type=1503 audit(1247161612.297:21): operation="inode_permission" requested_mask="x::" denied_mask="x::" fsuid=0 name="/home/extraSpace/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6663 profile="/sbin/dhclient3"
Jul  9 13:46:56 ubuntu dhclient: execve (/usr/lib/NetworkManager/nm-dhcp-client.action, ...): Permission denied
Jul  9 13:46:56 ubuntu kernel: [ 6623.546928] type=1503 audit(1247161616.008:22): operation="inode_permission" requested_mask="x::" denied_mask="x::" fsuid=0 name="/home/extraSpace/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6664 profile="/sbin/dhclient3"
Jul  9 13:47:37 ubuntu NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>45s), stopping it. [/INDENT]

apparmor_status:

[INDENT]apparmor module is loaded.
9 profiles are loaded.
9 profiles are in enforce mode.
   /usr/lib/connman/scripts/dhclient-script
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/mysqld
   /sbin/dhclient3
   /usr/sbin/cupsd
   /sbin/dhclient-script
   /usr/lib/NetworkManager/nm-dhcp-client.action
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode :
   /sbin/dhclient3 (8549) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.[/INDENT]

---

### Post by superprash2003 on 2009-07-09
post output of /etc/network/interfaces file

---

### Post by projectshave on 2009-07-09
/etc/network/interfaces:

[INDENT]auto lo
iface lo inet loopback[/INDENT]

Though it doesn't mention eth1, networking still works. I's just NetworkManager that's failing. I appended the following to the interfaces file, but still no luck:
[INDENT]auto eth1
iface eth1 inet dhcp[/INDENT]

Also, in the if-pre-up.d/ directory I've got dhclient3-apparmor.

---

### Post by projectshave on 2009-07-09
double post. no delete button here.

---

### Post by slugmax on 2009-07-09
Do you have a section like this in your /etc/apparmor.d/sbin.dhclient3? Also what version of Ubuntu is this?

```

/usr/lib/NetworkManager/nm-dhcp-client.action {
  #include <abstractions/base>
  #include <abstractions/dbus>
  /usr/lib/NetworkManager/nm-dhcp-client.action mr,
}

```

---

### Post by projectshave on 2009-07-09
Yep, I've got that chunk in there. I'm running 9.04. All version info and more details are in my first post. 

Thanks.

---

### Post by slugmax on 2009-07-09
> **projectshave said:**
> Yep, I've got that chunk in there. I'm running 9.04. All version info and more details are in my first post. 

Thanks.

Missed that, sorry. I see a couple of related bugs for this, [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/332521](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/332521) and [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/343898](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/343898).

The latter bug describes a workaround - you can disable the dhclient apparmor profile:

[https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile](https://help.ubuntu.com/community/AppArmor#Disable%20one%20profile)

Also this:

[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

---

### Post by projectshave on 2009-07-09
Thanks, it works now. For future reference, I disabled apparmor for dhclient and retried NetworkManager. It connected just fine. Here are the commands: 

sudo ln -s /etc/apparmor.d/sbin.dhclient3 /etc/apparmor.d/disable/
sudo apparmor_parser -R < /etc/apparmor.d/sbin.dhclient3

---

### Post by projectshave on 2009-07-09
Spoke too soon. After a reboot, same problem. I had to rerun that last line "apparmor_parser" to get it to work. This seems related to this problem: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417)

Basically, networkmanager is hosed in Jaunty.

---

