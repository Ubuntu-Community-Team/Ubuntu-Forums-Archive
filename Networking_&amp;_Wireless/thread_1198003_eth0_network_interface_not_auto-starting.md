---
title: "eth0 network interface not auto-starting?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Lorin Ricker on 2009-06-26
Ubuntu HH v8.04 on a Sony Viao notebook:

```
$ uname -a
Linux burro 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```I must have busted something, but I can't figure it out -- this "used to work":   At some indeterminate point in the fairly recent past, my eth0 interface stopped auto-starting after reboots.

After a reboot, I cannot reach/ping anything, either local net or Internet.

In command line, I can see:

```
$ ifconfig -a
  eth0   Link encap:Ethernet  HWaddr 08:00:46:xx:xx:xx
         inet6 addr: fe80::a00:46ff:fecd:xxxx/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         (and lots more usual RX, TX, collisions stuff...)
```Note that the 2nd line, which usually reads something like for IPV4 info:

```
         inet addr:10.0.1.xx  Bcast:10.0.1.255  Mask:255.255.255.0
```is missing...  But when I manually do:

```
$ sudo ifup eth0
```This reliably brings the interface up, and then I can see what I'd expect:

```
$ ifconfig -a
  eth0   Link encap:Ethernet  HWaddr 08:00:46:xx:xx:xx
         inet addr:10.0.1.xx  Bcast:10.0.1.255  Mask:255.255.255.0
         inet6 addr: fe80::a00:46ff:fecd:xxxx/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         (and lots more usual RX, TX, collisions stuff...) 
```And the 'net is reachable/pingable again.

At all points, /etc/hosts file looks just fine, including entries for localhost and "burro" (name of this laptop).  Checking the menu/tool System|Administration|Network shows nothing unexpected or incorrect (DNS servers, static IP address, etc.).  I'm just not sure what script or config-file must be out-of-whack somehow?..

I do not think that this is a driver or kernel problem, just something I've accidentally fouled up.  I've also checked the search-tag "eth0 disappears": interesting, but so far, no real joy...

...except now this:  a thread suggests checking file /etc/network/interfaces -- comparing between the laptop and my desktop shows one line of relevant difference:

```
auto eth0
```which is missing from the laptop's .../interfaces file.  Is this what auto-starts the interface?  Is it safe to simply edit the file to fix this?

If that's not right, any advice on what else to check, what might have been accidentally altered by an innocent blunder?  If my hunch is right, how can/did .../interfaces get altered (I sure didn't do it!)???  TIA

---

### Post by Lorin Ricker on 2009-06-26
> **Lorin Ricker said:**
> 
...except now this:  a thread suggests checking file /etc/network/interfaces -- comparing between the laptop and my desktop shows one line of relevant difference:

```
auto eth0
```which is missing from the laptop's .../interfaces file.  Is this what auto-starts the interface?  Is it safe to simply edit the file to fix this?


Yup, it is... Being impatient & intrepid, I just did the experiment.  Adding "auto eth0" (and removing other "auto..." lines does what I hoped.  Rebooting now brings that interface right up.

Hope all the above helps someone else with this kind of thing...

---

