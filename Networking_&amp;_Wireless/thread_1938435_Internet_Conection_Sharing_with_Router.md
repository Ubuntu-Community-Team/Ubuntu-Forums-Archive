---
title: "Internet Conection Sharing with Router"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by Coronach on 2012-03-09
I've done a search, but I didn't find my answer in the myriad of results. If I missed something obvious I apologize. I'm new, so this may be asked and answered already, but I didn't see it.
 
Here's my situation. I live in the sticks and my only viable internet connection is cellular. Right now I have my Android phone set up to provide wired tether to my Ubuntu-equipped laptop. I also have a LAN (centered on a Linksys E4200 router) for file and print sharing, and also for a media server on a NAS. So, if I want to connect to the internet I need to disconnect from the LAN and hook up the phone, and if I want to file share or stream media, I need to disconnect from the internet and reconnect to the LAN. It works, but it's cumbersome. I want to get everything running through the LAN.
 
What I'm trying to do is as follows:
 
Connect my phone to the laptop (usb0) and share that connection with the router (via eth0). Can I achieve this by just setting up conection sharing in Ubuntu and plugging an ethernet cable into the ethernet port on my laptop and into the WAN port on the router? If yes, is there a tutorial or write up already that I can read? If no, is there something that I can do that will achieve the same end result?
 
I'm running Ubuntu 11.04 (Natty) Kernel Linux 2.6.38-13-generic.
 
Thanks in advance for your help!
 
Mike

---

### Post by inobe on 2012-03-09
here are some solutions.

1) ad hoc [http://www.youtube.com/watch?v=pt-gFJTgp9k](http://www.youtube.com/watch?v=pt-gFJTgp9k)

2) or get a second router, tap directly into router wan port from your lan card, open your network manager and share your lan/ eth0... restart router to renew the ip.

downside, no file sharing, only internet!, but this defeats the purpose of everything working together considering the extra hardware and switching between them.

3) an evdo router [https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=evdo+router](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=evdo+router)

that router uses your usb/ phone device as a modem and the entire system functions simultaneously.

the best i got mike.

---

### Post by 741Baus on 2012-03-09
Hi Coronach , I recently set up Internet Connection Sharing from my main computer through a router to a second computer running XBMC in a situation similar to you  using this guide 
[http://help.ubuntu.com/community/Internet/ConnectionSharing]("http://help.ubuntu.com/community/Internet/ConnectionSharing")
But there were a few hurdles that I had to get over before I could achieve this 
1 A few years ago a lighting strike blew out the lan port in my modem so was only able to connect to internet via usb this worked fine but running 2 computers and swapping usb connection out to either computer became very tiresome really fast.
2 To enable I-C-S I had to install drivers for ethernet to allow I-C-S through the lan port.
Once this was done I was able to share the internet connection and files between both computers and also as the router was wi-fi I was able to set it up so as both my and my wifes smart phones could connect to the internet via the router using my broad band data plan.
Yes it is possible I just followed the above guide how ever a couple of the commands have been superseded namely 
```
sudo /etc/init.d/network-manager restart
```
with
```
 sudo service network-manager restart
```
if you wish to stop Network Manager
```
sudo service network-manager stop
```
I hope this helps Pete
BTW if the url doesn't work (I've tried before to insert urls but without any luck)try Googling Internet Connection Sharing Ubuntu

---

### Post by Coronach on 2012-03-10
Thanks for the replies. A couple of questions:

Does the wireless LAN on the router side work "normally"? As in, can you connect to it just like you would a normal wireless network, or is there a lot of setup every time you log in?

In the same vein, each time you hook up the phone, is it a simple connection, or do you have to go through a setup process?

Thanks,

Mike

---

### Post by Coronach on 2012-03-10
OK, halfway there. I have the connection configured to share to another computer. Now all I have to do is work out the router angle and I'm set.

To confirm, the ethernet cable will go into the WAN port, not one of the LAN ports, correct?

Thanks again!

Mike

---

### Post by Coronach on 2012-03-10
Also, to clarify (and display my n00bishness for all to see), you type the following command in Terminal, right? Or someplace else?> sudo iptables -t nat -A POSTROUTING -j MASQUERADEMike

---

### Post by Coronach on 2012-03-10
OK, it's working with the router, too.

The only glitch I encountered was in typing in the command line, it game me an error message that it could not locate MASQUERADE. I made sure that dnsmasq-base was installed and dnsmasq was not. However, despite not executing the command, the connection still seems to work via the router.

Still testing, but is there any reason to expect problems?

Thanks again, guys.

Mike

---

### Post by inobe on 2012-03-10
mike, where are we at now, what did you do as far?

kinda lost on those commands you were doing, and why.

---

### Post by 741Baus on 2012-03-10
Hi Coronach with issuing 
           ```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE 
```
 I didn't get an error when running that command but with the router working I really don't know if it is necessary or not ? 

I just followed the guide and have had it up and running for a few weeks now with out any issues but I think I've set it up via the gateway method using ip addresses , but being a few weeks ago my memory is a bit hazy , I should really write this stuff down for reference , but I can't see you having to many problems if your router is working . Peter

---

### Post by Coronach on 2012-03-10
I was just following the instructions provided in the link. It seemed to be working fine with the router even though the command didn't work. I dunno.

My wife called me at work and said it no longer works, but I'm not able to troubleshoot it from 35 miles away, so I'll look at it when I get home. It was simple enough to set up, so if it all needs to be rebooted/reset every now and then it's not a huge deal. She still has LAN and internet access the old way, so its fine. I'll be curious to see what failed, though.

Mike

---

### Post by Coronach on 2012-03-11
Well, I got home, connected my phone and it worked fine, so I'm not sure what happened. I'm also not sure of the issue was between the phone and the computer or the computer and the router. I'll have to wait for her to break it again. ;)

Mike

---

### Post by Coronach on 2012-03-12
OK, I still have not observed a failure to connect or share the connection, but we have noticed an oddity or two:
 
1. My wife uses an email program (Thunderbird) to connect to her work email. Sometimes it works, sometimes it does not.
 
2. Some websites don't seem to work sometimes. The most obvious ones are banking websites. However, it's not an https issue, as several other banking websites work just fine, despite using an https connection, and logging on to my work email via an Exchange server (also https) works fine. It's possible (probable?) that there is some additional security at play on some of these sites, but I don't know what it is.
 
Oddly, the connection difficulty is experienced both on machines accessing the LAN and on the machine directly connected to the phone. And yes, I have had success connecting to those sites in the past.
 
Any ideas?
 
Thanks,
 
Mike
 
ETA: This seems to be an Ubuntu issue, though not necessarily and ICS one. I did a little testing at one of the sites ([www.53.com]("http://www.53.com")) using the following methods and came up with the following results:
 
1. Phone USB-tethered to Ubuntu computer, Ubuntu computer doing ICS to the LAN, looking at the site from a Win7 computer on the LAN. Result: can't connect.
 
2. Phone USB-tethered to Ubuntu computer, Ubuntu computer looking at the site directly (taking the LAN/ICS out of the equation). Result: Can't connect.
 
3. Phone USB-tethered to a Win7 computer, using that computer to access the site. Result: connects fine.
 
4. Phone wirelessly-tethered to a Win7 computer, using that computer to access the site. Result: connects fine.
 
Is this a known issue with Ubuntu? Is there a fix?

---

### Post by 741Baus on 2012-03-12
Hi Mike, I just read your last post and your problems (oddities) are getting a bit beyond my expertise , however I have had at times connection issues through ICS and have fixed temporarily ( it seems to happen more or less after a week ) by running these commands ,

```
 sudo service network-manager stop
``` 

```
 sudo rm /var/lib/NetworkManager/NetworkManager.state
```

```
 sudo service network-manager start
```

to get ICS up and working again , I have no idea why this happens but running these commands resolves the problem for me .Peter

---

### Post by Coronach on 2012-03-13
OK, last night I realied that there was one thing I did not test, running the connection wirelessly. So, I disconnected th ephone from USB tether (usb0) and connected via wireless. I can access the sites just fine. So, the difference seems to be whether the phone is connected via a wireless connection or a USB connection. Does this make any sense?
 
Also, oddly, the wireless connection seems to be slightly faster. I ran some network speed tests and using the wireless tether was slightly faster. The difference was small, but consistent. Any idea why this would be?
 
Mike

---

### Post by 741Baus on 2012-03-13
Mike, 
     here's a thought perhaps its the phone itself and how it connects either via usb or wirelessley , if you get better connection wirelessley , then go that route rather than usb tethering ,I'm only speculating here as it does seem odd that you get a better connection wirelessley than tethered again I'm only speculating .

> So, the difference seems to be whether the phone is connected via a wireless connection or a USB connection.

Last year when we got new mobile phones I tried tethering via usb (as you have), but because we are right on the fringe of a wireless black spot connection was very spotty , lucky to get 1 bar of service , very slow connection and timed out more times than not , this was to be my back up plan in case I lost broad-band and have since discarded that option .

I'm plumb out of ideas as to why this is so ,as I said go the route that works best for you , Peter

---

### Post by Coronach on 2012-03-14
Yeah, right now I'm just going with the flow and using wireless. It has a few disadvantages, like slower charging and a little less connection stability, but it's slightly easier to set up, so it's kind of a wash.

The difference seems to be how Ubuntu sees the connection. The windows machines don't care if the connection is usb or wireless, but apparently ubuntu does. I just don't know why.

Hmmm. I should run a speed test on windows and see if the same throughput speeds are seen. I wonder if whatever is messing with the usb connection is also throttling back the speeds...

Thanks again!

Mike

---

