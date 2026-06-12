---
title: "Using natd and my comp as a router"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by acmeinc on 2009-03-16
I want to use my ubuntu box as a router to route my wireless connection 
to other computers in my room.  Has anyone done this before?  Diagram 
below:

[IMG]http://pwnspeak.com/setup.png[/IMG]

I have read some helpful articles regarding the use of natd to do this with two ethernet cards.  And normally the connection was made pre-router, following the modem.

My current Wireless NIC settings:

```

wlan0     Link encap:Ethernet  HWaddr 00:1d:7d:7a:e4:dd  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe7a:e4dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775248 (775.2 KB)  TX bytes:185584 (185.5 KB)

```

---

### Post by acmeinc on 2009-03-19
Just wanted to let this forum know I got this to work:

My method. I used Firestarter, I know, I wish I could have done it through the shell. However, the network config files did not match up as I know them in FreeBSD, which threw me off.

Sharing wlan0 through eth0

1. Create a new wired connection for eth0, or edit the current config. I created a new one because editing the current config did not save after restarting.
2. The new config will be manually setup, IP=192.168.0.1 Mask=255.255.255.0 Gateway=0.0.0.0.
3. I also have a static route from router to wlan0, but this should not be necessary.
4. sudo apt-get install firestarter dhcp3-server
5. edit /etc/default/dhcp3-server to include INTERFACES=”eth0&#8243;
6. Open firestart, run the config wizard, and select to share connection from wlan0 to eth0.
7. Edit /etc/sysctl.conf, append 'net.ipv4.ip_forward = 1' (no quotes)

And this worked!

---

### Post by Azubah on 2010-03-13
How would I apply this sort of thing to my own network? I have a wirelesss access point and two ethernet cards. I want to run the internet through the computer and to the access point.

---

### Post by acmeinc on 2010-03-13
You should be able to follow the instuction above.  I also have this information listed in one of my blog entries.  There is more detail here:

[http://blog.pwnspeak.com/2009/04/wireless-bridging-with-ubuntu.html](http://blog.pwnspeak.com/2009/04/wireless-bridging-with-ubuntu.html)

---

### Post by Azubah on 2010-03-13
I tried those steps and it gives me the error that eth0 isn't ready and it says it can't start the firewall to check my network connections to make sure my internet connection is active...

oddly upon deleting the eth0 I previously had it hasn't gotten a MAC address.

I want to use my machine asa  router for my wlan access point... I have the machine wired to the wlan and teh modem for internet...

tried starting firestarter again...

'eth0 is not ready.'
'Please check your network device settings and make sure your internet connection is active'

---

### Post by acmeinc on 2010-03-13
> 'eth0 is not ready.'
'Please check your network device settings and make sure your internet connection is active' 

Firestarter can not start the internet connection sharing until both ethernet cables are plugged in and active.  

Typically both cables would need to plugged in as well as the access point be powered before you can start the connection.  You will know when the connection is active by checking the Active Connection typically in the top right of your screen.

Be sure you are using the correct eth# for the internet connection as well as the outgoing shared connection.

---

### Post by Azubah on 2010-03-13
yeah eth0 is using my internet connected ethernet card to connect. only eth1 (my internet connection) is working apparently.

eth1 is plugged into my modem. eth0 is supposed to be the other network card I have in my machine and that card is connected to my accesspoint. which is powered on.

---

### Post by acmeinc on 2010-03-13
Provided both connections are actually connected, I am not sure why you are getting that error.  

Typically I receive that error when the connections are not established via the Connections dock item on the top right.

You will want to setup static a static connection to the "bridged" device, otherwise known as eth0 in your case.

---

### Post by Azubah on 2010-03-13
eth0 isn't connecting actually... I'm not sure how to bridge eth1 -> eth0 
I followed every step on your blog you gave me.

---

### Post by acmeinc on 2010-03-13
What happens when you click on the Connections dock item, then you click "eth0" or "auth eth0" or some form of that?

Does an error occur?  Or does it attempt to connect?

---

### Post by Azubah on 2010-03-13
it connects eth0 in place of eth1 ._.;;

connected another machine in place of my wlan access point and the machine timed out tryingt o get an ip address but my machine says eth0(bridge) connected.

---

### Post by acmeinc on 2010-03-13
The eth0 cable is going to the INPUT of the access point, correct, not the OUTPUT?  

Other than that, I'm not sure why you comp won't allow you to have both connected at once...sorry :(

---

### Post by Azubah on 2010-03-13
I believe it is my AP only has one port to plug into anyways.

it seems I may have configured it all wrong though... i actually followed your directions in everyway including ip addresses...

---

