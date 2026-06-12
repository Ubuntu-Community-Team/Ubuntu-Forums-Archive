---
title: "Channel listing scripts"
date: 2011-10-30
forum: Mythbuntu
---

### Post by trippy21 on 2011-10-30
Hi Guys
Have built my first ever Mythbuntu box (using 64 bit 10.10) this weekend and am progressing well, especially with the all the info posted on this site. But i have finally become stuck and can't work something out, please help. This is my first time using Linux so i think i'm missing something obvious.

So i have everything setup and working. Last night i got Freeview working and this morning after realising the firmware for my HVR4000 was not loaded properly got the Freesat working also. Having run a channel scan on both frontends of the tv card i would like to sort my channel lists in to one neat list, combining the common channels of Freeview and Freesat. I found this page [http://www.mythtv.org/wiki/UK_Channel_Assignments](http://www.mythtv.org/wiki/UK_Channel_Assignments) which gives the details of a script that will do the job, but i can't work out how to get the script on to my pc and run it. It has something to do with SQL which i've never had any dealings with before. So if anybody can offer an idiots guide as to how to take the script from the website and make it run on my machine i would be most grateful.

My setup is: 
Gigabyte M85M-US2H MOBO
AMD Athlon X2 5050e
4Gb Ram
60gb drive with dual boot with windows 7 (Win 7 will go and a bigger drive put in once i've convinced the wife this is as easy to use as Sky+)
Hauppauge HVR4000 TV card

---

### Post by Kronalias on 2011-10-30
I don't know whether this will help, but I've developed some scripts - really for my own use - that seem to do what you want.

They're on Launchpad here:
[http://bazaar.launchpad.net/~kronalias-beebotron/+junk/trunk/files/head:/my-channels-trio/]("http://bazaar.launchpad.net/%7Ekronalias-beebotron/+junk/trunk/files/head:/my-channels-trio/")

They handle Freeview and Freesat channels, and provide a way to list, rename, and renumber your channel lineup.

The trio are benign - as in they won't write to your database unless run with a -xqt switch - so you can play with them quite safely if you fancy a go.

Please post back here if you need any further info.

Cheers, K

---

### Post by trippy21 on 2011-10-30
Thanks for the scripts. will give them a try this week. I'll post again if i need any hep.

---

