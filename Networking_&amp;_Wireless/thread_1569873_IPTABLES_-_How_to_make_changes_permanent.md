---
title: "IPTABLES - How to make changes permanent?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by Kerubu on 2010-09-07
Hello,

I'm having problems with my iptables. I'm trying to allow the multicast address 22.4.0.0.251 and can do so by adding a rule to the OUTPUT chain of iptables. Unfortunately on reboot the rule I added is not there and I have to type it in again.

Can anyone tell me where the default rules for Ubuntu are read from? There must be a file somewhere that loads these at startup so I can add my own rule. 

I have firestarter installed too but only because it was loaded when I installed Ubuntu. It's outbound policy is selt to permissive by default so it doesn't seem to be a problem with firestarter.

Can anyone advise me how to make changes to iptables permanent?

---

### Post by wesleybailey on 2010-09-07
[http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server](http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server)

Save our rules permanently:

```
iptables-save > /etc/iptables.up.rules
```

Now we need to ensure that the iptables rules are applied when we reboot the server. 

Open the file /etc/network/interfaces

```
nano /etc/network/interfaces
```

Add a single line (shown below) just after ‘iface lo inet loopback’:
```

    ...
    auto lo
    iface lo inet loopback
    pre-up iptables-restore < /etc/iptables.up.rules

    # The primary network interface
    ...

```

As you can see, this line will restore the iptables rules from the /etc/iptables.up.rules file.

Latest Tutorial:[uif to iso converter ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by Kerubu on 2010-09-07
> **wesleybailey said:**
> [http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server](http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server)

Save our rules permanently:

```
iptables-save > /etc/iptables.up.rules
```

Now we need to ensure that the iptables rules are applied when we reboot the server. 

Open the file /etc/network/interfaces

```
nano /etc/network/interfaces
```

Add a single line (shown below) just after ‘iface lo inet loopback’:
```

    ...
    auto lo
    iface lo inet loopback
    pre-up iptables-restore < /etc/iptables.up.rules

    # The primary network interface
    ...

```

As you can see, this line will restore the iptables rules from the /etc/iptables.up.rules file.

Latest Tutorial:[uif to iso converter ]("http://wesleybailey.com/articles/uif-to-iso-converter")

'fraid that didn't work. Ubuntu just loads its default rules, wherever it gets those from.

Also I'm not using server addition.

any ideas?

---

