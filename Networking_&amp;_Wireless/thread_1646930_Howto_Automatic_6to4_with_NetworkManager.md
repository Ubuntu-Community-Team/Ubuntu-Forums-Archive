---
title: "Howto: Automatic 6to4 with NetworkManager"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by zebastian on 2010-12-16
Just set this up on my computer, Ubuntu 10.10. Borrowed most of the script from [Parallel]("http://ubuntuforums.org/showthread.php?t=825122").

**!!! If you are behind a NAT, you wont get a IPv6 address that's reachable from the outside world. !!!**  But you still can reach(ping) the outside world, at least did I. If you want a well functioning IPv6 connection from behind a NAT you should use Teredo or some tunnelbroker like sixxs.net. 

1. Start a terminal emulator, e.g. gnome-terminal. 

2. # sudo bash
   # cd /etc/NetworkManager/dispatcher.d
   # vi 6to4

3. Press the letter "i" once to start input mode. 

4. Copy script from below, right click in terminal and select Paste.

5. Terminal again: [Esc] once to exit input mode. ":wq" [enter] to save script and exit.

6. # chmod +x 6to4
   for the right permissions

```
#!/bin/sh

IF=$1
STATE=$2

if [ "$STATE" = "up" ]; then

IPV4=`/sbin/ip -4 addr show dev $IF|grep "^ *inet"|sed -r -e 's:.*inet ([0-9\.]+)/.*:\1:'`
IPV4STRIP=`echo $IPV4 | tr "." " "`
IPV6=`printf "2002:%02x%02x:%02x%02x::1" $IPV4STRIP`

echo $IPV4 >> /tmp/IPV6DEBUG
echo $IPV4STRIP >> /tmp/IPV6DEBUG
echo $IPV6 >> /tmp/IPV6DEBUG

/sbin/ip tunnel add tun6to4 mode sit ttl 64 remote any local $IPV4 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip link set dev tun6to4 up 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip -6 addr add $IPV6/16 dev tun6to4 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip -6 route add 2000::/3 via ::192.88.99.1 dev tun6to4 metric 1 2>&1 >> /tmp/IPV6DEBUG

else

/sbin/ip -6 route del 2000::/3 via ::192.88.99.1 dev tun6to4 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip link set dev tun6to4 down 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip tunnel del tun6to4

fi
```

---

