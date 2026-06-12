---
title: "How can I block my neighbors wireless router signal?"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by crjackson on 2009-07-14
Here's my problem.  I have my home internet filtered by using OpenDNS.com which is great, but my other family members (6 kids) have found that the neighbours router is not secured and they are now connecting to that network and visiting prohibited sites.

Is there a way to block the signal or preventing Ubuntu from connecting? I don't want to disable all roaming because these laptops are used at school (which serves only filtered content) and I'm not concerned about other hotspots.  It's just 2 specific signals I want to prevent them from connecting to.

I thought about going to the neighbour and asking him to secure his signal, but we don't really get along that well, and it's embarrassing to tell him I have porn hounds in the house. 

Please help...

Also, is there a way to block craigslist personals, without blocking the rest of craigslist?

---

### Post by fballem on 2009-07-14
> **crjackson said:**
> Here's my problem.  I have my home internet filtered by using OpenDNS.com which is great, but my other family members (6 kids) have found that the neighbours router is not secured and they are now connecting to that network and visiting prohibited sites.

Is there a way to block the signal or preventing Ubuntu from connecting? I don't want to disable all roaming because these laptops are used at school (which serves only filtered content) and I'm not concerned about other hotspots.  It's just 2 specific signals I want to prevent them from connecting to.

I thought about going to the neighbour and asking him to secure his signal, but we don't really get along that well, and it's embarrassing to tell him I have porn hounds in the house. 

Please help...

Also, is there a way to block craigslist personals, without blocking the rest of craigslist?

Your neighbour will have to secure the wireless router.

The best way is to research how to do MAC filtering on that brand of router. He, or she, will also need to know how to get the MAC addresses for the computers in their house (so that these can be setup on the filter).

Depending on the ages of your children, you may want to approach it as asking, nicely, if they would mind and that if they would like your help, then of course you will.

If your children are older, then you might want to suggest that by using MAC filtering to restrict access, this will prevent his neighbours from accessing the router and slowing down the internet for their computers.

The other option would be to put net nanny software on the kids computers, but that raises it own issues, including the fact that the kids can, and will, find ways around it.

I'm sorry, I can't help with the craigslist question.

Hope this helps,

---

### Post by crjackson on 2009-07-14
> **fballem said:**
> Your neighbour will have to secure the wireless router.

The best way is to research how to do MAC filtering on that brand of router. He, or she, will also need to know how to get the MAC addresses for the computers in their house (so that these can be setup on the filter).

Depending on the ages of your children, you may want to approach it as asking, nicely, if they would mind and that if they would like your help, then of course you will.

If your children are older, then you might want to suggest that by using MAC filtering to restrict access, this will prevent his neighbours from accessing the router and slowing down the internet for their computers.

The other option would be to put net nanny software on the kids computers, but that raises it own issues, including the fact that the kids can, and will, find ways around it.

I'm sorry, I can't help with the craigslist question.

Hope this helps,

That's too bad.  You would think that there would be a method of telling Ubuntu to refuse a specific connection.  It seems like I should just be able to tag the connection and tell Ubuntu to reject it.

I wasn't aware Net Nanny could be used with Ubuntu.

Thanks for the reply.

---

### Post by Chemical Imbalance on 2009-07-14
> **crjackson said:**
> That's too bad.  You would think that there would be a method of telling Ubuntu to refuse a specific connection.  It seems like I should just be able to tag the connection and tell Ubuntu to reject it.

I wasn't aware Net Nanny could be used with Ubuntu.

Thanks for the reply.

Here's another Net Nanny-like program:

[http://dansguardian.org/](http://dansguardian.org/)

---

### Post by fballem on 2009-07-15
> **crjackson said:**
> That's too bad.  You would think that there would be a method of telling Ubuntu to refuse a specific connection.  It seems like I should just be able to tag the connection and tell Ubuntu to reject it.

I wasn't aware Net Nanny could be used with Ubuntu.

Thanks for the reply.

Sorry - I wasn't referring to Net Nanny, the _specific program_ but rather Net Nanny the _type_ of program. As Chemical Imbalance pointed out, "Dan's Guardian" is the Linux equivalent. I have never used it, so I will leave it for others to comment.

---

### Post by lisati on 2009-07-15
In our house, where we don't actually have children but occasionally have nieces and nephews over, we have our internet-capable computer gear in the main living area. This way, if they want internet access, we can be aware of what sites they are visiting, and say "no" if we have to.

---

### Post by t0mppa on 2009-07-15
Well, if you don't get along with your neighbour, you could always just thank him for keeping an open wireless access point, so that you don't have to pay for your own Internet connection and can just leach on his instead. That should annoy him enough to secure his access point.

Unless of course there's a law against connecting to other peoples wireless networks without a permission (like around here), in which case you can just persuade your kids to agree that paying fines and dealing with cops is not worth it just to view porn.

> **fballem said:**
> Your neighbour will have to secure the wireless router.

The best way is to research how to do MAC filtering on that brand of router.

Wrong. Firstly, MAC addresses can be changed and thus MAC filtering broken. Secondly keeping the list up-to-date when new hardware is introduced (whether it's yours or a friends who just dropped by) is a bit annoying. And thirdly it only denies access to others, but they can still catch all the traffic between you and the access point and record any important information.

The second best way is to enable WPA/WPA2 and thus deny access to everyone who doesn't know the password (or better yet, passphrase) and also as a byproduct encrypt all traffic, so anyone trying to listen to it can't make any sense out of it.

And the best way is to just tone down the transmission strength of the access point, so no one outside your appartment can catch it and thus you can simply control access to it by deciding who you let in from the door with a computer.

---

### Post by lisati on 2009-07-15
I concur with t0mppa that using MAC filtering on its own is inadequate: it might help keep out (or at least slow down) casual attempts to connect but won't stop the determined cracker. I also concur that using something in the nature of WPA/WPA2 as well would be a good idea. Forget WEP though unless you really have to, its easier to break into than the WPA family of methods, and WPA is stronger.

---

### Post by automaton26 on 2009-07-15
If you really can't stop your kids doing that, I'd strongly suggest putting an anonymous card in their mailbox, telling them to secure their router with WPA/WPA2 asap.

I don't know about the US, but in the UK:

[LIST]
[*]Every ISP has to record each URL that you visit, for the previous 12 months, and the government has access to that (this also means the new "Privacy mode" in Firefox 3.5 still does not make your surfing anonymous).

[*]Having illegal images/videos in your browser cache is your responsibility. "Accidentally" surfing to a dodgy website is no excuse.

[*]Using another person's wireless is illegal.
[/LIST]

So, the government can easily locate you and prosecute you whenever they feel like it.

---

### Post by indigest on 2009-07-15
Try logging into your neighbor's router configuration page.  If he hasn't secured it, chances are he hasn't changed the default password either.  You can find a list of default passwords once you know which brand of router it is.  Once you can configure his router, set up MAC filtering to prevent your machines from connecting.

---

### Post by jerome1232 on 2009-07-15
Can I jokingly suggest that you secure it for them? Nah... that would be mean, and they'd end up calling their broadband company who will just have them reset the router to factory settings and undo the security.:rolleyes:

---

### Post by mobilediesel on 2009-07-15
I forced someone I didn't know to secure their wireless router by:
[LIST=1]
[*]Logging in with the default password
[*]changing the password to the longest string of random characters it would let me type
[*]Changing the ESSID to a space character
[*]turning off the wireless part of the router
[*]rebooting the router
[/LIST]
When the router showed up in the list of possible wireless connections again, it was quite secure.

---

### Post by MartyBuntu on 2009-07-15
Tampering with someone else's router, even if they're not smart enough to secure it is unethical.

I agree with the "note in the mailbox" idea. That's a good first start.

---

### Post by mobilediesel on 2009-07-15
> **MartyBuntu said:**
> Tampering with someone else's router, even if they're not smart enough to secure it is unethical.

I agree with the "note in the mailbox" idea. That's a good first start.

It's exactly the same as seeing someone's car unlocked and opening the door to lock it for them. It may be a gray area but the owner of the property is better off having someone honest notice that it was unlocked first.

---

### Post by fiendishfish on 2009-07-15
> **mobilediesel said:**
> It's exactly the same as seeing someone's car unlocked and opening the door to lock it for them. It may be a gray area but the owner of the property is better off having someone honest notice that it was unlocked first.

I would somewhat disagree, as with a car, it's as simple as putting a key in. However, if they don't know much about routers (and the ability to reset) it would be akin to having to smash the car window, to get back in your car, as some idiot has locked your keys IN THERE.

PS - Nice analogy though, but it has been debunked

---

### Post by mobilediesel on 2009-07-15
> **fiendishfish said:**
> I would somewhat disagree, as with a car, it's as simple as putting a key in. However, if they don't know much about routers (and the ability to reset) it would be akin to having to smash the car window, to get back in your car, as some idiot has locked your keys IN THERE.

PS - Nice analogy though, but it has been debunked

Even with limited knowledge of the router they wouldn't have to damage it to regain access. They might damage it out of frustration if they didn't know much about the technology.

..and the one who left the keys in the car is the idiot just like the one who left the default password on the router.

---

### Post by lisati on 2009-07-15
> **mobilediesel said:**
> 

..and the one who left the keys in the car is the idiot just like the one who left the default password on the router.

LOL!!!! 

Sometimes I see a security firm who tend to ATMs parked in a taxi stand at one of my local supermarkets, presumably to tend to an in-store ATM. I wonder how well it would go down if I hopped in their truck, pointed to the signs identifying it as a taxi stand, and ask how much they charge for their taxi service.

---

### Post by martinbaselier on 2009-07-15
I personally don't see the problem with porn, but I presume you are American. My experience is, that the more "forbidden" something is for a child, the more interesting it becomes. It was so for me :)

But about the problem. You don't want to ask your neighbors. The easiest way to solve it then, would be to log in the router, check the used mac adresses. (most routers show those), turn on mac filtering and fill in the used mac addresses. 

You could call it unethical to temper with their routers, but you'll only be putting some extra security on it. Only if they have someone visiting with a laptop, it can't go on-line.

This will not prevent your kids from seeing porn though. They could still use internet proxies, or just visit a friend with a less secured network.

---

### Post by megamania on 2009-07-15
Since you say you don't get along with your neighbours, I'd use this occasion to cool things down a bit: go to their house, say hi and explain that you "realized that their router is not secure" and offer them to secure it for them.

Your relationship will improve and your problem will be solved.

---

### Post by iponeverything on 2009-07-15
I would go the route of just logging into the AP and setting up WPA changing the and the login password. 

If and when he figures out how to fix it, he may decide to secure it himself. 

Unethical - I don't think so, I would be more concerned with the legal side. The laws about "unauthorized access" are stupidly vague and the people enforcing them are generally clueless about technology. 

That said, if you and your neighbour are not on good terms, I would just shrug my shoulders if he came by to ask about it.

---

### Post by martinbaselier on 2009-07-15
@iponeverything.
Let's translate your example to a real world equivalent.
Suppose you have a very cheap lock on your house, which I can open with a clothes hanger (I used to live in a house with a lock like that)
Suppose you go on holiday for two weeks and I decide to change your lock, for a safer one and put the keys for your new lock on your kitchen table.
While I'm at it, I notice the lock on your back door is just as weak and I decide to change it too and leave keys for it. 

Would you thank me for making your house safer?

---

### Post by mobilediesel on 2009-07-15
> **martinbaselier said:**
> @iponeverything.
Let's translate your example to a real world equivalent.
Suppose you have a very cheap lock on your house, which I can open with a clothes hanger (I used to live in a house with a lock like that)
Suppose you go on holiday for two weeks and I decide to change your lock, for a safer one and put the keys for your new lock on your kitchen table.
While I'm at it, I notice the lock on your back door is just as weak and I decide to change it too and leave keys for it. 

Would you thank me for making your house safer?

That's not quite equivalent. The factory default password is not like a cheap lock, it is like having no lock at all since the default passwords for most routers are widely available even to non-hackers.

---

### Post by lswb on 2009-07-15
I can't tell you the exact syntax, or if it can be done via ufw, but iptables can be configured to block a MAC address. Google for something like "linux firewall iptables block MAC address" and you should find out how to block your neighbor's router.

---

### Post by martinbaselier on 2009-07-15
> **mobilediesel said:**
> That's not quite equivalent. The factory default password is not like a cheap lock, it is like having no lock at all since the default passwords for most routers are widely available even to non-hackers.

Mine could be opened by sticking a clothes hanger through the letterbox in the door and lifting the handle. I must say it's quite easy If you've forgotten your keys and your neighbors have a bent hanger readily available for it. But the method was also publicly available (the whole neighborhood knew about it.) It's just like having no lock at all. 

About the mac-filtering:

[http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html](http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html)

Has good instruction on how to do it.

---

### Post by calrogman on 2009-07-15
You are all over-complicating things, just set the preferred DNS servers on the computer, not the router.

Use /etc/resolv.conf and use the following syntax.

```
nameserver xxx.xxx.xxx.xxx
```

A sample for someone using OpenDNS would be:

nameserver 208.67.222.222
nameserver 208.67.220.220

If your /etc/resolv.conf is overwritten every time a connection is made then place:

prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;

in /etc/dhcp3/dhclient.conf

---

### Post by RD1 on 2009-07-15
Have you considered disciplining your children?

The only sure way of denying access to restricted websites is to take away the computers!

---

### Post by martinbaselier on 2009-07-15
@calrogman
You just provided the perfect solution for his kids, to avoid the router blocking certain websites (unless he blocks them on ip-level, which would be more secure.) That is however the opposite of what he wants. 

@RD1
> 
The only sure way of denying access to restricted websites is to take away the computers! 

You forget there are still other computers they could use. (libraries,friends internet cafés) There also are magazines and DVD's.

---

### Post by Grenage on 2009-07-15
There are things you can do, but each presents it's own set of problems.  The wifi point is most likely using a standard network address (192.168.1.0 or 192.168.0.0), so blocking that port will stop connections at most other access points.

Setting the DNS on on machines can give you similar problems to a lesser extent (I'd consider this option 2).

Your best bet really is to have a word with your neighbor and explain the situation.  As illegal as it is to use someone else's access point, it's probably also illegal to provide minors with inappropriate content.  You can hard-ball them with that if you get issues.


Edit:  Regarding 'Ethical Hacking'; it's not ok to go around securing people's connections for them.  Yes most of us have tried to do the right thing when we were younger, I used to love sending messages to people's printers, telling them how to secure their access point.  Either the ethical lines get thicker as you get older, or I was simply a punk (probably the latter); buttom line, you shouldn't 'break' into people's networks just to prove that they are insecure, any more than you should wander around people's houses when they don't lock the door.

---

### Post by martinbaselier on 2009-07-15
This whole discussion is quite entertaining, but lswb has already provided the solution, And exactly like the the person starting this thread had in mind.

---

### Post by calrogman on 2009-07-15
> **martinbaselier said:**
> @calrogman
You just provided the perfect solution for his kids, to avoid the router blocking certain websites (unless he blocks them on ip-level, which would be more secure.) That is however the opposite of what he wants. 

And who says his kids will ever read this?

A quick fix for this is not giving kids root access.

---

### Post by fballem on 2009-07-15
> **lisati said:**
> I concur with t0mppa that using MAC filtering on its own is inadequate: it might help keep out (or at least slow down) casual attempts to connect but won't stop the determined cracker. I also concur that using something in the nature of WPA/WPA2 as well would be a good idea. Forget WEP though unless you really have to, its easier to break into than the WPA family of methods, and WPA is stronger.

Agreed with both posters. On my router, I use both MAC and WEP. The MAC is used for all computers - wired and wireless connection. Only those computers that are recognised by the router can access the internet.

The WEP encrypts the transmission between computer and wireless on the router. As a side benefit, you can't use the router if you don't know the key.

I also agree with the posters who said that doing the security for your neighbour without their consent is unethical, and probably illegal.

It sounds like you will need to have a chat with your neighbour. Explain the situation as you have explained it to us - and add the fact that others can freeload on his connection. If he agrees to secure his router, then offer any assistance that you can - whether it is to help him set up the security or to test it - using one of the wireless computers in your house. Who knows, it might help thaw relations with your neighbour. Approaching it with a sense of humour might help.

If you feel that one or both of you are 'losing it', or the conversation is going nowhere, walk away. In that case, you'll either need to restrict the kids' computer use to public areas of your home, where you can see what's going on, or try some of the other solutions - including dns addressing that have been suggested.

Hope this helps,

---

### Post by martinbaselier on 2009-07-15
@calrogman

I just saw, I made a mistake. Implementing opendns on the laptops would be a good way to have the same security everywhere. I didn't read the first post well enough. I usually only use openDNS as a backup for my provider's DNS, so I did not know it could be used for content filtering.

So there are 2 solutions for the problem. Setup openDNS locally or use iptables to block the computer from using your neighbor's networks. 

There is however a problem with the local setup. Since openDNS uses your ip to know your account, you would have to set it up using dynamic ip's, meaning the local computer will need a daemon to tell openDNS its current ip. This way the computer will always have the same security, no matter where it's used. This also means a separate account for each computer. 

They might still offer the option of multiple dynamic ip's, which would be a better solution. For that you'd best contact openDNS. 

So, using iptables still is the easiest solution. 

By the way; There are still quite a few holes in this setup:
ip's are not blocked. If they know the ip of the forbidden site, it can be accessed directly. 
You would need to block webproxies too.
The settings can still be changed, either by choosing the rootprompt while booting or by booting from a live cd. Both give you root access to the system.

---

### Post by aesis05401 on 2009-07-15
> **Grenage said:**
> *snip* ...Edit:  Regarding 'Ethical Hacking'; it's not ok to go around securing people's connections for them.  Yes most of us have tried to do the right thing when we were younger, I used to love sending messages to people's printers, telling them how to secure their access point.  Either the ethical lines get thicker as you get older, or I was simply a punk (probably the latter); buttom line, you shouldn't 'break' into people's networks just to prove that they are insecure, any more than you should wander around people's houses when they don't lock the door.

People are not recommending hacking of any sort.  

Using common knowledge to login to an unsecured access point to secure it is simple vigilantism.  

Discovering the vuln in a presumed secure system is hacking.  
Exploiting a vuln is a crime.
Logging into the neighbor's access point without permission is just a lot of potential consequences for no real gain.

---

### Post by iponeverything on 2009-07-15
> **martinbaselier said:**
> @iponeverything.
Let's translate your example to a real world equivalent.
Suppose you have a very cheap lock on your house, which I can open with a clothes hanger (I used to live in a house with a lock like that)
Suppose you go on holiday for two weeks and I decide to change your lock, for a safer one and put the keys for your new lock on your kitchen table.
While I'm at it, I notice the lock on your back door is just as weak and I decide to change it too and leave keys for it. 

Would you thank me for making your house safer?

The goal is not help him secure his network, but to stop the kids from easyly circumventing their parents wishes.

If you "fixed" my locks while I was on vacation to stop the neighbourhood kids from using it as place to drink, because they are not allowed to drink at home. I might actually thank you.

---

### Post by crjackson on 2009-07-16
> **calrogman said:**
> You are all over-complicating things, just set the preferred DNS servers on the computer, not the router.

Use /etc/resolv.conf and use the following syntax.

```
nameserver xxx.xxx.xxx.xxx
```

A sample for someone using OpenDNS would be:

nameserver 208.67.222.222
nameserver 208.67.220.220

If your /etc/resolv.conf is overwritten every time a connection is made then place:

prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;

in /etc/dhcp3/dhclient.conf

This looks useful.  I'll give it a try...  Thanks...

---

### Post by crjackson on 2009-07-16
> **lswb said:**
> I can't tell you the exact syntax, or if it can be done via ufw, but iptables can be configured to block a MAC address. Google for something like "linux firewall iptables block MAC address" and you should find out how to block your neighbor's router.

Okay, I'll look into this.

---

### Post by crjackson on 2009-07-16
> **martinbaselier said:**
> @calrogman
You just provided the perfect solution for his kids, to avoid the router blocking certain websites (unless he blocks them on ip-level, which would be more secure.) That is however the opposite of what he wants. 

@RD1

You forget there are still other computers they could use. (libraries,friends internet cafés) There also are magazines and DVD's.

I'm not worried about other computers.  If a person is that determined there will always be a way. I just want to secure from the neighbors house. I can't make it impossible, but I would like to make it less than simple/easy in my own hose.

---

### Post by crjackson on 2009-07-16
> **calrogman said:**
> And who says his kids will ever read this?

A quick fix for this is not giving kids root access.

They don't have sudo rights.  They are all restricted users and the last thing I'm worried about is them reading these posts.

---

### Post by chkneater on 2010-09-07
I believe that under administatration or under preferences you can find an option for users and groups, somewhere in there in the hosts tab you can block certain hosts, which would be the name of their essid or whatever their host name shows up as.  They can always change this so you will have to check you network to see if they are accessing it. Hope this helps.

---

### Post by chkneater on 2010-09-07
also you can look for their essid using a a terminal and using these commands : lshw , iwconfig --help and iwlist --help

---

### Post by crjackson on 2010-09-07
> **chkneater said:**
> I believe that under administatration or under preferences you can find an option for users and groups, somewhere in there in the hosts tab you can block certain hosts, which would be the name of their essid or whatever their host name shows up as.  They can always change this so you will have to check you network to see if they are accessing it. Hope this helps.

it's under System>Administration however, I can't find anything pertaining to hosts or host names.  If you can locate it, please tell me the specific location.

---

### Post by Cabalbl4 on 2010-09-07
To disable wireless connection You may use this thread: 
(there is described a way to autoCONNECT to a network, using Dbus and NetworkManager)
[http://ubuntuforums.org/showthread.php?t=800330](http://ubuntuforums.org/showthread.php?t=800330)
create a nmcli script as described there and make it executable.
Then use the final script from my post which auto-enables the connection, and use the name of desired network to disable instead of VPNNAME and stop instead of start.
The network will be auto-disconnetcted in the given ammount of time. 
Here is how script commands work by me:
```
yan@yan-laptop:~$ nmcli
Usage: nmcli connexion_name start|stop
---Available Connections:
Auto eth0
Auto UbuntuAdhoc
Auto Beeline_WiFi_FREE
Auto Beeline_WiFi
Auto TIS
Auto wl11(tel.988-7636)
Auto TDEBC-1-AP
Auto Beeline_WiFi_PREMIUM
Auto LPQ_Free
---Active Connections:
Auto Beeline_WiFi
yan@yan-laptop:~$ nmcli Auto\ Beeline_WiFi stop
active_connection_path=/org/freedesktop/NetworkManager/ActiveConnection/3
method return sender=:1.2 -> dest=:1.350 reply_serial=2

```
And the connection breaks...

---

### Post by whitefort on 2010-09-07
I deleted this post before I started any wars... but some of those proposed 'solutions' are criminal and made me angry!

I'm all calmed down now.  Sorta.

---

### Post by Cabalbl4 on 2010-09-07
Actually, the script to disable the connection using nmcli should look like this: 

```
#!/bin/bash

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli|grep -c WIFI)
# WIFI here is the name of desired connection to monitor. The results can be:
# 0 - this connection does not exist
# 1 - connection exists, but not active
# 2 - connection exists, and is active
case $tested in
"0")
echo "cannot find desired connection in avaliable list"
;;
"1")
echo "conection avaliable, but not connected" 
;;
"2")
echo "connection seems to work, disabling it NOW" 
nmcli WIFI stop
;;
esac
# enter desired time between checks here.
sleep 30 
done
```

then put this script to autorun

---

