---
title: "internet sharing between LAN and WLAN"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by Casper34 on 2010-11-08
I am having an issue sharing my Internet connection. I have a desktop (DT) running Ubuntu 10.10, a laptop (LT) running Ubuntu 10.04, a laptop (WIN7) running Windows 7, and 2 iPhones. The issue is no matter what I try, Firestarter or Sharing the eth0 connection, I cannot share my internet to my router via wireless (wlan). 

My internet access is in the LAN. I would like to share my LAN to my router, so i can connect all my computers and phones. Everything that i have found on the web is LAN to LAN sharing, I do not have 2 LAN cards in my DT. I have a LAN and a WLAN. Is there a simple way? Am I just missing something simple?

---

### Post by spiky001 on 2010-11-08
Is the router the modem I thought that is how they were

---

### Post by Casper34 on 2010-11-08
a modem allows you to have internet access, a router aloows you to share that access... but here is the issue. The reason why i need to do it this way is that i am on a shared access now and my router will not allow access to the net. 

I can connect EVERYTHING to the router with zero problem, but i cannot have internet access. sooooooo i was thinking about since i am posting here, i  have net access with one computer at a time, that i could connect to the net through my LAN on my DT and share the connection to the router via the WLAN.

---

### Post by spiky001 on 2010-11-08
In network manager is the eth0 connection on Dt set to share with other computers

---

### Post by puppywhacker on 2010-11-08
if you only get internet on one device at the time you are getting only one IP address from your internet provider, to get internet on all devices you will have to make a NAT. This means that either your modem or your 'router' will have to translate internal ip-addresses to your one real internet address.

internal ip-addresses start with 192.168 or 172.16 or 10

you can use your ubuntu as a sharing device if you set up your ubuntu as default gateway for all your other devices.

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo sysctl -w net.ipv4.conf.all.forwarding=1

```

---

### Post by Casper34 on 2010-11-08
@ Spiky...

I have done that and i still get no connections.

@ Puppywhacker... (wrong, but funny name)

will that "code" allow me to use share my LAN connection through my WLAN card? and my IP address starts out as 192.168

---

### Post by Gotenks on 2010-11-08
Ooh, I need exactly that. Right now, I am sharing my internet with a bunch of people via ad hoc, using windows, so it's kind of a problem, since I can't really start using ubuntu. I've tried guides, like this one
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)   with zero results. If someone succeeds in making this possible, please enlighten me with your knowledge!

---

### Post by Its_Rishi on 2010-11-09
I have two desktops ones os is UBUNTU 10.10 which is downloaded from
"http://www.ubuntu.com/desktop/get-ubuntu/download"
 and the other is Windows 7
I am new to experience the linux world so i don't know the commands and atleast where to type them
I had a broadband connection which allows to connect about 5 systems at a time through WLAN 
I want to share my internet connection to both of my systems with ubuntu to windows 7
can it possible...?
if so how can i made it easy...?

---

### Post by Casper34 on 2010-11-12
bump

---

### Post by grahammechanical on 2010-11-13
I do not know how to solve this but I want to try to understand what you want to do. The desktop has the wireless device that connects to the Internet and you are using ethernet to connect the other computers to the desktop, perhaps thought a router. Is this correct?

If the desktop is in Infrastructure mode then it will not work. According to my motherboard user guide infrastructure mode makes the machine a part of a Local Area Network that connects to a wireless access point. You want the desktop to be an wireless access point for your own little LAN. Try Ad-hoc mode. Just guessing.

regards.

---

### Post by Casper34 on 2010-11-13
@[grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")

Ok, i live in a studio apt. the owner has one line headed in for about 10 units. She has that routed off. So, for some reason when I plug my router to the wall, i cannot get out to the net, BUT i can if i hook up one computer at a time. I have tried changing the settings in my router and i have spoken to someone else about this issue. 

I have a LAN (wired) card and a WLAN (wireless) card in a desktop, 2 wireless laptops and 2 iphones. I would LOVE to have the desktop wired to the net vis the LAN, then share that connection through my WLAN to my router, so my 2 laptops and 2 iPhones can connect. I do not have a problem connecting anything to the router, laptops, phones, or the desktop. where the issue is i cannot share my LAN to my WLAN on the desktop. Everything i have read online is LAN to LAN, I need LAN to WLAN.

---

### Post by motsteve on 2010-11-14
I have a similar situation here.  I have a cable modem hooked to a 4 port router (DLINK DIR600) with one wlan port also.  One of my hosts, an iMac is configured to receive internet through ethernet and it is also configured to share internet through its internal wifi port.  No fancy anything to do that. This works fine for my host on the other side of the house, but I want to set up my Ubuntu box which is also receiving internet through eth0 from the router with a wifi-USB adapter, so that I can put the adapter in a corner reflector to give it some good gain and share the network with my neighbor across the street.  I thought internet sharing on Ubuntu would be easy like the Mac, but no go.  Believe me!! I'm not knocking Linux as that is my primary OS, but this situation shouldn't be that difficult I would think.  Networking GURU's out there, PLEASE help.

BTW, I tried all the tricks in this thread and still no go.

Bottom line: How to set up a Lucid Lynx machine with eth0 in and a wifi-USB so that it is an AP.:confused:

---

### Post by motsteve on 2010-11-15
Since no one seems to want to respond, I would like to tell the people still waiting that there is still some more info on this site that I just found.  I think it was published today.  I hope it is useful info for ya'll.


[http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools](http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools)

Steve

---

### Post by Casper34 on 2010-11-15
> **motsteve said:**
> Since no one seems to want to respond, I would like to tell the people still waiting that there is still some more info on this site that I just found.  I think it was published today.  I hope it is useful info for ya'll.


[http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools](http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools)

Steve

Were you able to have the net in on you eth0 connection and share with the wlan0 connection? I know i can do this VERY easily on windoz.... I REALLY DONT WANT TO INSTALL WINDOZ ON MY DESKTOP!!!!:rolleyes:

---

### Post by Casper34 on 2010-11-18
Please someone let me know if this is possible, Im begging you!!!

---

### Post by Casper34 on 2010-11-23
YAY!!!!! i would like to thank you all for your help!!!! yes i am exaggerating!!! just so you know how EASY this is to do with WIN7.....

1) make sure your connected to the net and your router.
2) goto network sharing center
3) click change adapter settings
4) highlight both your wired and wlan connections
5) right click, BRIDGE connections........

30 seconds later i have WIFI!!!!!!!! it sucks that i have to have a WIN7 computer, but hey its been 2 weeks and no real answer. Again thank you all!!!! and i really hope i can help some of the others that are looking for the same thing i am. maybe with this post someone will say.... ohhh ya thats simple to do in UBUNTU!

---

