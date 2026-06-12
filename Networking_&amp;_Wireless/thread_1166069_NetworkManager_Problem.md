---
title: "NetworkManager Problem"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by habib_seif on 2009-05-21
Hi all,

The problem I have is related to DSL connections in NetworkManager. I have created a DSL Connection using DSL tab of NetworkManager. The connection has been added to networks list when I left click the NetworkManager icon. **But the problem is that when I connect to DSL modem using wifi card, the created DSL connection has been grayed out. But when I connect to DSL modem via ethernet, the connection is enabled and works perfectly**

I guess the problem is that NetworkManager categorizes DSL Connections under Wired Networks, but nowadays most of DSL modems have wifi capability which is so easier than ethernet.

I have the problem at least with jaunty and intrepid (I haven't checked the problem in other versions).

Another problem with NetworkManager is that it recently has added a connection named "ifupdown (eth1)" to Wired Networks tab. What's it? Is it because of adding DSL connection? Can it solve the problem?

Sincerely,
Habib Seifzadeh

---

### Post by superprash2003 on 2009-05-21
it could also be because your wireless isnt getting an ip from the router??post output of** ifconfig** and **iwconfig** from the terminal ( when you are conncted via wifi)

---

### Post by habib_seif on 2009-05-21
> **superprash2003 said:**
> it could also be because your wireless isnt getting an ip from the router??post output of** ifconfig** and **iwconfig** from the terminal ( when you are conncted via wifi)

Superprash,

First of all, thank you so much for the reply.

The wifi connection hasn't any problem. I see my router, can use shared folders and printers in the LAN, ....

Please let me know if you want the exact output of ifconfig and iwconfig commands.

Yours truely,
Habib Seifzadeh

---

### Post by superprash2003 on 2009-05-22
yes please post outputs for better understanding..

---

### Post by habib_seif on 2009-05-22
Here is the output of **ifconfig** command:

```

eth0      Link encap:Ethernet  HWaddr 00:12:3f:e0:21:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:0e:6c:4c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe0e:6c4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1492 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2052991 (2.0 MB)  TX bytes:708267 (708.2 KB)
          Interrupt:17 Base address:0x6000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:409099 (409.0 KB)  TX bytes:409099 (409.0 KB)

```
and here is the output of **iwconfig** command:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Broadcom"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E3:A7:E2:E3   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-44 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
The outputs were taken when my wifi was connected but the DSL connection in NetworkManager networks list was grayed out :(

By the way, I connect to DSL connection by pppoeconf. I also deleted /etc/ppp/peers/dsl-provider file but it didn't solve the problem.

Thanks,
Habib

---

### Post by superprash2003 on 2009-05-22
ok try this, create ANOTHER DSL connection , when only WIFI is on, and then try

---

### Post by habib_seif on 2009-05-22
Dear Superprash,

I created several DSL connections but all of them are grayed out :mad:

As I told before, I guess the problem is because of listing DSL connections under Wired networks. In this way, until a wired network is plugged, all of DSL connections are grayed out.
Is there any way to change the category of DSL connections to wireless?

Sincerely,
Habib

---

### Post by habib_seif on 2009-05-22
I finally found a mail in networkmanager mailing list which shows that networkmanager doesn't support PPPoE over Wifi.
Here it is:
```

On Thu, 2008-11-20 at 12:08 +0100, Yann Simon wrote:
> Hi,
> 
> to connect to my DSL provider with wireless network, I have to:
> - set up a static IP
> - use PPPoe (with pon dsl-provider)

NM doesn't support PPPoE over wireless yet, but that was mostly an
oversight.  NM 0.7 won't ship with that support but it could most likely
be added as an update thereafter.

Dan

> I do not use NetworkManager now. I have instead parametered everything
> with command line tools (iwconfig, ifconfig and pppoeconf).
> It works quite well. But the connection is sometimes down, and I have
> to use the command line to repair it.
> While I'm ok with that, the other peoples that use the computer do not
> have the skills to do that.
> 
> I though that I could use NetworkManager to configure the network and
> display information through the nm-applet.
> I tried with the live CD of Ubuntu 8.10 (which use NetworkManager v 0.7)
> 
> I could:
> - set up a static IP in wireless mode.
> - set up a PPPoe connection in wired mode.
> 
> But I could not set up a PPPoe connection in wireless mode.
> 
> Is it an actual limitation of NetworkManager? Or am I missing something?
> Is there a workaround for this?
> 
> Thank you in advance for your answers.
> 
> Yann
> _______________________________________________

```

Is it true?
Habib

---

### Post by habib_seif on 2009-05-22
Any suggestion?

---

### Post by superprash2003 on 2009-05-24
well , i guess thats how it is.. never tried it though :)

---

### Post by Iowan on 2009-05-24
Jaunty *seems* to have that option... but I haven't tried to set it up.

Oops... maybe that's WIRED.

---

