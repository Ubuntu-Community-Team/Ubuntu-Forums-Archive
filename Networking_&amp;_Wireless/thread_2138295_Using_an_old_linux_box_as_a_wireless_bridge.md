---
title: "Using an old linux box as a wireless bridge?"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by politenessman on 2013-04-23
I have an old eepc900 that use for odd projects. Right now what I want to make is a wireless to ethernet bridge. Here is why.

In my living room I have my cable modem and my wireless router. My office is upstairs and I have a wireless printer and laptop. So far so good, right.
I also have a cisco office phone that requires a wired ethernet connection.
What I would like to do is use the eeepc to connect to my wireless network and act as a bridge to connect the wired ethernet phone.
How do i do this?


----[modem] --- [Wireless router]  )  )  )  )  )  )  )     [eeepc -- ethernet port] ------------------------- [Cisco Phone]

---

### Post by politenessman on 2013-05-05
I have an update to this problem. I ditched the eeepc and decided to use the laptop on my desk instead - a little less clutter and I don't carry the laptop about with me much.

The Laptop has both a wireless adapter and an Ethernet port, so, much like in the OP, I connect to the modem via my wireless router. I figured I could create a bridge to connect the wireless interface on the laptop to the Ethernet port, and after some digging about on the net I figured that I could edit the wired connection, and set 'Method' to 'shared with other computers'. This should create the bridge - however - 

What I want is for the wireless / Ethernet bridge to be transparent to the IP phone, so that my router can see the phone MAC address and assign its fixed IP address (apparently it does need to be fixed). Unfortunately I am not seeing that happen, neither am I seeing any traffic from the ethernet ports.

What should I look for and what am I doing wrong?

---

### Post by ahallubuntu on 2013-05-05
~

---

### Post by politenessman on 2013-05-06
I looked at DD-WRT with an old N600 router that i had. Sadly that router was faulty so this is the only other option open to me. All I need to do is make a bridge between the wireless and wired port. I just don't understand why this is so hard and there is so much conflicting info out there about this. Does anyone have an answer?

---

### Post by Hadaka on 2013-05-06
Hi, I have a couple suggestions and questions.

----[modem] --- [Wireless router]  )  )  )  )  )  )  )     [eeepc -- ethernet port] ------------------------- [Cisco Phone]                 

1. is the eeepc able to currently connect to your router via wireless?
2. is the software loaded into the eeepc for the cisco phone and does it work?
3. what ubuntu version are you running?...12.04?

here is a link that seems simple enough, it assumes you currently have a working wireless connection
from there..it gives instruction on how to link the wireless connection to the internal wired card.
 * the instructions are on the top part of the page...other instructions for different issues below that.
so i would first make sure you have 100% working wireless connection to the eeepc...using WEP......   WPA/WPA2 won't work .
here ya go..
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by politenessman on 2013-05-06
1. Yes, no problems with that.
2. There is no software for the Cisco phone. However, with it connected directly to the router, it can make and receive calls just fine. I'm not sure of the technical details but I believe it has some IP based connection to a virtual pbx outside of my local network.
2. 12.10

That link appears to be for ethernet to wireless, with some sort of gateway function. I'm not sure that is what I am looking for.

---

### Post by Hadaka on 2013-05-07
Hi, I am curently using this configuration...on 12.04 to write this.
----[modem] --- [Wireless router]  )  )  )  )  )  )  )     [Laptop -- ethernet port] ------------------------- [Laptop] 				

How To:
1.establish your wireless connection
2.connect your phone to the computer's ethernet port
3.Click the wireless icon...upper right corner
4.Click Edit Connections
5.Click Wired -delete any past wired connections.
6.Click Add (let it default to wired connection 1)
7.Click iPv4 Settings
8.Click down arrow on METHOD line
9.Click Shared to other computers
10.Click SAVE...then BOOT the machine
thats it..
This works on 11.10 and 12.04..it "should" work on 12.10
good luck!

---

### Post by politenessman on 2013-05-07
I can't tell if that works however, when I check my router tables, the phone does not appear to be connected to the router, and its (assigned) ip address has now changed to something completely different. 
The IP addresses on my network all run the same format - 192.168.2.x, in the case of the phone, it is fixed by the router (MAC address binding) to 192.168.2.4

Currently the phone thinks its IP address is 10.42.0.64
I'm guessing the above setup is not a pure pass though?

---

### Post by iponeverything on 2013-05-07
its not -- doing that through nm creates a masq'ed connection not transparent bridge. 

Word of warning if you decide to try doing it with dd-wrt - transparent bridging is pretty buggy - I am doing it now using dd-wrt that and my device has to rebooted at least once a week..

Getting a device that support transparent bridging with open-wrt is your best bet - if you decide not go the recycled laptop route.  

If your still going to try with the laptop -
- ditch nm and manually manage the device
- make sure the laptop's wireless device supports AP mode

---

### Post by politenessman on 2013-05-07
Given that the spare router I had is junk at this point, I have to go with the laptop route.

> If your still going to try with the laptop -
- ditch nm and manually manage the device
- make sure the laptop's wireless device supports AP mode

Can you expand on this for me?
- I'm not sure what nm is or how it is used in this case.
- Why AP mode? Shouldn't the wireless essentially remain unchanged from its current configuration?

---

