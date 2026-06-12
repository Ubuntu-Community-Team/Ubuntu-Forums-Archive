---
title: "NetworkManaget applet dropdown menu items missing"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2012-05-29
After upgrading Asus EEE-1215N from 11.10 --> 12.04, the nm-applet dropdown menus, right- or left-click, on the system-tray nm icon show only 'Enable Networking', 'Enable Wireless', 'Connection Information', 'Edit Connections...'. Other items such as the list of wired and wireless interfaces, available hotspots, wireless connection options, and VPN options, are not present at first. After a variable time, usually more than 5 minutes after boot-up / login, the missing items appear.

At all times the network connections, wired and wireless, work normally, except of course that I cannot connect to a different wireless spot or start a VPN connection (OpenVPN) other than manually (which works just fine). Of course, all the nm-applet menu items appeared right away under 11.10; this behavior appeared upon upgrading.

Nothing unusual in NetworkManager.conf or interfaces:
```
:/etc$ cat network/interfaces
auto lo
iface lo inet loopback

auto eth0

```
```
:/etc$ cat NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

Perhaps this has something to do with the default [Connectivity] interval=300 seconds in NetworkManager.conf, but only because the timing is pretty much the same. I'll tweak that and post the result. Meantime, has anyone experienced this?

---

### Post by DrJohn999 on 2012-05-29
[connectivity] interval=30 makes no difference. This time had to wait ~ 1 hour for the full drop-down menu to appear. 

Found in syslog:
```
~$ cat /var/log/syslog | grep "May 29.*Netw.*error"
May 29 13:19:42 eee-1215N NetworkManager[941]: <error> [1338322782.289666] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
```
Filed BugReport [1006141]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1006141")
This occurs once per boot.

---

### Post by DrJohn999 on 2012-05-29
Restarting nm-applet brings it up with the full drop-down menu list:
```
username@eee-1215N:/etc$ ps -A | grep nm-applet
 3119 ?        00:00:00 nm-applet
username@eee-1215N:/etc$ kill 3119
username@eee-1215N:/etc$ nohup nm-applet &
[1] 3366
username@eee-1215N:/etc$ nohup: ignoring input and appending output to `/home/username/nohup.out'
^C
username@eee-1215N:/etc$exit

```

---

### Post by andersdd on 2012-06-07
Thanks for posting this solution.  I had the same issue and your solution fixed it for me as well.

---

### Post by darktowermage on 2012-06-07
I just upgraded to 12.04 and noticed this as well.  This hadn't happened (that I noticed) until I went into synaptic the other day and marked all upgrade packages and applied.  I remember seeing something about a DNS and other network packages in that upgrade but don't have the details.  Currently running NetworkManager 0.9.4.0.  

To offer another workaround using the GUI, unchecking the "Enable Networking" menu item in the network indicator menu and then checking it again made the menu items show back up.

Does anyone have any suggestions on how to determine the cause of the problem?  I've been using Linux for a couple years but don't know how to trace back issues like this.

---

### Post by rbjscv on 2012-10-01
> **darktowermage said:**
>  

To offer another workaround using the GUI, unchecking the "Enable Networking" menu item in the network indicator menu and then checking it again made the menu items show back up.

Does anyone have any suggestions on how to determine the cause of the problem?  I've been using Linux for a couple years but don't know how to trace back issues like this.

I don't know what the cause is, but I do very same work-around that you do. So far I haven't seen anything, anywhere about how to fix it permanently. And I search pretty much daily. These type of things make me wish I'd never left 10.04.

---

### Post by n.hinton on 2012-10-05
could also try
```
gksudo service network-manager restart
```

---

