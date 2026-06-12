---
title: "Karmic--can't set static ip config"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by shawnisalk on 2009-12-09
Hello,

I'm running Karmic on a Dell Inspiron and having problems I didn't have with Jaunty.

One of those issues is this:
I am unable to set eth0 with a static ip config.

Through the Gnome interface in Network Connections, if I edit eth0, when I switch from DHCP, the "apply" button disappears. If set the configuration I want, anyway, and then close out that window, the changes are lost.

I tried editing /etc/network/interfaces, and though I did it properly, this disabled the interfaces, altogether.

I successfully set the IP of eth0 with ifconfig, but this brought down the connection (possibly because I couldn't find a way to set a DNS server through ifconfig).

I have also tried all of these steps while logged in as root with the same results.

Anyone have any ideas? I'm starting to curse the name Ubuntu...

Thanks for help,
Shawn

---

### Post by Iowan on 2009-12-09
What's the current state of things?
Does */etc/network/interfaces* have more than the two lines defining "lo"?
Were you editing from the Network Manager applet, or from the pulldown menu?

---

### Post by doas777 on 2009-12-09
for dns servers, put them in /etc/resolv.conf
```
nameserver ###.###.###.###
```

---

### Post by shawnisalk on 2009-12-09
Iowan--
There are only two lines defining lo in /etc/network/interfaces

I was editing from the pull-down menu: System--Preferences--Network Connections


doas777--
Thanks. I'll see if that gets me what I want.

---

### Post by Iowan on 2009-12-09
On at least one occasion, my Jaunty box would let me edit via the NM applet where the pull down would not (although they looked identical...)

I've seen people put a nameserver line in */etc/network/interfaces*, but the preferred way is (as mentioned) */etc/resolv.conf*.

---

### Post by imtheguru on 2009-12-09
> **shawnisalk said:**
> I am unable to set eth0 with a static ip config.
...
I tried editing /etc/network/interfaces, and though I did it properly, this disabled the interfaces, altogether.Here's what i had to do between 9.04 and 9.10 to fix the same problem.

In /etc/network/interfaces, keep the lo lines as is, but replace the ethx lines with ```
auto eth0
``` or equivalent. This enables DHCP, so your router better be handing out ip addresses.

In /etc/NetworkManager/nm-*
Keep the managed=false.

Restart the computer and login.

Add a new connection entry to the NetworkManager and adjust it to your requirements.

Cheers.

---

### Post by doas777 on 2009-12-10
> **imtheguru said:**
> Here's what i had to do between 9.04 and 9.10 to fix the same problem.

In /etc/network/interfaces, keep the lo lines as is, but replace the ethx lines with ```
auto eth0
``` or equivalent. This enables DHCP, so your router better be handing out ip addresses.

In /etc/NetworkManager/nm-*
Keep the managed=false.

Restart the computer and login.

Add a new connection entry to the NetworkManager and adjust it to your requirements.

Cheers.


I've always been under the impression that to enable DHCP, you still have to add an iface line:

```

auto eth0
iface eth0 inet dhcp

```

---

### Post by Iowan on 2009-12-10
> **doas777 said:**
> I've always been under the impression that to enable DHCP, you still have to add an iface line: I've always done it that way, too - otherwise, it seems like NM won't touch it, but the system doesn't know what to do with it either.

---

### Post by shawnisalk on 2009-12-11
Welp. I've got an ethernet connection, now.

I uninstalled Network Manager and config'd ***/etc/network/interfaces*** and* **/etc/resolv.conf***
(the lack of automation feels surprisingly Clean and Safe)

I don't understand why the wireless card isn't working, though.
I added 

[B]"auto eth1
iface eth1 inet dhcp"[/B]

to ***interfaces*** but no luck. I think I could get it working by assigning it static IP, but I don't want to do that because of potential conflicts with other networks.

Any other thoughts?

---

### Post by shawnisalk on 2009-12-11
Thanks so much for your intelligent and helpful feedback, by the way (everyone). 
I really appreciate the support.

---

### Post by Iowan on 2009-12-11
> **shawnisalk said:**
> I don't understand why the wireless card isn't working, though.
Your machine uses eth1 for wireless? My laptop does, as well, but wlan0 is another common alias. I presume you've checked **lshw -C network** to verify interface status.

---

### Post by kcn_viper on 2010-01-07
Hi,  It is rather bad on the part of ubuntu that my internet connection changed for me after upgrading from 9.04 to 9.10. Earlier I had a static IP on the laptop and the new network manager refused to take a static IP. On doing networking restart, I would get the static IP.  My solution:  1 sudo apt-get remove network-manager network-manager-gnome 2 Restarted system on dialog asking for same. 3 sudo apt-get install gnome-network-admin 4 Added 192.168.1.1 in DNS servers using network-admin  Regards,  KCN

---

### Post by shawnisalk on 2010-01-30
I actually discovered a solution. I had previously uninstalled Network Manager.

I re-installed it and of course, it wiped out any static settings I'd made.
Then, instead of trying to edit Eth0 in Network Manager (which it would never let me do),
I created a new network connection, defined it the way I wanted (statically) and then I deleted Eth0.

So now I have what I wanted: wireless nic config'd via dhcp and ethernet nic config'd statically

I just wish I had thought of that earlier.

*shrug*

---

### Post by ManyBeers on 2010-02-10
> **shawnisalk said:**
> I actually discovered a solution. I had previously uninstalled Network Manager.

I re-installed it and of course, it wiped out any static settings I'd made.
Then, instead of trying to edit Eth0 in Network Manager (which it would never let me do),
I created a new network connection, defined it the way I wanted (statically) and then I deleted Eth0.

So now I have what I wanted: wireless nic config'd via dhcp and ethernet nic config'd statically

I just wish I had thought of that earlier.

*shrug*

I had the exact same problem as you did. Apply button was not available when attempting to set Manual config. However you can change the default ethO to manual. After clicking the IPV4 tab to edit select Manual(which you did) then click the add button in Addresses field and add your static IP hit Enter then click on Netmask(did you do this?)and you will be able to enter it, then 
click on Gateway and enter it.Either after clicking on Netmask
or Gateway (I don't remember which) I noticed Apply was available.
I couldn't figure out how to enter my Netmask/Gateway values when
I just clicked on Netmask and the enter field appeared. Anyways this worked for me.

---

### Post by henriquemaia on 2010-04-20
> **ManyBeers said:**
> I had the exact same problem as you did. Apply button was not available when attempting to set Manual config. However you can change the default ethO to manual. After clicking the IPV4 tab to edit select Manual(which you did) then click the add button in Addresses field and add your static IP hit Enter then click on Netmask(did you do this?)and you will be able to enter it, then 
click on Gateway and enter it.Either after clicking on Netmask
or Gateway (I don't remember which) I noticed Apply was available.
I couldn't figure out how to enter my Netmask/Gateway values when
I just clicked on Netmask and the enter field appeared. Anyways this worked for me.

You're right, this works. I was kind of stuck and willing to try some more unconventional approaches, but fortunately I read your post. When I entered the Netmask info, the apply button appeared. Thanks.

---

