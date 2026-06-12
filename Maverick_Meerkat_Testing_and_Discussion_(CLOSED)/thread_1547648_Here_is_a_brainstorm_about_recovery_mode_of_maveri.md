---
title: "Here is a brainstorm about recovery mode of maverick"
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-07
[http://brainstorm.ubuntu.com/idea/25542/](http://brainstorm.ubuntu.com/idea/25542/)

---

### Post by ranch hand on 2010-08-07
As folks tried to tell you and as stated in the documentation, the "dpkg fix broken packages" option does have networking.  It yours, in an alpha release, does not work you do not go jogging off to the forum or brainfever, you file a bug report so it can be fixed.

When you use that option, one thing it does is update.upgrade your system, all by itself.

So, to sum up, you have now, once again, without listening to anyone or reading the STICKIES, been very successful at making your self look really silly, here and on braindrizzle.

To top that off, you come back here to brag about it.

<snip>

---

### Post by k3lt01 on 2010-08-07
> **ranch hand said:**
> As folks tried to tell you and as stated in the documentation, the "dpkg fix broken packages" option does have networking.  It yours, in an alpha release, does not work you do not go jogging off to the forum or brainfever, you file a bug report so it can be fixed.

When you use that option, one thing it does is update.upgrade your system, all by itself.

So, to sum up, you have now, once again, without listening to anyone or reading the STICKIES, been very successful at making your self look really silly, here and on braindrizzle.

To top that off, you come back here to brag about it.

I really think you can come up with better way of getting attention than this.  That or seek professional help.My first day with Maverick and RanchHand shows he hasn't lost any of his zing. I forgot how much I loved testing. :p

---

### Post by aviramof on 2010-08-07
> **ranch hand said:**
>  you file a bug report so it can be fixed.

I did posted a bug report.

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/614609](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/614609)

---

### Post by MacUntu on 2010-08-07
@1. You don't necessarily need internet access to fix broken packages. If you do need internet access, then there's an option for it.

@2. Adding a single task to the menu is against the KISS design principle (IMO).

@3. You are using a development... ah, wait, I forgot it's you. :-?

---

### Post by aviramof on 2010-08-07
if lucid for instance have good recovery mode which i don't remember but it might i see no reason to change it in maverick and as i said the current recovery mode didn't helped me too much in the end when i really needed it.

---

### Post by MacUntu on 2010-08-07
> **aviramof said:**
> if lucid for instance have good recovery mode which i don't remember but it might
What?

I just tested recovery mode in Karmic, Lucid, and Maverick Alpha 3: the "dpkg" mode had networking enabled (wired of course) in Karmic, Lucid, and Maverick Alpha 3.

---

### Post by autocrosser on 2010-08-07
> **k3lt01 said:**
> My first day with Maverick and RanchHand shows he hasn't lost any of his zing. I forgot how much I loved testing. :p

WHAT????  You are JUST now getting started???  Tisk--Tisk on you!!!  The last couple of months have been fairly uneventful....I'm still waiting for the breakage  :(

---

### Post by plun on 2010-08-07
> **MacUntu said:**
> What?

I just tested recovery mode in Karmic, Lucid, and Maverick Alpha 3: the "dpkg" mode had networking enabled (wired of course) in Karmic, Lucid, and Maverick Alpha 3.

Yup... works just fine.....;)

But.... maybe its possible to make this recovery more "noob"-friendly, "aviramof" got a point that its more on an "nerd" level....:-$

Wireless connection without messing with commands would be great...;)

---

### Post by k3lt01 on 2010-08-07
> **autocrosser said:**
> WHAT????  You are JUST now getting started???  Tisk--Tisk on you!!!  The last couple of months have been fairly uneventful....I'm still waiting for the breakage  :(Yeah sorry, my bad. Poor health, looking after old parents, and a deciding whether to put my laptop through it all again (Lucid was hard on it cause it's a poverty pack unit) aren't really good excuses at all are they? :p

Truthfully, I'm glad to be back into it.

Oh and guys/gals, we are not in a medieval zoo. I wonder how many will get that? ;)

---

### Post by aviramof on 2010-08-07
> **MacUntu said:**
> What?

I just tested recovery mode in Karmic, Lucid, and Maverick Alpha 3: the "dpkg" mode had networking enabled (wired of course) in Karmic, Lucid, and Maverick Alpha 3.

Too be honest i was also surprised that it didn't worked considering the fact that i am connected via router meaning the router does the dialing not the OS but for some reason
dpkg mode showed me a lot of errors of not being able to connect however the command 
line with web support did something previous to showing me the command line and that
enabled me to type apt-get update && upgrade and by doing so enabled me to replace 
the bad packages with the good one.

And as i said dpkg mode didn't do that period.

---

### Post by psyke83 on 2010-08-07
> **aviramof said:**
> Too be honest i was also surprised that it didn't worked considering the fact that i am connected via router meaning the router does the dialing not the OS but for some reason
dpkg mode showed me a lot of errors of not being able to connect however the command 
line with web support did something previous to showing me the command line and that
enabled me to type apt-get update && upgrade and by doing so enabled me to replace 
the bad packages with the good one.

And as i said dpkg mode didn't do that period.

Your connection (PPPoE) and several other connection types (e.g. wireless connections using encryption) will not work during recovery mode. Why? Because NetworkManager bypasses the traditional /etc/network/interfaces method for network configuration. The only case in which your internet will function during the recovery mode is when your wired network uses plain DHCP, or else, when you have already created an automatic profile for your connection in /etc/network/interfaces (generally not recommended these days, as it will disable NetworkManager's control of your device).

The solution to this problem will come come when NetworkManager can function 100% from a terminal (in other words: when it is no longer dependant on nm-applet within a graphical environment to initialize a connection). I vaguely recall this capability mentioned in the release notes for a recent Fedora release, so perhaps the capability is now present.

Edit: version 0.8.1 of NetworkManager includes a command-line interface. See here: [http://live.gnome.org/NetworkManager/ReleaseProcess](http://live.gnome.org/NetworkManager/ReleaseProcess) - Maverick is still on 0.8, so we'll need to wait.

---

### Post by MacUntu on 2010-08-08
> **psyke83 said:**
> Your connection (PPPoE) and several other connection types (e.g. wireless connections using encryption) will not work during recovery mode.
But he says it worked in "netroot" - strange, I guess it was coincidence and something else went wrong (connection problems, servers down, etc.).

> **psyke83 said:**
> See here: [http://live.gnome.org/NetworkManager/ReleaseProcess](http://live.gnome.org/NetworkManager/ReleaseProcess)
Oh, that's nice. I especially like this: "Ability to suppress periodic scans by locking connection to a BSSID".

---

### Post by aviramof on 2010-08-09
> **psyke83 said:**
> Your connection (PPPoE) and several other connection types (e.g. wireless connections using encryption) will not work during recovery mode.

You know this is getting ridiculous Ubuntu maverick 10.10 don't even have recovery mode support for PPPoE which is a protocol that entire countries use in my company this is what 
the biggest infrastructure use and your telling me that ubuntu 10.10 recovery mode doesn't support it?

To tell you the truth i sure hope that final maverick would be a major improvement because at the moment i am not terribly impress from her,and most likely lucid and all other versions
don't support recovery mode PPPoE so i am not terribly impressed from 
them in the end,i mean recovery mode is what you use when you really need it and if 
that doesn't work well then what does?

---

### Post by psyke83 on 2010-08-09
> **aviramof said:**
> You know this is getting ridiculous Ubuntu maverick 10.10 don't even have recovery mode support for PPPoE which is a protocol that entire countries use in my company this is what 
the biggest infrastructure use and your telling me that ubuntu 10.10 recovery mode doesn't support it?

To tell you the truth i sure hope that final maverick would be a major improvement because at the moment i am not terribly impress from her,and most likely lucid and all other versions
don't support recovery mode PPPoE so i am not terribly impressed from 
them in the end,i mean recovery mode is what you use when you really need it and if 
that doesn't work well then what does?

What's truly ridiculous is that you made no effort to properly understand the information that was provided to you, not only by myself, but several others too. I am honestly getting to the point in which I wonder if you're deliberately trolling the forums.

---

### Post by rajeev1204 on 2010-08-09
> **ranch hand said:**
> 

<snip>

<snip>

---

### Post by aviramof on 2010-08-09
> **psyke83 said:**
> What's truly ridiculous is that you made no effort to properly understand the information that was provided to you, not only by myself, but several others too. I am honestly getting to the point in which I wonder if you're deliberately trolling the forums.
What information? he said that PPPoE don't work in recovery mode which is ridiculous 
considering the fact that in my country at least 80% of the internet users  are using 
this protocol, so i really don't understand why in ubuntu 10.10 there is still no support
for this protocol in recovery mode.

I mean i am connected and dialed via router not via any operating system via wierd  so what does ubuntu need in order to connect to the internet in recovery mode? an isp server connected to my computer?

If i am connected via router it should work on all circumstances because i am already connected,the fact that ubuntu can't recognize and work properly with a standard router in recovery mode is indeed very ridiculous to me.

---

### Post by ronacc on 2010-08-09
> **rajeev1204 said:**
> No need to be that rude .

if you check out this guys threads going back to the start of MM you'll see that RH is justified in what he said , I have been resisting the urge to say something similar or rather harsher .

---

### Post by ronacc on 2010-08-09
> **aviramof said:**
> What information? he said that PPPoE don't work in recovery mode which is ridiculous 
considering the fact that in my country at least 80% of the internet users  are using 
this protocol, so i really don't understand why in ubuntu 10.10 there is still no support
for this protocol in recovery mode.

I mean i am connected and dialed via router not via any operating system via wierd  so what does ubuntu need in order to connect to the internet in recovery mode? an isp server connected to my computer?

If i am connected via router it should work on all circumstances because i am already connected,the fact that ubuntu can't recognize and work properly with a standard router in recovery mode is indeed very ridiculous to me.

first of all there is no Ubuntu 10.10 as of yet , Maverick meerkat will become ubuntu 10.10 when it is released . What part of "development" do you not understand ? Your long string of aggressively stated complaints going back to the start is getting tiresome and causing people to question your motives .

---

### Post by MacUntu on 2010-08-09
> **aviramof said:**
> the fact that ubuntu can't recognize and work properly with a standard router in recovery mode is indeed very ridiculous to me.
That's no fact, that's an isolated case at your end.

---

### Post by aviramof on 2010-08-09
There is nothing uniq about my connection my router is the same as any one eles in my infastructure internet company and is set the same to everyone by default if it doesn't work for me it doesn't work for any of the other users period.

---

### Post by MacUntu on 2010-08-09
Ok, I'm outta here. Period. :D

---

### Post by cariboo on 2010-08-09
This thread is really going nowhere, closed.

---

