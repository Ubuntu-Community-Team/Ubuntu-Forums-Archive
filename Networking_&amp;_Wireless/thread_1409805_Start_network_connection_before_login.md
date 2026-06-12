---
title: "Start network connection before login"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Magnesium on 2010-02-18
Hi folks,

I've got a Kubuntu Karmic install that I ssh into on a frequent basis. It stays running 24/7, but sometimes the power goes out, etc. and it reboots.

The thing is, when it reboots, before I log in to KDE, there is no network connection. It is only *after* I log into KDE that nm-applet (I use the GNOME one because it works better than KNetworkManager) makes the connection and gets an IP address. And it does so completely automatically...no customizations by me. If I try to connect manually (sudo ifup eth0) before log in, I don't get an IP address.

How can I get it to connect to the network and get an IP address at boot, before I touch it?

Thanks,
Mg

---

### Post by chili555 on 2010-02-18
The classic method is like servers are configured; remove Network Manager and set all your details in */etc/network/interfaces*. If you ssh into it, it would seem handy to set up a static IP address. Here, as an example, is the *interfaces* file on my desktop machine:```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.117
netmask 255.255.255.0
gateway 192.168.1.254
```Just be sure the static address is outside the DHCP range of the router.

---

### Post by Magnesium on 2010-02-18
Ahhh...so I need to remove NetworkManager to get it to work! I *did* add the auto eth0 and iface ... lines, but I never removed NetworkManager.

I'll test it out tonight when I get back to my computer. Thanks!

Mg

---

### Post by Magnesium on 2010-02-20
Ok Chili, I uninstalled Network Manager (sudo apt-get remove network-manager) and modified my /etc/network/interfaces like you suggested, and rebooted. I also tried modifying it to include the dhcp version of eth0. Either way, it gets my network working, but I can only ping computers in the network. I can also access the router configuration. But I can't ping google, etc.

It makes me think that it's a DNS problem...but I don't know really how to troubleshoot that. How come network-manager does everything so well?

Mg

---

### Post by chili555 on 2010-02-20
> How come network-manager does everything so well?You'd probably get some arguments about that here on this forum!

It probably is a DNS issue. I hoped that your working DNS settings survived the change from DHCP to static. Let's take a look at a file:```
sudo gedit /etc/resolv.conf
```I am assuming it is empty or incorrect in some respect. You may safely appoint the router to do the DNS duties. Add a single line:```
nameserver 192.168.1.254
```Substitute the IP address of your router/gateway. Eliminate any other lines. Proofread, save and close gedit. Now do:```
ping -c3 74.125.45.147
ping -c3 www.google.com
```

---

### Post by Magnesium on 2010-02-20
> **chili555 said:**
> You'd probably get some arguments about that here on this forum!

It probably is a DNS issue. I hoped that your working DNS settings survived the change from DHCP to static. Let's take a look at a file:```
sudo gedit /etc/resolv.conf
```I am assuming it is empty or incorrect in some respect. You may safely appoint the router to do the DNS duties. Add a single line:```
nameserver 192.168.1.254
```Substitute the IP address of your router/gateway. Eliminate any other lines. Proofread, save and close gedit. Now do:```
ping -c3 74.125.45.147
ping -c3 www.google.com
```

Thank you Chili! :D :D That was so simple...I thought I had tried something like that, but apparently it didn't work (maybe I still had NetworkManager installed at the time...IDK).

After I re-removed NetworkManager, added that line, and ran "sudo ifup eth0" everything worked...so I added ifup eth0 to my /etc/rc.local...is that the best way to have it connect automatically at boot? (As opposed to using another one of the rc files, or crontab, or something.)

Thanks again for your help!\\:D/

Mg

---

### Post by chili555 on 2010-02-20
> is that the best way to have it connect automatically at boot? If you have this in */etc/network/interfaces*:```
auto eth0

```It should start on boot with no further steps. Glad it's working!

---

### Post by Magnesium on 2010-02-20
> **chili555 said:**
> If you have this in */etc/network/interfaces*:```
auto eth0

```It should start on boot with no further steps. Glad it's working!

Hmmm...I've got that line, but it's not starting on boot without running sudo ifup eth0 (either manually or by putting it in rc.local.) It's okay...it works with that line in rc.local....but that's strange that it is not starting without it. :confused:

Mg

---

