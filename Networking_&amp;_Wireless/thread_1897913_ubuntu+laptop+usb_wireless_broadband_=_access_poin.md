---
title: "ubuntu+laptop+usb wireless broadband = access point?"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by willow370 on 2011-12-20
hey guys, a common question as ive discovered from trying to research this myself, but couldnt get a full answer.

id like to set my laptop which runs the newest ubuntu to act as an access point for my iphone to connect to wirelessly. my Internet is a usb dongle thingo with wireless broadband.

i can do this on the other partition of the laptop which contains windows 7 and using [U]connectify me
[/U]
is there a similar software for ubuntu? ive tried _firestarter_ as i read that it can act the same? but its not happening for me.

the only other way ive read is to edit files in editor which i really dont want to do as im new to linux.

is there any easier way for this?

cheers

---

### Post by praseodym on 2011-12-20
You can setup Internet-Connection-Sharing in the NetworkManager-applet, normally only WEP encryption works with that

---

### Post by willow370 on 2011-12-20
Sounds to easy, how do i access this app?

---

### Post by marin123 on 2011-12-20
It's the Network Manager applet next to the clock on the top right.
Click it and one of the options is Create New Wireless Network. Follow the steps and you can have new network for your phone.

If you have any questions or problems, ask here :)

---

### Post by willow370 on 2011-12-21
ok so when i create this network, how do i get the iphone to use the internet of the laptops? i can get my iphone to connect but its still 3G and not wireless.

thanks!

---

### Post by tkabir11 on 2011-12-21
Hey guys. 
I just started using ubuntu and im also facing a similar problem to willow370. I read some posts about setting up adhoc wifi in ubuntu- followed them precisely- but whatever I do I jus cant seem to connect my ipod touch 4g with the adhoc wifi. 
The first way i tried was choosing the ''share to other computers'' option under IPv4 settings of the adhoc I set up in ubuntu. When I do that- the connection seems to simultaneously connect and disconnect- with the wifi LED on my laptop going on and off. 
In another post I read that I should choose ''automatic DHCP'' under ipv4. This time- the connection is established and it holds....but cannot connect on ipod. Yet in another post I read i should choose ''link local only''...tried it. still no luck.

Can anyone please give me a solution to this? Ive been at this for too long now :(

---

### Post by marin123 on 2011-12-21
> **willow370 said:**
> ok so when i create this network, how do i get the iphone to use the internet of the laptops? i can get my iphone to connect but its still 3G and not wireless.

thanks!

Do you have 2 network interfaces? If you create access point, you will disable internet on your laptop, so you need one interface that is connected to internet and wireless interface that you will use for your phone.
Example: Connect wired connection to internet (plug in the cable that is connected to a router). Make access point, connect your phone to the access point. Now you should be able to connect through your computer's connection.
This will work if you have 2 wlan interfaces, but I doubt they put that kind of cards in laptops...

---

### Post by willow370 on 2011-12-21
The connections are sepperate, ones my ppp connection for my wireless broadband, and i made a seperate wireless connection which was a wlan connection.

---

### Post by willow370 on 2011-12-23
Bump

---

### Post by tkabir11 on 2011-12-24
Hey willow370- do you know if the wireless/wlan card on your laptop is compatible with ubuntu??
I've been having the same problem as you and just found out that the reason is that the wireless card on my laptop doesn't work on ubuntu. :(

---

### Post by willow370 on 2011-12-27
Yep shes compatible

---

### Post by willow370 on 2011-12-29
Bump

---

### Post by soyunharlequin on 2012-01-01
Hello Marin and other guys,

I'm trying to setup the same configuration as willow: I have 2 wifi USB interfaces (one of them located outside the house and gets internet connection from ISP, the other, which is weaker, is meant to create access point for the rest of the devices - like laptops, smartphones etc -)

The network manager applet works fine but is there some other app that could give me more control over the network, like viewing who connects to AP? Plus, while I was experimenting with creating new networks, I created some useless ones that don't seem to shut down. It's really annoying, the network list is crowded with names that don't work,even long after I disconnect both USB interfaces. How do i manage that list, and delete those?

Thanks a lot,

SuH

---

### Post by marin123 on 2012-01-01
> **soyunharlequin said:**
> Hello Marin and other guys,

I'm trying to setup the same configuration as willow: I have 2 wifi USB interfaces (one of them located outside the house and gets internet connection from ISP, the other, which is weaker, is meant to create access point for the rest of the devices - like laptops, smartphones etc -)

The network manager applet works fine but is there some other app that could give me more control over the network, like viewing who connects to AP? Plus, while I was experimenting with creating new networks, I created some useless ones that don't seem to shut down. It's really annoying, the network list is crowded with names that don't work,even long after I disconnect both USB interfaces. How do i manage that list, and delete those?

Thanks a lot,

SuH

In Network Manager applet, choose Edit connections and go to Wireless tab and delete networks you don't need.

You could check aircrack-ng pack. I had to create a fake access point for a project in college and I have used a script that uses airmon and airbase programs. Essentially, airbase creates new wireless network, just as you would configure a router. Then you need a DHCP server (check Synaptic or USC for dhcp server programs) and thats it. But I have to warn you, it is complicated, try googling it. After you set it up, you will be able to monitor who connects to the network (and cool other stuff that these forums don't tolerate, but you can ask on BackTrack forums).

---

### Post by willow370 on 2012-01-02
a minor update

i decided to try use a wireless (adsl2) router, ignoring that its an adsl2 router im using it for the wireless on it.

so i have my xbox plugged into the router via ethernet, and my laptop connected via wireless, and i get the same problems as before, do i have to configure something on the router in order to let the xbox use the internet on the laptop?

cheers

---

### Post by soyunharlequin on 2012-01-02
> **marin123 said:**
> In Network Manager applet, choose Edit connections and go to Wireless tab and delete networks you don't need.

You could check aircrack-ng pack. I had to create a fake access point for a project in college and I have used a script that uses airmon and airbase programs. Essentially, airbase creates new wireless network, just as you would configure a router. Then you need a DHCP server (check Synaptic or USC for dhcp server programs) and thats it. But I have to warn you, it is complicated, try googling it. After you set it up, you will be able to monitor who connects to the network (and cool other stuff that these forums don't tolerate, but you can ask on BackTrack forums).

Well I was hoping more of a GUI interface but nevertheless I decided to give it a try and I have to tell you the capabilities seem quite interesting. But three coffee milk shakes and five hours later i came to realize it's just not my thing. I'll stick to Network Manager until a better GUI will pop up (any suggestions?)

Thanks anyways, 

and happy new year!

UPDATE - I tried wicd but it doesn't support more than one interface. Damn....

---

### Post by willow370 on 2012-01-02
hijacked

yay

---

### Post by spiky001 on 2012-01-02
Did you manage to get it working via adsl router???

---

### Post by willow370 on 2012-01-02
No, i just get the same problem as not using one.

I will be investing in a 3g router soon, if that doesnt work - goodbye ubuntu

---

### Post by tkabir11 on 2012-01-06
> **willow370 said:**
> No, i just get the same problem as not using one.

I will be investing in a 3g router soon, if that doesnt work - goodbye ubuntu

Hey willow370- I'm just wondering what have you tried in the beginning to make a hotspot in ubuntu for your iphone. I finally managed to (although rather unintentionally) share my usb dongle connection over wifi for my ipod touch. 
The problem I was having is that through the network connections options in ubuntu I created a new wireless connection- chose adhoc- and chose 'share with other computers' under ipv4 settings. Doing this creates the hotspot- and I could even connect to this new network on my ipod touch- but it doesn't work....and the wifi LED on my laptop kept on blinking. Then I read online that my wifi card may be incompatible with ubuntu- so I didn't bother trying anymore.
Recently I installed Kubuntu Desktop (KDE plasma desktop) on my ubuntu- then in the kde desktop I followed the same steps to setup the adhoc wifi- and wallah!!! I could connect to the internet perfectly on my ipod!!! :D The wifi LED still blinks but only when its busy connecting :) lol- looks like there was no incompability issues with my wifi card after all.
You might wanna give KDE plasma desktop a try (I find it to be way better than the ubuntu unity dekstop)- or if you don't wanna install KDE- you could always install and run windows 7 on virtualbox and try to use 'connectify me' there.

---

