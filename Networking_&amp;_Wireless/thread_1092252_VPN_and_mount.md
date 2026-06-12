---
title: "VPN and mount"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by borobudur on 2009-03-10
Hi, I have a VPN connection (in Intrepid) and would like to call a mount command after the connection is established. 

I'm losing the connection once in a while so I was thinking to add the mount to a existing VPN script.

Does anyone know where I could place that mount command the best?

---

### Post by puppywhacker on 2009-03-10
you can point to a script per interface in the interfaces file. below I assume (wrongly) your interface is vpn0, and I also assume (wrongly) your mount command

```
/etc/network/interfaces
iface vpn0 inet dhcp
        up mount -f cifs //server/share

```

alternatively you can add a script in
```
/etc/network/if-up.d
```

you could 
```
ifup vpn0
```

---

### Post by borobudur on 2009-03-10
It was surprisingly simple to configure VPN over the graphical interface. 
With a *ifconfig* I don't see any *vpn0*. I'm working with my wlan. But if I go over *wlan0* I don't solve my problem of disconnection.

---

### Post by borobudur on 2009-03-16
I guess I checked it when I was disconnected. Well yes, I see my vpn in the *ifconfig* output. It's called *tun0*.
And it works perfectly with this command in the /etc/network/interfaces file:
```
iface tun0 inet dhcp
        up mount -t cifs -o 'username=me,password=mypasswd,domain=subdomain.domain.tld,port=9999,netbiosname=mymachine' '//subdomain.domain.tld/dir' /mnt/local/
        down umount /mnt/local
```Thanks puppywhacker!!

---

