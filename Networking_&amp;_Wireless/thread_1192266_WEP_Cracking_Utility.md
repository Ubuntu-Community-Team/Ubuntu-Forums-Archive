---
title: "WEP Cracking Utility"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by vahnx on 2009-06-19
I got my Nintendo DS repaired but unfortunately WPA takes too much power so Nintendo only lets the DS connect to WEP, therefore I must lower my security. I wish to attempt to crack my own network to see how insecure WEP really is as I've only heard about how WEP can be broken into within 5 minutes. I've downloaded aircrack but airsnort is not in the Jaunty respos. Is there a **single** utility that will just crack a WEP connection in Ubuntu? It's been like three years since I last bothered trying to crack WEP but I assume since 3 years passed that someone has developed an all in one by now.

---

### Post by cariboo on 2009-06-20
You may just want to download [Backtrack]("http://www.remote-exploit.org/backtrack_download.html"), it is a live cd, and us it for penetration testing.

---

### Post by kerry_s on 2009-06-20
i just use a hidden essid & mac filtering, that way it doesn't look secure so theres no temptation to want to crack it. ;)

---

### Post by carcar1 on 2009-06-20
Me having recently picked this and picked up on really fast.  You see mac filtering on wep isn't all that great.  If someone really wanted to get on your wireless all they had to do it wait for you to connect and then they have you mac.  then all they have to do is de-auth you like a million times which makes you loose all packets from the router or access point.  And there now your connection is gone.  Then they recorded your mac and will change there mac and ip to your info.  And then they do the whole airodump-ng and aireplay-ng stuff and aircrack and packetforge etc etc.  Then they can have you password and locked you out of your own house basically. I would know I have done this for test purposes many many times.  And longer password on wep don't matter.  Its all about how your router takes the arp packets and hwo0 fast.  If the attacker can manage 40,000 stolen then he has your password.

And backtrack still see's your not broadcasting essid. 

And the best wep cracker program is airecrack-ng suite works wonders :)

---

### Post by kerry_s on 2009-06-20
thats what i'm saying the thrill is in the crack right? if theres nothing to crack would you still mess with it? most i know just don't bother with the unsecured connections because they want to work at it. :lolflag:

---

### Post by carcar1 on 2009-06-20
Yep, the more the thrill the more fun we have :)  I cracked 2 weps yesterday each in under 10 minutes.  Wished they had some mac filtering for me to mess with.  Then for the fun of it de-authed somebody that was probably surfing the web and they lost connection:lolflag:


All for testing purposes was in a controlled environment.

---

### Post by munky99999 on 2009-06-20
> I got my Nintendo DS repaired but unfortunately WPA takes too much power so Nintendo only lets the DS connect to WEP, therefore I must lower my security. I wish to attempt to crack my own network to see how insecure WEP really is as I've only heard about how WEP can be broken into within 5 minutes.
wow I had to grab my DS to check that out. How sad is that.

> I've downloaded aircrack but airsnort is not in the Jaunty respos. Is there a single utility that will just crack a WEP connection in Ubuntu? It's been like three years since I last bothered trying to crack WEP but I assume since 3 years passed that someone has developed an all in one by now.
The aircrack suite in the repos is enough.

> i just use a hidden essid & mac filtering, that way it doesn't look secure so theres no temptation to want to crack it. 
Dont even use hidden broadcasting. That's never a default feature and thusly if that's being used the person has some reason for security. So hidden means it's time for cracking.

Open, not hidden, with mac filtering. Is probably the most secure unless you can do wpa with a strong password.

---

### Post by Phil Urich on 2009-06-22
> **kerry_s said:**
> i just use a hidden essid & mac filtering, that way it doesn't look secure so theres no temptation to want to crack it. ;)

Uhhhh that would show up just fine in Kismet, and I hope you have SOME encryption on it otherwise people can just capture all your internet traffic right out of the air!  However if you're just discouraging random Windows/OSX-using folks who don't pay for their own internet and want to crib someone else's, then actually that's a pretty effective way :)  I guess it depends on what you're using it for; mac filtering is broken as soon as someone's paying attention at the same time as you're on though, heh.

> **vahnx said:**
> Is there a **single** utility that will just crack a WEP connection in Ubuntu? It's been like three years since I last bothered trying to crack WEP but I assume since 3 years passed that someone has developed an all in one by now.

 Yeah; if you want just one single program that can attempt to crack a WEP-encrypted network, the lazy way is to use SpoonWEP.  It automates almost all of it for you.  I can tell you right off the bat though that WEP, no matter how complex the password is, can be broken in a heartbeat as long as you're putting out enough traffic.  So if you torrent something (like a new Ubuntu .iso, of course) and your neighbor is running Kismet or airodump-ng or whatever, I can tell you from experience that it can take as little as a few minutes!  And at very least, the Long Hack will always work against WEP (ie. just setting up a sniffer and slowly over time getting enough packets, since it's all just about getting 5,000-20,000 packets and laughing at the power of statistics.  Of course, you *could* respond to this by continuously changing your WEP key, which would especially screw up anyone if they had data from multiple different WEP keys.  

A better option might be to get a spare wifi card that Linux can tell to be an AP (they definitely exist, just gotta get the right chipset) and do some connection sharing from another computer on your network.

When it comes down to it, though, if you're actually worried about real security then there's no actual way to use WEP.  The security of WEP plateaus pretty quickly (just use the maximum number of characters/hexidecimals...that's it) and even the most secure WEP network can be cracked trivially, especially if one is using packet injection.

---

### Post by Phil Urich on 2009-06-22
> **munky99999 said:**
> Open, not hidden, with mac filtering. Is probably the most secure unless you can do wpa with a strong password.

I really would disagree.  As long as you can "hear" a packet meant for a wireless client, bam, you can then just fake that MAC address and connect to the access point.  I know myself whenever I see an unencrypted access point that for some reason I can't connect to the first thing I think is "aha! Mac filtering!" and I sniff for a minute (or a moment) until I see a client.  The other thing is, if it isn't encrypted, then even without bother to do anything else you can just overhear all the  traffic (mac filtering only prevents someone from authenticating with the AP).  So if by a bad coincidence a plaintext password or other sensitive data of yours is being transferred over your wireless . . .

---

### Post by kerry_s on 2009-06-22
it just can't be helped, there will always be people out there who just spends days cracking & the harder it is the more they will try.

i'm just not 1 of those people. ;)

---

### Post by lisati on 2009-06-22
I've only ever noticed WPA and WPA2 networks nearby, and they're not on 24/7. Since I have a connection I've paid for myself, I don't see any point (other than maybe the fun of checking my own connections)

---

### Post by kerry_s on 2009-06-22
> **lisati said:**
> I've only ever noticed WPA and WPA2 networks nearby, and they're not on 24/7. Since I have a connection I've paid for myself, I don't see any point (other than maybe the fun of checking my own connections)

a lot of people are hardly ever at home & they may wish to get on the Internet now & then, with most people made paranoid by ms, there are places where every 1's encrypted in some way. so if you most, knowing how to is not a bad thing. just because you know how, does not mean you have to, unless your left with no choice & you just got to get your Internet fix.

in the end it's just another thing you learn. using what you learned, you never know.

---

### Post by lisati on 2009-06-22
> **kerry_s said:**
> a lot of people are hardly ever at home & they may wish to get on the Internet now & then, with most people made paranoid by ms, there are places where every 1's encrypted in some way. so if you most, knowing how to is not a bad thing. just because you know how, does not mean you have to, unless your left with no choice & you just got to get your Internet fix.

in the end it's just another thing you learn. using what you learned, you never know.

As long as it's fun, potentially useful (learning something can be a good thing), and **legal**....... 
With my new cellphone I can get online with my laptop (shame Jaunty doesn't list my mobile carrier, but there's workarounds), and there's a handful of hotspots I can use legally downtown without the need to leech off someone else's connection without their permission.

---

### Post by kerry_s on 2009-06-22
> **lisati said:**
> As long as it's fun, potentially useful (learning something can be a good thing), and **legal**....... 
With my new cellphone I can get online with my laptop (shame Jaunty doesn't list my mobile carrier, but there's workarounds), and there's a handful of hotspots I can use legally downtown without the need to leech off someone else's connection without their permission.

very true, times have changed. there was a time where home was where ever i got tired, i use to have this old omnibook(i think can't remember the brand/model) that i used to keep in touch with family, i remember it use to be hard finding wifi spots, now a days there everywhere. i think its way easier to find a open connection now a days.

---

