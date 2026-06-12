---
title: "Some one attempts to hack my wifi"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-06
I just check the router log and notice

```
Saturday March 07, 2009 02:09:57 Unallowed access from WLAN xx-xx-xx-xx-xx-xx
Saturday March 07, 2009 02:09:57 Unallowed access from WLAN xx-xx-xx-xx-xx-xx
Saturday March 07, 2009 02:10:13 Unallowed access from WLAN xx-xx-xx-xx-xx-xx
Saturday March 07, 2009 02:10:13 Unallowed access from WLAN xx-xx-xx-xx-xx-xx

```

My log is full of this annoying message. That guy attempts to connect every few seconds. He may have done this for hours. I think it's my mac filter blocking him. 
The encryption is WPA-AES with a 63 random characters password.  Will he be able to break it and does it affect my connection speed?

---

### Post by chriskin on 2009-03-06
if you have a mac filter, wouldn't it stop anyone not connecting from your computer?
and your password seems strong enough , i think he will fail


yet a rule says, that if he wants it badly enough, and know enough , he will make it. if he does, just change the password and he will have to spend even more time to obtain the new one, he will get bored, and try hacking into another connection around

or try making the connection hidden, one might not be able to see a hidden connection without its name, he might think you changed to wired

---

### Post by afeasfaerw23231233 on 2009-03-06
Thanks for your reply. I read somewhere in this forum that MAC address filter and hiddent ssid are quite useless to an experience cracker. Only a strong WAP password is the way to go except the cracker has great computation power. But that's a bit annoying seeing him attempting to connect every four second. 
Err.. I just check the log again and he now is using two MAC adrresses (two wireless lan cards?) to do the attack. It's 2.30am here and he still has his box on to do the cracking job?

---

### Post by chriskin on 2009-03-06
he seems determined :P

(yes i know they are kind of weak methods, but we do not know how experienced he is right? for all we know, he could be just using some app and a tutorial he found online :S)

if he fails all the time, let him fail, he will get bored soon enough

i do know it for sure, but isn't there a way to block his mac addresses?

---

### Post by afeasfaerw23231233 on 2009-03-06
Yes, I have already applied MAC filter. And I think it's the MAC filter blocking him from access. But from what I read in other threads MAC filtering is no use against a determined hacker.
 AHAHA, he stopped 10 minutes ago. I think he went to sleep. See if he will come again tmr.

---

### Post by chriskin on 2009-03-06
i meant making it automatically to fail AND not write anything about it in the logs
if he is meant to fail all the time, why should your log get messy?

hope he stopped for good :P

---

### Post by Iowan on 2009-03-06
There are ways to spoof a MAC address - so it is not bulletproof insurance. I've never used it, but read that fail2ban might help (It's in the repo's).

---

### Post by kevdog on 2009-03-06
Im no hacker, however done some experimenting with aircrack-ng.  If you use a wireless monitoring service such as kismet, you are easily able to see the wireless networks nearby, the clients connected to the various access points, and the MAC addresses of the various clients.  Although a MAC filter does filter out extraneous MAC addresses, aircrack makes it possible to spoof one of the clients MAC addresses, actually boot the client from the router, and then have the attacker connect to the AP using the booted MAC address of the former client.  That is how a MAC filter is circumvented.  

Lastly I would like to challenge the assumptions that MAC filters can be broken by only experienced hackers.  Within several hours of reading the aircrack wiki and trying some of the various attacks available with this software -- I suppose you would then consider this person to be an experienced hacker!  My point is that it doesn't take a lot of work or effort to circumvent a MAC filter.  It does pose an additional obstacle that one needs to work around, but its not fool proof.

---

### Post by eldragon on 2009-03-06
you could always let him get it, set a dhcp server on your linux box, and a transparent proxy, then make all images in webpages he visits come from goatse or inverted / blurred using imagemagik :D that'll teach him
you could even log passwords if hes dumb enough and steal his accounts. that will teach him too

---

### Post by tuskenraider on 2009-03-06
since he stopped... make your wireless network hidden..and rename it...  

badabing.. he 1 cant see it..  and 2 doesnt know the name.. 

so if he still tries to connect to your wireless network.. he will be trying to connect to the OLD ssid name. 

no fancy antihackery needed. 


tusken 

when in doubt the simplest fix is usually the best. <--- not a direct quote. lol

---

### Post by kevdog on 2009-03-07
> **tuskenraider said:**
> since he stopped... make your wireless network hidden..and rename it...  

badabing.. he 1 cant see it..  and 2 doesnt know the name.. 

so if he still tries to connect to your wireless network.. he will be trying to connect to the OLD ssid name. 

no fancy antihackery needed. 


tusken 

when in doubt the simplest fix is usually the best. <--- not a direct quote. lol

Kismet??

---

### Post by wannadumpwindows on 2009-03-07
> **kevdog said:**
> Kismet??

Exactly. It sees hidden SSID's without any trouble.

I've tried various ways of securing my own wifi, I had a couple problems a while back.

Hidden SSID's and MAC filtering are basically useless against anyone willing to use google and read a few paragraphs.

Heck, there's even programs in the repo's and a script or two floating around out there that can automate the whole process so all you have to do is hit a couple keys, and it does the rest for you.

The ONLY thing to keep someone off your network is your password. Make it long, strong and random. Mix letters, numbers and puntuation. Don't use ANY words either.

---

### Post by kevdog on 2009-03-07
Yes, the only words of advice I can give currently is to use WPA2 with a very long random password.  MAC filters, hidden SSIDs provide obstacles to those less determined.

---

### Post by eldragon on 2009-03-07
i still vote my option... even if they can get into the network, you could even set their ips to a local webpage telling them their computer is being hacked or something, scaring the hell out of them.. and in the meantime, scan for shared printers / folders and well, do your magic :D its probably a script kiddie

---

### Post by wannadumpwindows on 2009-03-07
Static I.P.'s help a bit too. They easily confuse the average joe. 

Most people have no clue what one even is, let alone how to configure their wifi card to connect with one.

Obviously, the determined cracker isn't even going to notice. But it's one more thing to muck up the works.

---

### Post by wannadumpwindows on 2009-03-07
> **eldragon said:**
> i still vote my option... even if they can get into the network, you could even set their ips to a local webpage telling them their computer is being hacked or something, scaring the hell out of them.. and in the meantime, scan for shared printers / folders and well, do your magic :D its probably a script kiddie

The problem with your option, is that it's against forum policy, and probably better judgement, to suggest these sorts of things.

EDIT: The only reason I know this, is because I started almost the exact same thread about a year ago.

And here's the link: [http://ubuntuforums.org/showthread.php?t=744817]("http://ubuntuforums.org/showthread.php?t=744817")

---

### Post by eldragon on 2009-03-07
> **wannadumpwindows said:**
> The problem with your option, is that it's against forum policy, and probably better judgement, to suggest these sorts of things.

EDIT: The only reason I know this, is because I started almost the exact same thread about a year ago.

And here's the link: [http://ubuntuforums.org/showthread.php?t=744817]("http://ubuntuforums.org/showthread.php?t=744817")

ive read your thread, still i dont see how im breaking the rules...just suggesting someone modify his own LAN in order to teach a lesson?

the best aproach is to let him believe hes won (switch to wep) and teach him a lesson. hell never do it again.

heres something to get you started: [http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

---

### Post by wannadumpwindows on 2009-03-07
> **eldragon said:**
> ive read your thread, still i dont see how im breaking the rules...just suggesting someone modify his own LAN in order to teach a lesson?

the best aproach is to let him believe hes won (switch to wep) and teach him a lesson. hell never do it again.

heres something to get you started: [http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

The changing his own network part is fine. It's his, he can do as he pleases.

However, once you start suggesting he probe the attackers computer for shared resources and files, that's an entirely different thing.

I'm not a mod, it makes no difference to me. I'd probably do the exact same thing.

Just trying to save you the trouble of an infraction.

---

### Post by Steve78 on 2010-04-07
I am a Cisco engineer and I only have one years experience with real wireless networks. Mac filtering IS NOT GOING TO STOP anyone. Mac's can spoofed easily even if you have no networking knowledge , as along as you can read n copy paste cmds n search on google.
Just like anything, man made it man can unmake it (ie reverse engineer).
I test networks all the time and annoys me when people deploy WPA/WPA2 and use a common word. With Bactrack or Ubuntu I can use dictionaries or rainbow tables and find the password quicker than most people think.
THE ONLY WAY STOP HACKERS IS USE A PASSWORD WITH MORE THAN 10 CHARACTERS AND DO NOT USE NORMAL WORD FOUND IN THE DICTIONARY. USE SYMBOLS LETTERS (LOWER & UPPERCASE) AND NUMBERS IN A RANDOM WAY
IE GJ^6Y%8Blp3Hji7yho
Then the hacker will move on to the next wireless network. He will get bored and find other networks much easier to hack.
If you have something to hide ie database with credit card details or other info that could be used to make money or bribe you then it is just a matter of time before a pro can get access to the network. Then you need to chance your password regular as past of your security procedures.

---

### Post by Iowan on 2010-04-07
Thread is over a year old - RIP :)

---

