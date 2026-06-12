---
title: "WPA Enterprise trouble (Eduroam)"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by dreamsR4living on 2011-09-22
About two weeks ago I bought an Asus Eee PC to be able to work on my assignments at school. The first thing I did was to install Ubuntu 11.04 of course, which is very smooth on my new netbook.

For more than a week I am trying to connect to my school's WPA Enterprise wifi (Eduroam), but whatever I try, nothing seems to work.

I am entering all the information I am supposed to, but I can't get the wifi to connect.

I tried to connect with the standard Gnome Network Manager. I tried to connect with WICD. Then I tried to change my password on my schoolnetwork, which didn't work, so I changed it back. Yesterday I removed Ubuntu and installed Fedora 15, just to see if this is an Ubuntu related problem. But also Fedora can't connect to the network in any way.

This is driving me crazy. I am able to connect with the internet at school through my Android phone, but this is not ideal, because it is draining my phone's battery quickly.

I would like to know it if there is anyone who has any idea why my laptop cannot connect to WPA Enterprise.

Thanks in advance.

WPA Enterprise settings below;

Wireless security: WPA & WPA2 Enterprise
Authentication: Tunneled TLS
Anonymous Identity: blank
CA Certificate: Equifax Secure Global eBusiness CA-1
Inner authentication: MSCHAPv2
Username: ********
Password: ********

---

### Post by Chiel92 on 2011-09-23
> **dreamsR4living said:**
> 
I am entering all the information I am supposed to, but I can't get the wifi to connect.


Same problem here. Still no one knows a solution?

---

### Post by dreamsR4living on 2011-09-26
> Same problem here. Still no one knows a solution?

I would think that there are a lot of professional users on this forum with some WPA Enterprise configuring experience...

I also posted in an existing thread on the Dutch Ubuntu Forum, but also there I got no reaction.

---

### Post by Baneblade on 2011-11-23
This is not a new bug either. I have found posts with the exact same problems from years ago.

I'm seeing this problem on my laptop (Intel PRO/Wireless 4965 AGN) with Eduroam at university. There doesn't seem to be a fix from all the posts I have read about it. My work around at the minute is to tether my phone :(

---

### Post by I_can_see_the_light on 2011-11-23
Are you sure all the settings are correct? I've been able to connect to the same type of network at my university but I've had to change the authentication type to PEAP according to the instructions provided.

---

### Post by Baneblade on 2011-11-23
> **I_can_see_the_light said:**
> Are you sure all the settings are correct? I've been able to connect to the same type of network at my university but I've had to change the authentication type to PEAP according to the instructions provided.

Yes, very sure my details are correct. I have tested them on a friends laptop who is running ubuntu (11.04) as well and they work fine. I have included a screenshot in case it will help someone else though.

I seem to be able to connect very rarely if the machine has just started for the first time while at University in range of the wifi. It will not work through a reboot, or turning it off and on again. Is there some sort of time-based cache that would cause this sort of behaviour? 

I have tried talking with the IT department, but when I showed him the problem, he couldn't say anything other than, "I have never seen this type of interface before", and after explained it was linux he said, "why do you use linux?". So not much help there, lol.

---

### Post by sparhxc on 2012-09-05
Has anyone found a solution to this? I'm currently experiencing the same issue.

---

### Post by pjottr on 2012-11-01
I use an EeePC netbook and had the same problem, connecting to eduroam. My college (in the Netherlands) only provided information on how to connect with Ubuntu 8.04, but not with ubuntu 12.10. In the older tuturial they suggested you should not use any certificate. However, this did not work for me. So I downloaded the "AddTrustExternalCARoot.crt" certificate and used it with the same setting I had before: WPA & WPA2 enterprise/ Protected EAP (PEAP)/ ..../ PEAP version: automatic/ inner authentication: MSCHAPv2 
It worked for me, so maybe the trick is to try different certificates and check information from other universities using eduroam on Ubuntu 12.04 (which I did).

---

### Post by rdymac on 2012-11-20
Ubuntu (12.04):

Connection name: eduroam

SSID: eduroam

- Wireless Security

Security: WPA & WPA2 Enterprise

Authentication: Tuneled TLS (TTLS)

Anonymous identity: _blank_

CA certificate: download a certificate and place ir here

Inner authentication: PAP

Username: [email]mystudentusername@us.es[/email]

Password: mypassoftheUniversity


--

As seen here [http://randybrito.tumblr.com/post/36142380979/wifi-eduroam-universidad-de-sevilla](http://randybrito.tumblr.com/post/36142380979/wifi-eduroam-universidad-de-sevilla) I'll update the post with those include in the To Do list, I've successfully set up wifi on those

---

