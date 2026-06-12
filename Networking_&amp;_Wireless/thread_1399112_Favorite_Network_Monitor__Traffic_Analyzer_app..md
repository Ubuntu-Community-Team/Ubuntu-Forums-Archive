---
title: "Favorite Network Monitor | Traffic Analyzer app."
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by alienprdkt on 2010-02-05
Let me start by saying that I have tried Cacti, Darkstat and a few others but they seem to lack what I am looking for or maybe I was using the software incorrectly. What I would like is something to help me pin-point to what network device is eating up my bandwidth throughput during certain times of the day. Also if this can send info to Nagios that would be a plus also.

From the applications that I have tested a bit, they tell me info per host. I need something I can look at a scope of my entire network. We have about 14 desktops and 6 servers, and about 20 VOIP telephones. So you can see how viewing a graph of one device at a time is not efficient. I need something that I can view the entire network, and maybe color coded to the use of bandwidth the device is using.

Can I achieve this with Cacti or Darkstat, or what would be a better solution, or simply put what is some of your favorite applications for analyzing network traffic? 

Thanks in advance for your posts.

---

### Post by alienprdkt on 2010-05-14
Sill looking!

---

### Post by AmpersUK on 2010-07-24
I'd be interested as well

---

### Post by Fatman_UK on 2010-07-29
> **alienprdkt said:**
> Let me start by saying that I have tried Cacti, Darkstat and a few others but they seem to lack what I am looking for or maybe I was using the software incorrectly.

I haven't tried Cacti or Darkstat but it sounds to me like you want some sort of packet logging going on. Does your main router have the ability to log all packets? If it can capture them in .pcap format, you can read the capture file with Wireshark. Then you can apply filters, follow TCP conversations, etc. I'm not sure about Wireshark's statistical analysis ability but you should be able to get some idea of who's doing what and how much.

---

### Post by alienprdkt on 2010-09-22
Bump

Still looking after all these months!

---

### Post by mrhhug on 2010-11-15
additional bump

---

### Post by Windows Nerd on 2010-11-15
If you are looking to stop one device from eating up all the bandwidth most routers these days (and open router distributions) have the ability to cap a certain protocol or mac address from sucking up more than, say 75% of the bandwidth.

---

### Post by mrhhug on 2010-11-15
> If you are looking to stop one device from eating up all the bandwidth most routers these days (and open router distributions) have the ability to cap a certain protocol or mac address from sucking up more than, say 75% of the bandwidth.

im ok with nodes using all the bandwidth when i am on that node. - its when one of the kids obviously left one of the various filesharing programs to upload or download freely when im trying run something. My trendnet 652 - brp does allow System Activity, Debug Information, Attacks, Dropped Packets, and Notice log information. 

I just want to see who when and where my bandwidth is going so that i can temporarily restrict bandwidth when my tv is trying to download netflix.

i think windows nerd it right though, the router is the only thing that can see the gross network traffic....

---

### Post by mrhhug on 2010-11-16
only the router knows all the ins and outs of your network, unless you have a PC acting as router, any software installed on your PC could only monitor your PC's traffic

---

### Post by alienprdkt on 2010-11-17
I was asking because here at work on our T1 line with the only thing on it is our VOIP phones and an MS2007 exchange I sometimes get undesirable cutting out on phone calls, was wondering if there was any way to monitor our bandwidth to see if that is a problem. Even though I have strict QoS enabled on our Sonicwall.

---

### Post by Tlingit on 2010-11-17
Google this ```
dd-wrt
``` it a micro linux you can install on your router, it will give you a bunch of great information along with graphs and what interfaces are using what from where.
Note this is just a small portion of what its capable of. If you want more info or any questions let me know I know its not an app but hey it will do the job and then some. I also know there is another project ```
tomato
```.

Let me know

---

### Post by mrhhug on 2010-11-17
> **alienprdkt said:**
> I was asking because here at work on our T1 line with the only thing on it is our VOIP phones and an MS2007 exchange I sometimes get undesirable cutting out on phone calls, was wondering if there was any way to monitor our bandwidth to see if that is a problem. Even though I have strict QoS enabled on our Sonicwall.

what kind of router/switch are you using in between your T1 modem and your, VOIP / exchange servers? 

that router or switch is really the only device thats going to know all the incomming / outgoing connections on that subnet

---

### Post by alienprdkt on 2010-11-19
> **mrhhug said:**
> what kind of router/switch are you using in between your T1 modem and your, VOIP / exchange servers? 

that router or switch is really the only device thats going to know all the incomming / outgoing connections on that subnet

We have a sonicwall tz-100 and a dell gigabit switch... which we have configured for QoS for VOIP.. but still at times get undesired results. Think actually maybe a bandwidth issue because of the VPN between our office and an offsite location. The offsite are mainly the ones with the problems.

Really wish we could atleast get cable in our building but they want 25k for installation, and Verizion with FIOS gives usthe run around because why pay them 50 a month when we get from there subs at 10 times that for the T1.

---

### Post by eatberrys on 2010-11-19
If you are still looking try ntop. Great little program.

Don't think it is for Linux but: [http://www.paessler.com/prtg/](http://www.paessler.com/prtg/) is also good.

As I'm sure your aware that these kind of applications need to be run off of a SPAN or other monitor port or in-line to work properly. 

Mabe the QOS is not working properly? Just a thought.

Any ways, good luck with the problem. If it continues I may have a few more ideas for you.

---

### Post by seamus.tuffy on 2010-11-23
It appears that it involved many stuff.
1. Real-time monitoring who/what application eats up your uplink
2. VOIP is kinda tricky, it's not only the bandwidth but a window in millisecond:
If you have the bandwidth, then regular settings  will give them the entire amount. The only difference between guaranteed bandwidth and regular settings is that guaranteed bandiwdth gives them the  bandwidth every time period (a window in milliseconds), whereas regular  bandwidth is averaged over longer periods. So to simplify, if the  window was 1 second, a minimum setting of 512kbs would make certain that  they COULD GET AT LEAST 512K each second. A regular setting of 512K  might give them 480K one second and 540K the next. There are no regular  applications other than VOIP that notice such differences over small  time periods.
3. You might want to go a step further: manage your bandwidth to have VOIP running smoothly, Sonicwall QoS is based queue which is not very suitable for VOIP, because queue implies that all the traffic should be delay, in turn it introduces the latency in the network.

Take a look at MyQoS([www.myqos.net](www.myqos.net)), if your uplink is less than 2Mb/s you could get it for free.

---

### Post by alienprdkt on 2010-12-03
ok how about something new, 
best app to monitor traffic type on a network scale?
SIP, HTTP, SMTP. 
any help is greatly appreciated?

---

### Post by eschvoca on 2012-02-15
I'm interested in this too.  I'm leaning towards running Toastman's tomato build on a recent router.  This will give you:

1) Bandwidth usage history per IP on the LAN
2) QOS that works
3) VPN client/server
4) VLAN (isolated networks)

I'm am looking at installing darkstat.

The most powerful router supported seems to be the Linksys E4200.  Most recent builds are here:

[http://www.4shared.com/dir/v1BuINP3/Toastman_Builds.html#dir=149787153](http://www.4shared.com/dir/v1BuINP3/Toastman_Builds.html#dir=149787153)

Forums are at linksysinfo.org.

Thanks.

---

