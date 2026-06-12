---
title: "Firewire Questions"
date: 2008-02-25
forum: Mythbuntu
---

### Post by nadolph on 2008-02-25
Hi, I'm new here.

 I've been trying for a couple days to get firewire to work. I have a 6200 STB. The HTPC I'm building is at my fathers house and I have been there a couple times with no success, so I figured I would ask all my questions before I go back to try again. Unfortunately, this means I won't be able to reply quickly with the results of anything.

First, my results:
I'm in Calgary, on Shaw. I've checked the diagnostics and I am certain I should be able to use firewire. 

I have mainly been using the guide on the mythtv wiki as a reference but I wasn't sure if I had to follow all of the steps or not. In plugreport, everything seems good.  After doing the plugctl stuff, I've got firewire_tester to work and get consistent success using both p2p and broadcast. I have not done any test_mpeg2 things. I have not done anything regarding raw1934 permissions. I have set up everything in mythtv-setup, presumably correctly. When I try to watch TV it says tuner 1 is unavailable.

Here are my questions:
0. Have I done anything blatantly wrong based on what I said above?
1. Should I be using 7.10 or 8.04a2 (I've tried both with the same result)? Does it matter? 
2. Assuming the answer to 1 is either, are the instructions to get firewire working the same?
3. What guide should I be following, if any? 

Thank you in advance. I've tried my best to figure it out based on other peoples forum posts and guides, but I want to be sure I've got everything figured out before I go back to try again.

---

### Post by newlinux on 2008-02-25
0. Not that I can think of. Have you added a video source and some channels that aren't 5c protected?
1. It shouldn't matter for firewire. I'm using it on 6.10 :)
2. Should be
3. [https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

Do you backend logs show any errors with the tuner? Do you have it set to start on a non 5c copy protected channel?

---

### Post by nadolph on 2008-02-25
Ive got a video source and all the channels set up. Most of the channels are not 5c protected. I've got it set to start one which is unprotected. But it won't even attempt to tune in far as I can tell. In 7.10 it says all the available tuners are in use, and under info, it says that tuner 1 is unavailable. In 8.04 it doesn't say they're all in use but instead just flashes black and then back to the menu, but it still says unavailable. 

I've read the guide you pointed me to. In the STB diagnostics, it says 1934 port is available but not active. But if it wasn't active, would i still get positive results from firewire_tester?

I haven't been giving firewire ownership to Mythtv, is that the cause of my problems? Its odd that I missed that step, I've done everything else on the guide, aside from priming, which as far as i can tell i shouldn't worry about until I at least have it working.

---

### Post by nadolph on 2008-02-25
I am also wondering, does a firewire configuration allow for the capture of non-digital channels through the STB or do i need a separate capture card for that?

---

### Post by newlinux on 2008-02-25
> **nadolph said:**
> I am also wondering, does a firewire configuration allow for the capture of non-digital channels through the STB or do i need a separate capture card for that?

As long as the channel is not 5c protected and firewire is active you should be able to stream it via firewire. Have you looked at your backend logs when starting your backend and when trying to tune a channel with firewire?

---

### Post by nadolph on 2008-02-25
I won't be able to try until Friday most likely. Thank you for your help.

---

### Post by 4dognight on 2008-02-26
You might want to read my posts on firewire, as I just finished getting it to work on a motorola dch3200. 

To summarize. follow the HOWto, dont skip any steps. (permissions,prime, startup script etc)

NEVER tune to a channel that isnt working(encrypted etc) As myth will be "stuck' on that channel. you will have to change the starting channel in the config to get around it.

Play close attention to which node you setup for  your STB on, in firewire_tester,myth_prime and Myth backend config. It changes on reboots and if you pull out the firewire cable. 

You may want to get the newest version of firewire_tester. Mine didnt have the -R option, which resets the firewire bus.

---

### Post by nadolph on 2008-02-26
thanks, I saw your thread but i didn't want to hijack it with my own problems. :S

---

### Post by majoridiot on 2008-02-26
> **nadolph said:**
> I am also wondering, does a firewire configuration allow for the capture of non-digital channels through the STB or do i need a separate capture card for that?

yes.  you will be able to stream any non-5c, non-encrypted channel via firewire, including the
SD analog channels.

> **nadolph said:**
> Ive got a video source and all the channels set up. Most of the channels are not 5c protected. I've got it set to start one which is unprotected. 

you should be just as concerned with the CCI of the channel as well- the channel can be 5c=0 
but still have CCI set to 0x02 or 0x01 and you will not be able to record it. 

> **nadolph said:**
> But it won't even attempt to tune in far as I can tell...  it says all the available tuners are in use, and under info, it says that tuner 1 is unavailable. In 8.04 it doesn't say they're all in use but instead just flashes black and then back to the menu, but it still says unavailable...  I haven't been giving firewire ownership to Mythtv, is that the cause of my problems?

this is *absolutely* a problem!  if you do not give ownership to mythtv, it can not access
/dev/raw1394 and mythtv will always consider that tuner "unavailable".

> **nadolph said:**
> I've read the guide you pointed me to. In the STB diagnostics, it says 1934 port is available but not active. But if it wasn't active, would i still get positive results from firewire_tester?

on the 6200 series, you probably will not show an "active" connection until there is one.  just having
the cable connected is not considered "active" on those boxes afaik.

> **nadolph said:**
> I haven't been giving firewire ownership to Mythtv, is that the cause of my problems? Its odd that I missed that step, I've done everything else on the guide, aside from priming, which as far as i can tell i shouldn't worry about until I at least have it working.

i repeat quoted this to point out how CRITICAL it is you *both* give ownership of /dev/raw1394 
*and* prime that stb, in order to get a working connection mythtv can use.

if, after setting the ownership, you are still not able to get anything from the stb over firewire, 
then it is likely that the port is not active, in which case your cable company is madated by
law to activate it- so give them a call and let them know that you know that.

---

### Post by nadolph on 2008-02-26
> **majoridiot said:**
> 
you should be just as concerned with the CCI of the channel as well- the channel can be 5c=0 
but still have CCI set to 0x02 or 0x01 and you will not be able to record it. 
I've checked the CCI bit as well, they are all 0.

> **majoridiot said:**
> 
this is *absolutely* a problem!  if you do not give ownership to mythtv, it can not access
/dev/raw1394 and mythtv will always consider that tuner "unavailable".
 
I guess this was my problem then, I'm not sure why I didn't do this. I've been using linux for 6 years, you'd think I would be proficient at following HOWTOs.

> **majoridiot said:**
> 
i repeat quoted this to point out how CRITICAL it is you *both* give ownership of /dev/raw1394 
*and* prime that stb, in order to get a working connection mythtv can use.
 
To clairify, if I'm using p2p, should I be using the myth_prime_p2p script? It says it is for the sa4200hd STB, but I've heard it works for the 6200 for p2p.

> **majoridiot said:**
> 
if, after setting the ownership, you are still not able to get anything from the stb over firewire, 
then it is likely that the port is not active, in which case your cable company is madated by
law to activate it- so give them a call and let them know that you know that.
I've heard many reports from people in my city who have firewire working, so I know the port is active. 

Thank you for your help.

---

### Post by majoridiot on 2008-02-26
> **nadolph said:**
> To clairify, if I'm using p2p, should I be using the myth_prime_p2p script? It says it is for the sa4200hd STB, but I've heard it works for the 6200 for p2p.

yes, that us the script you want.  the script is specific only to the method of priming-
p2p vs. broadcast and not to a stb itself.  

some 6200 series boxes work fine p2p, some not.  mine always worked best broadcast.

---

