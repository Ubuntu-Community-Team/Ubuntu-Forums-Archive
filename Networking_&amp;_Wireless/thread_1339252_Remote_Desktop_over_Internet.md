---
title: "Remote Desktop over Internet"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by conradtheart on 2009-11-27
Hi,

I'm trying to connect to a Ubuntu machine from my Ubuntu machine over the internet. Doing this on the local network is a piece of cake, but doing so over the internet is proving to me a problem.

When I go to my remote desktop options it says "Your desktop is only reachable over the local network."

Am I correct in saying as long this says that there is no way of reaching the machine over the internet?

How do I fix this. Does anyone have a tutorial? I've searched and searched, but don't find anything mentioning the above fact.

Thank you.

---

### Post by cj13579 on 2009-11-27
Do you just want to be able to access a terminal or do you want to be able to see the desktop?

---

### Post by cj13579 on 2009-11-27
Maybe I should read the title of your post! To access your desktop from the internet you will need to know your public ip ([http://www.whatsmyip.net](http://www.whatsmyip.net)) and have forwarded port 5900 on your router that the computer is connected to. Then where you would put in a local ip address for the machine that you want to connect to just enter the ip address that you got from the website.

Note: If you have a dynamic local and/or public ip then these will change and you will need to either get a static ip address or monitor it closely!

Hope this helps!

---

### Post by conradtheart on 2009-11-27
Thanks for the reply CJ. 

I do have a router on the work computer, but when I disconnect the ADSL router and use 3G or use 3G on my laptop, I still get the "Your desktop is only reachable over the local network" message. 

Is there a port I need to open on the computers itself aswell?

---

### Post by cj13579 on 2009-11-27
So long as you have got allow users to view/control your desktop checked you shouldn't need to. Have you tried connecting to the machine even though it says that it is only reachable over the local network? I just VNC'd into one of my boxes from work and it said that it was only reachable over the local network even though I was reading the message over the net :confused:!!

---

### Post by conradtheart on 2009-11-27
Yip. I tried it anyway. I tried from ADSL to 3G, from 3G to ADSL and 3G to 3G, but nothing. The only thing that works is ADSL to ADSL because its on the same network.

---

### Post by Nicholas_M on 2009-11-27
> **conradtheart said:**
> Yip. I tried it anyway. I tried from ADSL to 3G, from 3G to ADSL and 3G to 3G, but nothing. The only thing that works is ADSL to ADSL because its on the same network.

It should work with openvpn/global IP.
Like example  networkgate.us provide it.

---

### Post by joshajames on 2009-11-27
Are you running firestarter/ufw or anything similar on the box your trying to access?

---

### Post by conradtheart on 2009-11-27
> **Nicholas_M said:**
> It should work with openvpn/global IP.
Like example  networkgate.us provide it.

A VPN is more like a virtual network right? I don't really want to do that. I just want to remotely access the other machine.

And isn't networkgate more like a file accessing service than a remote access service?

Thanks for the help.

---

### Post by conradtheart on 2009-11-27
> **joshajames said:**
> Are you running firestarter/ufw or anything similar on the box your trying to access?

Unless Ubuntu installs with a firewall by default, no.

---

### Post by joshajames on 2009-11-27
do a iptables -v -L and post it.  This should show if we have any ports blocked.  (on the machine you are accessing)

---

### Post by conradtheart on 2009-11-27
> **joshajames said:**
> do a iptables -v -L and post it.  This should show if we have any ports blocked.  (on the machine you are accessing)

The main machine I'm testing this with is at work, (ultimately want to access my friend's computer like this) but I tried accessing my own computer in the same way with the same problem, so the setup is the same.

This is the output:

```
$ sudo iptables -v -L
[sudo] password for conradtheart: 
Chain INPUT (policy ACCEPT 5134 packets, 2944K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 5257 packets, 800K bytes)
 pkts bytes target     prot opt in     out     source               destination     
```

---

### Post by joshajames on 2009-11-27
Hmmm,  No problems there.

---

### Post by joshajames on 2009-11-27
I'm still thinking this is a connectivity issue.  What settings do you have under System>Pref>Remote Desktop?

---

### Post by Nicholas_M on 2009-11-27
> **conradtheart said:**
> 
And isn't networkgate more like a file accessing service than a remote access service?

Thanks for the help.

It`s just provide you a global IP.
So you can get to your pc from everywhere.

---

### Post by conradtheart on 2009-11-27
> **joshajames said:**
> I'm still thinking this is a connectivity issue.  What settings do you have under System>Pref>Remote Desktop?

[IMG]http://farm3.static.flickr.com/2573/4139186574_88617fa66f_o.png[/IMG]

---

### Post by joshajames on 2009-11-27
Try portscanning your internet IP.  This should show port 5900 as open.

---

### Post by conradtheart on 2009-11-27
> **Nicholas_M said:**
> It`s just provide you a global IP.
So you can get to your pc from everywhere.

Oh you mean like a static IP?

---

### Post by conradtheart on 2009-11-27
> **joshajames said:**
> Try portscanning your internet IP.  This should show port 5900 as open.

Er... Okay, how do I do that?

---

### Post by Nicholas_M on 2009-11-27
> **conradtheart said:**
> Oh you mean like a static IP?

Sure. 
[https://networkgate.us/public/node/10](https://networkgate.us/public/node/10)

---

### Post by conradtheart on 2009-11-28
> **Nicholas_M said:**
> Sure. 
[https://networkgate.us/public/node/10](https://networkgate.us/public/node/10)

Am I correct in saying that is a paid service? Really not looking to pay anyway. I'm using Linux afterall. :-p

---

### Post by Nicholas_M on 2009-11-29
> **conradtheart said:**
> Am I correct in saying that is a paid service? Really not looking to pay anyway. I'm using Linux afterall. :-p

Well, you have to pay for the Internet service, right ?
But most common a service not include a static IP. So, it`s "one-way internet".
It`s up to you, but you have a choice in this case where to buy that convenient stuff if you need it. For me it sound good - you can find it at the lowest price. 

And  for me a static IP is much better than hosting - I can use all my hard drive for web/ftp... I have my own host.

Regards.

---

### Post by zaphod777 on 2009-11-29
don't have to pay just configure dynamic dns it's free if you don't want a custom domain name.

your machine will update the site so the domain you chose (something like home.homelinux.net) will always have your current public ip.

then just put the FQDN(fully qualified domain name) in instead of the ip address.

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

make sure that the port 5900 is forwarded from your router to the machine you want to connect to. also make sure the destination machine has a local static ip so it doesn't change.
test this site from the destination pc and type single port 5900 if the port forward is configured correctly it should come back successful.

[http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by prkos on 2009-11-29
I also have this problem

There was one time when I got it to work, I was adjusting the router to allow port 5900. 

Now when I want to share I always get only local network. 


Edit: Found it!! It's in your router settings.

I'm not sure if it applies to everyone but here is what it looks like for me: 
Toolbox > Game and application sharing

There I found drop downs where I chose VNC and the name of the computer I wanted to share, it automatically got applied. 

I also found that the option in the Remote desktop window "Configure network automatically to accept connections" behaves a bit weird, sometimes you have to tick it and untick several times to get the internet ip instead of the local one (wait while it reloads).

---

### Post by dmizer on 2009-11-29
> **cj13579 said:**
> To access your desktop from the internet you will need to know your public ip ([http://www.whatsmyip.net](http://www.whatsmyip.net)) and have forwarded port 5900 on your router that the computer is connected to.

Never ever do this! The only thing between you and complete access by any hacker is a simple password. Desktop sharing is NOT meant to happen over the unfiltered internet.

Anyone who's made this configuration needs to get the port forwarding disabled ASAP.

Use SSH instead: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

