---
title: "Unlocking internet connection via cli"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by vik_2010 on 2010-05-01
Upon first turning on my computer, I need to input my password in order to allow network manager to activate my wireless connection (I'm just guessing how this works. Please correct me if I'm wrong.) To do this, I need to be using X

But what if I want my computer to go straight to a terminal when I turn on my computer? How would I access the internet from a tty, since currently the only manner I know how to do it is through X?

Regards,

-V

---

### Post by chili555 on 2010-05-01
If it is to be set up permanently in single user mode; that is a blinking cursor on a black screen, such as a server, then the usual way is to populate /etc/network/interfaces something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```You probably want static addresses in a server so you can administer it with ssh. It will start and connect on boot.

If you just want to run single user once, you can probably just do:```
sudo ifconfig eth0 192.168.1.101 up
```You will also need to fix up /etc/resolv.conf:```
sudo su
echo "nameserver 192.168.1.1" > /etc/resolv.conf
exit
```Obviously, substitute your details. Post back if you need examples for wireless and be sure to specify WEP or WPA.

---

### Post by vik_2010 on 2010-05-01
This is actually for a wireless connection. If you could help me with that, I'd appreciate it.

---

### Post by Iowan on 2010-05-01
The "Available to all users" checkbox *should* make the connection activate on power-up (though I haven't tested it...).

---

### Post by chili555 on 2010-05-01
> **Iowan said:**
> The "Available to all users" checkbox *should* make the connection activate on power-up (though I haven't tested it...).Hey, you got a demotion! Moderator! Congratulations.

I don't believe Network Manager can run without X.

---

### Post by chili555 on 2010-05-01
> **vik_2010 said:**
> This is actually for a wireless connection. If you could help me with that, I'd appreciate it.WEP or WPA?

---

### Post by vik_2010 on 2010-05-01
wep

---

### Post by chili555 on 2010-05-01
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid mylilrouter
wireless-key 01234ABCDE

#auto eth0
iface eth0 inet dhcp
```When you boot into single user mode, it should start on boot.

---

### Post by Iowan on 2010-05-01
> **chili555 said:**
> 
I don't believe Network Manager can run without X.:oops:Oops, I didn't get to the 2nd paragraph...
OK, I'm awake again, and agree that */etc/network/interfaces * would be the logical choice...

---

### Post by vik_2010 on 2010-05-01
hmm ... my wireless connection is eth2, not wlan0. 

thanks for the advice.

---

### Post by chili555 on 2010-05-01
> **vik_2010 said:**
> hmm ... my wireless connection is eth2, not wlan0. 

thanks for the advice.Obviously, substitute your details.

---

### Post by vik_2010 on 2010-05-02
Some things came up, so I wasn't able to check it out till now.

I substituted eth2 for wlan0. Also, my router uses DHCP, so I changed static to dhcp. This is what  I had then:

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp
wireless-essid venky
wireless-key 2346234

I restarted my computer to see if this would work, but I couldn't go directly to a terminal and access my wireless interace; I had to login to X before I got that little pic that says "Network connected" - and THEN I could go back to my shell and do whatever I wanted.

If you see anything I'm doing wrong, I would appreciate any advise.

---

### Post by chili555 on 2010-05-02
As I said, this works fine if you boot into single user mode. If you boot into X and then go back to single user, well, the results are unsure.> Also, my router uses DHCP, so I changed static to dhcp.Your router uses DHCP but it is not limited to DHCP. It will allow static IPs as well. If this is to be a server or MythTV or some such and run headless, that is sitting in a corner without a monitor attached, how can you get to it to administer it with DHCP, that is, an ever changing IP address? Just be sure to assign a static address well outside the range of the DHCP server. You can look in the router's administration pages or just guess; most consumer routers start at 192.168.x.1 and reserve 50 addresses for DHCP. You can generally safely use static IPs above 192.168.x.100.

Here is a tutorial that explains how to temporarily edit your GRUB options to boot into single user mode. [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Generally, to get to the GRUB menu, press Esc as the computer is booting.

Your settings look fine. Does your WEP key have 10 or 26 characters?

---

