---
title: "KVPNC VPN Please help!"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by provomike on 2009-10-06
I am slowly going crazy here. My new job requires that I connect to their MS VPN server. I have installed the network-manager-pptp and of course it is broken and shows no VPN options. I have installed KVPNC which I have set up and tried many configurations and nothing seems to work. At best I will connect for about 3 minutes and then the connection closes. During the time I am connected I have aquired an IP from the server but cannot do anything on the network - no browsing, no ssh logins on the intranet or internet. NADA. netstat -r shows the ppp0 connection with the new IP but just * for gateway.

I really need this working as my job depends on it. Right now I am using my XP for access - that just ain't right. Any and all suggestions will be appreciated!

---

### Post by jonobr on 2009-10-06
Hello,

I have seen before that VPNs and MTU sizes can be a bit of an issue, 

there have been cases where people have lowered their default MTU from (in the case of ethernet) 1500 to something lower then that eg 1412.

Also, if you look in the syslog, there are probably error messages that may give an indication of whats happening.

---

### Post by provomike on 2009-10-08
can any provide the EXACT settings I need to make this work. Basically I can connect to the corp network on my XP using the simple connection wizard and entering the system url, requiring data encryption and username/password authentication. Very simple stuff. Yet on Ubuntu 8.04 I cannot get ANY VPN connection working in any way shape or form. This is a total embarassment. Anything Windows can do Linux should be able to do better!

---

### Post by jonobr on 2009-10-08
Hello


Im a linux/ubuntu advocate and try my best to help and encourage others to move to linux, not necessarily ubuntu but x operating systems in general.

IMHO I am thinking given your job depending on it, and now, embarrassment that is stemming from this issue, you need to focus on your job rather then your operating system.

There is no click of the finger or button to press with some of these issues, but regarding my post on changing the MTU, if you run ifconfig, find out the name of the ethernet device, Im going to assume its a eth0 ethernet device.
THen note the current MTU, again, Im assuming its 1500

To change the MTU to a lower vaule
```
sudo ifconfig eth0 mtu 1412
```
If that doesnt improve things then you could up to the MTU 
1492.

I also mentioned taking a look at and posting the contents of syslog.

---

### Post by provomike on 2009-10-08
jonobr,

I appreciate your suggestions. I have dropped the MTU from 1500 to 1412 with the same result. The same for 1492. Below is the syslog out put during an attempted connection. I might add I have worked with Unix since 1982 however, Linux is another thing. I can get my SGI origin 2000 working just fine. While I am trying to get KVPNC to work I can't even get the VPN tab on the network manager to show up. Very flakey.

Okay - pasting the text of the syslog makes this editor think I am putting in a bunch of images so I have attached the syslog.txt file

---

### Post by jonobr on 2009-10-08
You cut me to the quick,

Im an old Unix person myself. SCNA for the 2.5.1 and Sol 8 enviroments, and kicking around the idea of going for Sol10, although Im thinking of hanging around a while to see what happens with this oracle thing.
(BTW old as in working with , not as in age, although now Im getting a bit grey.)


In that time I did a lot of work in modem dialup and carrier/ISP modem troublshooting.


Im not sure how much you know on negotiaton of PPTP and PPP, but its been some time since I have done it, so Im a bit rusty.

Your trace was useful, 

There are two parts to negotiation of PPP and PPTP.
LCP and IPCP.
In your trace its all LCP , thats why you see a lot of config requests and config ack.
Its pretty much, "here is what I want you to do", and the client says, "ok, I agree with this and this but not this" and so on.

I notice you never get to the next step up which is IPCP.

The thing tried to kick off with a username offer (michael)
> sent [EAP Response id=0x26 Identity <Name "michael">]
which is rejected and the server side terminates the link.
> LCP terminated by peer ((1rM->^@<M-Mt^@^@^BM-3)


You notice it does not even try to renegotiate.

Im guessing , with my rusty knowledge, that your client is set up to only support EAP and will not entertain anything.

I dont have my kvpnc in front of me, but is there a check box or option to disable EAP.

Maybe you could try that again, and get another syslog to see oif it goes a bit further?

My first thought looking at your log was MRU = 1400.

I was thinking if you set your mtu to that and try also it would be interesting to see if this had any affect.

Looking down through the logs though, I can see it gets further so, I thought MRU is not the cuase.

I would also, if you were able, have a chat with the admin, if they are reasonable.
He may be able to tell you whats what and whats supported.

---

### Post by jonobr on 2009-10-09
one other thing I should add,

if your asking your IT mananger about settings,
I would ask about the authentication mechnaism used.
It will either be PAP chap or MSCHAP or similar.

In your windows client when you setup a VPN it enables almost all by default PAP< CHAP, MSCHAP(and has EAP disabled) , see attahced,
LCP will figure from the server if its doing pap (ie simple sending of usernames and passwords in clear text9 or chap, (a challenge hanshake authenticatio protcol

Figuring that out may be of use.

You may be able to figure it by disabling each protocol one at a time and see when the windows box fails to connect.

Cheers

PS
This all works so long as your IT guy is not [THIS GUY]("http://www.youtube.com/watch?v=geZoES9KQ-Q")

---

### Post by provomike on 2009-10-09
I actually made some new headway last night. I am now connecting and doing an ifconfig returns the following:

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.0.0.216  P-t-P:10.0.0.217  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:126 (126.0 B)  TX bytes:90 (90.0 B)
My only real issue now is that the gateway for the ppp0 connection does not appear to be configured. Experimenting with that now.

thanks for the help. While I have been working with Unix since Torvalds was in diappers this was well before the VPN days - we used uucp back then. I haven't done all that much with VPN and find it very frustrating.

---

### Post by jonobr on 2009-10-09
Mmmm, thats good to hear.


I notice your MTU soze is different. did you change that yourself?

Also, looking at your routing table may help out here if you do a netstat -rn
You may need to add in a default route for your ppp0 interface.

Im wondering also, can you ping the tunnel terminator 10.0.0.217?


uucp..... they were the days.
Next we will be talking semaphore :-)

---

### Post by jonobr on 2009-10-09
I saw your other post on a similar problem where the guy gives his routing table,
as mentioned above it seems as if your issue is the same as that one

---

