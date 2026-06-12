---
title: "Anyone else have MythTV lockup the whole system?"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by OldGaf on 2007-04-14
Hi,

I have MythTV on the latest Edgy. Everything works fine, but when entering or leaving the program guide, it occasionally freezes and locks up the whole system.

I have reinstalled on various diff systems to eliminate hardware issues and finally purchased a brand new system with the same results.

Myth is not supposed to be able to do this (so I am told).... has anyone else had or heard of this problem?

BTW, I am using lirc and a remote.

---

### Post by OldGaf on 2007-04-14
bump

---

### Post by OldGaf on 2007-04-20
> **OldGaf said:**
> Hi,

I have MythTV on the latest Edgy. Everything works fine, but when entering or leaving the program guide, it occasionally freezes and locks up the whole system.

I have reinstalled on various diff systems to eliminate hardware issues and finally purchased a brand new system with the same results.

Myth is not supposed to be able to do this (so I am told).... has anyone else had or heard of this problem?

BTW, I am using lirc and a remote.

Anyone? 

This is recurring on a few machines with completely diff. hardware. The only constants are the data base settings and that is is Edgy. Going to try in on Feisty next. I see many people are using Fedora, but I was hopping to stay with Kubuntu.

And it ONLY seems to happen when accessing or leaving the program guide.

Oh, and it also has happened without using the remote so lirc is out.

---

### Post by crispingatiesa on 2007-04-20
I have had this behaviour the last couple of week. (Has happen three times). Interesting thing is that I ran the rig for more than 8 month with no problem, and I haven't update anything.

---

### Post by OldGaf on 2007-04-23
> **crispingatiesa said:**
> I have had this behaviour the last couple of week. (Has happen three times). Interesting thing is that I ran the rig for more than 8 month with no problem, and I haven't update anything.

Thanks for replying. This is really a nasty issue.

Does it happen to you only when you access  or leave the TV Guide?

What distro are you using?

---

### Post by pjman on 2007-04-30
I'm having a similar issue. I've been running MythTV with dual PVR-150's on 6.10 for the past 3 months with no problems. In the last couple of days my PC is locking up after choosing a show to watch in the live-tv program guide. During this lockup the computer is unresponsive.

-doesn't respond to remote commands
-screen is 'frozen"
-cannot ping computer

After rebooting I've checked all the logs in /var/log and nothing stands out as odd to me. What else can I do to pinpoint the problem?

Thanks!

---

### Post by pjman on 2007-04-30
Will the suggestion in [this thread]("http://www.gossamer-threads.com/lists/mythtv/users/266764") help?

I dissabled realtime priority... I'll see if it locks up in the next couple of days.

**EDIT**

It's now been working for three weeks without a lockup :-)

---

### Post by ml98133 on 2007-10-10
YES!  I'm sorry to hear other people are having trouble but kind of glad it's not some fluke with my system.

I had been using FC3 64 bit for years with mythtv with no trouble.  I had to upgrade to get the new program guide software since Zapit was going away.  I thought, Ubuntu is neat, I'll try upgrading the whole system to something a little more modern.

I installed fiesty 64 bit and was happy with how easy it was.  I did the same for a system my parents rely on.  Both systems are locking up every week or maybe a little bit longer.

Now, every couple weeks it locks up with completely.  The screen freezes.  
It does not necessarily happen when I'm interacting with it.

We never watch live TV, it seems to lock up on the screen with the program guide with the little preview window.

We have also experienced stuttered, choppy video on playback from time to time.

We have a PVR350 and a PVR500 in our system and a pvr350 in the other.

On the PVR350 only system, the ivtv driver would  freak out sometimes and cause the system to require a reboot, but it was easy to see the issue in the logs and everything didn't freeze. (reloading drivers didn't help).  That was part of the reason I decided to re-install the OS also.

The logs with Ubuntu show nothing significant and it seems as if the system just locks completely without the ability to log anything.

I thought of swapping the MB or trying a bios upgrade, but am glad someone already tried it.
(maybe a bios upgrade would be worth it if it's available either way.)

Did disabling the RT priority continue to help it.  (It is already disabled for me.)  It's so hard to know since it takes weeks to see the problem.

Are you using an NVidia card with the nvidia drivers?  Could they be causing the problem?

---

### Post by NT4usB on 2007-10-10
I had a similar problem a while back. Come home to find one or both mythboxes locked up solid.
Turned out, my Netgear GB switch was malfunctioning and taking out the system. 
I managed to catch it in the act a couple times. The activity lights would all flicker and glow. If I unplugged it right away, I wouldn't lose the machines. If it happened while I was away, only a hard reboot would bring them back.
Replaced the router and all is well.

---

### Post by sjwk on 2007-10-14
Interesting posts...  Sadly I don't think anything so far tallies with my problems - My Ubuntu myth box has been running fine for a year or so.  I've just updated it to Feisty (I figured with Gutsy due out soon, it was about time) and since then the whole machine is locking solid after a few hours, even if it's just sitting idle.  I don't think it's myth itself but the whole machine just freezes which suggests hardware or drivers.  Probably the latter since it's been fine on the same hardware until the update.  No response to pings.  Nothing in the log files post-hard reboot to indicate the cause.  I've tried both fglrx and default ati xorg drivers.  But getting to be a bit of a pain now!  Tempted to do a clean reinstall apart from the disk full of existing content that I've not watched yet!

Steve.

---

### Post by OldGaf on 2007-10-28
Very  interesting. I just replaced my DI-624 as I was having  wireless issues  with other PC's on my LAN (Myth is NOT wireless). Now that I think of it, I have not had a freeze sense.


BTW, I am using Nvidia drivers installed with envy. I have an onboard 6150.

---

### Post by OldGaf on 2007-10-28
> **ml98133 said:**
> YES!  I'm sorry to hear other people are having trouble but kind of glad it's not some fluke with my system.

I had been using FC3 64 bit for years with mythtv with no trouble.  I had to upgrade to get the new program guide software since Zapit was going away.  I thought, Ubuntu is neat, I'll try upgrading the whole system to something a little more modern.

I installed fiesty 64 bit and was happy with how easy it was.  I did the same for a system my parents rely on.  Both systems are locking up every week or maybe a little bit longer.

Now, every couple weeks it locks up with completely.  The screen freezes.  
It does not necessarily happen when I'm interacting with it.

We never watch live TV, it seems to lock up on the screen with the program guide with the little preview window.

We have also experienced stuttered, choppy video on playback from time to time.

We have a PVR350 and a PVR500 in our system and a pvr350 in the other.

On the PVR350 only system, the ivtv driver would  freak out sometimes and cause the system to require a reboot, but it was easy to see the issue in the logs and everything didn't freeze. (reloading drivers didn't help).  That was part of the reason I decided to re-install the OS also.

The logs with Ubuntu show nothing significant and it seems as if the system just locks completely without the ability to log anything.

I thought of swapping the MB or trying a bios upgrade, but am glad someone already tried it.
(maybe a bios upgrade would be worth it if it's available either way.)

Did disabling the RT priority continue to help it.  (It is already disabled for me.)  It's so hard to know since it takes weeks to see the problem.

Are you using an NVidia card with the nvidia drivers?  Could they be causing the problem?

I have fixed my issue (it seems) by replacing a bad router. It kind of makes sense that it only happened when checking the guide... the onlt thing that really needs the network.

Another issue I had was once the system  did  freeze and I have to manually boot it was that the fast  forward, rewind and some playback would get jerky. After some investigation,I found that the database tables had errors (from having the rug pulled out from under it). Not enough to kack it, but enough to make things rough. So, after a fixing them a few times I wrote a script to clean them up. I will post it if any of you are interested.

The only issue I have now is the Lirc dies on me from time to time. Really sucks it it dies while fast forwarding!

---

### Post by ml98133 on 2007-11-29
Wow...bad router locking up the system....crazy....
I do have a somewhat flaky hub with one of my systems (the one with 2 cards), but not the other.
They both have troubles.

I'm in the process of upgrading to Gusty.  I've never done an "upgrade" on a linux distro before, so I'm hoping all goes well.

---

