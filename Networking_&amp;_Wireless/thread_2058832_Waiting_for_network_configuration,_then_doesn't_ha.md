---
title: "Waiting for network configuration, then doesn't have wi-fi"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by blacktrance on 2012-09-16
I installed 12.04 from the minimal ISO, then installed MATE. The network connection works fine when I'm connected to ethernet, but when ethernet isn't connected, it takes over a minute to load (says it's waiting for network configuration), then, when it finally loads, it doesn't connect to wi-fi. It's not a problem with my wireless card itself because it works fine in Windows. What should I do?

I have an Acer Aspire 8730, if it helps.

---

### Post by blacktrance on 2012-09-16
Anyone know anything about this?

---

### Post by steeldriver on 2012-09-16
I'm sure one of the wireless experts on here will be happy to step in if you can post some more info

--> [**Sticky: Supported wireless cards list and procedure to get help.**]("http://ubuntuforums.org/showthread.php?t=370108")

---

### Post by blacktrance on 2012-09-16
I know my wireless card is supported because it worked in a previous Ubuntu install.

Edit: Installed Wicd from Synaptic, found my wireless network listed, connected to it, and everything works. Fixed.

---

### Post by myzeus on 2012-10-10
I just had the same issue installing Kubuntu 12.04 from a Minimal ISO. I solved it this way.

During the installation procedure, the installer prompt the user  to configure an Internet connection and the configuration is saved in **/etc/network/interfaces**. At each boots it seems the systems waits for all the network interfaces defined in **/etc/network/interfaces** to start up, using the Failsafe Boot Delay as defined in **/etc/init/failsafe.conf **

Therefore you must remove all the lines added by the installer. In my case **/etc/network/interfaces** was like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

[COLOR=Red]# The primary network interface
auto eth0
iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto[/COLOR]
```Following the comment #5 in [here]("http://ubuntuforums.org/showthread.php?t=2033406&highlight=Waiting+network+configuration") I removed all the red lines in the file, leaving only the definition of the local network, which is really need to be checked during the boot.

To reconfigure the Ethernet connection I edited the Network Manager configuration in **/etc/NetworkManager/nm-system-settings.conf** , changing the line
```
[ifupdown] managed=false
``` to 
```
[ifupdown] managed=true
```Now you can reboot and use the Network Manager to manage the Ethernet connection. This should solve this issue.

---

