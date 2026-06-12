---
title: "DHCP Router and Network"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Dagahk on 2009-05-24
Hello.
I have a 9.04 ubuntu, and been having problems with the network since I installed a router here. It gives the machines dynamic IP's and is responsible for the internet connection as well.

I cannot see/ping the machines unless I type their names in /etc/hosts, wich is a solution but very annoying seeing that the IP's themselves are dynamic and I need to change the /etc/hosts on all computers of the network from week to week to the updated IP's.

The problem is:

dags@dags-desktop:~$ smbtree
Password: 
WORKGROUP
	\\NINA-DESKTOP   		nina-desktop server (Samba, Ubuntu)
timeout connecting to 208.70.188.17:445
timeout connecting to 208.70.188.17:139
cli_start_connection: failed to connect to NINA-DESKTOP<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED

dags@dags-desktop:~$ 

Meaning: Samba tries to ping a IP that isnt NINA-DESKTOP's Ip (or any other computer on the network). So unless I define on /etc/hosts NINA-DESKTOP's IP, it won't work the network between these two computers.

Can anyone help me, please?

Thanks in advance.

---

### Post by puppywhacker on 2009-05-24
can't you assign static addresses to your interfaces? those dynamic addresses are the problem, plus windows networking historically was built around networkname, WINS and LMHOSTS rather than hostname, DNS and HOSTS. Using static addresses makes life a lot easier

you could at least assign static addresses to aliasses of your interfaces.

---

### Post by Iowan on 2009-05-24
A few possibilities come to mind.  One involves setting Samba server as WINS server... but I seem to remember another thread that discouraged this.
Another involves installing Winbind and adjusting settings in /etc/nsswitch.conf (adding "wins" before "dns" on "hosts:" line).
Yet another option involves linking DNS with DHCP so DNS server knows how to link "computer1" with "192.168.1.101". 

Or... you could assign static addresses/leases ;)

---

### Post by Dagahk on 2009-05-24
> **puppywhacker said:**
> you could at least assign static addresses to aliasses of your interfaces.

Yes, I know it would be better, even better then typing on /etc/hosts the IPs all the time. But I'm trying first to spend all the other options, for it's a network that have a lot of new computers coming and going. So leting DHCP define their IP, and machines using Ubuntu pinging it, it would be great.

[QUOTE=Iowan]Yet another option involves linking DNS with DHCP so DNS server knows how to link "computer1" with "192.168.1.101.[/QUOTE]

It seems a nice option. How do I do that?

Thanks for the help, guys.

---

### Post by puppywhacker on 2009-05-24
hi,

the reason why I'm a huge fan of static ip-addresses is that you will be in control in a simple way. it's easy. I'm also a big fan of "the hard way" but they are more difficult to explain on forum's.

The best way of getting your ip-addresses less random and more static is by using a proper dhcp server on linux, not those toy dhcpservers in cheap dsl-modems. The server itself will already implement a memory of which leases were handed out, so devices will get assigned a recurrent semi-permanent ip-address. 

You can also let the dhcp server permanently assign an address by configuring it

```
host fantasia {
  hardware ethernet 08:00:07:26:c0:a5;
  fixed-address fantasia.fugue.com;
}

```

And the coolest solution of them all, use a DHCP server to update the DNS server using ddns-update-style. can't remember to use ad-hoc or interim? 

And like Iowan said, winbind and a wins-server will solve it windows style

---

### Post by Dagahk on 2009-05-24
Liked a lot the idea of replacing the DHCP from the hub and modem with one on my PC! It's already working here, just need to fix some minor set-ups.

Thanks a lot Iowan and puppywhacker!

---

