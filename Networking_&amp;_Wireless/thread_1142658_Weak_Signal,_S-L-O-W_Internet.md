---
title: "Weak Signal, S-L-O-W Internet"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by Iosys on 2009-04-29
I've seen this problem around online but have not seen any good fixes, so I'll try here.  I could totally be missing something, and if so I apologize for posting a common question.  Quick specs: I have a desktop PC running Jaunty 64 bit and I also have Windows XP still installed since I had it first and am still learning Linux/Ubuntu.  In XP, my wireless card connects to the network no problem - wireless G, 54mbps, strong signal (the router is in the same room with the computer), just quick, as it should be.  In Ubuntu, however, the signal shows only one bar and the connection is terribly slow, so much so that I end up using a wireless B bridge that is normally reserved for my Xbox 360.  If I have to get a bridge, that's fine I guess, but I would like to see the wireless work. 
 
The card is an Encore ENLWI-G
The router is a Linksys WRT54G
 
I downloaded and (I think) installed the Linux driver from the Encore site in case it would do a better job than the default driver Ubuntu used, but no dice.  Does anyone have an answer to this issue?  Bear in mind I'm a noob but willing to jump into the terminal if someone can point me in the direction of what to do.  I want to learn Linux and Ubuntu as a flavor as much as possible, but being new I'm not much use on my own!  Thank you muchly in advance for any help!

---

### Post by Kobalt on 2009-04-29
Your wireless card is based off a Marvel 8335 chipset, this could help you : [https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

### Post by Iosys on 2009-04-29
Wow, thanks.  I'll check this out as soon as I get home and see if it does the trick.  Mine's the 64-bit, so I see I need a specific driver that's known to work.  Thanks for the pointer!

---

### Post by Iosys on 2009-04-29
Well, according to what I'm seeing, it's Realtek.  I found a page showing level of support and it was in the yellow, saying that some are supported.  So, I still don't have an answer at this point, doesn't look like.

---

### Post by tjazar on 2009-05-03
Well, I'm having the same problem as Iosys, only the wireless adapter in question is the Encore ENUWI-G2 USB adapter.  A connection is made in Ubuntu, but the signal is at best half of what I got in XP, and the connection tops out at about 1kb/s.  Ugh.  I've tried ndiswrapper, but I keep getting error messages.  So, any help for Iosys may help me too!

---

### Post by thismuchiknow on 2009-05-04
.

---

### Post by thismuchiknow on 2009-05-04
Can someone help me? I have installed ubuntu 9.04  and have now suffered this problem of a weak wireless signal and slow internet. I saw on another forum that I should alter the 'bitrate' but i dont know what that means.

Like the poster above, I'm not very familiar with ubuntu and am not a techie, and I cannot find the solution to this anywhere! I want to make Linux work for me but am becoming disheartened!!

---

### Post by smoothcne on 2009-05-09
[B]Hi folks, just didn't want to be left out. I just built a brand new Athelon 64bit X2 machine with a WMP54G ver.4 wireless card that gets 98% signal strength with XP and Vista and only 47% with 1Kbps throughput on 9.04 64bit Ubuntu installed. 

Can someone that's more into Linux than myself help us?

THanks,
Smooth
[/B]

---

