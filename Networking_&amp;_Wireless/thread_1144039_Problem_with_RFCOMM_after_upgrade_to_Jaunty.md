---
title: "Problem with RFCOMM after upgrade to Jaunty"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by jobrahms on 2009-04-30
A couple of weeks ago I set up my Motorola Q as a bluetooth modem using the instructions here:

[http://ubuntuforums.org/showthread.php?t=629528]("http://ubuntuforums.org/showthread.php?t=629528")

Everything worked perfectly. Then I upgraded to Jaunty. Here is the output of dial-motoq.sh:

```
Finding PDAnet Channel on MotoQ:
Dialing channel 1:
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: Permission denied
--> Cannot open /dev/rfcomm0: Permission denied
--> Cannot open /dev/rfcomm0: Permission denied
```

and this is what I get from trying to connect with rfcomm directly:

```
sudo rfcomm connect 00:1A:1B:1D:BF:AE 1
Can't connect RFCOMM socket: Host is down
```

Any ideas?

---

### Post by jtfowl0 on 2009-04-30
I have this same problem following an upgrade to jaunty.  Anybody have any ideas?

---

### Post by jobrahms on 2009-05-07
Anyone have any ideas?

---

### Post by mrsynock on 2009-05-11
try to add 0 or 1 after connect:

```
sudo rfcomm connect 0 00:1A:1B:1D:BF:AE 1
```

to dial you need to do it with sudo. Since jeunty I can't connect anymore with simple user.

---

### Post by quixote_arg on 2009-05-11
> **mrsynock said:**
> 
to dial you need to do it with sudo. Since jeunty I can't connect anymore with simple user.

Any particular reason and/or workaround for that?

---

### Post by mrsynock on 2009-05-11
I think /dev/rfcomm doesn't have good permissions. But I only suppose.

---

### Post by jobrahms on 2009-05-12
It looks like the "Host is down" problem might have been fixed in an update or something since I'm not seeing it anymore. Now it's giving me:

```
sudo dial-motoq.sh 
Finding PDAnet Channel on MotoQ:
Dialing channel 2:
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm2: Permission denied
--> Cannot open /dev/rfcomm2: Permission denied
--> Cannot open /dev/rfcomm2: Permission denied
```

So I guess the permissions changed on those devices. So, I changed this line in dial-motoq.sh:

```
sudo -H -u \#1000 wvdial motoq$CHAN
```

to:
```

sudo -H wvdial motoq$CHAN
```

making that part of the script actually run as root instead of user 1000. Now it's working for me.

---

