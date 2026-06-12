---
title: "Static IP changed back to DHCP IP every few hours."
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by Kane Hart on 2010-06-27
So I'm running ubuntu 10.04 and my issue is I have a server on ESXi and I have of course it set to a static IP and every few hours it loses connection and grabs the ip DHCP would grab and not even assigned so I would guess DHCP kicks in again.


```
nano /etc/network/interfaces
```This is the contents I did star out most my IP for personal protection not like it matters much but anyways.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address *.*.65.141
netmask 255.255.255.248
gateway *.*.65.137
```
So when this happens like the IP gets switched back to *.*.65.138 the same IP DHCP grabs then I have to run this command: sudo /etc/init.d/networking restart and then it gets *.*.65.141 again.

---

### Post by Kane Hart on 2010-06-27
Think I resolved it someone else can confirm since this happen 2-3 times a day I will not find out right away.


sudo apt-get remove dhcp-client

---

### Post by sanderj on 2010-06-27
I would not set /etc/network/interfaces by hand; I guess it can be overwritten.

Best way to set a static IP (IMHO): via the GUI. So right-click on the network icon, then Edit Connections, and then set what you want to set.

See screendump.

---

### Post by Kane Hart on 2010-06-27
I'm a very by hand type of person :P Even more when this a server :)

---

### Post by fogjuice on 2010-06-28
I just stumbled across this thread on google because unfortunately I'm having a very similar problem.

Does anyone know how to fix this? I can't use the GUI either because I'm running this on a server.

---

### Post by Kane Hart on 2010-06-28
I just trying sudo aptitude remove network-manager

I will let you know if it works and hopefully someone else who knows what the hell their doing will pitch in.

---

### Post by endotherm on 2010-06-28
as close as i can tell, network-manager is a gnome only thing, so it prolly isn;t there on a cli server. I'm more inclined to blame dhcp so hopefully removing it did the trick.
if not, check your logs (/var/log/auth.log, /var/log/kern.log, /var/log/messages, and any others that have been updated since the last fix), to see if you can get any clues about what is going on.

---

### Post by Kane Hart on 2010-06-28
Yeah I still have the problem with all what I have done so far :(

I also checked all 3 logs and nothing. Going try full server reset.

---

### Post by Charlietje on 2010-06-28
Question:

Is your ubuntu a gnome box, or 100% server edition with only cli?

if a gnome box, do as Kane Hart said:
sudo aptitude remove network-manager


regards

---

### Post by Iowan on 2010-06-28
@Kane Hart:
Same question as above - is yours a server (CLI) or desktop-turned-server (GUI/NM)? 
Was it originally set up with static address (or did it have DHCP address at one time)?
With dhcp-client removed, does **sudo dhclient** do anything?

---

### Post by Kane Hart on 2010-06-29
> **Iowan said:**
> @Kane Hart:
Same question as above - is yours a server (CLI) or desktop-turned-server (GUI/NM)? 
Was it originally set up with static address (or did it have DHCP address at one time)?
With dhcp-client removed, does **sudo dhclient** do anything?


Darn ya hehe yes sudo dhclient does mess up the system again back to the dhcp ip and yes it was originally done by dhcp but their was some conflicts since I run ESXi and 2 or more VM's were fighting for the same IP so I decided to static ip each VM.

All them work fine but this one that keeps going back to DHCP :P

---

### Post by Kane Hart on 2010-06-29
This issue is still going on just happen.

---

### Post by Iowan on 2010-06-29
[Here]("http://ubuntuforums.org/showthread.php?t=1489690") is a similar thread. [This]("http://ubuntuforums.org/showthread.php?t=1463506") thread has more information...

---

### Post by Kane Hart on 2010-06-30
Thanks going to try the following next:

```
$ sudo killall -v -9 dhclient
Killed dhclient(14064) with signal 9
$ sudo chmod -x /sbin/dhclient
$ sudo chmod +x /sbin/dhclient
```

---

