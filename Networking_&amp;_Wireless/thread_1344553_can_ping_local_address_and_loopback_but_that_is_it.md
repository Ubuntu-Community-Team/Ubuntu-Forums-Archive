---
title: "can ping local address and loopback but that is it"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2009-12-03
Hi there, I have a 2nd Jaunty system on the blink, 

I have firestarter installed then uninstalled, then re-installed from the cache after internet went down.

anyway I can ping 127.0.0.1 and 10.1.1.44 (my static address for interface)

firestarter picks up no activity but network tools does.

So I ```
iptables -F
``` but still nothing.


I don't have network manager installed so I use a script which works if I use it on my Backtrack install, so how can I reset my networking..... i though iptables - F would do it but apparently not...

here is a copy of my interfaces file, I suspect it is wrong

```

auto eth0
iface wlan0 inet static
netmask 255.0.0.0
network 10.1.1.0
broadcast 10.1.1.255
address 10.1.1.44
gateway 10.1.1.1
essid DLINK key
```> 




please help

---

### Post by chili555 on 2009-12-03
> auto eth0
iface wlan0 inet static
netmask 255.0.0.0
network 10.1.1.0
broadcast 10.1.1.255
address 10.1.1.44
gateway 10.1.1.1
essid DLINK keyI suggest changing it to this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 10.1.1.44
netmask 255.255.255.0
gateway 10.1.1.1
essid DLINK
key xxxxxxxx
```Is the essid of your network really DLINK? or Dlink? or dlink? It must be letter-perfect in *interfaces*. Check with:```
sudo iwlist wlan0 scan
```May I assume you are using WEP encryption? Replace 'xxxxxxxx' with your HEX key. If encryption is turned off, remove the key line from *interfaces*.

Did you set up */etc/resolv.conf*? How about letting us take a peek?```
cat /etc/resolv.conf
```Please post the result.

---

### Post by andytof47 on 2009-12-03
sure thing i'll let you take a peek,
here 'tis

```
nameserver 10.1.1.1
```

so it's just set to the gateway....... I could set them to public servers but I know the DNS is ok on the network.

I'll be sure to adjust and let you know 'bout my internet.

oh and yes the name is exactly right, been caught out on that b4 but thanks 4 your help

---

### Post by andytof47 on 2009-12-03
cheers mate worked a treat except I think I have the format wrong for the wireless part

my file looked like this

```
auto wlan0
iface wlan0 inet static
address 10.1.1.44
netmask 255.0.0.0
gateway 10.1.1.1
essid DLINK key XXXX
```

but I changed it to this and will reboot later, but the good news is i'm writing this on my ubuntu installed on my HDD instead of a live CD

changed to this

```
auto wlan0
iface wlan0 inet static
address 10.1.1.44
netmask 255.0.0.0
gateway 10.1.1.1
essid DLINK
key 
```

i'm on a funny netmask so don't worry bout that she works:p

---

### Post by andytof47 on 2009-12-03
hi, I have rebooted and most of it works but It still doesn't do any of the wireless association, unless I manually copy and paste the essid,/key

as soon as I do that i'm fine.....


any suggestions?

---

### Post by chili555 on 2009-12-03
> nameserver 10.1.1.1Perfect.> any suggestions?Yes. Don't catch old Chili when he's rushing to the doctor! Please try this:```
auto wlan0
iface wlan0 inet static
address 10.1.1.44
netmask 255.0.0.0
gateway 10.1.1.1
[COLOR="Red"]wireless-[/COLOR]essid DLINK
[COLOR="Red"]wireless-[/COLOR]key 0123etc.
```Restart networking and check my sometimes hasty work:```
sudo /etc/init.d/networking restart
```Post back and give me some good news, please.

---

### Post by andytof47 on 2009-12-03
i'll be sure about the chilli :)

thanks for the details really appreciate it

---

