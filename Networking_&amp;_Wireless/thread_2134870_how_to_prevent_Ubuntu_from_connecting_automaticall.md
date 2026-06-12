---
title: "how to prevent Ubuntu from connecting automatically to internet"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by santiagorf on 2013-04-12
Hi all,
I'm creating a script for a device that is connected via an ethernet card, and I need to stop Ubuntu from connecting to the internet automatically via the eth0 device.
I can do that manually if I go to the network manager and uncheck on "Connect automatically", but I would like to know how can I do it from the shell.
any hel would be much appreciated

---

### Post by WildOscar on 2013-04-12
Your question is unclear. What is it you are trying to achieve?

---

### Post by deadflowr on 2013-04-12
You could probably do that by setting your firewall to prevent/deny the system access to outside devices.
Figure out what the address for your router is and block that address. 
Maybe.

---

### Post by santiagorf on 2013-04-12
> **deadflowr said:**
> You could probably do that by setting your firewall to prevent/deny the system access to outside devices.
Figure out what the address for your router is and block that address. 
Maybe.

I use my ethernet card to connect to a piece of hardware. 
During boot up I created a service that configures the card to connect to the device, and I am able to work with it until Ubuntu tries to reconnect to the internet.
I can stop Ubuntu from doing that going to the network manager, but I would like to have a script to do that.

---

### Post by santiagorf on 2013-05-01
no one?

---

### Post by steeldriver on 2013-05-01
IMHO the easiest way would be to remove network-manager entirely and use /etc/network/interfaces to configure a non-auto eth0 that you can bring up manually when required

If you are determined to use network-manager, then afaik you will need to talk to it via dbus - similar to what's discussed here --> [http://ubuntuforums.org/showthread.php?t=2134738](http://ubuntuforums.org/showthread.php?t=2134738)

---

### Post by santiagorf on 2013-06-27
> **steeldriver said:**
> IMHO the easiest way would be to remove network-manager entirely and use /etc/network/interfaces to configure a non-auto eth0 that you can bring up manually when required

If you are determined to use network-manager, then afaik you will need to talk to it via dbus - similar to what's discussed here --> [http://ubuntuforums.org/showthread.php?t=2134738](http://ubuntuforums.org/showthread.php?t=2134738)

thanks!!
this seems to solve the issue.

---

