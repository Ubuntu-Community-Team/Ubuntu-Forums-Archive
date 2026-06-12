---
title: "DHCP lease times very short after installing 8.10"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by quonsar on 2008-12-24
What is up with this? Every 4 to 12 minutes, DHCP is renewing my IP lease. I never saw this on Hardy. My log is pretty much nothing but:

```

Dec 24 15:51:40 tsidkenu dhclient: DHCPREQUEST of xxx.xxx.xxx.xxx on eth0 to xxx.xxx.xxx.xxx port 67
Dec 24 15:51:40 tsidkenu dhclient: DHCPACK of xxx.xxx.xxx.xxx from xxx.xxx.xxx.xxx
Dec 24 15:51:40 tsidkenu dhclient: bound to xxx.xxx.xxx.xxx -- renewal in 931 seconds.

```

every few minutes.

????:confused:????

---

### Post by dnanders on 2009-02-23
Hi,

 I am having the same problems. My network connection drops every 5 minutes. After searching on the web for a while I was able to piece together that it is my DHCP lease being way too short. How do we adjust the lease?

"bound to xxx.xxx.xxx.xxx -- renewal in 667 seconds."

---

### Post by Iowan on 2009-02-23
There is a line in /etc/dhcp3/dhclient.conf:```
#send dhcp-lease-time 3600;
```but it's commented out. My DHCP server has the following lines in /etc/dhcp3/dhcpd.conf:```
default-lease-time 604800;
max-lease-time 604800;
.
.
.
subnet ...
#  default-lease-time 600;
#  max-lease-time 7200;
}

```If the default-lease-time option got uncommented in the subnet declaration...

---

### Post by dnanders on 2009-02-23
I played around with that and it didn't make a difference. I find that it will pull the IP from the router but make the lease only 600 seconds or less. All my other systems get correct leases except for Intrepid 8.10.

**
I just discovered the /var/lib/dhcp3/dhclient.eth0.leases file. In that file it has a lease time of 1440 which would be about 720 seconds which is 50% of the lease time when the client will request a new lease. So I updated that file and restarted. I just checked the file after a reboot and it has been set back to 1440 after I changed the number. Does anyone know how that file gets created? Maybe that is my answer?
**
I have tried static IPs as well and the connection is still dropping every 5 minutes.

---

### Post by dnanders on 2009-02-25
> **dnanders said:**
> I played around with that and it didn't make a difference. I find that it will pull the IP from the router but make the lease only 600 seconds or less. All my other systems get correct leases except for Intrepid 8.10.

**
I just discovered the /var/lib/dhcp3/dhclient.eth0.leases file. In that file it has a lease time of 1440 which would be about 720 seconds which is 50% of the lease time when the client will request a new lease. So I updated that file and restarted. I just checked the file after a reboot and it has been set back to 1440 after I changed the number. Does anyone know how that file gets created? Maybe that is my answer?
**
I have tried static IPs as well and the connection is still dropping every 5 minutes.

So I was able to get the lease time way up but that is no help. It still drops the connection every 6 minutes and reconnects.

Anyone have a solution?

---

