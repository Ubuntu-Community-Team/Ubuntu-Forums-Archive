---
title: "DDNS on two ISP"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by razing32 on 2011-09-21
Hi,
My first post and it's going to be something weird so bear with me please.

I want to set up a network lab at home. I have two ISP providers. 
I want to set up DDNS as to be able to access a computer connected to both the Router connected via PPOE to one provider and via a modem to another provider. I want to do this for redundancy.(Don't ask why I have two ISPs , it's a very long and boring story)

The section you have on DDNS in the help section was helpful but in my case I'm not sure how to exploit the redundancy provided by two ISPs.How can I swich over default gateway ?

Keep in mind I'm what you call a n00b in regards to Linux - I've played with it in the past but I can't claim to be competent in using it just yet.

---

### Post by dave01945 on 2011-09-21
i believe you will need to use 2 dyndns hostnames one for each ip address the easiest way to set that up would be if your router has options for dynamic dns update in it use that for one of the connections and use the dyndns client for the other so you will have one hostname for the router connection and one for the modem

also i am presuming you do not have static ip's if you do just enter them on the dyndns website and you wont need to update them

---

### Post by razing32 on 2011-09-21
No , I don't have static IPs . If I did this would be much easier.

My Router which is a WRT54GL is capable of supporting DDNS if its manual is to be believed. I'll have to try it. The modem , I'm not sure , it's a Huaweii Echo Echo 520b.

So if I understand you correctly , I will have one DDNS setup on the router for ISP1 with one domain and a second domain for the modem ISP with the client running on the PC , right ?

And what additional config need i make to the PC to use both ISPs ?

---

### Post by dave01945 on 2011-09-21
yeah that is correct the router will update the dns on 1 isp and the computer will update on the other also for incoming connections you will have to configure the firewall on the router and pc to allow the connection on the ports you require also you will need services listening to those ports i.e if you was using ssh for example you would need to configure ssh to listen for connections on the forwarded ports

---

### Post by razing32 on 2011-09-21
So does an operating system like Ubuntu now how to handle two different NICs by default ? 
The router has a default gateway of 192.168.1.1 while the modem has a default gateway of 192.168.0.1 so don't I have to make a script that tries to ping via each of the NICs and then chooses its default gateway to be the one that is up ? 
Don't I need to config the files in /etc/ ?

Also , I may have a static IP address on the modem's ISP but I am not sure - just noticed they offer the service but I am unsure if it's just for companies or if they offer for private use also.

---

### Post by dave01945 on 2011-09-21
if you want to use both connections for outgoing traffic that will require some configuration and possibly a script to ping the interface to see if it's active this post gives some advice on how to achieve this 

[http://ubuntuforums.org/showpost.php?p=5572761&postcount=15](http://ubuntuforums.org/showpost.php?p=5572761&postcount=15)

for incoming connections the services just need to listen too the right interfaces or both depending on the service you're using usually ip 0.0.0.0 will listen to all available interfaces

some isp's do offer static ip's to customers but you will have to contact the provider to find out what the ip would be

--edit--

here is another post that should help if you want 2 outgoing connections alot more detail in this one

[http://ubuntuforums.org/showthread.php?p=8129464](http://ubuntuforums.org/showthread.php?p=8129464)

---

### Post by razing32 on 2011-09-22
Firstly , dave01945 thanks for the links. The idea may change though.
 
Just got an interesting idea from a work colleague.
 
I can upgrade my Linksys router from a WRT54GL to a E3000 - it does cost a bit , but he said I can install a DD-WRT Linux OS and can set up rules on it so that it uses the WAN port for ISP1 and LAN port 4 to get to the modem for ISP 2.
 
And then I can add a script there to prevenet traffic from one ISP going to the other - that would be very bad ; and also a ping script that tries to reach google or yahoo or something and uses one link and if it gets more than 50% loss it tries the other. Also , I can add two static routes with different metrics. 
 
Another LAN port can be used statically to connect to a PC where I want to connect and the other two ports go into a switch(es) and give the rest of my home devices redundancy.
 
What do you guys think ?

---

### Post by perspectoff on 2011-09-22
For a network lab, you're talking about moving towards a load balancer (in the Beowulf model), for which you ought to have a dedicated machine. That's not a noob task.

For a home basement "network lab", why not just have two routers, each assigned to an ISP and each on its own subnet?

That's a cheap, fast, easy solution (and what I did at home for many years). Wireless connections would choose one subnet or the other manually. Machines that connect to both networks can have two NICs, one for each network. 

You can nest networks, keep them independent, keep identical settings for a machine that moves back and forth, or different settings for each network. 

I personally prefer independent parallel networks without crosstalk between them so that I can quarantine some machines with certain purposes to one network and other machines to the other. 

If you're doing it just for redundancy, however, a load balancer is the way to go.

---

### Post by razing32 on 2011-09-22
@perspectoff
 
That's why i mentioned upgrading to Linksys E3000 , for the better hardware that can run a small distro(I think there is a DD-WRT specfic distro). It's for redundancy so if there's a problem on one ISP , I can use the other. Then from the E3000 I go to a Linux machine which has network devices connected on console ports - that's my current idea. 
 
I know this is hard , but once I have a SSH tunnel , the colleague who gave me the idea told me he would show me how to set up rules, scripts , VPN and DDNS so I can access this device regardless of its IP.
 
It will be a big challenge , but I actually think fondly about the experience I will get from this.
 
If it helps I can make a diagram of this setup. Although I don't know any free/open tools other than Visio which is proprietary.

---

