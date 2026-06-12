---
title: "Renew ip address without rebooting PC+Modem"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by qwertyzxcv on 2010-12-28
I have a cable modem
No router
2 PCs, one with windows XP and one with an old version of ubuntu

To access the internet on either PC, I simply disconnect the ethernet cable from one PC and connect it to the other

The problem is, after each time I do this, I need to renew the ip address.

On my windows PC, it's simply. I simply run the command ipconfig /renew

**On my ubuntu PC, nothing that I've tried so far has worked. I need to reboot the PC and the modem every time. This is too tedious. How can I renew it easily?**

---

### Post by howefield on 2010-12-28
Have a look at the ifconfig up/down commands.

```
man ifconfig
```

for more info.

---

### Post by qwertyzxcv on 2010-12-28
When I try to use 

ifconfig up

or

ifconfig down

it says: error fetching interface configuration. device not found


however, when i reboot the PC and the modem, it works. i have a wired connection - dhcp

i need a way to do this without rebooting every time

---

### Post by howefield on 2010-12-28
I am updating a Vista VM so don't want to check it, but I think it is something like...

sudo ifconfig interface options that you'd need to use.... for example

```
sudo ifconfig eth0 down
```



As I say, man ifconfig will give you more info.

---

### Post by daimaru on 2010-12-28
[COLOR=Red]method 1:[/COLOR]
to release
```
sudo dhclient -r
```then to obtain new ip
```
sudo dhclient
```[COLOR=Red]
method 2:[/COLOR]
```
sudo /etc/init.d/networking restart 
```
[COLOR=Red]method 3:[/COLOR]
```
sudo ifdown eth0
sudo ifup eth0
sudo /etc/init.d/network restart 
```

@least i think that should work.

---

### Post by qwertyzxcv on 2010-12-28
when i type 

sudo ifconfig eth0 up
sudo ifconfig eth0 down

nothing at all appears to happen when i type them


when i type sudo dhclient -r 

it says there is already a pid file var/run/chclient.pid with
pid number <####> 
killed old client process, removed pid file

when i type sudo dhclient it says

DHCPDISCOVER on eth0 to 255.255.255.255 port <#> interval <#>
DHCPDISCOVER on eth0 to 255.255.255.255 port <#> interval <#>
DHCPDISCOVER on eth0 to 255.255.255.255 port <#> interval <#>
DHCPDISCOVER on eth0 to 255.255.255.255 port <#> interval <#>

no dhcpoffers received
no working leases in persistent database - sleeping


the method 2 and 3 you mentioned gives me the same result as the menthod 1 you mentioned

---

### Post by daimaru on 2010-12-28
crap sorry i couldnt help. guess your not using dhcp. weird though that a network restart does not work either

---

### Post by qwertyzxcv on 2010-12-28
hmm in my network settings i do have it set to dhcp. is it responding as if i'm not using dhcp? what would cause that?

---

### Post by qwertyzxcv on 2010-12-28
so maybe the problem isn't renewing the ip address? that works for my windows PC, but it doesn't seem like it's going to work for the ubuntu PC? restarting the pc+rebooting the modem gives the ubuntu PC a connection, but when I switch to my windows PC and then back to the ubuntu PC,  i need to restart+reboot again.... what could be causing this?

---

### Post by pricetech on 2010-12-28
Cable modems associate themselves with a particular MAC address and don't talk to any other.  Restarting the modem allows it to associate with a new MAC.

The only thing that doesn't make sense is your Windows box connecting without restarting the modem.

Anyway, routers aren't that expensive.  Pick one up and save yourself the headache.

---

