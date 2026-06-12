---
title: "Installing Cisco Aironet 350 for ubuntu"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by hmooners on 2005-03-16
hi, 

i just installed ubuntu about a month ago, and i'm having problem with installing my cisco aironet 350.  i was running the 'install' sh for the driver, but i got to this message: 

ldcmd ldconfig
Checking for libsigc++ ...
libsigc++ not installed.
Checking for gtkmm ...
libgtkmm not installed.

The libraries can be downloaded from the web.

Sources are available from sourceforge.net (projects gtkmm and
libsigc++). Be sure that you download the correct versions (1.2.10
of gtkmm and 1.0.4 of libsigc++). You must install libsigc++ before
you can install gtkmm.

RPM packages of the libraries can be obtained from freshrpms.net.

i tried to install libsigc++ 1.0.4, which is not the version i had (1.2.5), and while following the instruction, i think i did install it, but still couldn't get the installation for cisco driver to work any further. 

i appreciate any help. 

regards,
hmooners

---

### Post by erkki70 on 2005-03-23
Hi, 

I've experienced the same problem on Hoary powerpc. 
After lots of googling, I tried to set up, install extra softs and modules but didn,t succeed at all.
The only way I found to work out was to reinstall from scatch with the card attached to laptop. 
It worked smoothly without the need of any extras.
You can read my post here:
[http://ubuntuforums.org/showthread.php?t=21662]("http://ubuntuforums.org/showthread.php?t=21662")

Hope this help.

---

### Post by boobytrapped on 2005-03-23
I am running a Ubuntu machine with Cisco Aironet 350 Card, and it works fine.  You do not need the Cisco Airo Client Utils in order to make basic WiFi work (you *do* need it if you want run Cisco LEAP, or upload firmware etc.)

The airo kernel module should work fine with the network card.  Have you tried that module?  I'd be glad to help out if the airo module does not work for you.

---

### Post by hmooners on 2005-03-23
hi thank you first of all,  but i need to use the leap. so any suggestion?

---

### Post by boobytrapped on 2005-03-23
[QUOTE=hmooners]hi thank you first of all,  but i need to use the leap. so any suggestion?[/QUOTE]

Running LEAP works for me too as long as you do not need th GUI.  The Cisco ACU GUI requires some libraries that do not come by default on Ubuntu.

Here's how associate with a LEAP access point (eth0 is my cisco wireless card - replace eth0 with the name of your wireless interface.  Also note that I installed my Cisco client utils in /opt/cisco/bin).

```

iwconfig eth0 essid MYNETWORK enc open
/opt/cisco/bin/leapscript 'myusername@mydomain.com' 'mySecretPassword'

``` 

After this you will see ouput from LEAP telling you if the authentication was successful or not.  Upon success, you need to do the following to get a dhcp ipaddress
```
dhclient eth0
```

Hope this works for you.

Ali.

---

### Post by real_ate on 2006-12-06
> **hmooners said:**
> 
ldcmd ldconfig
Checking for libsigc++ ...
libsigc++ not installed.
Checking for gtkmm ...
libgtkmm not installed.

The libraries can be downloaded from the web.

Sources are available from sourceforge.net (projects gtkmm and
libsigc++). Be sure that you download the correct versions (1.2.10
of gtkmm and 1.0.4 of libsigc++). You must install libsigc++ before
you can install gtkmm.

RPM packages of the libraries can be obtained from freshrpms.net.


Well i now have the acu successfully installed (a few bugs but i think thats my own fault and i don't think it has anything to do with the card.) i just installed the packages it asks for from the semantic package manager! just search for them and make sure you install the right versions that its asking for. if you can't find them then you need to update your software sources.

---

### Post by arangel on 2007-03-14
The card works by default with Ubuntu Edy (ppc). The problem is I don't see the signal strength with the network-manager. Anyone has a solution for this?

---

