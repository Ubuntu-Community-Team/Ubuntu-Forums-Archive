---
title: "macchanger script"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by j_arquimbau on 2010-03-24
Hello,

I'm trying to create an script so that the mac address get changed at the boot for every interface in the computer (eth0, wlan0, etc...).

I've tried with 
```
for IFACE in $(ifconfig -a -s | egrep -v "^(lo|Iface)" | cut -f 1 -d" ")
do
        macchanger -r $IFACE
done
```
and with ```
#!/bin/sh

# Radomize the mac address for the given interface
/usr/bin/macchanger -r $IFACE
```
but they don't work.

The answer to the first one is:
```
ERROR: Can't change MAC: interface up or not permission: Operation not permitted

```
which doesn't change when I type ```
sudo ifconfig wlan0 down
```
and to the sencond one:
```
GNU MAC Changer
Usage: macchanger [options] device

Try `macchanger --help' for more options.

```

It would also be nice if there was a little program which would ask you at the boot if you want to change the mac address.

Any help so far? Thank you

---

### Post by j_arquimbau on 2010-04-09
I finally decided to use macchanger-gtk. I didn't even know there was a GUI for macchanger.

---

### Post by thabelo on 2010-04-09
1: Disable all networks from the top right [i am using ubuntu so its on my right]
2: open terminal  and install airmon then:
               sudo airmon-ng stop wlan0  [wlan0 for wireless can be any]
3: sudo ifconfig wlan0 down
4: sudo macchanger --mac xx:xx:xx:xx:xx:xx  waln0    [any mac you want]
5: sudo airmon-ng start wlan0 

and you are done just set 
sudo ifconfig wlan0 up
then enable all networks on the top right [i am using ubuntu so its on my right]

---

