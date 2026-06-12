---
title: "Firefox and other browsers stuck on &quot;Looking up...&quot; in Ubuntu Lucid"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by revo8778 on 2011-08-09
Title pretty much describes the extent of the problem - all of my web browsers (FF3 and Chrome) stall for up to a minute on "Looking up..." when opening a new page. I can still visit other pages normally on all other computers that share this connection (some even running ubuntu). I can even ping as fast as those computers. It's just browser use where this problem crops up.

Any help sincerely appreciated.

---

### Post by jualin on 2011-08-10
It's probably because you have IPv6 enabled and your router is not working well with it.
Some people advise on not disabling IPv6 but it might help you load pages faster. Try it in firefox first by typing "about:config" on the address bar and then searching for IPv6 and toggling the value to "true." 
Restart your firefox session and check it. 
If this works then you can disable IPv6 globally. [Here is an example for Ubuntu 10.04]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html")
Hope this helps!

---

### Post by revo8778 on 2011-08-10
Is it the setting "network.dns.disableIPv6" you speak of? Already set to true.

---

### Post by revo8778 on 2011-08-14
Tried setting up a new DNS server. No changes...

---

### Post by revo8778 on 2011-08-15
Is there any way to log the network modules on Ubuntu? If somethings timing out, I could see it in a log.

---

### Post by jualin on 2011-08-17
I am sorry for the late reply. Hopefully you already solved your issue.

> **revo8778 said:**
> Is it the setting "network.dns.disableIPv6" you speak of? Already set to true.

Yes. Usually IPV6 slows things down for some routers or ISPs. But if it is already "true" then that is not the issue.

>  Is there any way to log the network modules on Ubuntu? If somethings timing out, I could see it in a log.

You can take a look at "Network Tools" which is usually under System, Administration.

---

### Post by dineshs on 2011-08-18
If disabling ipv6 and setting a different DNS doesnt help please try setting a different MTU value.If you are using Network manager pl try this
Click on network manager icon-edit connections-wired tab (orDSL tab as the case may be ) -select the connection say eth0-edit-set MTU to say 1492 and apply.
Restart NM using```
sudo service network-manager restart
```

---

### Post by revo8778 on 2011-08-18
@dineshs Tried, did not improve. I think something is wrong with how Ubuntu is contacting my DNS servers. What .conf files control that?

---

### Post by revo8778 on 2011-08-18
Copied a fresh /etc/dhcp3/dhclient.conf from my 10.04 cd, to see if that would help (I modified that file some point earlier.) Resolving still takes forever.

---

### Post by dineshs on 2011-08-18
If you are using Network manager there will be seperate files for eth0, eth1, DSL etc in /etc/NetworkManager/system-connections.In my case I have an Auto eth0 which looks ```
[802-3-ethernet]
duplex=full
mac-address=0:1e:a6:1:11:8
mtu=1492

[connection]
id=Auto eth0
uuid=87726219-c05f-49c9-89b7-b5e9611f0140
type=802-3-ethernet
timestamp=1313564784

[ipv6]
method=ignore

[ipv4]
method=manual
[COLOR="Red"]dns=8.8.8.8;4.2.2.1;[/COLOR]
addresses1=10.44.106.59;24;10.44.106.33;
may-fail=true
```
which has the DNS entries
BTW pl see if [this]("http://ubuntuforums.org/showpost.php?p=10223225&postcount=17") helps.You should backup the file before editing

---

### Post by revo8778 on 2011-08-19
That link you gave me seems to have fixed it. I had "wins" before "dns."

One remaining concern: My current primary is my router, and the secondary DNS is an actual DNS server. I'll see if a change to my Auto eth0 file will fix that.

---

