---
title: "Sagem Fast 800 with Ueagle-Atm"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by mar10 on 2006-06-05
Hello. I have problems with ueagle-atm on Ubuntu 6.06.
I follow these [instructions]("http://ubuntuforums.org/showthread.php?t=144468"). Modem works fine (it's operational), but after pppd call ueagle-atm, connection don't work.
Here's /var/log/messages
```

Jun  5 01:20:37 mar10 pppd[7711]: Using interface ppp0
Jun  5 01:20:37 mar10 pppd[7711]: Connect: ppp0 <--> 8.48
Jun  5 01:20:39 mar10 pppd[7711]: Remote message: Access Denied
Jun  5 01:20:40 mar10 pppd[7711]: Connection terminated.

```
I don't know what's wrong.. Is /etc/ppp/chap-secrets case sensitive, cause my password is with low, up-cases.. or what should be wrong???

Thanks for help..

PS: Sorry about my english :)

---

### Post by dvarsam on 2006-06-09
I will provide another Installation instructions of the _Sagem Fast 800 ADSL Modem_:

1. Download the file "eagle-usb-2.3.2.tar.bz2" from:
    [http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2](http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2)

2. Unzip the file using the command ```
tar jxfv eagle-usb-2.3.2.tar.bz2
```

3. Then "cd eagle-usb-2.3.2"

4. Then: ```
/configure
make uninstall
make clean
make
su -c 'make install'
```

5. Then ```
eagleconfig
```

6. Add the country (e.g. for Greece, type "GR01"), user (e.g. [email]tony@forthnet.gr[/email]), & password.

7. Then give it some time for the "synchronization" procedure...

8. Then, type: ```
startadsl
```

9. If you do not get connected to the Net, type: ```
eaglectrl -w
``` & then type again ```
startadsl
```

Good Luck!

---

### Post by mar10 on 2006-06-10
dvarsam: What version of Ubuntu are you using? This eagle-usb don't work on Ubuntu 6.06. Make of eagle-usb-2.3.2 failed. This is because of new version of Kernel.
Anyway, thanks for reply.

---

### Post by mar10 on 2006-06-11
Well, problem is solved. Problem was with
```
/etc/ppp/pap-secrets
```
where i must add following line...
```
"login" "*" "passw" "*"
```

---

### Post by swigrid on 2007-01-07
--

---

