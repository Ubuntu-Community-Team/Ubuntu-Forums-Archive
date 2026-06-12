---
title: "Connected to wireless but cannot browse or ping"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by rajn on 2011-02-01
Please help.
I have a edimax USB wireless and as soon as I plugged it in it worked i.e., it is able to connect to a wireless.
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Ajana-Wireless"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: EE:E0:38:1F:60:15   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr:off
          Encryption key:AA9C-#### some numbers displayed
          Power Management on
          
I am a newbee and do not know how to get the IP address.

 ifconfig gives me
Link encap:Ethernet  HWaddr 00:1f:1f:76:10:b8  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe76:10b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8385 (8.3 KB)

Is inet addr same as IP address?
also power management is ON. Would that create problem? 
Any help is appreciated.
Thanks

---

### Post by rajn on 2011-02-01
Bump anyone?

Again when i plug the USB on Mandriva I am able to get it to work to see the active networks around. I can see their names and also mine. However, I went to the extent of setting up the IP address, DNS etc. Tried to change mode from Ad-hoc to managed but nothing I do helps me browse. I always get the error 'server not seen'.

I tried all methods to set the edimax USB but looks like the post on Ubuntu network is perhaps old? In Ubuntu Lucid the USB worked i.e., I could see the driver automatically installed without the need of a CD. I do not know how it happened but I had the wire network ON.
But again cannot get to my network and internet.

---

### Post by grahammechanical on 2011-02-01
Take things a step at a time. Not connecting to a modem/router by wireless is not the same problem as not connecting to websites. From what you write it seems that you can make a wireless connection and also a wired connection to the modem/router. What are you unable to do? Connect to websites?

The error "server not seen" could indicate that the modem/router is switched off, the url is incorrect or that the web site is not available. Yes, it could also indicate that networking is disabled in the Operating system. But then you would not have even a wired connection, which you say you have.

As regards the ifconfig listing. inet addr is the IP address of the modem/router. Or it should be. If you enter [http://10.42.43.1](http://10.42.43.1) as a url in the web browser do you get access to the modem set up program.

ifconfig says UP BROADCAST RUNNING MULTICAST. I am guessing that you were connected by wireless when you ran the command. You want to see exactly that for the wireless connection.

Regards.

---

### Post by rajn on 2011-02-01
Hi Grahammechanical,
Your encouraging words kind of prodded me to go further. From what you said it gave me some confidence that I was near to the solution but had no idea and concept of what was to be done next. I did go to the browser and entered [http://10.42.43.1]("http://10.42.43.1/") as a url in the web browser but could not get access to the modem set up program. Same server not found issue.

And then guess what - somewhere I learn't this one
sudo dhclient.

And that was it. I am now writing this with the wireless connection. And all that was needed was that command. 

However, though overjoyed I am - I am quite unsatisfied. I wish someone could tell me what the hell happened and why the above command worked and before that nothing seemed to work whatever I did.

Can you or someone enlighten me please?
Thanks
Rajan

PS: Although, I am assigning this chain as "SOLVED" I am not too satisfied. Does it mean that when I reboot I have to write the above command every time?

---

### Post by rajn on 2011-02-03
So I take back my earlier euphoria.
It works on Ubuntu Lucid but I cannot get it to work on Mandriva.
On Mandriva it sees all the local area networks and when I try connecting it to my router it says problem with router or modem or network parameters. That does not help does it?

When I do lsusb I do see the USB device.

ifconfig does show up ra0: wlan0 but ..............here is the catch - I do not see IP net address as I used to see in Ubuntu.

In fact I see another strange network ra0:9 sometimes but most of the time it is not seen but when I do find it I see the IP address, broadcast address and netmask address. But no connection can be made.

When I try making connection using restricted WEP or WAP, the light from the dongle shuts off and recovers after a long long time. It blinks on open WEP but in any case does not connect to my router.

ra0       Link encap:Ethernet  HWaddr 00:1F:1F:76:10:B8  
          inet6 addr: fe80::21f:1fff:fe76:10b8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:736809 (719.5 KiB)  TX bytes:101656 (99.2 KiB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
essid is incorrect. What is happening?

---

### Post by rajn on 2011-02-10
Ok, solved the Mandriva connection too.
Thanks,:P

---

