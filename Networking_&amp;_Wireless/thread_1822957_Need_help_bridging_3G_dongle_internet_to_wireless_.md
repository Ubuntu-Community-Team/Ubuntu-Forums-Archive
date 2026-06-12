---
title: "Need help bridging 3G dongle internet to wireless router ?"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by dude77 on 2011-08-11
I dont know if its possible or not ? I'm using 3G dongle (ppp0 interface) for connecting to internet on my laptop running ubuntu 11.04 , now i want to share this 3G connection to my wireless router(Trendnet TEW-652BRP) through eth0 interface 

in simple my connection should be like this 

INTERNET<<<3G WIRELESS MODEM<<<LAPTOP----WIRED CONNECTION TO WIRELESS ROUTER<<<OTHER DEVICES (LIKE ANDROID MOBILE/LAPTOPS SHOULD CONNECT THROUGH THIS WI-FI CONNECTION)

please help ppl i'm having big time figuring out how to do this ? :confused:

---

### Post by spegru on 2011-08-15
I would also like to be able to do this

---

### Post by imortalninja161 on 2011-08-15
unfortunately Those USB dongle Devices are not able to do that because the USB dongles are modems only they have no switching or routing capability they would only be able to route to other devices if directly connected  however the USB card inside the dongle or the dongle itself can be placed inside a wireless router something like this [http://www.shop2connect.com.au/product_info.php?cPath=4&products_id=23](http://www.shop2connect.com.au/product_info.php?cPath=4&products_id=23) 

Also make sure you have the riite router for the rite type of 3G connection and the brand


Thanks 
imortalninja161

---

### Post by spegru on 2011-08-15
I'm certain this is possible. It doesn't use any routing in the dongle. It needs a bridge between wifi and the dongle with the PC doing the switching and routing.
Only problem is I don't know how to set it up

---

### Post by pdc on 2011-08-15
is this not what some call a wireless access point?

[http://www.zdnet.com/blog/soho-networking/make-your-own-wi-fi-access-point-for-free/180](http://www.zdnet.com/blog/soho-networking/make-your-own-wi-fi-access-point-for-free/180)

---

### Post by imortalninja161 on 2011-08-16
you cant bridge threw the pc only from the dongle to a router like i posted above

and all a wirless access point does is broadcast a wireless signal from your modem to all devised is radius of the access point the exact same concept i listed above just that device can only spread wirless signal wheres what i posted can share wired and wirless.


Thanks
imortalninja161

---

### Post by alexfish on 2011-08-16
Hi

does this help

[https://help.ubuntu.com/community/SharingMobileBroadband](https://help.ubuntu.com/community/SharingMobileBroadband)

alexfish

---

### Post by dude77 on 2011-08-17
hi guys,

firstly thank you for the replies  i got this connection working yesterday after some failures, this is how its done 

1. first make sure that you are connected to internet through your 3G dongle
2. bring up the wireless router(i'm using TRENDNET-652 wireless router) check its working condition
3. connect an Ethernet cable from your laptop eth port to wan port of the wireless router
4. now that you can see an auto eth0 connection in your network manager edit this connection and goto ipv4 settings tab and change the connection method to "SHARED TO OTHER COMPUTERS"
5. change the connection type in your wireless router settings to automatic DHCP mode
6. save the settings in the wireless router and restart it and also restart the laptop
7. check whether the wireless router is able to get ip from the laptop or not 

once all this is done time to check the wifi connection, i used my android mobile to connect to the wifi and got the connection working and yes its using my 3G dongle internet connected to my laptop .:)

---

### Post by spegru on 2011-08-18
That's great and got it working here without bother using my sitecom wireless router. 

I did have to make sure that it was the WAN port that I plugged into and I also enabled spanning tree (the idea was to make sure all the ports can see eachother) although I'm not clear if that was really necessary.

For the next enhancement to the dongle sharing project, what I'd also like to do is to put the dongle into a laptop and use the built in wifi instead of an external router.
This must be very similar I expect

---

### Post by spegru on 2011-08-18
Wow that was easy!
I just created a New Wireless Network from network manager (with the dongle plugged in and working). From the previous experience I was expecting to have to change ipv4 settings to 'share to other computers' but it was already there by default!
So with another wireless pc I can now see the new wireless network I created and connect the internet via that!
Also means I can put the lower grade pc upstairs where I get a better mobile network connection.

Job done and am submitting this post that way now!

---

### Post by dude77 on 2011-08-18
@spegru : yes all we need to do is plug in the eth port wire from  laptop to wan port of wireless router that way job is done , at present  i'm facing problems in creating and adhoc on my laptop thought of using adhoc connection for my android mobile but later i learnt that android doesn't support adhoc networks but the 3G dongle to wireless router connection made the work lot easy and served as plan B for my mobile downloads ...phew !! 8)

---

### Post by spegru on 2011-08-28
Yes - ad hoc networks seem to be different. My Kindle doesnt that support either
I wonder how it would be possible to set this up in infrastructure mode?

---

### Post by willow370 on 2012-01-02
Has anyone tried this on ubuntu 11.10?

---

### Post by spiky001 on 2012-01-02
Hi   Willow I have done this on 11.04 and I have it running permently on 10.04. It dose depend on the wirless drvices being able to connect to adhoc

---

