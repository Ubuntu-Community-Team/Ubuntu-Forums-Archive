---
title: "Prevent people from seeing shared printer"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by jcd29 on 2010-09-04
I know it's very easy to share printers in Ubuntu, just went to System, Administration, Printing, Server Settings, Publish Printers connected to this system. Voilá.

My question is: How can I create an access list so only certain IP addresses are allowed to see it?

---

### Post by bilkay on 2010-09-04
> **jcd29 said:**
> I know it's very easy to share printers in Ubuntu, just went to System, Administration, Printing, Server Settings, Publish Printers connected to this system. Voilá.

My question is: How can I create an access list so only certain IP addresses are allowed to see it?
I'm guessing here, but this might work:

In server's /etc/hosts.allow add a line "printer:{allowed clients}

In server's /etc/hosts.deny add a line "printer: ALL"

Note: If there's a line in hosts.allow "ALL: ALL" this won't work since that will let everything through.

---

### Post by sikander3786 on 2010-09-04
I use the built-in firewall, ufw for that.

```

sudo ufw default deny

sudo ufw enable

```

And then allow specific IP addresses to print to the shared printer.

```

sudo ufw allow proto tcp to any port 631 from whatever-ip-address

sudo ufw allow proto udp to any port 631 from whatever-ip-address

```

There are a few downsides of using this method but it usually serves me well. Post back if you wanna adopt this one.

Regards.

---

### Post by bilkay on 2010-09-04
> **bilkay said:**
> I'm guessing here, but this might work:

In server's /etc/hosts.allow add a line "printer:{allowed clients}

In server's /etc/hosts.deny add a line "printer: ALL"

Note: If there's a line in hosts.allow "ALL: ALL" this won't work since that will let everything through.
On second thought, I wouldn't recommend this without a lot of research.

---

### Post by bilkay on 2010-09-04
> **sikander3786 said:**
> I use the built-in firewall, ufw for that.

```

sudo ufw default deny

sudo ufw enable

```And then allow specific IP addresses to print to the shared printer.

```

sudo ufw allow proto tcp to any port 631 from whatever-ip-address

sudo ufw allow proto udp to any port 631 from whatever-ip-address

```There are a few downsides of using this method but it usually serves me well. Post back if you wanna adopt this one.

Regards.
Wouldn't this block all other non-port 631 traffic?

---

### Post by sikander3786 on 2010-09-04
It surely will block all other traffic. Haven't you enabled ufw already? I am posting from cell. Will provide you details later.

---

### Post by jcd29 on 2010-09-05
Would you recommend enabling ufw?

---

### Post by sikander3786 on 2010-09-06
See this thread.

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

> **cprofitt said:**
> I looked for a current how-to for UFW and when I did not see one I wanted to add one.

(important note: UFW is not the firewall. UFW just configures your iptables)

in most cases I recommend doing the following immediately:

```

sudo ufw default deny
sudo ufw enable

```Then fine tuning can start:



All ports are closed by default on Ubuntu. No need of a firewall unless you open up a few ports. If the computer is on a network, acting as some sort of a server, sharing files, proxy server, ssh server, web server etc etc, I will recommend to enable the firewall immediately.

---

### Post by BkkBonanza on 2010-09-06
The CUPS Admin panel allows controlling user access via Classes. I haven't explored what limitations it has but it seems like something to look at first since it's built in.

Also in cupsd.conf you can specify "Allow from x.x.x.x" and so on, or Deny, or BrowseAllow etc. 

**man cupsd.conf**

---

