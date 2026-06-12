---
title: "Need Help Installing a Belkin N300 Wireless Router"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by w201 on 2012-01-01
Does anyone know how, or if I can get a **Belkin N300 wireless router  F9k1002** to work on ubuntu 11.10?

I did a quick search but turned up nothing. I have the driver CD which is compatible with Windows. I'm hoping someone can help me find a workaround. 

Thanks in advance.

---

### Post by w201 on 2012-01-02
Bump.

---

### Post by chili555 on 2012-01-02
Plug an ethernet cable into your computer and the other end into one of the four LAN ports. On your Ubuntu computer, type in a terminal:```
sudo ifconfig eth0 192.168.2.2 up
firefox 192.168.2.1
```You should now be in the setup pages of the router. 

Post back if you have trouble.

---

### Post by w201 on 2012-01-02
Thanks! Will try that and post back.

---

### Post by w201 on 2012-01-02
> **chili555 said:**
> Plug an ethernet cable into your computer and the other end into one of the four LAN ports. On your Ubuntu computer, type in a terminal:```
sudo ifconfig eth0 192.168.2.2 up
firefox 192.168.2.1
```You should now be in the setup pages of the router. 

Post back if you have trouble.

Not getting a setup page. My browser opens, but not connected.

---

### Post by chili555 on 2012-01-02
What does the browser say? about:blank or Page Not Found or...?? Please verify that you are connected to a **L**AN port, not the WAN port. Also, please try:```
sudo ifconfig eth0 192.168.2.2 up
firefox [COLOR="Red"]http://[/COLOR]192.168.2.1
```Thanks.

---

### Post by w201 on 2012-01-02
> **chili555 said:**
> What does the browser say? about:blank or Page Not Found or...?? Please verify that you are connected to a **L**AN port, not the WAN port. Also, please try:```
sudo ifconfig eth0 192.168.2.2 up
firefox [COLOR=Red]http://[/COLOR]192.168.2.1
```Thanks.

Says Unable to connect... Firefox can't establish a connection to the server at 192.168.2.1.

The second suggestion gets me the same result. Do the settings on my LAN router need to be changed at all?

---

### Post by chili555 on 2012-01-02
> Do the settings on my LAN router need to be changed at all?Since it's a wireless router, yes. You'll need to set encryption at a minimum. Please hook to the LAN port and try clicking the Network Manager icon to establish a wired connection. If it shows as connected, then try again:```
firefox http://192.168.2.1
```Do you plan to use wireless? If so, at least set up WPA2 encryption and change the router's administrative password so no-one but you can change settings.

---

### Post by fdrake on 2012-01-02
I had a belkin too and I remember everytime I plug-ed a cable i had to power on/off to give me an IP;
can you also provide (if chili's advice doen't work!) :
```

route -n

```
if you don't have a cable but you want to connect through wifi, connect to the essid and use the password written at the bottom of the router. Belkin by default come with a WPA2 encryption activated(at least mine did ;)).

---

### Post by w201 on 2012-01-02
Allow me to clarify a few things...

I have cable modem from Comcast. 

I picked up the belkin to transmit a wireless single from home for my ipad. The problem is that I can't get the belkin to talk to my ISP modem.

---

### Post by fdrake on 2012-01-02
> **w201 said:**
> Allow me to clarify a few things...

I have cable modem from Comcast. 

I picked up the belkin to transmit a wireless single from home for my ipad. The problem is that I can't get the belkin to talk to my ISP modem.

make sure that the router is connect to the modem then power off the router and the modem. Power on the router, then after 10sec power on the modem.

---

### Post by w201 on 2012-01-02
Just a quick update...

I see that  network manager recognizes the belkin router, but I have no connectivity.

---

### Post by fdrake on 2012-01-02
> **w201 said:**
> Just a quick update...

I see that  network manager recognizes the belkin router, but I have no connectivity.

if so can you run chili's command or provide the results for "route -n" ?

---

### Post by w201 on 2012-01-02
With Chili's command I get "unable to connect"

Here's the output of route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         24.125.232.1    0.0.0.0         UG    0      0        0 eth1
24.125.232.0    0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1

```

---

### Post by fdrake on 2012-01-02
ehmm, that's strange useally blkin's use 192.168.2.1 but yours is different. try this instead:
```
firefox 24.125.232.1
```

the default password is usally blank so don't type anything just press enter, unless you know for sure what it is.

---

### Post by w201 on 2012-01-02
> **fdrake said:**
> ehmm, that's strange useally blkin's use 192.168.2.1 but yours is different. try this instead:
```
firefox 24.125.232.1
```the default password is usally blank so don't type anything just press enter, unless you know for sure what it is.

Same result. I don't get it. Does my comcast modem need to be configured for this to work?

---

### Post by fdrake on 2012-01-02
this is quite strange can you try this please.. I think your gateway setup is wrong
```
sudo route add default gw 192.168.2.1 eth0
```
then try with firefox and put either one of these addresses:
192.168.2.1
[http://route](http://route)

this is a temporary fix it will change at rebbot. I just want to check if this works.

---

### Post by chili555 on 2012-01-02
> **w201 said:**
> With Chili's command I get "unable to connect"

Here's the output of route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [COLOR="Red"]24.125.232.1[/COLOR]    0.0.0.0         UG    0      0        0 eth1
24.125.232.0    0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1

```That looks as if you are connected directly to the Comcast modem. Connect the modem to the WAN port on the Belkin router and then connect your computer to the LAN port on the router and see if Network Manager connects. If so, you should get a 192.xx address for route -n and ifconfig.

---

### Post by fdrake on 2012-01-02
> **chili555 said:**
> That looks as if you are connected directly to the Comcast modem. Connect the modem to the WAN port on the Belkin router and then connect your computer to the LAN port on the router and see if Network Manager connects. If so, you should get a 192.xx address for route -n and ifconfig.
i thought that too at first but if that was the case he should have seen the modem's setup page...no?.. :-k

---

### Post by w201 on 2012-01-02
> **fdrake said:**
> this is quite strange can you try this please.. I think your gateway setup is wrong
```
sudo route add default gw 192.168.2.1 eth0
```then try with firefox and put either one of these addresses:
192.168.2.1
[http://route](http://route)

this is a temporary fix it will change at rebbot. I just want to check if this works.

That command gave me [B]"SIOCADDRT: No such proces"

[/B]Still cannot connect to the net.
I noticed earlier you mentioned something strange about my ip... 24.125.232.1. I can tell you with certainty that it's a recent change. I remember my ip address starting with 192... Appears like my ISP changed networks. Is this normal?

---

### Post by fdrake on 2012-01-02
> **w201 said:**
> That command gave me [B]"SIOCADDRT: No such proces"

[/B]Still cannot connect to the net.
I noticed earlier you mentioned something strange about my ip... 24.125.232.1. I can tell you with certainty that it's a recent change. I remember my ip address starting with 192... Appears like my ISP changed networks. Is this normal?

what i think is that something is wrong with your ip configuration. Did you try the router with other pcs/ devices? same problem?

can you post here the output of```

less /etc/network/interfaces

``` 
I'll try to check tomorrow and see if I(or chili555) find(s) something.

---

### Post by w201 on 2012-01-03
> **fdrake said:**
> what i think is that something is wrong with your ip configuration. Did you try the router with other pcs/ devices? same problem?

can you post here the output of```

less /etc/network/interfaces

```I'll try to check tomorrow and see if I(or chili555) find(s) something.

less /etc/network/interfaces:
```
auto lo
iface lo inet loopback

```Did not try the router with other devices. The router is brand new. I feel I shouldn't mention the obvious but I guess it can't hurt. 

On the router box, it reads compatible with MAC or Windows. I haven't actually gotten to the router setup page so I'm not surprised it's not connected. I wasn't expecting to connect the router and for it to work straight out of the box. So what are some basic network settings that I can check in ubuntu to make sure I have THAT right before I start entering additional commands?

Something else worth noting... 
with modem + router connected (internet not functional), ip begins with 192...
only modem connected (internet functional), ip begins with 24...

I have a wireless NIC installed on my machine. I'll remove it tomorrow because it's not being used anyway and might be creating some confusion. I noticed that some of the commands referenced **eth0** which I believe is the wireless NIC

Thanks for the help so far. I'll check back tomorrow.

---

### Post by chili555 on 2012-01-03
> I noticed that some of the commands referenced eth0 which I believe is the wireless NICIn most cases, **eth0** is *wired ethernet* and wlan0 is wireless. That is why we asked you to connect an ethernet cable to the router, so we could use wired ethernet.> On the router box, it reads compatible with MAC or Windows. I've never seen one that isn't also usable with all features with Linux and Ubuntu specifically. The manual for your router even describes the process on page #8.> with modem + router connected (internet not functional), ip begins with 192...If you computer is able to get an IP address of 192.xx, then you are connected to the router!!! Then try to get to [http://192.168.2.1](http://192.168.2.1) and set up the router.

Is this a DSL modem requiring user and password authentication?

---

### Post by w201 on 2012-01-03
Okay, I finally got into the router setup page.

I think I'm gonna need additional help to get these settings just right. I'm not a network guy and I don't want to pay comcast $80 bucks so they can come out to my place.

Most of the settings are in here, but I'm still not connected.

ifconfig shows wlan0 as 192.168.2.2 and eth1 (modem) as 24.125.232.118. Do I need to mirror that in the router settings?

There's a setting in here for Internet WAN, it asks for a host name, DNS, and MAC address. I think this is what I have to set up.

---

### Post by chili555 on 2012-01-03
> eth1 (modem) as 24.125.232.118. Then your computer is ***still*** connected directly to the modem. Connect the modem to the _router_ and set up the router. Someplace in the router pages is a page that deals with the WAN; that is, gets an IP address from the modem. Once the modem gets an IP from Comcast and gives one to the router, you will be connected to the internet.

Would instant messaging or Skype be helpful?

---

### Post by w201 on 2012-01-03
> **chili555 said:**
> Then your computer is ***still*** connected directly to the modem. Connect the modem to the _router_ and set up the router. Someplace in the router pages is a page that deals with the WAN; that is, gets an IP address from the modem. Once the modem gets an IP from Comcast and gives one to the router, you will be connected to the internet.

Would instant messaging or Skype be helpful?

When I accessed the router setup page my modem was connected to the router! I'm almost certain of it. I don't have a problem using instant messaging, problem is, when I connect the modem to the router, I loose my internet connection and can't use instant messaging!

add [EMAIL="camenschic@gmail.com"]camenschic@gmail.com[/EMAIL] for instant messenger

---

### Post by w201 on 2012-01-03
Thanks to fdrake and especially chili555 for all the help on this one. 

The solution was MAC address cloning under Internet WAN setting.

---

