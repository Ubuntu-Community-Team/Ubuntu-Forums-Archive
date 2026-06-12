---
title: "changes in VPN speed"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by annec on 2010-10-07
Hi!

I recently set up a VPN (with openvpn) and something bugs me : the speed of the connection is not consistent across time. For instance, 2 days ago, it was really fast and today it is slow as hell. 

Regardless of the VPN server provider, I was wondering what would usually cause such changes in the speed. For the record, I am using vpntunnel.se after reading some good reviews. My question is general but if you feel it might only be due to the provider, I'd appreciate some links to fast servers.

Thanks in advance for your insight!

AC

---

### Post by robert_pectol on 2010-10-07
Many personal VPN providers throttle their clients after a determined amount of data or time.  I'm not saying that is the case with your provider.  But it's not uncommon.  Because of that, I opted to set up my own OpenVPN server on a box that I have colocated at a data facility.  I run all my traffic through it for both my home Internet connection and my laptop when I'm at work, traveling, etc.  I have never noticed a decrease in throughput speeds unless there was something going on with my local connection to the 'Net.  But with a good local connection, it's always very fast, no matter how much data I put through it.  In fact, with compression enabled, I often times get equal or better performance through the VPN!  Latency does increase because of the extra path distance, but not significantly.

---

### Post by annec on 2010-10-07
Thanks for your answer! That is a possible explanation indeed. I'll investigate to see if they tend to slow down the throughput. 

Thanks again!

---

### Post by annec on 2010-10-07
Actually, something else is a little odd: browsing may take ages while downloading files is equally fast or faster than before VPN. 

I tested both Firefox and Chrome and the result is the same: many pages are very very slow to show up. 

Could it be that on top of the throughput slowing from the provider, I missed a step in the configuration of my browsers? 

Also, I have another VPN related question: Thunderbird receives my emails when my VPN is on, but won't send any. I googled this issue without success. Is it normal (I'm guessing Thunderbird expects some default parameters that change when the VPN is on)? Is there anything I can do? It is annoying to have to put the VPN down to send mail. 

As you will have probably understood, I'm new to this but I'd like to catch up!

Thanks in advance,

AC

---

### Post by annec on 2010-10-07
Just illustrating the slowness issue : 

No VPN: 

```
ac@AC:~$ ping -c 5 google.com

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 22.195/25.176/28.539/2.664 ms

``` 


With VPN: 

```
 

ac@AC:~$ ping -c 5 google.com

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 52591ms
rtt min/avg/max/mdev = 70.211/72.885/77.402/2.724 ms

``` 

That's quite a difference!

---

### Post by gombadi on 2010-10-07
No VPN - Path from your machine to google - just down the road

With VPN - Path from your machine through the VPN and then to google - may be longer and therefore will take longer :-)

---

### Post by annec on 2010-10-08
Yes I figured that much, but THIS slower? Most VPN providers I checked out do warn that the connection may be slower but not significantly. I have the impression that I'm back to 56k when browsing :)

That's it, I'm asking the service support...

Any insight on my Thunderbird/smtp issue?

Thanks!

---

### Post by gombadi on 2010-10-08
> 
Also, I have another VPN related question: Thunderbird receives my emails when my VPN is on, but won't send any.


Will need some more information. What type of "won't send any" do you mean? - Connection refused, connection times out, No route to host, relay access denied etc.

What does Thunderbird say when it won't send?

---

### Post by annec on 2010-10-08
Thanks for your answer Gombadi. 

Here's the error message I get: 

****************
An error occurred sending mail: The mail server sent an incorrect greeting:  5.7.1 <unknown[178.73.204.243]>: Client host rejected: Access denied.
****************

(where 178.... is the IP address I currently have through the VPN)

Actually, it seems quite logical to me that access is denied since Thunderbird tries to send mail through smtp.<myISP>.fr, but I was wondering whether there was a way to change the smtp settings (or use another type of protocol) to make it work with the VPN?

---

### Post by gombadi on 2010-10-08
You will have to check with your ISP to see what login methods they support for smtp and then configure Thunderbird to log into your ISP account with that method. You should be able to leave that as the default so you don't have to change if you are on or not on the vpn.

I don't use Thunderbird so you will have to hunt around to see how to configure it.

---

### Post by annec on 2010-10-09
OK, thanks.

Actually since I chose to replace Windows with Ubuntu, I am quite used to hunt for answers :) But it's worth it overall!

---

