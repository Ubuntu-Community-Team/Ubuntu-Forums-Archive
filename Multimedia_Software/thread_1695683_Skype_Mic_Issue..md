---
title: "Skype Mic Issue."
date: 2011-02-26
forum: Multimedia Software
---

### Post by switcha on 2011-02-26
Hi folks,

I am currently having an issue with my microphone working with Skype 2.1.0.81 on Ubuntu 10.10.

I have no issue using my microphone using Audacity to record direct sound, nor do I have any other sound related issues.

I have installed pulse audio volume control and everything appears fine.

However, when I have the skype application open it is not being recognized as an application for playing/recording audio.

Furthermore, when I attempt to make a test call from skype, the test call fails. Under Skype >> Options >> Sound Devices - my microphone is set to pulseaudio(local) and I can't seem to change it.

Any suggestions would be appreciated. Thanks for your time.

Cheers,
~Switcha~

---

### Post by SteveDee on 2011-02-26
> **switcha said:**
> 
Any suggestions would be appreciated. Thanks for your time....


If you haven't already done so, take a look at this: [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

### Post by Rumpty on 2011-02-26
Switcha said: "However, when I have the skype application open it is not being recognized as an application for playing/recording audio."

Skype doesn't appear in pavucontrol until you actually make a call, such as to the audio test call facility. Did you try that?

---

### Post by switcha on 2011-02-27
Hi SteveDee, 

Thanks for the reply - I've checked and worked through several of the troubleshooting issues on that site and had no luck.

I've even re-installed Skype in a bid to make it work.

I have attached a screenshot of what I get when I attempt to make a test call to Echo.

As you can see, it looks like pulseaudio is recognizing the device is attempting to make a call - bottom right.

I have enabled and disabled the "Allow Skype to automatically adjust my mixer levels". I've also attempted to change the Sound Devices with no luck - top right.

It seems as though my call feature has some sort of 'pause icon' permanently affixed to it - not sure how to remove this and it may be indicative of my issue - top left.

I also thought that perhaps skype users on linux can't use free voice calls or cam calls to other skype users or perhaps linux skype users can't use free voice or cam calls to windows skype users due to inter-operability. Either way, not sure b/c I can't test either of these scenarios - bottom left.

Any other suggestions?

cheers,
~Switcha~

---

### Post by switcha on 2011-02-27
Hi Rumpty,

Thanks for the response. Yes, I did - after the re-install it appeared in the pavucontrol when I attempted to make the test call.

Its like its not even connecting to the skype server. All my skype friends arn't appearing online (and I know a few are online) when I'm signed in.

Any suggestions?

Cheers,

~Switcha~

P.S. See above post for more info.

---

### Post by SteveDee on 2011-02-27
> **switcha said:**
> ...Its like its not even connecting to the skype server...

Can you just clarify a few points, as this sounds like you have a bigger problem than just your mic.

1. do any of your contacts ever appear to be on line i.e. green status?
2. If they do, are you able to use the chat feature, where you just type text to one another?
3. When you use Skype Echo, can you connect and hear the nice lady say "This is the Skype call testing service..."

The pause icon (your top left picture) is normal. You click on this to hold a call. The bottom left picture shows the services available that you have not paid for (again this is normal if you just want the free service, like most of us do!).

If you cannot reach the Echo service or see any friends you may be blocking Skype in some way (maybe at your router).

---

### Post by switcha on 2011-02-27
Hi,

Here are responses to your questions:

1. No. Right now, for instance, I know several people are online but the green status is not showing.

2. I can't currently use the chat feature at all. I have verified that when I type a text message to somebody they have not received it.

3. I can't use Skype Echo and, therefore, can not hear the nice lady chatting.

I don't think I'm blocking it at the router because I can use it fine on my windows xp operating system through the same router on the same lan.

Thanks for the response,

~Switcha~

---

### Post by SteveDee on 2011-02-27
Although the mic problem is pretty common (I had problems at the beginning of the year, but know it was working fine over Christmas), your primary problem is the lack of comms.

Perhaps there is something already installed on your system that is creating a conflict. So my only 3 remaining suggestions are:-
1. Try replacing Skype with the previous version: 2.1.0.47
2. Use Startup Disk Creator to make a bootable USB memory stick and run Linux from it. You could then try installing 2.1.0.81 on it to prove it works on your system/look for clues. 
2. Checkout this forum: [http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)  and maybe post your questions there.

---

### Post by switcha on 2011-02-27
Hi SteveDee,

I think I am going to have to do a re-install to get it working again.

Thanks for all your help,

~Switcha~

---

### Post by switcha on 2011-03-03
Hi, 

I re-installed and skype is successfully working now including voice and cam.
Thanks for your help,

~Switcha~

---

### Post by SteveDee on 2011-03-04
> **switcha said:**
> Hi, 

I re-installed and skype is successfully working now including voice and cam...

What did you re-install to fix this? If Skype, what version?

---

### Post by switcha on 2011-03-04
Hi SteveDee,

I ended up doing a complete re-install of the OS (10.10).
I think it was an issue with the dahdi module - abit to finite for my level of detail. However, as I'm not a pro, I can neither confirm nor deny this - just a deductive hunch.
Weirdly enough, I also needed to install the firmware for my wireless - I'm pretty certain this was a separate issue though - but it did continue through to my re-install which was strange, particularly considering I formatted the HD several times before the re-install.
Anyway, all is working now. Time to move onto my next linux issue - trying to organise a Leadtek DVR3100 H to work with ubuntu on my desktop. ...don't be surprised if you see another thread about this soon :)

~Switcha~

---

### Post by windeguy on 2011-03-07
I am currently using  Ubuntu 10.04 LTS- the Lucid Lynx on an Acer Aspire 9410Z laptop with Realtek audio. 

After a recent normal system update my mic and wireless both stopped working.  I found a way to get wireless back up using my original install disk as a repository and using some files the install disk. 

I have not found a way to get the internal mic to work at all in any program. It does not work with Skype, Google Talk, Ardour, you name it, the mic is disabled. I have re-installed SKYPE with no avail. 

Hopefully there will be a fix for this.

---

### Post by switcha on 2011-03-07
Windeguy,

As my previous comment states, I did a re-install of ubuntu using version 10.10 and now my mic. seems to be working well. Although installing PulseAudio Volume control has helped manage its volume levels.

Perhaps this could be a suggestion for you to resolve your issue.

~Switcha~

---

### Post by windeguy on 2011-03-08
> **switcha said:**
> Windeguy,

As my previous comment states, I did a re-install of ubuntu using version 10.10 and now my mic. seems to be working well. Although installing PulseAudio Volume control has helped manage its volume levels.

Perhaps this could be a suggestion for you to resolve your issue.

~Switcha~

I had been running 10.10 and had problem after a normal update with several things. Then I started from the beginning and loaded the LTS solution. After another normal update, I ran into the Mic problem. Rather than do another re-install of the OS I will continue to find a "rubber band" fix, but thank you for the suggestion.

---

### Post by switcha on 2011-03-08
Good luck with it. As long you understand that the repercussions of rubber band fixes are just that, flexible fixes, and not necessarily the ideal solution.

~Switcha~

---

