---
title: "A solution to Fixing the Missing Network Manager Icon in Ubuntu 9.10"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by cthulhucookie on 2009-11-02
Hello Everyone.

This morning, I booted up my laptop and tried to connect to the school's wireless when I noticed that the icon for Network Manager was missing from the toolbar. I checked to see that Network Manager was running and it was, the icon had just disappeared for some reason. After tinkering around with the panel a little bit, I discovered that if you remove the notification area on the panel (right click the three vertical dots and click "Remove From Panel") and then re-add it ( right click the panel, click "Add to Panel" and search for "Notification Area", then click it) the Network Manager icon will reappear, thus allowing you to connect to wireless networks. 

Hope this works if you're having the same problem! :D

---

### Post by Aging Aardvark on 2009-11-08
Had the same problem upgrading from 9.04 to 9.10.
Just want to say a big thank you to you people who bother to post to this forum.

---

### Post by Saurabh Deodhar on 2009-11-10
Thanks a lott bro. it was very useful. I had a tough tym searchin wat went wrong........ thanks a lott

---

### Post by Maupertus on 2009-11-16
I had (by accident) come to the same conclusion on this point, but it's not really a solution though is it? I was wondering if someone had found a more permanent resolution of the problem.

---

### Post by cthulhucookie on 2009-11-19
> **Maupertus said:**
> I had (by accident) come to the same conclusion on this point, but it's not really a solution though is it? I was wondering if someone had found a more permanent resolution of the problem.

I agree, it isn't a permanent solution. Every time I rebooted the icon would disappear and I'd have to reinstall the notification area. A few days ago, I was forced to do a clean install of Ubuntu 9.10 due to some dual-booting issues and I don't have that problem with the network manager icon anymore, it stays on the panel like it's supposed to. If I find a solution to the problem I'll definitely post it to this thread.

---

### Post by tonyhawz on 2009-11-20
it is afecting me also 
bug reported at:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/482684](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/482684)

---

### Post by LukonLinux on 2009-11-26
Me too, but my connection still works - I just get no feedback.

---

### Post by dee_tewari on 2009-11-30
I got this problem in a fresh install of 9.10!

So I was checking "Startup Applications" (System > Preferences) and I realized that the entry for indicator applet has the following:

sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py"

Just after it comes the entry for Network Manager. Now I'm not sure if they're executed in the order in which they're listed and I highly doubt that also but assuming that they're executed in the same order then the Network Manager would start after the Indicator Applet and that may have something to do with the fact that it's icon is missing from the indicator applet.

So I changed the line above to the following:


sh -c "sleep **90** && python /usr/share/gnome-panel/add-indicator-applet.py"

Now the network manager's icon is there always. If the problem re-appears I'll update that fact here. But for now this change seems to have solved the issue!

---

### Post by tonyhawz on 2009-11-30
it seems to be fixed now, I don't know how or in which point of an update.
The icon is always there, so my guess is: try updating.

---

### Post by HoTMetaL on 2009-12-07
> **tonyhawz said:**
> it seems to be fixed now, I don't know how or in which point of an update.
The icon is always there, so my guess is: try updating.
I'm fully up-to-date on updates (karmic-security, karmic-updates) and the problem persists. So, no, it hasn't been fixed. At least not on my machines.

---

### Post by Benz_200t on 2009-12-09
hi, having the same problem.....and i just have updated my 9.10....and still having the same problem.

but in my case,the wireless work for a while, then it disconnected and the logo goes missing.

after searching, i installed wifi radar...and thought it solved the problem....

but no can do.......hope somebody could guide me with this problem....

---

### Post by Benz_200t on 2009-12-09
**double post**

---

### Post by wwwphil on 2009-12-11
> **cthulhucookie said:**
> Hello Everyone.

This morning, I booted up my laptop and tried to connect to the school's wireless when I noticed that the icon for Network Manager was missing from the toolbar. I checked to see that Network Manager was running and it was, the icon had just disappeared for some reason. After tinkering around with the panel a little bit, I discovered that if you remove the notification area on the panel (right click the three vertical dots and click "Remove From Panel") and then re-add it ( right click the panel, click "Add to Panel" and search for "Notification Area", then click it) the Network Manager icon will reappear, thus allowing you to connect to wireless networks. 

Hope this works if you're having the same problem! :D

Thanks for posting, got my icon back:D

---

### Post by MEmO33 on 2009-12-27
I'm absolute beginner. I reinstall the network manager and found that nm-applet didn't show up in the notification area.

So, this is what I did and it worked for me.

1. Go to **_/usr/share/app-install/desktop_** and find** Network Manager**
2. Right click.. Properties.. copy the command line
3. Go to **_System.. Preferences.. Startup Applications_** and look for [B] Network Manager
[/B]4. Click Edit and paste the command then save
5. Log out, log in

Command should be something like this
```
nm-applet --sm-disable 
```

Hope it works for you.

---

### Post by larsman1 on 2010-01-06
Wed. 01/06/2010
I did 9.10 security updates this morning, and the Network Connection Icon and Sound Volume Icon on the tool bar disappeared.  Forgive me forum for not checking 2 hours ago to save my aggravation.  Your fix worked.
See wwwphil's reposting of **cthulhucookie.**

---

### Post by cthulhucookie on 2010-01-08
Hey everyone.

I hope you're all doing well in 2010. I found an article posted on Ubuntu Geek today that's based on this forum thread. 

[http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html](http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html)

Perhaps the comments left on this article will help some of you.

---

### Post by mhiggins1979 on 2010-02-04
still not getting the network manager icon back. got everything else back. any idea how to get the icon back so that I can connect to wireless networks at places like coffee shops and such?

---

### Post by cthulhucookie on 2010-02-08
> **mhiggins1979 said:**
> still not getting the network manager icon back. got everything else back. any idea how to get the icon back so that I can connect to wireless networks at places like coffee shops and such?

Hi there.

If none of the solutions in the thread are doing it for you, might I suggest using Wicd Network Manager instead? Just open up a terminal and type:

```
sudo apt-get install wicd
```

Allow network-manager and nm-applet to be removed. Wicd will takes its place.

I switched over to Wicd a while ago and haven't had any problems since.

For more information: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by nightwolf2k5 on 2010-02-15
Hey guys...

I was facing the same problem.. the volume control and the network connection icons were missing.

I tried adding the notification area (rt click + Add to Panel) but was not successful.

During a restart i noticed that in my login screen, the session was "Failsafe Gnome".
I changed that to "Gnome", logged in and added the notification area again. This time it worked!

Thought of sharing this as a possible solution.

Good luck.

---

### Post by zvibu on 2010-02-18
Thank you for solution' I'll never thought to find it under this nomination.

---

### Post by And1945 on 2010-02-19
> **MEmO33 said:**
> I'm absolute beginner. I reinstall the network manager and found that nm-applet didn't show up in the notification area.

So, this is what I did and it worked for me.

1. Go to **_/usr/share/app-install/desktop_** and find** Network Manager**
2. Right click.. Properties.. copy the command line
3. Go to **_System.. Preferences.. Startup Applications_** and look for [B] Network Manager
[/B]4. Click Edit and paste the command then save
5. Log out, log in

Command should be something like this
```
nm-applet --sm-disable 
```

Hope it works for you.
This worked for me. For some reason, the command line in my startup applications just stated: "nm-applet". Then it is completely understandable why it did not work.

---

### Post by omicron42 on 2010-06-10
Hi everyone,

I have tried everything listed in this thread, and still can't get networkmanager to show up. I just started using 9.10, so I've never actually seen it there.

Any suggestions for anything else I could do? When I tried the wcid idea, it couldn't find it.

Thanks

---

### Post by mooneyk20 on 2010-06-13
I was having all the same issues I tried everything and nothing worked my network icon was still missing.  

Finally I changed my  Preferences > Appearance > theme from "Ambiance" to "Clear looks" and the wireless icon reappeared and has stayed in the system tray since.

I don't know why but clearly I will not be altering the theme until I figure it out.

---

### Post by santhust on 2010-06-15
> **cthulhucookie said:**
> Hello Everyone.

This morning, I booted up my laptop and tried to connect to the school's wireless when I noticed that the icon for Network Manager was missing from the toolbar. I checked to see that Network Manager was running and it was, the icon had just disappeared for some reason. After tinkering around with the panel a little bit, I discovered that if you remove the notification area on the panel (right click the three vertical dots and click "Remove From Panel") and then re-add it ( right click the panel, click "Add to Panel" and search for "Notification Area", then click it) the Network Manager icon will reappear, thus allowing you to connect to wireless networks. 

Hope this works if you're having the same problem! :D

Thanks :p

---

### Post by fmurrieta on 2010-09-03
I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:

All I need to do to fix the missing nm-applet was1.- Login as your first user
[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT]Hope thi*s can save you* some time!


Fernando Murrieta

---

