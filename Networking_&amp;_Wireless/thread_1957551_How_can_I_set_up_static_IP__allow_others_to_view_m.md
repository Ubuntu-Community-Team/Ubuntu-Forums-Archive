---
title: "How can I set up static IP / allow others to view my Lampp install? (11.10)"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by Lucypie on 2012-04-12
I am a complete know nothing. I mean, I know nothing about networking. Its so far above my head. I need like step by step instructions. I've looked everywhere and I keep getting hard to understand tutorials.
I saw something in some settings saying I use Lo, but if I go to my internet connection and hit edit, the device is wlan0. So I have no idea what I'm doing. For any information you need, please tell me. I have no idea! I use 11.10.

---

### Post by roelforg on 2012-04-12
ifconfig gives you the ip on the lan

What do you mean by "others"?
If you mean...
...on the same lan: use ifconfig for your lan ip and others can use it to view
...the outside world: ouch, you're gonna need to do port forwarding and get a domain name (no-ip.org has free ones) == a lot of work

---

### Post by Lucypie on 2012-04-12
THe outside world. Some people have it set simply to their IP, a static IP. I just want about 3people to see it, one person is on my connection, two are not.
But also, IW ant to be able to add so more people can if I want to. I don't care much for security, these people are highly trustworthy.

---

### Post by roelforg on 2012-04-12
Look into portforwarding on your router.
I can't help because it's diferent for each router.

---

### Post by Lucypie on 2012-04-14
Okay. So I did this. I went to my Netgear router, I went to port forwarding. I typed in a random name, I opened port 4289 (something completely random) and I typed in the network IP of me: 192.168.1.4 (that is my individual computer). I set it as BOTH. Those were all the available settings. (PS, I was required to put a LAN IP (192.168.1.?) and it would not let me put my public IP)

I then went to /opt/lampp/etc/httpd.conf and put in the listening setting 4829 and to the servername 192.168.1.4:4289. I've tried variations from my public IP to the default network gateway. None of it works for others, and only that variation works for me.  If I go to 192.168.1.4:4289 it loads on my computer. Of course nobody ELSE can access it like that, but I can. If you go to my IP it will not work, and my IP:4829 it will not work. 

I went into ubuntu manuals and found out there is a baisc port blocking firewall, so I disabled it, still didn't work. I enabled it and added the rule allow all to 4829. Still didn';t work. Using canyouseeme.org, it can't see me. Usually i get the message "No route to host" or "Connection timed out". Currently it is the former. 

What am I doing wrong? Did I edit the wrong file? Do I need to set something else up? Thank you for any help!!

---

### Post by haqking on 2012-04-14
> **Lucypie said:**
> Okay. So I did this. I went to my Netgear router, I went to port forwarding. I typed in a random name, I opened port 4289 (something completely random) and I typed in the network IP of me: 192.168.1.4 (that is my individual computer). I set it as BOTH. Those were all the available settings. (PS, I was required to put a LAN IP (192.168.1.?) and it would not let me put my public IP)

I then went to /opt/lampp/etc/httpd.conf and put in the listening setting 4829 and to the servername 192.168.1.4:4289. I've tried variations from my public IP to the default network gateway. None of it works for others, and only that variation works for me.  If I go to 192.168.1.4:4289 it loads on my computer. Of course nobody ELSE can access it like that, but I can. If you go to my IP it will not work, and my IP:4829 it will not work. 

I went into ubuntu manuals and found out there is a baisc port blocking firewall, so I disabled it, still didn't work. I enabled it and added the rule allow all to 4829. Still didn';t work. Using canyouseeme.org, it can't see me. Usually i get the message "No route to host" or "Connection timed out". Currently it is the former. 

What am I doing wrong? Did I edit the wrong file? Do I need to set something else up? Thank you for any help!!

you cant go to your external address from inside due to loopback

from outside (a friend or on your phone or something) go to your public IP address and as long as port 80 is forwarded to your LAN IP it should work

peace

---

### Post by Lucypie on 2012-04-14
He cannot. Plus the canyouseeme.org is saying it has no route to host. We have both tested and tried and cannot figure this out.

---

### Post by haqking on 2012-04-14
> **Lucypie said:**
> He cannot. Plus the canyouseeme.org is saying it has no route to host. We have both tested and tried and cannot figure this out.

well what IP are you trying to go to from outside ?

dont post it on here

but i mean your public IP right and not your 192.x.x.x address

your router port forward needs to forward port 80 to your LAN IP hosting the server

no point forwarding port 4289 if your web server is not running on that port

---

### Post by Lucypie on 2012-04-14
It IS running on that port. I set it to that port. So yes, my server is on that port, the port is open, and still, nobody can access the public IP, even if it is IP:4829.

---

### Post by agillator on 2012-04-14
I don't know about port forwarding on your specific router, so will give some general thoughts. 

First, it will be easier to use a dynamic dns domain for the external ip address. One was suggested above, I use dyndns. There are others that are also free. I suggest you sign up with one of them. Your router should have a setting someplace you can have it automatically update the dynamic dns when your address changes.

Second, what port is your server listening to? Assuming port 80, you want to forward the port from your external address (4829, I believe you said) to port 80 on your server, which needs a static ip, of course. It sounds like that static ip has been taken care of. 

Third, check for firewalls on your router and on your server. Be sure the server allows port 80 (or whatever it is supposed to be listening to). Be sure the router will permit the external port (4829).

I assume you see what you should see if you go to localhost in you browser.

Let us know about these things and if the problem isn't solved, we'll dig a little deeper.

---

### Post by lisati on 2012-04-14
A couple of thoughts:

**On the public side**
Some routers have an option for automatically updating your IP address at your domain name provider's end. From memory, mine can cater for no-ip, dyndns and a couple of others, which helps avoid the need to either install a client on your server to do this for you or pay your ISP extra for a static IP address. 

**On your network**
As someone else mentioned, you'll need to look into port forwarding on your router.

For setting up a static IP address on your own network, there are a couple of options you can choose. My preference is to use address reservation on my router. Other people prefer to tinker with their networking configuration on their computer to request a set IP address.

---

### Post by Lucypie on 2012-04-14
I'm sorry, I didn't understand most of that LOL, I'm so much of a newbie with terms. Anyways-- let me address what I kind of understood.

-- I tried no-ip. I don't understand how it works. the hostname is lucypie.no-ip.org but I still don't know how to work it. i installed the no-ip client for linux

--port 4829 is set in the httpd.conf in lampp (Is that the right place to set it?? ) and is forwarded in my router settings. 

typing localhost no longer works. it I type 192.168.1.4:4829 it works.

---

### Post by d3v1150m471c on 2012-04-14
```

define networking

also:
    lo == local loopback, 127.0.0.0/8

if you're hosting services on lo then likely no clients can reach to such.

```

---

### Post by Lucypie on 2012-04-14
I don't know if its loopback or not. Its WLAN0 but it may be loopback. I don't know.... how do I find out and how can I fix it to where they can get to it?

---

### Post by lisati on 2012-04-14
> **Lucypie said:**
> I'm sorry, I didn't understand most of that LOL, I'm so much of a newbie with terms. Anyways-- let me address what I kind of understood.

-- I tried no-ip. I don't understand how it works. the hostname is lucypie.no-ip.org but I still don't know how to work it. i installed the no-ip client for linux

--port 4829 is set in the httpd.conf in lampp (Is that the right place to set it?? ) and is forwarded in my router settings. 

typing localhost no longer works. it I type 192.168.1.4:4829 it works.

The first thing that needs to happen is that no-ip needs to be able to find your system, using your public IP address, before people can access lucypie.no-ip.org from outside your network. If your ISP has given you a *dynamic* IP address, which is common for home connections, your public IP address could change. You will need to make arrangements for no-ip's record of your IP address to be updated when your public IP address changes. Some routers can do this for you automatically. There is also software available that can be installed on your server to do the update for you.

The second thing that needs to happen is that when a request to see your website comes in from the outside world, it needs to be forwarded to your server. This is called "port forwarding".

---

### Post by d3v1150m471c on 2012-04-14
wlan0 != lo
wlan0 == wireless interface
if your wireless access point is a wireless router then probably
you will need to port forward to your lamp server and bind somewhere
on the ip assigned to you by your router. you can see your ip by using
the ifconfig command.

---

### Post by Lucypie on 2012-04-14
Would you like me to post results of the ifconfig command?

@ lisati - I've installed the automatic update client thing and I've set up the port forward. I don't know why it still won't work. everything is how it is supposed to be.

---

### Post by d3v1150m471c on 2012-04-15
probably not a good idea to post ifconfig output if you don't know if you're revealing your public ip.

---

### Post by Lucypie on 2012-04-15
It doesn't say my public IP. I know my public IP (according to websites like whatsmyip) and it doesn't show that. It shows things like HWaddr with some weird numbers and letter,s and some gateway addresses which I knew...

---

