---
title: "&quot;Updating connection failed: nm-ifupdown-connection.c&quot; in NetworkManager Applet 0.7.0"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by Aj204 on 2012-08-02
Hi,
*Summary
I have two network connections in the NetworkManager. "Wired Connection 1" and "ifupdown (eth0)", the first one works and the second one doesnt have the correct gateway. The second one is marked as autoconnect, so sometimes it will reconnect using "ifupdown (eth0)" and no more internet connection!

*Question:
1. "ifupdown (eth0)" is configured for static IP address, the gateway has changed and the address is different. I cannot change its settings with out getting "Updating connection failed: " error. How was it configured originally?

2. I am tempted to delete the "ifupdown (eth0)" connection (if it lets me do it) will my  "Wired Connection 1" still work or are they somehow intertwined?

3. The safest option would be to disable autoconnect on "ifupdown (eth0)" but i dont seem to be allowed to do that. Must i "sudo" into network manager somehow?


*Background research 
I have read the page explaining how to use NetworkManager 0.7.0:
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

The FAQ has the following for this error:

```
a. ** Updating connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only). ** 
thats a read-only connection (its auto). You can only edit it when you rename the connection otherwise the above error will show. 
```Now i have a similar error but mine is in line 76 rater than 82.. since we both using 0.7.0 maybe its a different error or maybe not.

For the benefit of google search, exact error is
```
Updating connection failed: nm-ifupdown-connection.c.76 - connection update not supported (read-only)..
```4. The FAQ seems to say i simply need to rename "ifupdown (eth0)" to something else to allow me to edit it. That still gives me the same error. Am i understanding the FAQ wrongly?


System: Ubuntu 8.10
Ifconfig (when using Wired Connection 1):

eth0      Link encap:Ethernet  HWaddr 00:21:5a:d4:1f:64  
          inet addr:10.20.21.3  Bcast:10.20.21.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5aff:fed4:1f64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1714424468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:961648139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2428705152080 (2.4 TB)  TX bytes:182022289632 (182.0 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:409229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209277290 (209.2 MB)  TX bytes:209277290 (209.2 MB)

---

### Post by steeldriver on 2012-08-02
That's all very confusing - 'ifupdown' is a keyword in the NetworkManager.conf file, it's hard to see why you would have that in a connection name (unless you - or someone else - manually changed it)

You should be able to see any non-default (i.e. manually configured) NetworkManager connections by doing

```
ls /etc/NetworkManager/system-connections/
```Note that you won't be able to change / delete system connections without sudo permission.

Alternatively it is possible that the 'ifupdown' connection is established via the older /etc/network/interfaces file: can you post the outputs of these two commands?

```
cat /etc/NetworkManager/NetworkManager.conf 

cat /etc/network/interfaces
```

---

### Post by Aj204 on 2012-08-02
Thanks for the suggestion steeldriver. Below is what i found:

```

dennis@ubuntu-server:~$ ls /etc/NetworkManager/system-connections/
dennis@ubuntu-server:~$ 

```So no manually added connections it seems.


```

dennis@ubuntu-server:~$ cat /etc/NetworkManager/NetworkManager.conf 
cat: /etc/NetworkManager/NetworkManager.conf: No such file or directory

```But their is another conf file.

```

dennis@ubuntu-server:/etc/NetworkManager$ cat /etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

dennis@ubuntu-server:/etc/NetworkManager$ 

``````
dennis@ubuntu-server:/etc/NetworkManager$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp
iface eth0 inet static
    address 10.20.21.3
    netmask 255.255.255.0
    network 10.20.21.0
    broadcast 10.20.21.255
    gateway 10.20.21.254
    dns-nameservers 212.23.3.100
    dns-search lan

auto eth0

dennis@ubuntu-server:/etc/NetworkManager$ 

```These settings seem to be from the wrong "ifupdown (eth0)" connection, I was wrong in my original description, the gateway is the same but the DNS server changed. "Wired Connection 1" has the correct DNS server (same as the gateway 10.20.21.254) while "ifupdown (eth0)" cannot be changed from 212.23.3.100.

So is nm-system-settings.conf where i am getting my weird interface from?

---

### Post by steeldriver on 2012-08-02
Apologies - I didn't know the NetworkManager configuration file name had changed but it looks like you found the right one

So your 'mystery' connection is being set up via /etc/network/interfaces and the reason it is appearing in the nm-applet is that your nm-system-settings.conf file is telling network-manager to 'manage' such connections, via

```
[ifupdown]
managed=true
```If you really don't use the static wired connection then afaik there's no harm in just removing it from /etc/network/interfaces (or if you are not sure, just comment it out using # characters at the beginning of each line) so that the only 'active' interface is

```
auto lo
iface lo inet loopback
```Then it should not show up on next reboot - or if you don't want to reboot, you can restart both services after making the file changes

```
sudo service networking restart
sudo service network-manager restart
```Hope this helps - let us know if it works

---

### Post by Aj204 on 2012-08-02
Well editing interface file to update the dns name then restarting the network interface gave me a workaround for the problem and DNS resolving now works with "ifupdown (eth0)" connection.

```
dennis@ubuntu-server:/etc/network$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp
iface eth0 inet static
    address 10.20.21.3
    netmask 255.255.255.0
    network 10.20.21.0
    broadcast 10.20.21.255
    gateway 10.20.21.254
    dns-nameservers 10.20.21.254
    dns-search lan

auto eth0

dennis@ubuntu-server:/etc/network$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          SIOCDELRT: No such process
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]
dennis@ubuntu-server:/etc/network$ 

```Looking at:
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

1. I have the impression my dns resolving configs should be in
/etc/resolv.conf rather than directly in /etc/network/interfaces, is this an old method?

2. Should i understand that giving the connection the name of "ifupdown" is causing NetworkManager to choke on the name when i try and change settings?

---

### Post by Aj204 on 2012-08-02
Hi Steeldriver, while you where replying i was fidling with the interface file. I cried victory a bit early, for some reason sometimes ifupdown (eth0) still did not resolve..

I followed your advice and commented out all the settings relating to that interface. Restarted and now Network Manager is showing 2 connections:

"Wired Connection 1" which is statically configured
"Auto Eth0" which is set to DHCP, but i can now change it to not automatically connect.

---

### Post by steeldriver on 2012-08-02
did you remember to comment out the 

```
auto eth0
```line at the bottom of /etc/network/interfaces? it should ONLY contain the lines I posted above (the 'lo' or loopback interface definition)

The /etc/network/interfaces way of doing things (aka 'ifupdown') is great for servers, where you typically want statically configured interfaces that come up at boot time and can be managed via CLI. In contrast NetworkManager is targeted towards roaming configurations like laptops where you want to modify / add connections on the fly in userspace. There is rarely any reason to run both - although the network-manager service is technically aware of the older networking service (hence the [ifupdown] managed = true line in your config file) the truth is they don't play well together at the moment.

If you don't need the older static connection then commenting out EVERYTHING related to it should work. If you DO need that connection then you should be able to set it up via the nm-applet (the static IP / DNS details can be entered under the IPv4 tab). Or configure everything via /etc/network/interfaces and remove network-manager altogether. Not both (unless you're a masochist).

---

