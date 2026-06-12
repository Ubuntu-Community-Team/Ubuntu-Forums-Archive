---
title: "networks problems with a Dapper clean install"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by pistoncito on 2006-05-29
Hi, i installed today the Dapper on my AMD64 machine. The live CD works perfectly, and i can chat when the ubuntu was installing. But, when rebbot with the new ubuntu installed, the network interfaces doesn't work. Recognized the two interfaces, but none of they connected via DHCP with the modem.

I read someone else have problems with it, but i don't know if he could fix it. Is there a problem with the dhcp-client?

Thanks in advance.

---

### Post by fabiomb on 2006-05-29
the same problem here: [http://www.ubuntuforums.org/showthread.php?t=182618&page=2](http://www.ubuntuforums.org/showthread.php?t=182618&page=2)

but no answers :(

---

### Post by Pyro MX on 2006-05-29
I don't know if that trick works in Dapper, but what I did (because I had a problem with DHCP in 5.10), you put your settings (not the router, your computer) in static IP, manually add the gateway, the subnet mask and the DNS (all this info can be accessed trough the router's admin panel usually) and put your IP to a number that is outside the router's DHCP range. For examples, I used 192.168.1.**50** . But no other machines must run with static ip on the netowrk. Try it out!

---

### Post by pistoncito on 2006-05-30
No, it didn't work for dapper, almost in my installation. I tried again with the live CD, but this time doesn't work. I don't know which was the problem. Maybe the final release could fix it.

---

### Post by Pyro MX on 2006-05-30
You said you had 2 network interfaces. Which one of the two are you using? Wired? Wireless?

---

### Post by christian.convey on 2006-05-30
What is your ethernet adapter's chipset?  In my case the chipset's driver seems to have a regression.  lspci give the following info about the chipset I have that runs into trouble:

Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

I was able to work around the problem by using a different ethernet adapter.

---

### Post by pistoncito on 2006-05-30
I had two ethernet cards (one onboard). I take off the other network card and now is working. With IP static (like somebody tld me) and with DHCP.

Thanks

---

### Post by pistoncito on 2006-05-31
Yesterday works fine, but today, with the reboot, it doesn't work anymore. I can't configure again. Somebody found the solution?

Thanks

---

### Post by jakenn-linux on 2006-06-01
[QUOTE=christian.convey]What is your ethernet adapter's chipset?  In my case the chipset's driver seems to have a regression.  lspci give the following info about the chipset I have that runs into trouble:

Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

I was able to work around the problem by using a different ethernet adapter.[/QUOTE]
Boy was I glad that I came across your posting.  I've been trying for weeks to figure out why my network wouldn't work correctly.  If I used the liveCD network was fine, if I went back over to WinXP the network was fine; but trying to run the installed version (even with all the updates that have come out) it wouldn't.  I did find out that I could get temp network connection by taking out the network cable and putting it back in.  Then I'd have network for a few minutes.  Then I would have to do the "procedure" again.  Got rather tiring when you had a lot of updates to download.

I tried a number of the suggestions like they mentioned here (static IP), but none of that worked.  Someone locally said something about the NIC but since the liveCD and WinXP worked fine, I just didn't think it would be the NIC.

However, I have the exact same chipset as you.  So I guess it is the NIC.  I was just about to install OpenSuSE to see it that worked, but I really want to be able to use Ubuntu.  What did you get to replace your NIC?

John

---

### Post by christian.convey on 2006-06-01
My work computer has no other ethernet adapter, so I'm simply not going to run Dapper on it until the issue gets fixed.

My home computer has the ethernet card in question, but also an nForce-4 motherboard which has built-in ethernet.  (I wasn't using the nForce ethernet when I had Breezy installed because Breezy didn't have a driver for it.  That's why I installed the now-problematic NIC in my home computer.)  Anyway, the nForce adapter now works under Dapper, so I got lucky.

---

### Post by raublekick on 2006-06-01
so it's the DAVICOM stuff that doesn't work? awesome... i can't afford a new ethernet card right now :(

---

### Post by TimJ on 2006-06-01
Is there anyway of checking what network cards will work? It's not a great work  around but scrounging a new network card might fix thing.s

---

### Post by pistoncito on 2006-06-01
The nVidia onboard ethrnet adapter doesn't work for me. Yesterday works, but no more. I unplugged and re plugged but nothing. Maybe i will install the final release.

---

### Post by HolyMurderer on 2006-06-01
I'm having the same problem. Specifying manually IP, subnet mask and gateway worked, but I already have my router setting my network card's ip address by dhcp, using static IP through the mac address, so I prefer automatic IP and gateway, that static...

So if anybody has a solution, I would really appreciate it.

---

### Post by pistoncito on 2006-06-01
I haven't a solution. But, at least i haven't a rationale solution. I connected again the davicom card, work with the live CD, but not with the nstall. I plugged to the nVidia ethernet, run manually DHCP and now work. But i don't know how much time.

Something is wrong. Somebody knows is working well with the final release?

---

### Post by phoenix_1983 on 2006-06-01
[QUOTE=pistoncito]The nVidia onboard ethrnet adapter doesn't work for me. Yesterday works, but no more. I unplugged and re plugged but nothing. Maybe i will install the final release.[/QUOTE]

I've got the same issue.  nVidia onboard ethernet that was working under breezy with Static IP assigned through Mac addresses on a D-link g604T wireless router. Breezy didn't auto configure the gateway so I had to manually enter the DNS everytime i wanted to get onto the internet.

Still i installed DApper this morning and no joy... not a cracker...  i'm a bit of a newbie so help please...

---

### Post by raublekick on 2006-06-02
well, i solved it for myself by nabbing a card from one of my dad's old junk machines... not exactly the best solution though :\

---

### Post by christian.convey on 2006-06-02
I've been having no problem at all with my nVidia adapter.  Here's my "lspci | grep -i ethernet" results:

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)
0000:01:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

---

### Post by h3h_timo on 2006-06-02
here ya go:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

works like a charm for davicom adapters!! good luck!

---

### Post by astrauss on 2006-06-03
Anyone come across a solution for Realtek onboard ethernet (on Gigabyte mobo)?

---

### Post by jakenn-linux on 2006-06-03
[QUOTE=raublekick]well, i solved it for myself by nabbing a card from one of my dad's old junk machines... not exactly the best solution though :\[/QUOTE]


I solved it by buying a new NIC.  Things working great.  Bought it before the posting for the fix.  Would almost put the Davicom back in to see if I can get the fix to work.  But while things are working with the new NIC, I'll stick with it.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by astrauss on 2006-06-04
OK, so I solved mine by removing the PCI WIFI card I had in the same PC

---

