---
title: "Share an internet connection via wifi"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by Woookash on 2006-06-25
Hi everyone,

this is my first message here, I'll try to make things as clear as possible :-p

I have a desktop computer, connected to the internet using a cable modem; it's only a "basic" modem, so no switch, router or anything else; this computer has a usb wifi stick connected;

I also have a laptop, with integrated wifi; works fine;

What I want to do: use the desktop computer as internet acess point for the laptop..

I've read a lot of how to and so, but I have NO IDEA where to start from.. ](*,)

I understood that I need: to set up my desktop computer to be a DHCP server, and then create the internet share using firestarter ? I tryed to set it up that way, but it always says that wlan0 is down, wheter it's down or up..

---

### Post by Peter76 on 2006-06-25
If the usb stick is working fine ( If not look for the wireless troublechooting in the wiki and in this forum ) You can use firestarter to set this up. You can install that through Synaptic. Don't forget to enable the universe repository. Good luck

---

### Post by Woookash on 2006-06-25
```
woookash@AMD-2000:~$ iwlist wlan0 scan
``` gives me the list of the available APN here, so I assume it works correctly;

I've installed firestarter and set it up; then when I start it:
```
woookash@AMD-2000:~$ sudo firestarter
Internal network device wlan0 is not ready. Aborting..
```

---

### Post by Peter76 on 2006-06-25
Hi, you have to give your wlan0 an ip-address, eg; 192.168.0.1, but make sure the third number is different than the one on your eth0; I mean the 0. Read man iwconfig how to do this. or you can probably set it up through the network manager. Sorry if I'm not really clear, but I'm really tired:-) To bring the wlan0 up:

sudo ifconfig wlan0 up

Good luck again, going to sleep now, but will be back tomorrow night and will be clearer then if you need more help... I did this configuration at a friends place so it is very possible, so don't give up

PS, don't use a dhcp server yet; makes thing more complicated; stick with static ip's till you got it working

---

### Post by Woookash on 2006-06-25
Thanks anyway for your help ;-)

Ok, I've changed the settings in the network manager, but some things are still unclear; normally, I should detect with the laptop the acess point, with the name I gave him ? This didn't happen yet;

Actually, I have the feeling that the usb stick is still performing as trying to connect to a network, not as "acess provider", does someone know if there is any setting to specify that somewhere ?

---

### Post by matthew on 2006-06-25
Take a look at this wiki page (I'm the author). It's the reverse of what you are wanting to do, but you should be able to figure out how to adapt it for your purposes.

[https://help.ubuntu.com/community/WifiDocs/WirelessLaptopInternetAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessLaptopInternetAccessPoint)

---

### Post by Woookash on 2006-06-25
Hi matthew, great howto, thanks!!

But, I don't have a router in my configuration, so I don't know what to set up as gateway for my wireless connection :(

and I still can't see the wifi acess point from the laptop :((

firestarter don't give me any error messages anymore, so it runs correctly;

it's correct that I should see the wireless network on the laptop ? by the way, the laptop is running win XP.. (yeah I know, but it's not mine^^)

---

### Post by Woookash on 2006-06-26
I'm till at the same point, does anyone know ome anwers to the questions related to the visibility of the wifi apn ?

---

### Post by Woookash on 2006-06-30
#-o #-o #-o

---

### Post by davidmaxwaterman on 2006-07-25
I'm having this same problem.

I don't know how to make the wifi card act as an access point - ie having it create a wifi network that others can join.

It is trivial on Apple OS X and Microsoft Windows, but how to do it on Ubuntu?

Max.

---

### Post by fugative on 2007-01-04
guys I'm in the same boat such a trivial thing yet i've been trying to get a definitive and newb-friendly answer for ages. My lappy is virtually useless without a wlan internet. I'm not going out and buying wireless routers et al when i just got a wireless card i don't believe in throwing money at problems (not that I'd be throwing for long) . 
Anyway I asked the same question and  [this]("http://ubuntuforums.org/showthread.php?t=330460") is what i got so far.
we have to help each other on this one no one seems to have the answer and if they have they ain't letting us in on it.
we probably have the answer between us already we just haven't put it together right.

---

### Post by gaelfx on 2007-07-16
You should use ifconfig to change IP addresses, not iwconfig, but iwconfig does bring up a few interesting points, such as the ability to set ESSID on a wireless card. I am looking into it since looking at those man pages inspired me that it's possible. That and the fact that Final Fantasy hasn't finished downloading yet. If I figure out a solution, I'll be sure and let you know. Keep those fingers crossed.

---

