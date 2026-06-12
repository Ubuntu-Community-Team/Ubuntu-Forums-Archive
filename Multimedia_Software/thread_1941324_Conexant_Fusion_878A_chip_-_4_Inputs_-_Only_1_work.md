---
title: "Conexant Fusion 878A chip - 4 Inputs - Only 1 working"
date: 2012-03-15
forum: Multimedia Software
---

### Post by volbug on 2012-03-15
I'm trying to get a 4 port video capture card to work in Ubuntu 10.04. I've tried looking around online to find something to get me on the right track but haven't found a solution yet. Here's what I know:
 
Its a single Conexant Fusion 878A chip with 4 video inputs. I purchased it from ebay for about $30 and I don't see a manufacturer's name on it. When I view it in either ZoneMinder or Xawtv it displays video from channel 0 but not from 1-3. On channels 1-3 I get a blue screen and ZoneMinder will report fps so I think that the computer see's the input but just is not processing it correctly.
 
I have the card setup in the /etc/modprobe.d/bttv.conf file as card=77 and have tried it with several other card=## with no luck. I do not have a modprobe.conf file. There are dip switches on the card but changing them seems to have no impact on anything.
 
On a different installation of Ubuntu (cannot remember if it was 9.x or 11.x) it was showing video on all 4 channels but in 10.04 I cannot get anyhting but channel 0 to work.
 
Any help would be greatly appreciated.
 
I found a post where someone else solved a similar sounding problem but I cannot follow what it means if someone with more linux experience can help me out.
[http://www.zoneminder.com/forums/viewtopic.php?f=21&t=16674&hilit=Conexant+Fusion+878A](http://www.zoneminder.com/forums/viewtopic.php?f=21&t=16674&hilit=Conexant+Fusion+878A)

---

### Post by ctimbrell on 2012-06-22
i have the same problem too. i have a similar bt878 capture card that works with card type 150 but the new one wont work on that number.

Did you or has anyone got a solution to this or can offer help on identifying what the card number should be

ps the card you have pictured is identical to mine

---

### Post by Zulu-Zeffir on 2013-04-09
I know your post is over a year old but perhaps try these settings in /etc/modprobe.d/bttv (if the file doesn't exist create it):

options bttv gbuffers=16 card=131 tuner=4 radio=0 triton1=0 vsfx=0
alias char-major-81 bttv

I have the same conexant fusion bt878a chip that you are describing and this worked for me.

---

### Post by aliexpress on 2013-10-07
I'm having this same problem. I got it from Videosecu

---

### Post by oldos2er on 2013-10-07
Hi aliexpress, since this is a fairly old thread, please start a new one, and give full details of your problem including Ubuntu version, etc.

Closed.

---

