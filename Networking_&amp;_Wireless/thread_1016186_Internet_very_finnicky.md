---
title: "Internet very finnicky"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Valok on 2008-12-19
So this morning I updated my system and ever since I've been having problems with my internet.  Namely with being able to stay connected to World of Warcraft.  About every 10 minutes or so I will lag out and won't be able to log back in for about another 5 minutes.  The weird thing is every other aspect of my internet sill works, its only WoW that gets messed up.

I'm not entirely sure what updates I installed, or what could be causing this, but if anyone knows I'd love to figure this one out with your help.  Thanks!

*Edit* I'm using  MCP51 Ethernet Controller (wired internet) and forcedeath drivers.  When I go into the network tools menu it says that my network device is "loopback".  If I try and switch it to "ethernet interface" I get an error saying 'The interface does not exist'.  Is that a problem?

---

### Post by Valok on 2008-12-19
Still crippled by this problem =(

---

### Post by xDeadcowx on 2008-12-19
I am having the same exact problem.  I will let you know if i find out anything.

---

### Post by Valok on 2008-12-19
Awesome, I'll do the same

---

### Post by cariboo on 2008-12-19
In a terminal type:

```
ifcong
```

and 

```
sudo lshw -C bridge
```

I have the same nic and it doesn't show up as a network device. 

If it is just the Wow site that you are having the problem with, more then likely the problem is on their end.

Jim

---

### Post by xDeadcowx on 2008-12-19
Well, i cant seem to pinpoint the issue.  I am going to start running some traces and see if anything comes from that.  What i did learn is that there have been major issues between WOW and Comcast.  If you happen to be using comcast as your isp like i am, then that may be the issue.  WoW and Comcast are fighting back and forth, Comcast blames Blizz, and Blizz blames Comcast.

The part that is still bugging me is that i played just fine up until the update today.

Again i will update with any new info i find.

---

### Post by Valok on 2008-12-19
Thanks Cariboo, although I'm not entirely sure what I'm looking for after typing in that code.

Sucks that Comcast (who is my isp) is having such trouble with blizz.  I really hope they figure their **** out soon.  I'm at least glad to hear I'm not the only one with this problem.

---

### Post by Valok on 2008-12-19
For anyone still having this problem, check out this. 

[WoW Tech Support Forums](http://forums.worldofwarcraft.com/board.html?forumId=11110&sid=1)

Apparently there is a massive problem with Comcast and WoW.  So its not just us, and its not just ubuntu.  Read on over there for the most up to date info, hopefully they fix it soon.

---

### Post by yggdrasil255 on 2008-12-19
Oddly enough, I'm also having trouble getting to the wine repository.  Maybe blizzard should be warned about that.  At first I thought it was Ubuntu as well, maybe it still is.  

jyoshu@shadow:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                        
...


Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg     
  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US
  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]
Reading package lists... Done
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg)  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2)  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


First time this has happened.  Happens on both my main box and a laptop.  The former having wine hacked onto it to play WoW.

When I try to get it through the GUI manager, it shows most sites as failing, but again, it hangs when it gets to the bottom. I don't know if this is a separate issue or the same, but both coincided on today.

---

### Post by Valok on 2008-12-19
I've been having the same error with WINE when trying to update my system too, but that was a while before this problem started to happen.

---

