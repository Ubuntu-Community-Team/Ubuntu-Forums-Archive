---
title: "Can't Access Samba Share via Hostname"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by Wardrop on 2012-11-01
I seem to get this a lot. I can never access my Samba shares via hostname, though they're always accessible via IP address. I've googled this for an hour, and while a lot of people seem to experience this, the solutions vary and nothing has worked for me. Obviously, DNS is the first thing one would check, but this seems to account for the majority of the solutions I came across.

Basically, when accessing the share via name rather than IP (I've tried multiple A records and C names that point to the box), Samba fails to authenticate the user. The log shows relatively useless information, as usual, so I'm at a loss as to what I need to do to get this to work. Both SMBD and NMBD are running, and everything works perfectly when I access the shares via IP address.

One thing worth noting is that I CAN access the samba share via hostname from my Mac. I can only conclude that OS X resolves the IP address before attempting to connect. It's obviously an issue with Windows trying to talk to Samba via hostname. It could well be a Netbios issue, but I don't know where to begin troubleshooting.

Any help is much appreciated.

---

### Post by bab1 on 2012-11-02
> **Wardrop said:**
> I seem to get this a lot. I can never access my Samba shares via hostname, though they're always accessible via IP address. I've googled this for an hour, and while a lot of people seem to experience this, the solutions vary and nothing has worked for me. Obviously, DNS is the first thing one would check, but this seems to account for the majority of the solutions I came across.

Basically, when accessing the share via name rather than IP (I've tried multiple A records and C names that point to the box), Samba fails to authenticate the user. The log shows relatively useless information, as usual, so I'm at a loss as to what I need to do to get this to work. Both SMBD and NMBD are running, and everything works perfectly when I access the shares via IP address.

One thing worth noting is that I CAN access the samba share via hostname from my Mac. I can only conclude that OS X resolves the IP address before attempting to connect. It's obviously an issue with Windows trying to talk to Samba via hostname. It could well be a Netbios issue, but I don't know where to begin troubleshooting.

Any help is much appreciated.

All SMB resources (the Samba share) are ID'd with this format //NETBIOS_NAME/share_name (or //IP_address/share_name).  If you have working hosts files or a local DNS server the the Samba naming daemon (nmbd) will convert DNS hostnames to NETBIOS names.  

Are you trying to browse or connect to Samba shares from an Ubuntu client?  Is the Samba client on the same host as the Samba server?   From the terminal, what is the output from this ```
smbtree
```

---

