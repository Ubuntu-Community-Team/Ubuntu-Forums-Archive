---
title: "PC giving strange results when being pinged"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by geidorei on 2011-05-27
Right then... all DHCP

PEGASUS 192.168.0.101 

when being pinged from another PC aok, but also pings back on 192.168.0.100 ??

when being pinged from itself using ping 192.168.0.101 (or 100) all is well - when pinged as ping PEGASUS is says following:

64 bytes from localhost.localdomain (127.0.0.1): icmp_req=1 ttl=64 time=0.033 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=2 ttl=64 time=0.044 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=3 ttl=64 time=0.042 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=4 ttl=64 time=0.040 ms
^C64 bytes from localhost.localdomain (127.0.0.1): icmp_req=5 ttl=64 time=0.042 ms

the ip says its 127.0.0.1 (home) - eh??? WTF is going on>

So the question is: why has PEGASUS been assigned 2 ips, and when pinging using HOSTNAME why does it point to home?

Hopefully someone will have an answer, this is very strange.

Thanks folks, Karl

---

### Post by geidorei on 2011-05-27
Well - ive tried renewing adaptors, searched all over the place - gawd knows. 2 IP address onto one PC, not setup be me. Help!

---

### Post by Iowan on 2011-05-27
What's in */etc/hosts*?

---

### Post by bab1 on 2011-05-27
...and what do you get from ```
ifconfig -a
```

---

### Post by geidorei on 2011-05-28
Hi - thanks for reply, says as follows, same as other pc's as far as I can tell:

127.0.0.1	localhost.localdomain	localhost
::1	PEGASUS	localhost6.localdomain6	localhost6
127.0.1.1	PEGASUS

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by geidorei on 2011-05-28
Hi - thanks for reply, as follows:
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:a6:44:48  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fea6:4448/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:624924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1599948 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:130346041 (130.3 MB)  TX bytes:1994234843 (1.9 GB)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34078 (34.0 KB)  TX bytes:34078 (34.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by bab1 on 2011-05-28
> eth0 Link encap:Ethernet HWaddr 00:1f:c6:a6:44:48
[COLOR="Blue"]inet addr:192.168.0.101[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0
...
lo Link encap:Local Loopback
[COLOR="Green"]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]

The *eth0* IP address that the host uses to communicate with the outside world is in **[COLOR="Blue"]Blue[/COLOR]**.  The *lo* address is internal and only talks to the local host (e.g. localhost) is in **[COLOR="Green"]Green[/COLOR]**.


> [COLOR="Green"]127.0.0.1 localhost.localdomain localhost[/COLOR]
...
[COLOR="Red"]127.0.1.1 PEGASUS[/COLOR]
Your mistake is in red.  The hostname should be associated with the [COLOR="Blue"]eth0 IP address[/COLOR].  The hostname should also be in lowercase.  NetBIOS names are in all CAPS.  Your host file should look something like this
```

[COLOR="Green"]127.0.0.1 localhost.localdomain localhost[/COLOR]
::1 localhost6.localdomain6 localhost6
[COLOR="Blue"]192.168.0.101 pegasus[/COLOR]
```

---

### Post by geidorei on 2011-05-28
Hi thanks for info.

Changed that and put 'pegasus' in lower case (is this tradition??) - oh well lol.

Hasnt made any difference - 100, and 101 still ping, and when pinging pegasus its still home 127.0.0.1

Karl

---

### Post by bab1 on 2011-05-28
> **geidorei said:**
> Hi thanks for info.

Changed that and put 'pegasus' in lower case (is this tradition??) - oh well lol.

Hasnt made any difference - 100, and 101 still ping, and when pinging pegasus its still home 127.0.0.1

Karl

From the terminal --

Post the output of ```
hostname
```

Post the output of ```
cat /etc/hosts
```

Post the output of ```
ping -c3 pegasus
```

---

### Post by geidorei on 2011-05-29
Hi - thanks for replying.

hostname PEGASUS - did change to hostname (ie small case), but when pc is rebooted it always goes back to caps!

cat:
127.0.0.1	localhost.localdomain	localhost
::1	pegasus	localhost6.localdomain6	localhost6
192.198.0.101	pegasus

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ping:
PING pegasus (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=1 ttl=64 time=0.036 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=2 ttl=64 time=0.041 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=3 ttl=64 time=0.046 ms

--- pegasus ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.036/0.041/0.046/0.004 ms

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> Hi - thanks for replying.

hostname PEGASUS - did change to hostname (ie small case), but when pc is rebooted it always goes back to caps!

cat:
127.0.0.1	localhost.localdomain	localhost
::1	pegasus	localhost6.localdomain6	localhost6
192.198.0.101	pegasus

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ping:
PING pegasus (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=1 ttl=64 time=0.036 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=2 ttl=64 time=0.041 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=3 ttl=64 time=0.046 ms

--- pegasus ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.036/0.041/0.046/0.004 ms

Pretty interesting. Why do you use CAP's for things like commands?  Linux is case sensitive.  [COLOR="Red"]PING[/COLOR] is not the same as [COLOR="Green"]ping[/COLOR].  When I do this```
PING malibu
``` I get this```
bab1@malibu:~$ PING malibu
PING: command not found

```Note the hostname (malibu) is not in cap's.  When I do this```
ping malibu
``` I get this```
bab1@malibu:~$ ping -c2 malibu
PING malibu (192.168.1.3) 56(84) bytes of data.
64 bytes from malibu (192.168.1.3): icmp_seq=1 ttl=64 time=0.014 ms
64 bytes from malibu (192.168.1.3): icmp_seq=2 ttl=64 time=0.011 ms

```

I would check the contents of the file /etc/hostname.```
cat /etc/hostname
```

The contents of /etc/hostname is what determines the name of the host.  :-)

If it is all caps then you should modify it the file.  You can do this```
sudo echo pegasus> /etc/hostname
``` Then check the contents.  

If you would rather edit the file you can do this```
sudo nano /etc/hostname 
``` 

Lets see how that works.

---

### Post by geidorei on 2011-05-29
hi answers as follows:
re PING in caps - I didnt, that was the first line of the response from the ping command. Have checked and thats what ping does - I didnt know that either. lol

albeit hostname is pegasus, cat /etc/hostname, pegasus is in caps and I cant seam to change it.

one sec - have to reset pc - ill answer rest in a few mins. cant run gedit, saying GtkWarning???

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> hi answers as follows:
re PING in caps - I didnt, that was the first line of the response from the ping command. Have checked and thats what ping does - I didnt know that either. lol

albeit hostname is pegasus, cat /etc/hostname, pegasus is in caps and I cant seam to change it.

one sec - have to reset pc - ill answer rest in a few mins. cant run gedit, saying GtkWarning???

I just realized that you are running DHCP for IP addressing.  Does DHCP also hand out the hostname.  You shouldn't statically map IP addresses to hostnames when using DHCP.  The dhcp client should offer that info up to the server.  

I'll bet you are running Network Manager.  How did you configure the interface in the first place.  Sometimes when NM is in control it doesn't matter what you put in /etc/hosts or /etc/network/interfaces.

---

### Post by geidorei on 2011-05-29
hi - right then - hostname was in caps now in lower case. gawd knows, was changed to lower case prior.

rechecked ping 192.168.0.100 & 101 - both ping back, and pinging pegasus still says home.

ahhhhhhhh!

---

### Post by geidorei on 2011-05-29
hi - have tried to change to static as follows:

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

and networking wouldnt restart.

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> hi - right then - hostname was in caps now in lower case. gawd knows, was changed to lower case prior.

rechecked ping 192.168.0.100 & 101 - both ping back, and pinging pegasus still says home.

ahhhhhhhh!

I need to see the output of the commands. It looks like NM is in control of the settings.  You will need to deal with that if you decide to configure the interface manually.

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> hi - have tried to change to static as follows:

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

and networking wouldnt restart.

Once again: this happens because NM is in control.

---

### Post by geidorei on 2011-05-29
ok - give us a clue, what do i need to do to sort then. Network Manager??

---

### Post by Iowan on 2011-05-29
You *_can_* use NM to set up static address.

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> ok - give us a clue, what do i need to do to sort then. Network Manager??

I have no experience with NM and Ethernet connections.  All of my Linux hosts are connected by Ethernet and have no NM.  My preference is to remove NM completely and configure the interface manually.  You can still use DHCP if you want, but I can't see a reason to do that.  The host is connected via a wire and is not going anywhere.  Do you really need DHCP?

---

### Post by geidorei on 2011-05-29
no - no dhcp isnt required - only in last 2 months moved onto Ubuntu, formally Windows and all were static then. But what in Network Manager? As I cant find it.

---

### Post by geidorei on 2011-05-29
doh! yep found NM - dozy git i am lol - ummm no not used it, never been into it on this machine - the only time I have ever used it was when setting up the laptops for wifi.

---

### Post by bab1 on 2011-05-29
> **geidorei said:**
> doh! yep found NM - dozy git i am lol - ummm no not used it, never been into it on this machine - the only time I have ever used it was when setting up the laptops for wifi.

That's how I feel.  If it isn't a laptop (i.e a device I'm going to use in wireless situations in multiple locations) then I would remove NM and setup the interface (Ethernet) manually.

Be advised that when you remove NM you will loose your network connectivity!  Save your settings that you wish to use in a separate file first.  The settings to save are```
hostname
address (IP address
netmask
broadcast
gateway

and the DNS settings you want to use


```

Do you want to proceed with this or wait for Iowan to explain how to do this in NM?

---

### Post by Iowan on 2011-05-29
Under NM, you can:
Select Edit connections
Highlight (select) the connection (like Auto eth0)
Click Edit.
Under the IPv4 Settings tab, use the pulldown to select the Manual method.
Enter the information.

There's a trick to getting the gateway information to accept - I have the link on another machine, but it's either a tab or <Enter> after entering the information (not just clicking elsewhere), otherwise the information doesn't get properly entered.

I have no problem with removing NM - it's just tricky to get it back without a network connection. I also have a link on the same "other" machine for disabling (without removing) Network Manager... but for an older version.

---

### Post by geidorei on 2011-05-31
hi - thanks for all your help folks all sorted now.

Re the bogus IP - I beleive it sthe VirgIn Media cable modem - disconnected that and pinged 192.168.0.100 and it vanished. Didnt realise cable modems had an ip?????

---

