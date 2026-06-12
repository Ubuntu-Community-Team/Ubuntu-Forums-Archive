---
title: "Vista Hijacked my NIC?"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by squidward_tentacles on 2006-07-10
I recently installed a dual-boot setup between Vista and Dapper, everything went fine until I booted back into Ubuntu, then suddenly my machine had no connectivity through the onboard NIC interface. I tried manualy setting the IP v.s. DHCP, no luck, couldnt even ping the router...I mounted a live CD , still no connection. 
   At this point I began to suspect hardware failure so I brought another machine over and hooked it up, instant connectivity no problem. Feeling a little perplexed, I booted back into Vista, and the connectivity works fine. Booted back into Dapper, No connection what so ever...the router was assigning with DHCP properly, because after I cleared everything out & choose DHCP again it would activate the eth0 interface and even assign DNS servers, but still no usable connection. At this point I added a new NIC card and Dapper picks it right up and it runs fine...However upon booting back into Vista it finds the new NIC card and wants to install a driver.
I will NOT allow Vista to interface with this card, and it runs fine as long as I plug the ethernet cable into the onboard NIC, Now when I boot back into Dapper, I have to unplug the ethernet cable and insert it into the new NIC card I added to get any type of connectivity....
I am puzzeled as to how M$ managed to "hijack" my onboard NIC and render it unusable to any other OS...anyone ever seen anything like this or have a possible workaround? I am getting tired of switching the ethernet cable ever time I want to switch between OS's. I tried completely resetting the router and everything else I could think of, any help would be greatly appreciated:confused:

---

### Post by Personatech on 2006-07-10
!!??

Wow.  Have you tried installing WinXP in the Vista partition to see what happens?  Whatever the result, this behavior should be reported to Microsoft as being unacceptable.

---

### Post by mozetti on 2006-07-10
Was the new "driver" Vista wanted to install a firmware? If so, maybe it upgraded the firmware to one Linux/Ubuntu doesn't support? That's my only thought on it. Weird problem, to say the least.

---

### Post by Hg80 on 2006-07-10
> **mozetti said:**
> Was the new "driver" Vista wanted to install a firmware? If so, maybe it upgraded the firmware to one Linux/Ubuntu doesn't support? That's my only thought on it. Weird problem, to say the least.

Still if this is the case Vista shouldnt be allowed to update a firmware without User input incase it screws it up!

---

### Post by jferrando on 2006-07-10
I can't believe it. It this is true, this information should be widespread, and warn people about Vista, new Microsoft's weapon of evil.

In my 1990s at Valencia's University in Spain, Microsoft was very popular because people like me who could not afford a Mac had a graphical environemt in the PC. Then they destroyed competition, first Lotus1-2-3 and Wordperfect, then Netscape, then ... Now it has became a dangerous "virus", that restricts freedom and binds us with chains... let's fight for our freedom. No more monopolistic Microsoft!

---

### Post by squidward_tentacles on 2006-07-10
Oh, its true....The firmware update sounds like the most logical explanation, However I have read in the forums where other people have set up a dual-boot between Dapper & Vista w/out any thing like this occuring. The machine in question is an AMD Sempron 3400+ , this seems nearly as insidious as Sonys root kit. I dont know how :evil: M$:evil:  pulled this off, but its pretty crappy, look like im stuck switching the ethernet cable at every reboot is my only solution for now...

---

### Post by garoo on 2006-07-19
I'm having the same problem since I installed XP. I had Dapper working fine on the first drive, installed XP on the second. I went back to Dapper for a few days, all good. Finally had time to install NIC drivers on the XP install and it worked fine. Booted back over to the Dapper and it doesn't work at all. No DHCP, not thru static. I can see packets going out but the router ignores them. Boot back to XP and it works great.

I ended up tossing in my spare NIC and just disabled the onboard. Still a pain though. Asus with an nvidia based NIC.

---

