---
title: "Virtual Network Interfaces"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by HotForLinux on 2010-03-16
When I boot the system, I have a virtual interface configured
[COLOR=DarkSlateGray]
```
eth0:avahi Link encap:Ethernet  HWaddr 00:a0:d1:bb:ae:17  
          inet addr:169.254.7.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 
```[/COLOR]

I would like to know where it is configured that way and what for.

Moreover, I would like to know if I can configure a virtual ethernet interface with a static or dynamic net address (to simulate having to cards for testing purposes) and how to do it.

---

### Post by Iowan on 2010-03-16
An **avahi** address (169.254.X.X) usually indicates a problem getting DHCP address. It's possible to set up a network using those addresses - Network Manager has the option under Edit Connections>IPv4 Settings> Method (Link Local Only).

---

### Post by HotForLinux on 2010-03-23
> **Iowan said:**
> An **avahi** address (169.254.X.X) usually indicates a problem getting DHCP address. It's possible to set up a network using those addresses - Network Manager has the option under Edit Connections>IPv4 Settings> Method (Link Local Only).

What kind of problem?
Anyway what is it for? Aren't problems informed through warning and error messages?

The wifi card config in the ***interfaces*** file was wrong. It had dchp and a wrong old essid. I always knew that but I didn't bother because I can always connect manually easily with a wifi config manager (receiving 192.168.1.128). I have just changed it.

I understand nothing...why would I want to change the network addresses to 169.254?

I still have the other questions.

---

### Post by Iowan on 2010-03-23
> **HotForLinux said:**
> I understand nothing...why would I want to change the network addresses to 169.254?Avahi is [ZeroConf]("http://en.wikipedia.org/wiki/Zero_configuration_networking") networking (from what I've read). It is *supposed* to be a quick/easy way to set up networking - but a 169.254.X.X *probably* won't work with a 192.168.X.X network. In brief - you probably *wouldn't* want to change to that address range...

---

### Post by HotForLinux on 2010-03-31
> **Iowan said:**
> Avahi is [ZeroConf]("http://en.wikipedia.org/wiki/Zero_configuration_networking") networking (from what I've read). It is *supposed* to be a quick/easy way to set up networking - but a 169.254.X.X *probably* won't work with a 192.168.X.X network. In brief - you probably *wouldn't* want to change to that address range...

Hmmm?
I don't understand if Avahi substitutes or can be used to substitute the traditional way of configuring the interfaces; if I should configure Avahi in case I wanted to use it or should I configure the network to meet Avahi's numbers?; if Avahi comes in when the traditional method fails in establishing a connection... In that case, should it also be configured for a particular network ip range ?... etc. etc..


1. I decided to properly configure that ***/etc/network/interfaces*** file to see what changes, if anything. Now it reads:

```
auto lo
  iface lo inet loopback
  address 127.0.0.1
  netmask 255.0.0.0

auto eth0
  iface eth0 inet dhcp

auto eth1
  iface eth1 inet dhcp
  wireless-essid  the_routers_essid
  wireless-key.... the_routers_wifi_key

``` 
After booting, eth1 is up, properly configures and connected but **ifconfig** still shows:

```

**...**

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth0:avahi Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:169.254.7.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

**...**

```
.
besides the way the other 2 interfaces (lo and eth1) are configured.
Why is still Avahi's configuration threre? Is it because eth0 is configures as 'auto' but failed to connect, at boot time,  because it is not connected by cable to the network? Does that trigger a try by Avahi's deamon or what?

I wanna learn a little bit.

---

### Post by capscrew on 2010-03-31
> **HotForLinux said:**
> ...
besides the way the other 2 interfaces (lo and eth1) are configured.
Why is still Avahi's configuration threre? Is it because eth0 is configures as 'auto' but failed to connect, at boot time,  because it is not connected by cable to the network? Does that trigger a try by Avahi's deamon or what?

I wanna learn a little bit.

You have configured **eth0 **for DHCP but it can't find a DHCP server to give it an IP address.  When **eth0** fails to be completely configured (no IP address), [COLOR="DarkSlateGray"]eth0:avahi[/COLOR] is created.

Do you have a working DHCP server in your network?

---

### Post by HotForLinux on 2010-03-31
> **capscrew said:**
> You have configured **eth0 **for DHCP but it can't find a DHCP server to give it an IP address.  When **eth0** fails to be completely configured (no IP address), [COLOR=DarkSlateGray]eth0:avahi[/COLOR] is created.

Do you have a working DHCP server in your network?

Yes, that's how the eth1 interface is configured. As I said, eth0 is not connected by cable to the network, to the dhcp server in the router. I asked if that could be the cause. 
I don't see the point in what Avahi does but anyways...

I also wanted to know if configuring  a virtual interface in the interfaces file and has virtually the same effect as having two interfaces.

---

### Post by capscrew on 2010-03-31
> **HotForLinux said:**
> Yes, that's how the eth1 interface is configured. I assume that you mean that you do have a DHCP server and that eth1 gets an IP address from that DHCP server.> 

As I said, eth0 is not connected by cable to the network, to the dhcp server in the router. I asked if that could be the cause.
Cause of what? If the eth0 interface is not connected, why do you have it configured?  It has to have DHCP server supplied IP address the way you have it configured.  

It needs a destination (connection to the network) to function.> 
I don't see the point in what Avahi does but anyways...
As Iowan described, Avahi provides an IP address on an interface that [COLOR="Red"]**requests a DHCP supplied IP address and fails to receive one**[/COLOR].  It's pool of addresses is in the 169.254.n.n range.> 
I also wanted to know if configuring  a virtual interface in the interfaces file and has virtually the same effect as having two interfaces.

Yes it does.  Remember that the real interface for which you are configuring a virtual interface on has to be physically connected to a network device for you to communicate.

You really have 2 questions here.  The Avahi protocol and virtual IP addresses do not mean the same thing.

---

### Post by HotForLinux on 2010-03-31
> Cause of what? If the eth0 interface is not connected, why do you have it configured?  I think you must  have skipped the following paragraph. This is what I said and asked:
[COLOR=Gray]
[/COLOR]> [COLOR=Black]Why is still Avahi's configuration there? Is it because eth0 is configured as 'auto' but failed to connect, at boot time, because it is not connected by cable to the network? Does that trigger a try by Avahi's deamon or what?[/COLOR]1. I'm not trying to connect with eth0 anywhere.
2. I don't have the net cable connected to eth0 because I don't want to use the cable
3. I have eth0 configured that way because I'm lazy: I like to use an auto configuration for when I connect through a cable in some networks and I don't want to edit the interfaces file every time I'm going to connect using the wifi eth1 interface.

Am I doing something strange or unusual?

I was just asking why the virtual avahi appeared there all the time and if it would be good to reconfigure something. I took the opportunity to ask about the general purpose and possibilities of virtual interfaces. Your answer to this vanishes my doubts, thank you.

---

### Post by Iowan on 2010-03-31
Sorry if I added confusion by bringing up **avahi**. Yes, if eth0 is not connected, but configured to "Connect Automatically", that might be the reason for the eth0:avahi address...

---

### Post by capscrew on 2010-03-31
> **HotForLinux said:**
> I think you must  have skipped this paragraph.
This is what I said and asked:

[I]"Why is still Avahi's configuration threre? Is it because eth0 is configured as 'auto' but failed to connect, at boot time, because it is not connected by cable to the network? Does that trigger a try by Avahi's deamon or what?
"[/I]
Both can cause it.  See my previous explanation in red.> 
1. I'm not trying to connect with eth0 anywhere.
I understand that.> 
2. I don't have the net cable connected to eth0 because I don't want to use the cable
Okay, I guess.> 
3. I have eth0 configured that way because I'm lazy: I like to use an auto configuration for when I connect through a cable in some networks and I don't want to edit the interfaces file every time I'm going to connect using the wifi eth1 interface.
As I said Avahi only appears if you do not connect with another DHCP server and get a supplied IP address.> 

Am I doing something strange or unusual?
No> 

I was just asking why the virtual avahi appeared there all the time and if it would be good to reconfigure something. 
See above an my previous response in red.> 
I took the oportunity toi ask about the general purpose and possibilities of virtual interfaces.

Virtual interfaces are to allow you to send TCP/IP traffic to a specific NIC using differing (and multiple) IP addresses.  All IP addresses are virtual anyway.  The only physical address is the MAC address.

---

### Post by capscrew on 2010-03-31
> **Iowan said:**
> Sorry if I added confusion by bringing up **avahi**. Yes, if eth0 is not connected, but configured to "Connect Automatically", that might be the reason for the eth0:avahi address...

Iowan,  You only clarified the issue.  Avahi **is exactly **the reason for the 168.254..n.n address assigned to the interface.

---

### Post by HotForLinux on 2010-03-31
I think there's much more to Avahi than has been said here. But I think that I understand now what had me intrigued.
Thank you.

---

### Post by capscrew on 2010-03-31
> **HotForLinux said:**
> I think there's much more to Avahi than has been said here. But I think that I understand now what had me intrigued.
Thank you.

For more info see:

[_[COLOR="Blue"]http://en.wikipedia.org/wiki/Avahi_(software)[/COLOR]_]("http://en.wikipedia.org/wiki/Avahi_(software)")

and 

[_[COLOR="Blue"]http://en.wikipedia.org/wiki/Zero_configuration_networking[/COLOR]_]("http://en.wikipedia.org/wiki/Zero_configuration_networking")

---

### Post by HotForLinux on 2010-03-31
> **capscrew said:**
> For more info see:

[_[COLOR=Blue]http://en.wikipedia.org/wiki/Avahi_(software)[/COLOR]_]("http://en.wikipedia.org/wiki/Avahi_%28software%29")

and 

[_[COLOR=Blue]http://en.wikipedia.org/wiki/Zero_configuration_networking[/COLOR]_]("http://en.wikipedia.org/wiki/Zero_configuration_networking")

Yes. I'll read that. Thank you both.
Sorry for my English. It's not very bad but the difficulty of expression may sometimes add confusion.

---

### Post by Iowan on 2010-03-31
Good luck - the goal is to solve problems - not make them worse...

---

