---
title: "static ip on usb0 and eth0 : plasma-widget-networkmanagement"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by woefulwabbit on 2009-11-04
Ok, this is starting to get me really annoyed.

I know I can remove network manager and solve all my problems with /etc/network/interfaces however I lose the plasma widget's nice capability of detecting and configuring my usb0 connection automatically when I plug in and out an embedded development board I'm working on.

So I'm giving plasma-widget-networkmanagement a chance again after my 9.10 upgrade. If everything works fine, I don't have to do "ifdown usb0; ifup usb0;" everytime I restart the dev board.

The first thing I've found is that i need to network manager to manage eth0, which means removing the eth0 lines from /etc/network/interfaces. This is because network-manager will *wipe out* my dns servers and domain from /etc/resolv.conf once it is started, so the dns servers have to be configured for an eth0 connection.

So I create an eth0 connection and a usb0 connection in "Network Connections" with static ips and the dns server/domain for the eth0 connection. From the widget icon in the system tray, I can select my eth0 and usb0 configured connection and everything works fine.

Here lies next problem, when I plug out and plug in the usb0 device, or when I restart Kubuntu, network-manager will immediately connect to "auto eth0" and "auto usb0" (which are configured to use DHCP) instead of the connections I have configured. I have to manually switch to my static configurations EVERYTIME. I've checked the configurations and I've no way to disable "auto eth0" and "auto usb0", or to set my static configurations to default. I can enable "Connect automatically" for both connections but neither will connect automatically. I looked at ~/.kde/share/config/networkmanagementrc and ~/.kde/share/apps/networkmanagement and found nothing that can disable "auto xxxx" or set my connections to default.

Am I missing something?

---

### Post by glebbelov on 2009-11-06
I have a much simpler problem in Kubuntu 9.10: I cannot assign a static address to eth0 or set my own static IP connection as default. Network Manager just doesn't show options for eth0.

Moreover, I cannot configure printers from systemsettings,

---

### Post by samoyed on 2009-11-15
Hello everybody, I also having the same problem in Kubuntu  i can't assign static ip address to Ethernet through default network manager, is there any way to assign static ip in network manager.

regards

---

### Post by gizmobay on 2009-12-11
Did you ever figure this out? I'm trying to assign a static ip but it always defaults to the eth0 connection and then I have to manually start the static ip connection. I tried it using network interfaces which works but then the tray icon shows unconnected.

---

### Post by FOSman on 2009-12-12
I basically followed the advice from this page:
[http://pdg86.wordpress.com/2009/08/11/howto-setup-dhcpstatic-ip-in-kubuntu/](http://pdg86.wordpress.com/2009/08/11/howto-setup-dhcpstatic-ip-in-kubuntu/)

That appears to be similar to this:
[http://kubuntuforums.net/forums/index.php?topic=3104277.msg184318#msg184318](http://kubuntuforums.net/forums/index.php?topic=3104277.msg184318#msg184318)

And this:
[http://kubuntuguide.org/Karmic#Set_a_static_IP_address](http://kubuntuguide.org/Karmic#Set_a_static_IP_address)

Here's what I did, specifically:
```
sudo apt-get remove network-manager
```
Then
```
sudo kate /etc/network/interfaces
```
Make a backup of that file, then modify it as follows:
```
auto eth0
iface eth0 inet static
address [your static ip]
netmask 255.255.255.0 [unless you know yours is different]
gateway [your router/switch ip]
```
Now start a new file in kate (click the New button, or go to File -> New) and add your nameserver ips.  For me, these were listed in my router.
```
nameserver [nameserver ip]
nameserver [2nd nameserver ip]
(etcetera)
```
Save that as resolve.conf in /etc.  So the full path for that file would be "/etc/resolve.conf"

Close kate and do a
```
sudo /etc/init.d/networking restart
```
Then
```
ifconfig
```
In the second line of eth0, you should now see
```
inet addr:[your static ip]
```
Hope that helps!

---

### Post by woefulwabbit on 2010-02-16
This works if I only need to work with eth0, but does not detect and autoconfigure usb0 when I plug it in/out.

---

