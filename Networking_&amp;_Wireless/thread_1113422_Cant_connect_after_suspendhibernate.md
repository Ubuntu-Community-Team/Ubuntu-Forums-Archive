---
title: "Cant connect after suspend/hibernate"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by psyberpnk on 2009-04-01
Every time I resume from standby or hibernating I loose my Internet connection and cannot reconnect without rebooting.  Note that this is a wired connection.

I have tried restating the network manager using the following command and it still does not work.

```
sudo /etc/init.d/networking restart
```anyone have a suggestion?

Thanks,
Psyberpnk

---

### Post by psyberpnk on 2009-04-03
Bump.  Any ideas?

---

### Post by SirWeazel on 2010-01-01
I think i'm having similar issue. Sometimes after the computer resumes from standby, i loose my internet connection. It appears to happen after the computer has been on standby (S3) for awhile.  When this happens i can still log into my router (WRT310N), but can not access the interent from firefox/opera. To fix the issue i click on the network manager icon, then click "auto", and it disconects and establishes connection again.

This is wierd becuase of couple reasones:

- i'm able to access router and its settings, but not the internet.
- when the computer comes out of standby, network manager shows it is reistablishing a connection. But i can't access internet until i click auto for it to reistablish connection again.

What do u think is going on? Running ubuntu 9.10 on asus A8n32-sli deluxe. Network adapters according to network manager Marvell 88E8053 PCI-E gigabit integrated controller, and nvidia CK804 integrated controller. I currently have it connencted to the nvidia one, but have tried both with no success. Hard wired on a WRT310N router. 

Thank you for any help you can provide.

---

### Post by SebXX on 2010-04-16
Hi there,
I'm seeing the exact same symptoms on Ubuntu 9.10 Karmic with only one of my two interfaces 
Here's the one causing troubles : 
```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
```

Anyone found a workaround for this ? (annoying to prevent the computer from sleeping)

In the meantime I tried : sudo gedit /etc/default/acpi-support 
And modified the following section
```
# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu **eth2**"
```
Thanks!

---

### Post by SirWeazel on 2010-04-20
I wish i could help, but my problem ended up being with the router.... and it happens with any distro (XP, Vista, Linux, Smart Phones). Funny that my super old Blue router still works like a charm and my new "N" router stinks.

---

