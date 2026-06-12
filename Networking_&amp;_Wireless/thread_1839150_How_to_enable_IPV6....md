---
title: "How to enable IPV6..."
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by dashang.trivedi on 2011-09-05
How to enable ipv6 module...

when i type modprobe ipv6...

and check with
[B]
lsmod | grep ipv6
[/B]
its display nothing....

**Please tell me how to enable Ipv6..and how to load this module.....**

---

### Post by northd_tech on 2011-09-05
I'm currently running Wicd (instead of the default Network Manager) under Ubuntu 10.04.3 LTS, and I don't think I needed to install or set up anything for IPv6- it just worked automatically.  What does this terminal command tell us?  :

```
ifconfig
```
Mine says this for my working Broadcom wireless interface:
> eth1      Link encap:Ethernet  HWaddr *WiFi MAC address*
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          **inet6 addr: fe80::221:ff:fe13:2412/64 **Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38769 errors:0 dropped:0 overruns:0 frame:3160
          TX packets:24505 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49859171 (49.8 MB)  TX bytes:2871183 (2.8 MB)
          Interrupt:19 
I believe that not all ISP's (and possibly routers) support IPv6 yet.  You can read the IPv6 manual page with "man ipv6" from a terminal.  I don't see any IPv6 specific modules when I issue a **lsmod** command- I think it is probably pretty transparent/automatic if your ISP supports it.

I found this at the following IPv6 test site for my wireless connection:
> **You appear to have no IPv6 at this time..**

      *You appear to have no IPv6 address.*
      It looks like you have only IPv4 Internet service at this time. Don't feel bad -** most people are in this     position right now. Most Internet service providers are not quite yet ready to provide IPv6 Internet to residential     customers.**
      Many of the visitors to the site are new to what IPv6 is. If you don't know why IPv6 matters, see the [Why IPv6 FAQ]("http://test-ipv6.com/#"). This will give you a bit of     background of what to expect with IPv4 in the coming months and years; and perhaps some incentive to ask your ISP     when they will offer IPv6.
      **If you strongly believe you have IPv6, but we were unable to detect it:** it means one of a couple of     things. Either your organization is blocking the use of IPv6 to talk to the outside Internet through network     policy; or perhaps what you see with IPv6 on your host is not a global address. Any address starting with "::",     "fc", "fd", or "fe" are unable to work with the public IPv6 Internet.
[http://test-ipv6.com/](http://test-ipv6.com/)
[http://test-ipv6.com/#](http://test-ipv6.com/#)

Honestly, I wouldn't worry too much about it if you have a reliable, decent internet connection.

---

### Post by ~!geek!~ on 2011-09-05
> **dashang.trivedi said:**
> How to enable ipv6 module...

when i type modprobe ipv6...

and check with
[B]
lsmod | grep ipv6
[/B]
its display nothing....

**Please tell me how to enable Ipv6..and how to load this module.....**

 Try >  lsmod | grep ip6 

---

### Post by dashang.trivedi on 2011-09-05
no sir,

lsmod | grep ip6 is not working its not displaying any module..

```

root@dashang-desktop:/home/dashang# lsmod
Module                  Size  Used by
sit                     8441  0 
tunnel4                 2225  1 sit
binfmt_misc             6413  1 
snd_ens1371            18375  4 
gameport                9021  1 snd_ens1371
snd_ac97_codec        100260  1 snd_ens1371
ac97_bus                1014  1 snd_ac97_codec
snd_pcm_oss            34731  0 
snd_mixer_oss          13750  1 snd_pcm_oss
snd_pcm                71250  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1350  0 
snd_seq_oss            26342  0 
snd_seq_midi            4620  0 
snd_rawmidi            19012  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      6047  2 snd_seq_oss,snd_seq_midi
snd_seq                46801  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18593  2 snd_pcm,snd_seq
snd_seq_device          5744  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5368  0 
intel_agp              26443  1 
lp                      7250  0 
parport_pc             26052  1 
i2c_piix4               8379  0 
psmouse                57307  0 
snd                    54491  18 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                31403  3 ppdev,lp,parport_pc
shpchp                 29655  0 
agpgart                31585  1 intel_agp
serio_raw               4022  0 
soundcore               6651  1 snd
snd_page_alloc          7184  1 snd_pcm
floppy                 52888  0 
pcnet32                31603  0 
mii                     4393  1 pcnet32
mptspi                 14899  2 
mptscsih               30827  1 mptspi
mptbase                84815  2 mptspi,mptscsih
scsi_transport_spi     21293  1 mptspi


```


**please tell me how to load ipv6 module ??? **

---

### Post by lemming465 on 2011-09-05
I think the ipv6 support may be statically compiled into your kernel, and not added post-boot as a dynamic module.  I prefer "ip" to "ifconfig" for working with IPv6; if "ip address show" includes a v6 link-local address starting with "fe80" on at least one interface you have kernel support for IPv6.  This is typical for all versions of Ubuntu in the last several years; you didn't happen to mention which version you are running to it is hard to be more specific.  The "sit" module is a hint; that's used for some kinds of IPv6 tunnels carried over IPv4 transit.

Your next hurdle is that your ISP, your wifi router/firewall, and your broadband modem may all be lacking IPv6 support.  Assuming your are working from home, on a private IP address, with a v4-only ISP, try installing the "miredo" package to get Teredo tunnel support.  It will only be used for IPv6 only sites, so try "ping6 -c4 ipv6.google.com" or something afterwards.  If that works, you can explore better options, such as a 6in4 point to point tunnel with tunnelbroker.net, sixxs, or gogo6.

---

### Post by praseodym on 2011-09-05
Hi,

the module "ipv6" is still used in Debian or in older Ubuntu-versions, its not valid anymore. Check with

```
ip a | grep inet6
```

if IPv6 is in use. In the network-manager applet you can activate it additionally in the "IPv6-settings"

---

### Post by dashang.trivedi on 2011-09-06
wooo thanx sirr......ip a |grep inet6 its display its working.....

but there is one problem....

my  machin 1)  2000:470:1f01:115::3/64   is connect to switch ...

one more server machine connect to switch at eth5 : 2000:470:1f01:115::4/64

now in that server machine eth7 ip : 2001:470:1f01:115::7/64
one other  machine connect with eth7 ip is 2001:470:1f01:115::8/64....

machine 1 to server eth5 ping6 is success full
eth5 to server machine eth5 ping6 is success full
eth5 to eth7 ping6 is success full
eth7 to eth5 ping6 is success full

**now from  machine1 2000:470:1f01:115::3/64 to eth7 ip : 2001:470:1f01:115::7/64 ping6 is not success full ..**

[B]Problem is Route  because of range 2000 and 2001....
i dont know how to add route of ipv6 and in which machine i have to add route....???[/B]

please suggest me....

---

### Post by lemming465 on 2011-09-06
Could we see the output of *ip -6 route show; ip -6 address show*?

I'm not clear on your topology.  Are these hosts all on a single vlan or switch, or are they separated by routers of some kind?

If machine1's address isn't a typographical error starting 2000:470:... then either it will need an explicit route for 2001:470:... if that different subnet is on-link with it (same vlan), or it will need a gateway address if there is a router hop.  Or the typo corrected if they are all supposed to be 2001:470:...

The former case, with two subnets on-link ```
ip -6 route add 2001:470:1f01:115::/64 dev ???
```
Please substitute the interface machine1 is using, e.g. eth0, for ???.

The later case, with a gateway involved, could look like```
ip -6 route add 2001:470:1f01:115::/64 via 2000:470:1f01:115::xxx dev ???
```
where xxx is the host part of the gateway onlink with the machine1 device from the first example.

---

