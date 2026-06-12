---
title: "Ping linux hostname from windows"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by M1Sports20 on 2008-12-08
I am guessing this has been answer.  I just can't seem to find the answer.

I can't ping my linux box hostname from my windows box.  However, I can ping my windows box hostname from linux.(I don't have samba install).  I can ping both machines from each other using ip address.  I also don't want to use static host files as I have dns/dhcp on my dd-wrt router.

What could be wrong?

Thanks.

---

### Post by tvtech on 2008-12-08
install samba ;)

---

### Post by M1Sports20 on 2008-12-08
I tried installing samba4 and when I set the Netbios name I still can't ping it from windows.

---

### Post by psusi on 2008-12-08
Installing samba should do the trick, otherwise you need to configure your dns server to know the host name.

---

### Post by Iowan on 2008-12-08
Dunno if installing **winbind** will help...

---

### Post by M1Sports20 on 2008-12-08
So I installed samba and Set NetBios Name = M1Sports20.

From the windows command line typing ping M1Sports20 does not work.  Is there anything else I need to do.  I know I can program my dns server to know the hostname.  But the dns server should be able to know the hostname of my box when it assigns an ip to my box.

---

### Post by Iowan on 2008-12-08
> **M1Sports20 said:**
> So I installed samba and Set NetBios Name = M1Sports20.

From the windows command line typing ping M1Sports20 does not work.  Is there anything else I need to do.  I know I can program my dns server to know the hostname.  [COLOR="Red"]But the dns server should be able to know the hostname of my box when it assigns an ip to my box.[/COLOR]**dnsmasq** reportedly ties DHCP with dns - the average dns server does not issue DHCP addresses.

---

### Post by M1Sports20 on 2008-12-08
I have dnsmasq on my dd-wrt router with enabled Local DNS.  So I would think that would work.  But it doesn't

---

### Post by handydan918 on 2008-12-08
One of the easiest things you can do on a small lan is to use MAC address reservations. IOW, tell the router to assign (still via dhcp!) the same IP address to a particular MAC address every time. All the advantages of static IP's with none of the disadvantages.

---

### Post by M1Sports20 on 2008-12-09
Well, I can ping the linux box from windows now.  I don't know what happened, I just woke up this morning and it worked.  Does NetBios take a while to propagate to other machines.

---

### Post by Iowan on 2008-12-09
> **M1Sports20 said:**
>  Does NetBios take a while to propagate to other machines. I've read that it can take 15-20 minutes.
Glad you got it working.  Some day I'm gonna put dnsmasq on my server...

---

