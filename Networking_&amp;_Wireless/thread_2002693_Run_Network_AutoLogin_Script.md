---
title: "Run Network AutoLogin Script"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by fantab on 2012-06-13
I have created a SCRIPT to autologin into my ISP at the System Start. Generally my ISP's login method is through Java enabled Web-Browser. 

The Script I have created is working and lets me login to my ISP Account without the Browser.

I need help to run this Script AFTER Network-Manager establishes connection (eth0) with my ISP. If I run this script before eth0 connection is established with my ISP, the Script does not work and I am forced to rerun it from the Terminal.

---

### Post by fantab on 2012-06-14
BUMP :(

Ok I tried to put the Script in /etc/NetworkManager/dispatcher.d and execute it with chmod +x. It is not working. However the same method is working in ArchLinux_gnome-shell.

Any help?

---

### Post by fantab on 2012-06-17
Bump :(

---

### Post by Cheesehead on 2012-06-17
There are several ways:

**Easiest:** When an interface comes up (via Network Manager or ifup), the scripts in /etc/network/if-up.d get run. Put your script (or a link) in that directory. Your script must have internal logic to check for the correct interface (eth0), since all interfaces will trigger those scripts.

**Upstart:** One of those scripts, /etc/network/if-up.d/upstart, emits an Upstart signal (net-device-up IFACE=eth0). You can write an Upstart listener that will trigger your script. (This is the method I use)

**Dbus:** Network Manager emits a Dbus signal whenever an interface goes up or down. You can write a dbus listener that will trigger your script.

---

### Post by fantab on 2012-06-17
Thank you so much [Cheesehead]("http://ubuntuforums.org/member.php?u=425951"). I placed my script in /etc/network/if-up.d and it works like a charm. I guess I was distracted by the /etc/NetworkManager/dispatcher.d.

Follow up question:
  > "your script must have internal logic to check for the correct interface (eth0), since all interfaces will trigger those scripts"

**How do I add 'internal logic' to my script to check for correct interface?**

I ask this because I sometimes use my faster Broadband Modem to download  media, and I wouldn't want this script to mess with it.

---

### Post by matt_symes on 2012-06-17
Hi

If you need to check which interface the script has been called for then i believe you can use the $IFACE environmental variable in the script.

Something along the lines of (in Dash)

```
if [ "$IFACE" = "eth0" ]; then
       .....
fi
```

I assume your modems are using different interfaces ? Maybe one is wireless and the other is wired ?

If you can post your script here with any sensitive data redacted then we may be able to help you write it.

Kind regards

---

### Post by fantab on 2012-06-17
The SCRIPT I created is to autologin into my ISP at the System Start. Generally my ISP's login method is through Java enabled Web-Browser.  

The Script I created follows:

```
#!/bin/bash
wget <ISP's URL> --post-data="function=ExecuteLogin&user=USERNAME&pwd=PASSWORD&remember=false&timestamp=xxxxxxxx"
```

I have placed this in /etc/network/if-up.d and chmod +x. 

@[COLOR="Blue"]** matt_symes**[/COLOR]: Yes, One connection is WIRED, eth0, for which the above script was made. And the other is WIRELESS Broadband USB Modem.

Thanks for the Help.

---

### Post by matt_symes on 2012-06-17
Hi

Try something like this...

```
#!/bin/sh

if [ "$IFACE" = "eth0" ]; then
       wget <ISP's URL> --post-data="function=ExecuteLogin&user=USERNAME&pwd=PASSWORD&remember=false&timestamp=xxxxxxxx"
fi
```

Notice i changed it to /bin/sh and not /bin/bash. No need for that beast :)

Post back on efficacy.

Kind regards

---

### Post by fantab on 2012-06-17
Thanks [matt_symes]("http://ubuntuforums.org/member.php?u=1067998").

I edited the Script as you suggested above. It is working with eth0 wired connection. I will try the wireless USB Broadband in a couple of days and get back to you. Presently a friend of mine has borrowed the USB Broadband and as such I cannot put the Script to test with Wireless connected.

Regards

---

### Post by fantab on 2012-10-10
After the recent updates the **autologin script is not working**... from /etc/network/if-up.d/autologinscript.
However. the script runs fine if I run it directly from the terminal...

Has something changed?

---

### Post by matt_symes on 2012-10-12
Hi

> **fantab said:**
> After the recent updates the **autologin script is not working**... from /etc/network/if-up.d/autologinscript.
However. the script runs fine if I run it directly from the terminal...

Has something changed?

What version of Ubuntu are you using ?

Kind regards

---

