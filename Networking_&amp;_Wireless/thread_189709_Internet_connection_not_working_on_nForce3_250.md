---
title: "Internet connection not working on nForce3 250"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by chainzz on 2006-06-05
First my motherboard specs: Gigabyte GA-K8NS (rev. 2.0) with nForce 3 250 chipset.
(I'm using the onboard ethernet controller)

Since the final release of Dapper my internet connection isn't working the way it should be. When I boot up most of the time the internet connection isn't working until I manually deactivate and active eth0 in System -> Administration -> Networking. In Breezy and the Dapper beta everything was working fine. I already tried to install the nForce drivers from Nvidia.com but it didn't work. I also tried this: [http://ubuntuforums.org/showthread.php?t=186848](http://ubuntuforums.org/showthread.php?t=186848), but without any positive result. I have no idea what's going on here and I don't know any more things to try. Does anyone know a fix to this problem?

---

### Post by chainzz on 2006-06-05
I tried the following now:
```
sudo gedit /etc/network/interfaces
```
Then I added this:
```
gateway 192.168.0.1
```
Under this:
```
auto eth0
iface eth0 inet dhcp
```

Change 192.168.0.1 to the adress of your gateway (router).

(I got this from a topic somewhere here on the forums, I can't find it anymore)

It seems to be working for me, I already rebooted a few times and all the times the internet worked.

---

### Post by Daboo on 2006-06-05
[QUOTE=chainzz]

Change 192.168.0.1 to the adress of your gateway (router).

(I got this from a topic somewhere here on the forums, I can't find it anymore)

It seems to be working for me, I already rebooted a few times and all the times the internet worked.[/QUOTE]

I've got the same mobo and I'm having the same problem. Except for me, when I hit activate the dhcp request just times out. I don't have a router though; I'm plugged directly into the modem (I have Current broadband). What would I use for the gateway, or does that not make sense here?

---

### Post by chainzz on 2006-06-05
[QUOTE=Daboo]I've got the same mobo and I'm having the same problem. Except for me, when I hit activate the dhcp request just times out. I don't have a router though; I'm plugged directly into the modem (I have Current broadband). What would I use for the gateway, or does that not make sense here?[/QUOTE]
If you're plugged directly into the modem you shouldn't need to set a gateway.  But it looks like this isn't the solution; it worked for me a few times but now my internet again doesn't work without deactivating - reactivating my ethernet controller.

It looks like there are a lot of networking problems with Dapper, especially with nForce chipsets...

---

### Post by chainzz on 2006-06-05
It seems that there is no real solution for this problem at the moment (I can't find one), I just disabled the ethernet controller in the BIOS and installed an old Realtek RTL8029AS network card I still had lying around somewhere. Everything works perfect now, but I hope this will be fixed as soon as possible.

---

### Post by Daboo on 2006-06-05
Bummer. Looks like its time to go digging for an old NIC....

---

