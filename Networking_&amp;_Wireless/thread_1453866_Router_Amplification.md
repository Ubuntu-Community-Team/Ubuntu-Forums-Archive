---
title: "Router Amplification"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by dunbrokin on 2010-04-13
Because of the configuration of my house, I need two routers.

I have a DLink ADSL router as my main router and the Belkin N1 as my repeater.

I have set up the IP address in the Belkin to be 10.1.1.10 - my DLink is 10.1.1.1. I have disable the dhcp in the Belkin and set the DNS as ISP provided.....much along the lines of this suggestion.

[http://www.ehow.com/how_2308651_use-router-as-repeater.html](http://www.ehow.com/how_2308651_use-router-as-repeater.html)

I have set the channel to 11 and in the Ubuntu Network Manger I have set the IPV4 to Link Local Only. I can see the Belkin and connect with my PC...but it will not take me through to the internet.

Where have I gone wrong?

---

### Post by dunbrokin on 2010-04-13
Because of the configuration of my house, I need two routers.

I have a DLink ADSL router as my main router and the Belkin N1 as my repeater.

I have set up the IP address in the Belkin to be 10.1.1.10 - my DLink is 10.1.1.1. I have disable the dhcp in the Belkin and set the DNS as ISP provided.....much along the lines of this suggestion.

[http://www.ehow.com/how_2308651_use-...-repeater.html](http://www.ehow.com/how_2308651_use-...-repeater.html)

I have set the channel to 11 and in the Ubuntu Network Manger I have set the IPV4 to Link Local Only. I can see the Belkin and connect with my PC...but it will not take me through to the internet.

Where have I gone wrong?

---

### Post by lisati on 2010-04-13
Please do not start multiple threads on the same question.

---

### Post by dunbrokin on 2010-04-13
OOoops! Sorry, which one should I kill....or should I just indicate that it was cross posted?

---

### Post by Iowan on 2010-04-13
Probably because I don't understand it, but I haven't had much luck with **avahi** or **link local**. What IP address did the machine get? Post results of **route -n**.

---

### Post by dunbrokin on 2010-04-13
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     2      0        0 wlan0


Hmmm, it did not pick up the gateway 10.1.1.1 at all....

Maybe my expectations are wrong here....I am expecting the main router the DLink to link by wireless to the Belkin which will then feed that link by wireless to my PC

---

### Post by cariboo on 2010-04-13
I have a similar setup, your problem is the **local-link**, just set it up as a normal network connection, you also may need a cross-over cable between the two routers.

---

### Post by lyall on 2010-04-13
this is how my network is set up at my house

DSL modem
to Belkin wireless router with 4 ethernet ports
to a 8 port hub (switch) 
   4 pc and 2 network printers connected to this hub

a 4 port hub (in sons room) for PC, laptop, Xbox, and network printer
conected to the Belkin router

I have 3 other laptops that connect to the wireless

if I need more ports I would add another hub at any location that I want

we can print to any network print that we need or want too at any time with out any problems

having two or mores routers can cause many head aches
it is best to have only one router and one or more hubs
if you need wireless use a wireless router with ethernet ports (4 or 8)
then to the hubs
it is hard to find a wireless switch

good luck and have fun learning

---

### Post by dunbrokin on 2010-04-13
> **lyall said:**
> t
to Belkin wireless router with 4 ethernet ports
to a 8 port hub (switch) 
   4 pc and 2 network printers connected to this hub

a 4 port hub (in sons room) for PC, laptop, Xbox, and network printer
conected to the Belkin router



What you are calling a hub here....is it connected to the original router by cable or by wireless.....I would have to string a new cable around the house - which I do not want to do.

---

### Post by dunbrokin on 2010-04-13
> **cariboo907 said:**
> I have a similar setup, your problem is the **local-link**, just set it up as a normal network connection, you also may need a cross-over cable between the two routers.


Do I definitely need a cable....I would have to rip out walls to put in a new cable and I am reluctant to do that...

---

### Post by dunbrokin on 2010-04-14
bump

---

### Post by cascade9 on 2010-04-14
> **dunbrokin said:**
> Do I definitely need a cable....I would have to rip out walls to put in a new cable and I am reluctant to do that...

There is another way around that- ethernet over power adapters. They arent as cheap as I would like, but they wrok pretty well and avoid ethernet lines going everywhere or having to install them.

---

### Post by confusedstingray on 2010-04-15
from what you are explaining you are creating a wireless bridge 

here is a link from belkin that explains what you are trying to do 
[http://en-uk-support.belkin.com/app/answers/detail/a_id/2090/p/4653](http://en-uk-support.belkin.com/app/answers/detail/a_id/2090/p/4653)
 
this is not hard if the 2 routers will allow this and from the belikn manual it is possible .

just set the belkin as a repeater and set the the ip 10.x.x.2, set you subnet to match you network, and set the gatway of the belkin to the ip of the dlink 
this should get what you want,

if you need more help configuring things will need to know the model of the dlink
hope this points you in the right direction,

---

### Post by mark bower on 2010-04-15
@dunbrokin

is your problem simply signal strength?  

i go modem>router.  my HP laserjet4 is connected to the router via a D-link print server on the printer's centrix port.  i have 2 pcs that have the WPN311 card and external antennas which talk thru a 3 wall equivalent to the router.  thus i go on line and print, via wifi to the router. 

as posted elsewhere, i am going to play with parabolic reflectors which are reported to provide a significant signal boost.  in the meantime, network manager says i get anywhere from 40 to 60% signal strength.  does this give you any ideas that might help/simplify your configuration?

mark

---

### Post by cgb on 2010-04-15
Like confusedstingray said you need to be able to set the Belkin Router as a wireless bridge/wireless repeater.  The instructions you linked to in the original post were strictly for a ethernet repeater not wireless.  Basically same steps though aside from missing the part of actually creating the wireless link between both devices.  Their is devices designed specifically for this and it might be easier obtaining one of these known devices.  Also you do not need to set IPV4 to Link Local Only.

---

### Post by dunbrokin on 2010-04-16
> **confusedstingray said:**
> from what you are explaining you are creating a wireless bridge 

here is a link from belkin that explains what you are trying to do 
[http://en-uk-support.belkin.com/app/answers/detail/a_id/2090/p/4653](http://en-uk-support.belkin.com/app/answers/detail/a_id/2090/p/4653)
 
this is not hard if the 2 routers will allow this and from the belikn manual it is possible .

just set the belkin as a repeater and set the the ip 10.x.x.2, set you subnet to match you network, and set the gatway of the belkin to the ip of the dlink 
this should get what you want,

if you need more help configuring things will need to know the model of the dlink
hope this points you in the right direction,

Thanks, this is exactly what I am trying to do....My DLink is a G604T...I have tried various combinations on the Belkin but not made a break through yet....

---

### Post by confusedstingray on 2010-04-16
ok from what i can make out on the dlink you don't have to change anything 
just set your DHCP (if you are using it ) when choosing a ip for the Belkin choose one that is NOT in the DHCP range

now on the belkin set it as a ap repeater from the manual this can be done 
and set the netmask to match you network (eg 255.255.255.0) 
the gateway is the ip of the dlink. turn nat and ip filtering off on the belkin  (leave it on for the dlink )
also for setup testing don't set security yet get the routers to talk first and transmit 
then set wpa keys

---

### Post by dunbrokin on 2010-04-16
> **confusedstingray said:**
> ok from what i can make out on the dlink you don't have to change anything 
just set your DHCP (if you are using it ) when choosing a ip for the Belkin choose one that is NOT in the DHCP range

now on the belkin set it as a ap repeater from the manual this can be done 
and set the netmask to match you network (eg 255.255.255.0) 
the gateway is the ip of the dlink. turn nat and ip filtering off on the belkin  (leave it on for the dlink )
also for setup testing don't set security yet get the routers to talk first and transmit 
then set wpa keys

Hmmm....according to the manual, you should use an IP for the Belkin which IS in the DHCP range....I am confused?!?

---

### Post by dunbrokin on 2010-04-17
Actually the router manual is different from I can see on the set up page. The manual shows a tab for use access point mode....this does not appear on my machine set up.....curiouser and curiouser!!

---

### Post by confusedstingray on 2010-04-17
if you use a ip from the DHCP range it will change loose your settings

---

### Post by dunbrokin on 2010-04-17
> **confusedstingray said:**
> if you use a ip from the DHCP range it will change loose your settings


Even if it is a static IP?

---

### Post by Iowan on 2010-04-17
Ordinarily, the DHCP server is free to assign any address in it's range (it keeps track of which ones it has used). If a machine uses an address in that range as a static IP, the DHCP server may assign that to another machine as well... nothing good comes from that.

---

