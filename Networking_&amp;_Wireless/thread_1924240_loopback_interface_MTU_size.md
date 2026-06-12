---
title: "loopback interface MTU size"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by free2rhyme2k on 2012-02-12
Hi all.

I have some files on an apache server (localhost) and i'm using simple AJAX commands to pull the files from the server. Whilst doing this, I am running wireshark to analyze the way in which the packets are received and acknowledged. 

To replicate ethernet stardards, I set the MTU at 1500 using the following command:
sudo ifconfig lo mtu 1500

Following that, ifconfig states:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:1500  Metric:1
          RX packets:3187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9154900 (9.1 MB)  TX bytes:9154900 (9.1 MB)


However when running wireshark, packets are of sizes in excess of 1500 such as: 8694, 5814, 7734 etc

Any idea why the packers would be larger than the MTU specified?:confused:

---

### Post by free2rhyme2k on 2012-02-13
up

---

### Post by bab1 on 2012-02-13
> **free2rhyme2k said:**
> Hi all.

I have some files on an apache server (localhost) and i'm using simple AJAX commands to pull the files from the server. Whilst doing this, I am running wireshark to analyze the way in which the packets are received and acknowledged. 

To replicate ethernet stardards, I set the MTU at 1500 using the following command:
sudo ifconfig lo mtu 1500

Following that, ifconfig states:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:1500  Metric:1
          RX packets:3187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9154900 (9.1 MB)  TX bytes:9154900 (9.1 MB)


However when running wireshark, packets are of sizes in excess of 1500 such as: 8694, 5814, 7734 etc

Any idea why the packers would be larger than the MTU specified?:confused:
The loopback adapter is a virtual NIC; no hardware at all.  It does not use Ethernet.  You can see this with the *Link encap *statement using the command *ifconfig* from the CLI.

```
lo     Link encap:Local Loopback
eth0   Link encap:Ethernet  HWaddr 00:13:54:58:1a:6e

```

The MTU sets the max size of packets transmitted over the wire via a layer 2 (link layer) protocol such as Ethernet.

---

### Post by free2rhyme2k on 2012-02-13
What you are suing makes sense, basically that the mtu gets set at a layer which isn't used when using the loopback interface (that's what I understood anyway). That being the case, changing the mtu should have no impact on packet sizes at all, however when I do set a lot mtu, it does decrease the packet sizes, but not to values that are less than the selected mtu. 

Eg - I select 1500 and packets are typically around 8000. 
I select 1000 and packets are typically around 6000 - 7000. 

It appears to be relatively arbitrary how the mtu affects the packet sizes captured in the trace but changing the mtu does have 'some' effect.

---

### Post by efflandt on 2012-02-14
Even with regular ethernet devices the mtu may be higher than set, if the specific connection is capable.

For example when I was playing with a mail server on DSL, I could send it small test e-mails from the internet, but for larger e-mail with attachments, sendmail kept timing out awaiting data transfer because packets larger than the mtu of PPPoE would get fragmented, and therefore, rejected.  So the sender kept trying to resend every 60 seconds when sendmail timed out.

The server was behind an old broadband router unaware that traffic had to fit through a 1492 mtu hole (PPPoE has an 8-byte header which shrinks its mtu).  Once I set the mtu of the sendmail nic to mtu 1492 the stalled mail came through.  That only seems to be a potential issue for servers receiving uninitiated connections, not client applications

However, from ping testing with data payload, while internet traffic was limited to the set mtu 1492, local LAN traffic used the full 1500.

---

