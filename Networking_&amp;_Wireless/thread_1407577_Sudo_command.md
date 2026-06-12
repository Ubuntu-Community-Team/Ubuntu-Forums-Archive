---
title: "Sudo command"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Visello on 2010-02-15
Hello i have been working alot getting my computer online on wireless agian and now i have but i have to type this following command

sudo route add default gw 192.168.1.1

Any way i can get it to pick that ip it self since i shall type that each time i re-boot my computer?

---

### Post by Cabs21 on 2010-02-15
you could write it into a script and have the script run at the beginning of every boot.  Also there should be a setting in your network manager to use a permanent IP address instead of the first available one.  You might, depending on your router, be able to set that IP address as your permanent IP in the router itself.  This way when ever you connect to your network your router will give you a predetermined IP address and will not allow other computers to use that IP.

---

### Post by slakkie on 2010-02-15
man interfaces

cat /etc/network/interfaces :)

---

### Post by Iowan on 2010-02-15
If you're using Network Manager, the IPv4 Settings tab has a Routes button.

---

### Post by Visello on 2010-02-16
Cheers sorry for the long delay on reply was alittel tired got some longs days on work i will try look into these things and post back what i do etc

---

