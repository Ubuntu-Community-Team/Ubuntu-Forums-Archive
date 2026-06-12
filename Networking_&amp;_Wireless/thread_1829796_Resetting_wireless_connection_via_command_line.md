---
title: "Resetting wireless connection via command line"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by Omegaham on 2011-08-20
Hey guys, I have a quick question.

How do you reset a connection via the command line?

I'm using a friend's wireless network, and for some reason it stops randomly. It still says that I'm connected, but no traffic goes through. This problem gets fixed by clicking the Wireless Networks tab on the Menu bar, going down to that network, and clicking it again. Ubuntu then disconnects and tries to reconnect again.

What I'd like to do is to be able to automate this; I want to make a shell script that will ping Google every minute or so, and if it doesn't get a response, reset the connection.

How would I go about doing this? I've been looking at iwconfig and the other internet tools, but they don't seem to be helping.

Thanks in advance!

---

### Post by papibe on 2011-08-20
Either this:
```
$ sudo service networking restart
```
or this:
```
$ sudo /etc/init.d/networking restart
```
Regards.

---

### Post by Omegaham on 2011-08-20
> **papibe said:**
> Either this:
```
$ sudo service networking restart
```or this:
```
$ sudo /etc/init.d/networking restart
```Regards.

Hello,

The first one returned the following: 
```
restart: Unknown instance: 
```

The second one returned the following:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

Neither reset the connection, though. Is there something inside /etc/init.d/networking that I can change to do this?

---

### Post by Omegaham on 2011-08-20
> **papibe said:**
> Either this:
```
$ sudo service networking restart
```or this:
```
$ sudo /etc/init.d/networking restart
```Regards.

Hello,

The first one returned the following: 
```
restart: Unknown instance: 
```The second one returned the following:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```Neither reset the connection, though. Is there something inside /etc/init.d/networking that I can change to do this?

---

### Post by Idefix82 on 2011-08-20
I don't know why the command that papibe suggested didn't reset the connection, but another option is to bring the interface down and then up again:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

```
You need to replace 'wlan0' by the correct name of your wireless interface. If the network manager is set to connect automatically to the wireless network, then you shouldn't have to do anything after restarting the interface.

To actually fix the problem, I would look into the configuration of the wireless router. My guess would be that it gives out an IP address with very short validity. Does the same problem occur with other wireless networks or under a different operating system?

---

### Post by praseodym on 2011-08-21
Try

```
sudo service network-manager restart
```

---

### Post by Omegaham on 2011-08-21
> **praseodym said:**
> Try

```
sudo service network-manager restart
```

Worked beautifully. Thank you very much!

---

