---
title: "wicd 1.7 - wireless - Connection Failed: Bad Password"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by finny388 on 2010-10-12
I switched to wicd a few months ago because it seemed to switch between wired and wireless very smoothly.

It's been a while since I've used wireless and now when I try I get> Connection Failed: Bad Passwordevery the time.

I know the password is correct b/c it is the pw I use everywhere on my laptop as well as the router and I am writing this on an old winxp box wirelessly.

I've gone into /etc/wicd/wireless-settings.conf and confirmed passwd.

I've tried it in quotes, I've converted to hexidecimal - same error.

I have network-manager and network-manager-gnome (0.8) installed but back then I somehow disabled the tray icon and now I can't remember how to restore it.

It will make the wired connection but not wireless.

I'm at my wit's end and hope somebody knows what I can try.

:confused:

---

### Post by ÄssfaceJackson on 2010-10-12
I have had this exact same problem since August. Every reference to it I can find through Google just says to "completely remove network-manager" but it never works. I actually tried a fresh install tonight because I couldn't take it anymore but I'm still hitting the same problem. What a disappointment...

---

### Post by ÄssfaceJackson on 2010-10-12
The instructions from this guy is similar to what everyone else says, but it never works:

[http://kubuntuforums.net/forums/index.php?topic=3110183.msg219877#msg219877](http://kubuntuforums.net/forums/index.php?topic=3110183.msg219877#msg219877)

Network-Manager is terrible. I used to be able to at least connect to wireless on my home router using wicd (but not on campus), but after upgrading to Maverick I can't connect to anything. So I essentially have no laptop now... :confused:

---

### Post by finny388 on 2010-10-13
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070]("https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070")

seems to be a known bug for a long time

I tried uninstalling network manager as in post #18 that many subsequent posts claim solved their problem.

But after restarting same problem.

What an old bug

how to abandon wicd and use network mgr again. or whatever.

I don't have access to wired connections right now :( :confused: :mad:

---

### Post by macem29 on 2010-10-13
same issue here, 10.04 on acer netbook, atheros wifi...gnome network manager was terrible, completely
removed it and installed wicd, would not take known good password, back to buggy gnome manager
that will at least let me connect, for a little while...don't know  long I'm gonna live with this, 10.04 fresh
install was great, bullet proof, updates seem to just make it worse...maybe blow this and redo XP, a netbook
without wifi is a doorstop

---

### Post by finny388 on 2010-10-13
> netbook
without wifi is a doorstop

no kidding! how can this issue not be mission critical?!?

---

### Post by ÄssfaceJackson on 2010-10-13
Tried reinstalling three times last night. No luck. Then I tried install Mint Linux. Still no luck. I've wasted a whole day trying to get this work. I'm really screwed on this problem.

------

I just switched back to Network-Manager and it seems to be working for now. The problem I have with NM is that it just seems to stop working randomly and it has trouble setting itself up properly when I travel to different universities (which isn't that often, but I am going to one tomorrow).

---

### Post by finny388 on 2010-10-13
> **ÄssfaceJackson said:**
> Tried reinstalling three times last night. No luck. Then I tried install Mint Linux. Still no luck. I've wasted a whole day trying to get this work. I'm really screwed on this problem.

------

I just switched back to Network-Manager and it seems to be working for now. The problem I have with NM is that it just seems to stop working randomly and it has trouble setting itself up properly when I travel to different universities (which isn't that often, but I am going to one tomorrow).

i just switched back too
waiting for 1.8
:cry:

---

### Post by bazzal1941 on 2010-10-15
For what it is worth I have to agree with you guys, how is it that wireless still doesn't work out of the box. Especially as NBR is specifically designed for netbooks.

Anyway I took your advice and re-installed nm. At least it will work for a while.

---

### Post by finny388 on 2010-10-15
I'd love to mark this thread SOLVED but it is so far from the case

---

### Post by claracc on 2010-10-17
I have had the same problem when upgrading to lucid Lynx. (Network manager gnome continuously connecting/disconnecting the wifi, so unusable)

Wicd asked for root pass for three times and then stopped.

I solved it in the following way:In /etc/init/networking.conf you add at the end: exec wicd

Then in a xterm you run wicd-client

The wireless works for me now. 

Then you create a launcher to execute wicd and put it as an application to run at the begining.

---

### Post by pwabrahams on 2010-10-17
I had wireless working beautifully under Lucid, though not without a lot of difficulty getting there (see [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros#KurianAlternative]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros#KurianAlternative").  But with Meerkat, I've gotten nowhere in defeating the "Bad Password" problem.  One frustrating thing about it is that you can't really demonstrate that the password is valid, so it's reassuring to see that other folks have had the same problem.

I too am running wicd 1.7.0 and madwifi version 0.10.5.6-r4126-20100324.  My laptop is an Asus K60.

---

### Post by pwabrahams on 2010-10-17
My wireless is working now!  I uninstalled wicd and reinstalled Network Manager, which now works for me.  The only minor hiccup was that I had to start the router connection explicitly, but then I found that I could get an automatic startup just by checking the box in the Network Manager controls.

I think that the problem lies in the latest version of wicd, which in the past has always worked well for me.

---

### Post by Travis Currit on 2010-10-20
I have the same problem using 10.10. Gnome network manager was constantly disconnecting and reconnecting, so I installed wicd, getting the bad password error for a known good password. Then even gnome network manager stopped connecting using the same good password. 

I uninstalled wicd trying to get back to the good old somewhat working state, but Gnome network manager still gives bad password error.

There needs to be a fix for this and SOON. I agree with the above posts that smoothly working wireless internet out of the box should be THE number one priority for any modern OS. Without it, you can't even do updates or internet searches to try to solve the problem.

update:

After writing that I rebooted into Ubuntu and now network-manager is able to connect. Perhaps wicd was still interfering somehow before the reboot. Here's hoping it will be able to hold the connection for more than a few minutes at a time.

---

### Post by vahnx on 2010-10-21
I just switched from a DLink 1310 rev D to a TP-Link WR941ND and I'm getting this error on my Arch Linux 2010.5 install.

---

### Post by cub on 2011-01-28
> **Travis Currit said:**
> I have the same problem using 10.10. Gnome network manager was constantly disconnecting and reconnecting, so I installed wicd, getting the bad password error for a known good password. Then even gnome network manager stopped connecting using the same good password. 

I uninstalled wicd trying to get back to the good old somewhat working state, but Gnome network manager still gives bad password error.

There needs to be a fix for this and SOON. I agree with the above posts that smoothly working wireless internet out of the box should be THE number one priority for any modern OS. Without it, you can't even do updates or internet searches to try to solve the problem.

update:

After writing that I rebooted into Ubuntu and now network-manager is able to connect. Perhaps wicd was still interfering somehow before the reboot. Here's hoping it will be able to hold the connection for more than a few minutes at a time.

I have the same issue with NM disconnecting and reconencting my wifi at work about 10-15 times an hour. Very annoying during video conferences... So I tried wicd as instructed in other threads. Got the Bad Password with 1.7. Read the instruction to remove network-manager from console, no difference. Read that downgrading wicd to 1.6.1 would work. And it did, sort of. Now I get authenticated, but instead it won't obtain an IP. *sigh* Back to NM then...I should have gotten a mac like my co-workers suggested when I started here...

---

### Post by bjlockie on 2011-01-28
I had the same problem.
I didn't unlock the key ring when Network Manager asked (because I prefer wicd) and wicd didn't work.
I unlocked the key ring and wicd works.
I'd rather get rid of Network Manager but apparently I need it.

---

### Post by rjv23 on 2011-06-17
same problem for me, both WEP and WAP security would not log on to networks.  Removed Network manager as explained here: [http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)
rebooted computer and logged on using wireless with no problem.

---

