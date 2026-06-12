---
title: "Home network problem"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by timbosity on 2009-05-07
Hi All,

I know this isnt exactly Ubuntu related but I am using Jaunty and I am trying to get internet to it... SO my problem goes something like this:

I have a netgear ADSL wireless modem which connects to the net. I ran a cat5e ethernet cable out of this modem ~60m to an outhouse in which I have a linksys wireless router I was hoping to use to create a wireless network with and connect thus to the internet.
No go...

The cable is a cat5e standard belkin blue thing. The cable is *not* cross linked (should it be??). I have the cable running out of ethernet port 1 of the netgear ADSL modem (which is also a router) into the port labelled "internet" of the linksys router. The cable runs beside a TV aerial cable for about five metres but apart from that its all by itself.

When the cable is connected up to PC, the orange link led lights up and flickers then settles for about a minute before going off for about five seconds. It then comes back on and goes through the same process. Network-manager (Ubuntu Jaunty) tells me that its trying to get an address.

I did some troubleshooting and came up with the hypothesis that the distance was at cause. Does this sound right? 
Do I simply need to add a switch between modem and 60m cable?
Is it possible the output of the ADSL modem/router needs to be changed by a switch? 

Thanks for any help

---

### Post by albinootje on 2009-05-07
> **timbosity said:**
> 
I did some troubleshooting and came up with the hypothesis that the distance was at cause. Does this sound right? 


I read that 100 metres is the maximum length for cat5 cable to work with.

---

### Post by timbosity on 2009-05-07
Yeah I also read that somewhere. My cable is only ~60m in length. I was thinking though that whatever is coming out of the Netgear ADSL modem/router doesnt work with that length and that I needed a switch in there to make it work. I have tested the cable with a cable testing tool so I know the cable isnt faulty. Furthermore the linksys modem connects to the internet with a 10m cable coming out of the netgear modem/router.

Anyone?

---

### Post by btaylor1982 on 2009-05-07
it sounds to me like you have a dual routing problem. Is the wireless linksys set up as a wireless switch? [maybe bridge is the correct term] If not, then your main router will be routing information and handling the DCHP, and at the same time the one behind it will be trying to handle DHCP as well. The 2nd router has to have DHCP deactivated. Try searching the internet for "setting up [insert your linksys's model # here] as a wireless switch". Hope that helps.

---

### Post by timbosity on 2009-05-09
I thought that might also be the problem however when I take the linksys wireless router and link it up with another cable (~10m) there are no problems with connecting.
Its really through a process of elimination I have come to conclude its something to do with the length of the cable although most people I have talked to appear to think that it should be an issue over 60m... Im at a loss and really would appreciate anyone's input here...

thanks

---

### Post by albinootje on 2009-05-09
> **timbosity said:**
> I thought that might also be the problem however when I take the linksys wireless router and link it up with another cable (~10m) there are no problems with connecting.
Is that 10 meter cable a cross-link or a regular cat5 cable ? Just wondering.

---

### Post by timbosity on 2009-05-09
both cables are regular. I crimped them myself and tested them. Should the 60m be cross wired?

The more I think about this the more it seems i need a switch to change the signal coming out of the modem??

---

### Post by capscrew on 2009-05-09
Crosover cables are only needed for direct computer to computer.  The modem to computer cable should be straight cable.

---

### Post by timbosity on 2009-05-09
Cool. At least I have that right!!
anyone else have a hint?

---

### Post by capscrew on 2009-05-09
If I understand correctly you have 3 cables.  The first being the one that connects the netgear ADSL wireless modem to the telco connection and then 10m and a 60m cable.  Try the 60m cable to connect the netgear ADSL wireless modem to the telco connection.  That will confirm that the 60m cable is good.

The reason that long cables are bad can be electrical interference and lack of signal.  The longer the cable is the more sensitive it is to these problems.  So if it works (rolled up) it still could be how (where) it is routed.

---

### Post by marcgh on 2009-05-09
I had some time ago a similar problem.

The lenght of the cable was only 45 meters but the cable was not of good quality.
I solved my problem by limiting the link speed to 10 Mbs.

Works fine for internet but when I transfert big files ( like DVD ) it's sooooo slow!

---

### Post by sgosnell on 2009-05-09
I think my solution would be to put both the modem and the router together, using standard phone cable to extend the telco wiring to the outbuilding (outhouse is slang for an outdoor latrine here), then connect the modem and router with a short cable.  You have much less of a problem with longer runs of telephone cable than ethernet.  Is there a reason you have to keep the modem where it is?

---

### Post by timbosity on 2009-05-09
thanks guys. #
So its *not* an outhouse, its a cottage:D 
The reason why the modem is there is because the landlady has the connection and has basically agreed to let me use her connection. I tried to get a stronger wireless signal across but vegetation seems to be a problem. Having read that ethernet could carry over 100m I thought sweet ill just run a cable and have us a wireless network of our own in the cottage.
Ill see how switching from 100 to 10 goes. If anyone has any other ideas it would be great.
To add more precision to the set up:

ADSL modem/router ---- 60 m cable----------linksys wireless router

there is just the one cable connecting the modem to the router.

If i substitute the linksys router for my pc i get what i described above re: orange ethernet light flickering and going off and trying over and over again.

Substituting 60m cable for 10m cable works fine, and testing shows there is nothing wrong with cable.
 Thanks guys

---

### Post by capscrew on 2009-05-09
No reason that you can't move the modem.  Remember that telephone cable might be **more** sensitive than you CAT5e **for data**.  Voice is below 4000hz in the USA and I assume it is the same in your area. This means that voice may not be affected but TCP/IP data may have troubles.

I don't understand why you would have problems with 60m in length.  I have had longer cable runs in data center environments with no problems.  Try moving the equipment away from all other electrical devices.  Can you borrow some CAT6e cable to test?

Edit: If you have a switch to try then I would try that.  Think of it as a line amplifier.

---

### Post by sgosnell on 2009-05-09
If she's using the modem, how are you also using it?  Modems I've seen have only one connection.  How about putting both the modem and router together in the landlady's house, then running ethernet from the router to the cottage?  I think that's the only way you're going to get a connection, and it should work fine.  That gives you just one wired connection, of course, unless you put in another router set up as a repeater, and that should give you a wireless network.

---

### Post by timbosity on 2009-05-12
Hi,

Thanks for replies. The modem is also a router. There is no way of moving that so running phoneline out to cottage is not possible. I have tried putting router in her house connected to modem and then running the 60m out to cottage to no avail. I think the idea of the line amplifier makes the most sense and i will test with a cat6 cable as well (though they are more expensive, will it really make a difference?)

so set up with switch/amplifier would be:

modem----4mcat5----switch/amplifier----60mcat5e-------router

Is that correct?

best regards and thanks again for help.

---

### Post by capscrew on 2009-05-12
> **timbosity said:**
> Hi,
... so set up with switch/amplifier would be:

modem----4mcat5----switch/amplifier----60mcat5e-------router

Is that correct?

best regards and thanks again for help.

I feel you need to boost the signal towards the middle of the run where the signal is the weak.  So it would look like this:
```
modem----4mcat5----switch/amplifier----30mcat5e----switch/amplifier------30mcat5e-----router
```
Have you tried the 60mcat5e cable rolled up, so the router is near the modem?  Are you sure there is no interference near the wires.  There is a difference between cat5 and cat6 cabling.  Most of it is to combat interference with a weak signal; just like what you have.

---

### Post by Lightingboy on 2009-05-12
I believe100 metres is the maximum length for cat5 cable to work with. So if you can shorten it up it would greatly help.
 
Thanks
[Lighting]("http://www.lightingtheweb.com")boy

---

### Post by capscrew on 2009-05-12
@ Lightingboy,

Yes he is at near the limits of the cat5e cable, but he has 60 metres of ground to cover.  So he really needs the signal regenerated.  The cat6e might help but signal strength will be an issue.  In the end he will need to have 2 cables (30m/30m) to make the 60m he needs.

---

