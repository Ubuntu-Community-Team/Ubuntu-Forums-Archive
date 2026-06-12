---
title: "Hostname for server"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by graabein on 2009-06-25
Hi, I have a second computer I use as a file server at home. I have installed Ubuntu and Samba on it and I can reach it from Places > Connect to server and selecting Windows share.

The thing is I want it to be known as its name and not the ip. I did add a line in **/etc/hosts** like this "10.0.0.3 kafka" (it's called kafka). The router is configured so to give the server that ip each time.

Still it shows up as the ip when I connect. How do I correct this?

---

### Post by Bachstelze on 2009-06-25
What do you mean "it shows up as the IP"? Where?

---

### Post by DGortze380 on 2009-06-25
> **graabein said:**
> Hi, I have a second computer I use as a file server at home. I have installed Ubuntu and Samba on it and I can reach it from Places > Connect to server and selecting Windows share.

The thing is I want it to be known as its name and not the ip. I did add a line in **/etc/hosts** like this "10.0.0.3 kafka" (it's called kafka). The router is configured so to give the server that ip each time.

Still it shows up as the ip when I connect. How do I correct this?

```

10.0.0.3 kafka

```

should have a tab not a space

```

10.0.0.3     kafka

```

---

### Post by Bachstelze on 2009-06-25
> **DGortze380 said:**
> ```

10.0.0.3 kafka

```

should have a tab not a space

```

10.0.0.3     kafka

```

Wrong. Both work equally fine.

---

### Post by graabein on 2009-06-26
> **HymnToLife said:**
> What do you mean "it shows up as the IP"? Where?

On the desktop it shows up as 10.0.0.3 and when I try to do "ssh kafka" it don't get it, but "ssh 10.0.0.3" works fine.

I'm on the latest Ubuntu with GNOME btw.

---

### Post by cariboo on 2009-06-26
You also have to enter

> 10.0.0.3 kafka

In the /etc/host file of every computer you want to connect to the server.

---

### Post by graabein on 2009-06-26
> **cariboo907 said:**
> You also have to enter

10.0.0.3 kafka 

In the /etc/host file of every computer you want to connect to the server.

There's only this one computer that's running Linux connected to the server. Can't remember if I saw a /etc/host file on it?

---

### Post by Iowan on 2009-06-26
> **cariboo907 said:**
> ... /etc/host file I presume you meant */etc/hosts*.

---

### Post by computer13137 on 2009-06-26
Wouldn't that require a DNS server?  Then you'd add the DNS entry.  I don't think the server's hostname would just resolve without a DNS server...

-Kirk

---

### Post by Iowan on 2009-06-26
A DNS server is a more elegant solution, but for a small network, adding address/hostname pairs to each machine will work. (It'd work for a large network, too - just becomes cumbersome). It becomes a problem when DHCP is involved - the address/hostname pairs aren't constant.

---

### Post by noway2 on 2009-06-26
This how to describes how to combine Bind9 and DHCP3 to allow dynamic IP addressing and dns: [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

I personally used it to set up my server and found that it worked as shown.
The key is that you generate a secret communicate file that is shared between the DHCP and the DNS that allows it to update automatically.

One word of caution, be careful when setting up the TTL values in your DHCP.  I accidentally set mine too short on one of the systems and it was renewing the IP address every 4 minutes.

---

