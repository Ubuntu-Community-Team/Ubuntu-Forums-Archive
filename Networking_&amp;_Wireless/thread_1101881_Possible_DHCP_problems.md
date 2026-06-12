---
title: "Possible DHCP problems"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by amurphy96822 on 2009-03-20
New to Ubuntu and love it.  Some trouble getting my Intel Wireless Pro card working, now here seeking knowledge.  I generally use my HP Pavillion laptop in my bedroom, which is a couple of walls and a lot of junk away from the router. What is interesting is that once I have it connected, it works fine, as now. But I never can get it started (for instance if I reboot); I have to unplug the laptop, walk out in the hall and down the hall to make visual contact with the router.  Then it usually connects although it takes a while and sometimes I have to click the network icon a couple of times.  I do not know much linux, but I assume when I click it, it starts some kind of script like network restart or similar; and that script consults the information in dhclient.conf file.  If so, is there some way to edit that file to make it work better? Or am I off on a wild goose chase (or do I have to remove the junk in the loft between me and the router?

So the mystery is why so hard to connect but works so well once connected. Aloha

---

### Post by amurphy96822 on 2009-03-31
This is really not a reply, just more information; i hope someone is listening out there. Have gone back to Hardy Heron since the tools seem to work better.  Thought I had a solution: went to my netgear router admin and disabled dhcp, went to laptop and disabled "roaming", installed fixed IP etc., and voila, automagically it connected and worked. Was able to browse the web etc.. Then, next time I booted, did not work, could not make it work.  Whassup? Also it gave my WinVista (dual boot on laptop in bedroom) fits, could not figure out how to assign a fixed IP to it, so had to go back to enabling dhcp on both sides.  

With all the brains out there, surely there is some reason why it cannot connect via dhcp in my bedroom, can connect (sometimes with multiple tries line of sight), but once connected works great in my bedroom. ?Some kind of Netgear>Intel communication issue? Help.

---

### Post by amurphy96822 on 2009-04-11
Solved:  hope someone sees this solution; took me forever to find it; the solution to my wireless laptop problem was a fixed IP, and it needed to be outside the range of my assigned DHCP addresses; that was the trick, once I assigned an IP outside of the dhcp range, it worked perfectly and I was able to connect every time. Someone should put this on the regular Ubuntu how to.  Aloha

---

### Post by iponeverything on 2009-04-11
I am glad that you posted your solution so that its here for others to find.

---

