---
title: "Hostapd and other network issues after upgrading to 10.10"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Xylian on 2010-10-16
Hi,
yesterday I've done a release upgrade from 10.4.1 LTS to 10.10 and I faced the following issues:

1) br0 does not bridge anymore eth0 and wlan0 (I have a DNMA92 wireless card that runs ath9k drivers) at startup even if specified in /etc/network/interfaces:
```

auto lo
iface lo inet loopback
pre-up /sbin/iptables-restore < /etc/network/firewall-rules.conf

# The primary network interface
auto eth0
iface eth0 inet manual

auto wlan0
iface wlan0 inet manual
post-up /sbin/iwconfig wlan0 txpower 17

auto br0
iface br0 inet static
        address 10.0.0.1
        network 10.0.0.0
        netmask 255.0.0.0
        broadcast 10.255.255.255
        bridge-ports eth0 wlan0

```

If I reboot the server, then *brctl show br0* shows only interface eth0.. before 10.10, everything worked without problems... I've solved the problem adding to the above code *pre-up /bin/sleep 5s* and it seems to work now... maybe wlan0 is not ready when the brctl tries to add it to the bridge br0? Any idea?

2) is there a configuration file or a particular statement that I can use to specify that I want wlan0 to work at 17dB instead of 27dB? I've added the post-up directive above to change the txpower when wlan0 is brought up, but maybe there is a better way (such as an option to pass to the ath9k kernel module..)

3) Hostapd seems to have problems at boot and if I try to connect to the WPA2 protected network after a server reboot it keeps telling me that I'm using a wrong password... I can not find useful messages in my syslog... if I restart the hostapd, everything works.. again, it worked before the upgrade. At present time I've solved the issue by adding a post-up directive to br0:
```

auto br0
[...]
post-up /etc/init.d/dhcp3-server start
post-up /etc/init.d/linux-igd start
post-up /etc/init.d/hostapd restart

```
As you can see, I need to start again also linux-igd (the upnp daemon) and dhcp3 since they fail to start up since the bridge is not ready yet when their respective startup scripts are invoked... maybe you have some useful ideas also to avoid these post-up directives and to tell dhcp3 and linux-igd to start after br0 is ready or to keep trying until br0 is ready.

---

### Post by Xylian on 2010-10-17
BUMP: anyone can help?

---

### Post by berland on 2010-10-26
I can confirm that I had the same issue and that I could solve it by adding sleep to  /etc/network/interfaces.

Thanks for your tip!
[INDENT]
[FONT="Fixedsys"]auto lo br0

iface lo inet loopback

iface eth0 inet manual
iface wlan0 inet manual

iface br0 inet dhcp 
   pre-up /bin/sleep 3s   ## HACK FOR UBUNTU 10.10
   bridge_ports eth0 wlan0
   bridge_hw 00:23:54:2a:08:93[/FONT]
[/INDENT]

---

### Post by Xylian on 2010-10-31
> **berland said:**
> I can confirm that I had the same issue and that I could solve it by adding sleep to  /etc/network/interfaces.

Thanks for your tip!
[INDENT]
[FONT="Fixedsys"]auto lo br0

iface lo inet loopback

iface eth0 inet manual
iface wlan0 inet manual

iface br0 inet dhcp 
   pre-up /bin/sleep 3s   ## HACK FOR UBUNTU 10.10
   bridge_ports eth0 wlan0
   bridge_hw 00:23:54:2a:08:93[/FONT]
[/INDENT]
Yesterday the sleep workaround failed, even setting it to 10s... I removed that line and changed the bridge interface initialization in the following way:
```

auto br0
iface br0 inet static
        address 10.0.0.1
        network 10.0.0.0
        netmask 255.0.0.0
        broadcast 10.255.255.255
        bridge-ports eth0 wlan0
post-up /etc/init.d/dhcp3-server start
post-up /etc/init.d/linux-igd start
post-up /etc/init.d/hostapd restart
**post-up /usr/sbin/brctl addif br0 wlan0**

```
Now, it works without the sleep (let's see when it breaks again O_o).

---

### Post by Tombuddy on 2010-11-07
I can confirm that this same exact problem is happening to me on 10.10 hostapd is always asking for the password after a reboot and dhcp3-server dosn't property start on bootup because it is reading the bridge at ip 0.0.0.0 instead of 10.1.1.1 which it changes when the bridge comes up.

If I restart all services manually everything works great.
I tried your workaround and had no luck .....

---

### Post by mkeller on 2011-01-31
Hi everyone, 

the same problem here... 

I think it has something to do with the boot sequence. As far as I can see, the networking stuff has already moved to upstart, the hostapd is still under init. 

Unfortunately I don't know anything about upstart. I just read on wikipedia, that it is able to run start scripts in parallel if they don't depend on each other. 

This may cause some sort of race condition: upstart starts netowrking and then ist fires up the old init stuff. Maybe there's no dependency defined, that init needs the networking. And so your hostapd is startet when networking is not yet ready.

Then, during the time you type in your username and password, networking comes up and running. After this you can fire up the /etc/init.d/hostapd start and it will run without errors. 

For debugging i wrote a ifconfig command in the very beginning of the /etc/init.d/hostapd skript to see which interfaces are already confiured and the only one showing up is the lo0. That's definetely not the one for wireless... ;)

So maybe there's someone out there who knows more about the boot process and upstart in special to get the dependencies right. For the meantime I can live with the post-up hook-hack in /etc/network/interfaces. 


Greetings

Michael

---

### Post by markus_t on 2011-03-09
I have observed the same effect after upgrading the kernel on 10.04.1 from 2.6.32-24-generic-pae to 2.6.35-25-generic-pae. The effect is that despite me telling my linux to initiate the bridge in /etc/network/interfaces with post-up /usr/sbin/brctl addif br0 wlan0 it wont initiate the bridge. Therefore arp requests are not not resolved etc ... If I manually initial the bridge from the user land everything works fine. 

Initiating the bridge manually (or if it works via the interfaces file) is only a workaround - this can IMHO be fixed in the kernel packages. I have reporduced all of this  by compiling the latest stable kernel from source - if I would only know what the magic flag is ....

---

### Post by iverasp on 2011-03-15
Same issue here after upgrading. The workarounds posted by Xylian did not work for me. Currently I'm running a script manually every time the server reboots (whenever there's a power outage) that adds wlan0 to br0 and starts hostapd. This needs more investigation.

---

### Post by tburkhol on 2011-04-04
I don't think post-up is a good solution, because if the post-up fails, the system will believe the interface to be still down.

I moved my post-up config of dhcp3-server and bind to /etc/network/if-up.d scripts, and this seems to work well.

I have wpa_supplicant or hostapd (depending on whether it's the AP or the client) start as pre-up for my wireless interface.  ie:
```

auto wlan0
        iface wlan0 inet static
        address XX
        netmask 255.255.255.192
        broadcast XX
#       pre-up /sbin/wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf -B
        pre-up /usr/sbin/hostapd -B /etc/hostapd/hostapd.conf

```

The other problems I've had seem to be new wireless card not yet fully supported by the kernel drivers.  backports-modules-wireless is some help with this, but new cards seem slow to get even into backports.

---

### Post by sosostris on 2011-05-13
What worked for me, although I only made 1 reboot so far, is to simply put the following to **/etc/rc.local**
```
brctl addif br0 wlan0
```

Regarding the change of tx power **/etc/hostapd/hostapd.conf**:
```

# Country code (ISO/IEC 3166-1). Used to set regulatory domain.
# Set as needed to indicate country in which device is operating.
# This can limit available channels and transmit power.
country_code=XY

```
Just use a country code that fits your needs.

---

