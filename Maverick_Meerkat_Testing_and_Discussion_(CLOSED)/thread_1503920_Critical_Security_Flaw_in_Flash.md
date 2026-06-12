---
title: "Critical Security Flaw in Flash"
date: 2010-06-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-06-07
Hi gang,

I'd suggest you have a read of [http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html) and act accordingly.

I don't know who to ask to get the one in repos updated, so if any mod passes by please ensure that they're aware & get the repo's updated sooner, rather than later.

Regards,

Phill.

---

### Post by ronacc on 2010-06-07
I thought critical security flaws were normal in flash .

---

### Post by phillw on 2010-06-07
> **ronacc said:**
> I thought critical security flaws were normal in flash .

Maybe, but it's the 1st time I've seen it affect Linux systems, hopefully it can only 'attack' at the user level (unless people are using root privalidges - another good reason not to do so ;-) )

Phill.

---

### Post by SteamInc on 2010-06-07
Phill is right. We need to avoid any amount of hackers from getting into Ubuntu. This could be seen as a way into Ubuntu. It must be fixed fast, because once one of these hackers notices it they will attack.

---

### Post by ronacc on 2010-06-07
I avoid flash when humanly possible , I use Opera for a browser and it is easy to enable and disable plugins .

---

### Post by SteamInc on 2010-06-07
Then you will lose the ability to use Youtube or use some other things on the Internet.

---

### Post by jfernyhough on 2010-06-07
Hmm... is the 64-bit version affected?

---

### Post by Jordanwb on 2010-06-07
> **phillw said:**
> Critical Security Flaw in Flash

Big shocker.

---

### Post by zekopeko on 2010-06-07
> **phillw said:**
> Maybe, but it's the 1st time I've seen it affect Linux systems, hopefully it can only 'attack' at the user level (unless people are using root privalidges - another good reason not to do so ;-) )

Phill.

I never understood this way of thinking. As a user I think that my data in my home is far more important then a system that I can install from scratch in 20 minutes.

---

### Post by MacUntu on 2010-06-07
> **ronacc said:**
> I avoid flash when humanly possible

Way too often it isn't. Let's go punch some webdesigners. :P

---

### Post by gnomeuser on 2010-06-07
> **zekopeko said:**
> I never understood this way of thinking. As a user I think that my data in my home is far more important then a system that I can install from scratch in 20 minutes.

Another problem is that users have access to the internet and programs can be run if compromised. E.g. one might easily become a member of a botnet that way.

Additionally like you say, sensitive data such as online banking data, documents, account data such as password files for everything. 

Being root really only gives you expanded presistence but the goal of most spammers e.g. namely growing a botnet could easily do so without superuser access.

---

### Post by phillw on 2010-06-07
I don't know how long Adobe have known about it, but unlike some other security alerts I have received for other operating systems e.g. Microsoft saying it will be weeks, or Apple hanging back for months IMHO Adobe has been very quick to respond, as they say the compromises are all ready 'out in the wild' you may say that they had no choice but to come forward, but it has never stopped the others, at least they have a solution that is fairly painless for us linux users.

But, we can argue about all of that at leisure - just make sure that you pass the knowledge on.

As a real quick hack, that worked on my multi boot system running more than one browser system, I cheated.(The listing below does not have all my partitions loaded, it just got messy :-D )
[list]
Download the new version
extract it
Mount all partitions
cd /
locate libflashplayer.so
replace all instances with the new one
restart your browser(s)
[/list]

I'm sure others can up with a more elegant solution, but it found all the ones that I expected in both Firefox and Chromium
```
phillw@piglet:~$ locate libflashplayer.so
/home/phillw/.mozilla/mozback/plugins/libflashplayer.so
/home/phillw/.mozilla/plugins/libflashplayer.so
/main/usr/lib/chromium-browser/plugins/libflashplayer.so
/main/usr/lib/flashplugin-installer/libflashplayer.so
/main/usr/share/ubufox/plugins/libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

```

Regards,

Phill.

---

### Post by Cavsfan on 2010-06-07
wrong thread I guess...
I fixed it on my system...

---

### Post by zika on 2010-06-07
> **phillw said:**
> I don't know how long Adobe have known about it, but unlike some other security alerts I have received for other operating systems e.g. Microsoft saying it will be weeks, or Apple hanging back for months IMHO Adobe has been very quick to respond, as they say the compromises are all ready 'out in the wild' you may say that they had no choice but to come forward, but it has never stopped the others, at least they have a solution that is fairly painless for us linux users.

But, we can argue about all of that at leisure - just make sure that you pass the knowledge on.

As a real quick hack, that worked on my multi boot system running more than one browser system, I cheated.(The listing below does not have all my partitions loaded, it just got messy :-D )
[list]
Download the new version
extract it
Mount all partitions
cd /
locate libflashplayer.so
replace all instances with the new one
restart your browser(s)
[/list]

I'm sure others can up with a more elegant solution, but it found all the ones that I expected in both Firefox and Chromium
```
phillw@piglet:~$ locate libflashplayer.so
/home/phillw/.mozilla/mozback/plugins/libflashplayer.so
/home/phillw/.mozilla/plugins/libflashplayer.so
/main/usr/lib/chromium-browser/plugins/libflashplayer.so
/main/usr/lib/flashplugin-installer/libflashplayer.so
/main/usr/share/ubufox/plugins/libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

```

Regards,

Phill.O boy! I have it only in one place: ~/.mozilla/plugins (symbolic link to a folder where I keep real libflashplayer.so and update it regularly...) It works, that way, with all FF, Chrome, Chromium, Opera, SwiftFox......

---

### Post by Atermoon on 2010-06-07
> **MacUntu said:**
> Way too often it isn't. Let's go punch some webdesigners. :P

I'd love to :lolflag:

---

### Post by moviemaniac on 2010-06-08
> klaus@klaus-imac:~/Desktop$ file libflashplayer.so 
libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped


So we 64bit users are left alone for who knows how long with this security hole? Screw you, Adobe!

---

### Post by dinamic1 on 2010-06-08
> **atermoon said:**
> i'd love to :lolflag:
no!

---

### Post by nerdopolis on 2010-06-08
> **zekopeko said:**
> I never understood this way of thinking. As a user I think that my data in my home is far more important then a system that I can install from scratch in 20 minutes.

I agree with that. Your home directory is left virtually in the open compared to the rest of the system.  

However I think you can use AppArmour to enable the firefox security profile on your account. I can kind of see why its not enabled by default, as Firefox not being able to access the documents might not sit well with users...

---

### Post by Atermoon on 2010-06-09
> **Chauncellor said:**
> What, you *like* those ostentatious sites that require a computer resembling 2001's HAL in order to run?

As much as I dislike Apple, and as bad as I feel for Adobe about the ipad/adobe situation, I think it's about time it gets killed off. Adobe has done a fantastically poor job at managing this standard-breaking dysfunctionality, and I'm glad that someone big gave them the middle finger.

+1 except I don't even feel bad for Adobe. Flash has been a pain in my *** for years, it's time to move on.

---

### Post by phillw on 2010-06-11
hi,

the patch for 32 bit is in the ubuntu updates, alas no news from adobe on when they will patch the 64 bit version.

Regards,

Phill.

---

