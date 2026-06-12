---
title: "update killed internet"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by illbashu on 2009-04-16
Well the internet was working fine until i went to update manager and updated the files and it told me to restart and I did so and now the internet is broken. I tried removing firestarter, that didn't really help... can someone tell me how to fix this? :(  

For those who want to know I am using the same comp just on windows to write this so its no hardware.

Edit: i am using ubuntu 9.04 beta.

---

### Post by P4oL1n0 on 2009-04-16
Well, I think that you give us few informations to help you. How are you connected via internet? wifi? ethernet? Generally you must install extra drivers to have a right connection?

Can you ping the router?

---

### Post by illbashu on 2009-04-16
Ethernet (wired connection) i don't need to install any drivers because it was working in 9.04 then i went into update manger and updated the packages then it broke... like it was working fine until the last update.

---

### Post by P4oL1n0 on 2009-04-17
Could you check if the settings of Network Manager are ok? Have you a static IP? post here the output of:

```
ifconfig
```

---

### Post by t0mppa on 2009-04-17
I actually had the exactly same thing happen to me a few weeks ago. The update had nothing to do with network, so the only plausible reason for it to happen that I could think of was that earlier I had used a proprietary driver from the System / Hardware Drivers that had disappeared from there during the update. Solved the issue by installing a new set of drivers.

---

### Post by P4oL1n0 on 2009-04-17
However I've asked him if he uses extra drivers! :???:

---

### Post by illbashu on 2009-04-17
I never ever installed drivers for it though, every distro I ever used it worked out of the box without any setup.


> **P4oL1n0 said:**
> Could you check if the settings of Network Manager are ok? Have you a static IP? post here the output of:

```
ifconfig
```

no I have dynamic IP.

i think i am going to get the network ip and gateway and stuff write it down and manually enter it in ubuntu see if that works.

---

### Post by illbashu on 2009-04-17
i just realised it connected fine and its got the info but its not working, so something must be blocking the connection. I removed Firestarter so is there anything else that can block internet?

---

### Post by P4oL1n0 on 2009-04-17
Have you check your DNS in /etc/resolv.conf ?

---

### Post by illbashu on 2009-04-18
nothing in there other then a generated <ip address>. Could this be the prob? i went to reinstall firestarter through source and i got this error.  

```
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gconftool-2... /usr/bin/gconftool-2
checking for pkg-config... /usr/bin/pkg-config
checking for libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package gnome-vfs-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gnome-vfs-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gnome-vfs-2.0' found
configure: error: Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

where can i get those missing source files?

---

### Post by illbashu on 2009-04-22
*sigh* I give up, I'll just reinstall Ubuntu tomorrow when 9.04 comes out.

---

