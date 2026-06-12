---
title: "Convert Ubuntu box into a gateway with Wireless WAN"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by dcbrian on 2013-07-16
Hi, I'm trying to use an XUbuntu box as a gateway.  I've done the best I can to render the topology.  Please forgive the poor ASCII art talent!

[FONT=courier new][LAN machine 1]------|
                     |
[LAN machine 2]---[LAN Router]---(eth0)[Ubuntu Box](wlan0)---[WAN]
                     |
[LAN machine 3]------|[/FONT]

I have tried several iptables configurations based on what I've found from other posts.  I've read through an iptables tutuorial.  However, I'm stuck.  This is the most recent attempt at a configuration.

[FONT=courier new]#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i !wlan0 -j ACCEPT
iptables -A FORWARD -i wlan0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o wlan0 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A FORWARD -i wlan0 -o wlan0 -j REJECT[/FONT]

I know this type of thing has been done before, but how to do it has eluded me.

Thank you for any help.

---

### Post by newbie-user on 2013-07-16
Did you enable ip forwarding in /etc/sysctl.conf?

---

### Post by dcbrian on 2013-07-16
Good question.  I should have mentioned this.  I did the following, which I believe has the same effect.

echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by newbie-user on 2013-07-17
> **dcbrian said:**
> echo 1 > /proc/sys/net/ipv4/ip_forward

Yes, I believe that's the same thing; however, I don't think that is persistent. IIRC, that's only good until the next restart. Manually setting it in /etc/sysctl.conf will make it persistent.

Anyway, here's an older tutorial on creating a linux access point: [https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

Glancing at it briefly, I believe it can easily be adapted for more modern Ubuntu releases.

---

