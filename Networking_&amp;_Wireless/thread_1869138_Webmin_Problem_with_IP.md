---
title: "Webmin Problem with IP"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by suniyo on 2011-10-25
Old Scenario:

I had a modem with static IP and DNS info provided by my ISP and Webmin and Virtualmin was working fine with more than one virtual hosts hosted on a single ubuntu machine.

Current Scenario:

I installed a NETGEAR wireless router WGR614v10 between my computer and modem and Webmin stopped working.

What I have concluded so far:

```
host domain.tld
```

command gives output that shows my local intranet address as the IP of the website and not the one provided by my ISP that is transferred to the Wireless router from modem during the installation.

So currently my wired connection eth2 is setup as Automatic and all the info is stored in the wireless router regarding DNS servers and Static IP.

I've forwarded ports 80 and 443 for HTTP and HTTPS in router and still get the same output for the command:

```
host domain.tld
```

When I ping my website on virtual host it goes to only one hop on LAN 10.0.0.2 that is the first address on intranet.

Additional info:

/etc/hosts file has only addresses for local host and not for any external IP addresses or hostnames.

---

### Post by suniyo on 2011-10-25
Does it related with the default domain name I supply during the virtualmin setup?

---

### Post by suniyo on 2011-10-25
I am using NAT router behind a firewall and when I uninstall and install virtualmin again it takes the IP of my router 10.0.0.2 and not the public IP but gives warning on the recheck config page about it.

In both cases it doesn't work if I keep public IP at both places in DNS settings or my router's IP. I've tried port forwarding and other settings in router but nothing worked for me. I even reboot machine after changes so that there are no errors or current settings loaded anywhere else in ubuntu.

Nothing worked.

What settings should I apply? Public IP in network config page in virtualmin or my router's private IP. With private IP it gives me some warnings, not errors, and says virtualmin is ready for use. But websites actually doesn't work. Sometimes when I do command: host domain.tld it gives me 10.0.0.2 or my DNS hosts addresses listed with google apps for mail which I have set at registrar.

Sometimes it works on intranet but not on internet. external IP settings never worked.

---

