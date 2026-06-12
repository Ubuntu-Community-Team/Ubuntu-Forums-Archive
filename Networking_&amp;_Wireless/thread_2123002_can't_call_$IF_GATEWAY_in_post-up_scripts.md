---
title: "can't call $IF_GATEWAY in post-up scripts"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by mattator on 2013-03-06
Hi,

I've created a script in /etc/network/if-up.d/my_script so that when an interface gets up, it creates a new routing table (and deletes it when the interface goes down):

Here is the script:
```

echo "Setup routing table \"$IFACE\" for address \"$IF_ADDRESS\", gateway \"$IF_GATEWAY\""

ip rule add from $IF_ADDRESS table $IFACE

# cree la route pour acceder a la gateway
ip route add $IF_NETWORK dev $IFACE src $IF_ADDRESS table $IFACE
ip route add default via $IF_GATEWAY dev $IFACE table $IFACE

```

The problem is that $IF_ADDRESS and $IF_GATEWAY are set only if I set them manually in /etc/network/interfaces but in case the interface goes up with dhcp, these variables are not set (though they should be recovered by dhcp). Is this the normal behavior and how would you advise me to circumvent this problem (how to retrieve gateway/network/address from the interface name $IFACE which is always set).

Regards

Matt

---

