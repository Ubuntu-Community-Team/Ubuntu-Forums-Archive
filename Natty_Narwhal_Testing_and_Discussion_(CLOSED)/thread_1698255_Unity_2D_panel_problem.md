---
title: "Unity 2D panel problem"
date: 2011-03-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by suryateja.sun on 2011-03-02
Hai,

Please check the screenshot here. There are no indicator applets in ubuntu panel. Also, when I hit 'ALT' for options, the menu bar looks like as shown. Please solve these issues.

Thanks

---

### Post by lucazade on 2011-03-02
> **suryateja.sun said:**
> Hai,

Please check the screenshot here. There are no indicator applets in ubuntu panel. Also, when I hit 'ALT' for options, the menu bar looks like as shown. Please solve these issues.

Thanks

No indicator applets in unity-2d-panel is a known issue and it is already being pushed a patch in bzr code, so this will be fixed in next release.

About the other issue I believe you should file a new bug report.

---

### Post by suryateja.sun on 2011-03-02
@lucazade: Thanks

Right Click is also not working in the desktop. How to do it?

---

### Post by lucazade on 2011-03-02
> **suryateja.sun said:**
> @lucazade: Thanks

Right Click is also not working in the desktop. How to do it?

Known issue also this.. if I remember well there is already a bug report and a branch related to this. ;)

---

### Post by suryateja.sun on 2011-03-03
I updated today and I got indicator-applet back, but still network icon is missing. How to get it?

---

### Post by lucazade on 2011-03-03
> **suryateja.sun said:**
> I updated today and I got indicator-applet back, but still network icon is missing. How to get it?

indicator-network is working correctly here, you should have it as well.

check if network-applet is present in system > startup applications and/or
try to kill unity-2d-panel to make indicators reload
```
killall unity-2d-panel

```

---

### Post by suryateja.sun on 2011-03-03
Actually, when I traversed through the bar, I found out a location  (which is small space) at which a dropdown menu came. The following are the items
Wired Network 
device not managed
Wireless Networks
wireless is disabled by hardware switch
VPN Connections >
Enable Networking
Enable Wireless
Connection Information
Edit Connections

But I click 'Connection Information', I dialog box showing 'No active connections are found'. I am typing this message through the same laptop!!? Even I change the Edit Connections, still there is no significant effect on my static IP address. I doubted, its internal network problem!

---

### Post by lucazade on 2011-03-03
> **suryateja.sun said:**
> Actually, when I traversed through the bar, I found out a location  (which is small space) at which a dropdown menu came. The following are the items
Wired Network 
device not managed
Wireless Networks
wireless is disabled by hardware switch
VPN Connections >
Enable Networking
Enable Wireless
Connection Information
Edit Connections

But I click 'Connection Information', I dialog box showing 'No active connections are found'. I am typing this message through the same laptop!!? Even I change the Edit Connections, still there is no significant effect on my static IP address. I doubted, its internal network problem!

You could try reinstalling network-manager, maybe some configuration files are gone

```
sudo apt-get --reinstall install network-manager network-manager-gnome

```
and reboot

look also if "ifconfig" output gives correct info

---

### Post by suryateja.sun on 2011-03-03
Error remains the same. 

Is there anyway to reset the network configuration and connections

---

### Post by lucazade on 2011-03-03
> **suryateja.sun said:**
> Error remains the same. 

Is there anyway to reset the network configuration and connections

Does it work in a Classic Desktop session?
No idea how to purge network configuration manually.. 

could you paste the output of  these commands:
```
service network-manager status

```
```
cat /etc/network/interfaces

```
```
ps -ax | grep nm
```

---

### Post by suryateja.sun on 2011-03-04
These are the following results of your request

```

service network-manager status

network-manager start/running, process 1050

```

```

cat /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.104.250.245
# network 10.104.0.0
netmask 255.255.0.0
gateway 10.104.250.1


```

```

ps -ax | grep nm

Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 1533 ?        Sl     0:00 nm-applet --sm-disable
 3037 pts/0    S+     0:00 grep --color=auto nm


```

---

### Post by lucazade on 2011-03-05
> **suryateja.sun said:**
> These are the following results of your request

```

service network-manager status

network-manager start/running, process 1050

```

```

cat /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.104.250.245
# network 10.104.0.0
netmask 255.255.0.0
gateway 10.104.250.1


```

```

ps -ax | grep nm

Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 1533 ?        Sl     0:00 nm-applet --sm-disable
 3037 pts/0    S+     0:00 grep --color=auto nm


```

Your settings file seems correct for a static IP, you could try switching back to dynamic IP to see if Network applet works.

leave only these in cat /etc/network/interfaces (network-manager should handle eth0 by itself)

auto lo
iface lo inet loopback

and you should also see dhcp client and applet in processes:
ps -ax | grep nm

1039 ?        Sl     0:00 nm-applet --sm-disable
 9976 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-1b815bd0-fcee-4428-9c13-116a095c6e41-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

if eth0 is not up and  running
sudo ifconfig eth0 up
sudo dhclient eth0

---

### Post by suryateja.sun on 2011-03-10
Thanks Lucazade,

It got it works.

But I will use my lappy at two distinct places. When I add another connection in 'Edit Connections', it is not detecting the available connections in network applet. Can you please tell me at what place will problem exists?

---

### Post by lucazade on 2011-03-11
> **suryateja.sun said:**
> Thanks Lucazade,

It got it works.

But I will use my lappy at two distinct places. When I add another connection in 'Edit Connections', it is not detecting the available connections in network applet. Can you please tell me at what place will problem exists?

This new update might solve your network issue.
Network-manager has been replaced by connman and a new indicator-network

look at this post: [http://www.omgubuntu.co.uk/2011/03/indicator-network-is-looking-good-in-natty/](http://www.omgubuntu.co.uk/2011/03/indicator-network-is-looking-good-in-natty/)
(update repositories, install indicator-network and reboot)

---

### Post by suryateja.sun on 2011-03-12
Lucazade: Problem Solved, Thanks.

How to change thread title to [SOLVED]?

---

### Post by Harry33 on 2011-03-12
> **suryateja.sun said:**
> Lucazade: Problem Solved, Thanks.

How to change thread title to [SOLVED]?

Choose from the upper right corner "Thread tools".

---

