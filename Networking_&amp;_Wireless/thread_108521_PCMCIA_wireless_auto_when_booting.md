---
title: "PCMCIA wireless auto when booting"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by rg_pablo on 2005-12-26
Hi guys,

My PCMCIA wireless don't up when I start the computer, I've to start it manually, and then it works fine. To start it at boot I added in /etc/network/interfaces:

# The primary network interface
auto ra0

but nothing. Is there any missing?

Thanks in advance.

---

### Post by Lambert on 2005-12-26
should look like this

iface ra0 inet dhcp
auto ra0

---

### Post by rg_pablo on 2005-12-26
Well, I asume that (if not then haven't worked manually). My complete /etc/network/interfaces, section ra0:

# The primary network interface
auto ra0
iface ra0 inet static
address 192.168.0.69
netmask 255.255.255.0
gateway 192.168.0.100

Any idea? :)

Regards

---

### Post by Lambert on 2005-12-26
sorry, not a lot of information in first post so I was going on assumptions.

I've seen this before in posts but no answers.

With out much research the only thing I ever found was this from the debian.org site.

>  Never list PCMCIA interfaces in auto stanzas.  The PCMCIA cardmgr is started later in the boot sequence than when /etc/rcS.d/S40networking runs [http://www.us.debian.org/doc/manuals/reference/ch-gateway.en.html]("http://www.us.debian.org/doc/manuals/reference/ch-gateway.en.html")
(section 10.8.1)

AS it says, when using auto ra0 the device is started when networking init script is run. There's another script pcmcia that runs after it later in the  boot process. 

Just a thought but no way to try, remove the auto ra0 line and add this to your interface file.

mapping hotplug
     script echo
     map ra0

You will probably have something similar to this in your file that says script grep map eth0. change grep to echo on that also as grep tells hotplug to not hotplug anyother device except this one.

---

### Post by rg_pablo on 2005-12-26
Hi again,

It worked under this configuration:

mapping hotplug
        script grep
        map ra0
        map eth1

iface ra0 inet static
address 192.168.0.69
netmask 255.255.255.0

Thank you very much, now to fight with opentype fonts in Openoffice -an impossible mission :-)-

Regards,

---

