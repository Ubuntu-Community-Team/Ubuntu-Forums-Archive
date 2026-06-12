---
title: "Ubuntu 9.04 only connects to unprotected networks"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by jesermay on 2009-05-16
Hey,

I love it that my wireless card finally works with ubuntu, thanks everyone who has made it possible! 

I do have an issue however. It will only connect to unsecured networks. My Mac and my Windows machine work with my router fine when it is protected but not linux. I have set my router to all the different WPA options and WEP but none of them work with linux. I have to use unprotected for it to work. I have the EW-2278IN Wireless card and the DIR-635 Router.

Please help me, I dont want to use unsecured :P

From,

Jeremy

---

### Post by jesermay on 2009-05-16
Any help would be appreciated...

---

### Post by jesermay on 2009-05-19
...

---

### Post by jsternberg on 2009-05-19
Same problem with 8.04, since some kernel upgrade in January. Have tried 8.1 and 9.04, same problem. Nobody seems to help. Something about the encryption. I tried everything you did, same strange conversion to hex values of ascii key. Wish someone had clues....

---

### Post by t0mppa on 2009-05-19
@jsternberg: To get help on the password keeps getting converted to hex value problem, take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1010650").

@jesermay: [Here]("http://ubuntuforums.org/showthread.php?t=571188")'s a generic thread for configuring your wireless from the command line to get through WPA encryption.

---

### Post by jsternberg on 2009-05-19
Thanks for the tip about that thread on the hex appearing. As it happens, before I saw your reply, I miraculously was able to resolve the issue somehow, after months of trying. I read a lot of posts and hints about my hardware combination (Intel 3945abg), and cannot remember exactly what I did, but I suspect it involved installing linux-backports-modules-hardy (I'm still on 8.04) and associated files (using Synaptic). Then I tried installing wifi-radar as an alternate network manager, and fiddling with Network Manager (the app) to disable it so I could enable wifi-radar. I tried changing from "roaming" mode via manual configuration to connect directly to my home network, which didn't work, with either network application, so I gave up on wifi-radar, and then set Network Manager (the app) back to Roaming mode, and decided to forget the whole thing. Imagine my surprise when looking back at screen, I saw the bars on the wireless icon were all blue! The wireless is working again. I've rebooted twice and it's still working, and doesn't ask for password anymore (seems to finally accept the non-hex version the way it used to, automagically). I'm still dazed by this semi-accidental success, and wish I could tell you what actually worked, but I don't know enough about Linux to do so. My hunch is the combination of installing the backports (whatever those are), plus disabling Roaming and then re-enabling Roaming in the Network Manager app, somehow did the trick. I hope others can have similar success, no matter what the version.
Happily,
jsternberg
Dell XPS M1330N
Ubuntu 8.04 (hardy)
Intel PRO/Wireless 3945ABG (rev 02)

---

### Post by cgb223 on 2009-05-19
thats weird because im having the exact oppisite problem i cant connect to unprotected wireless networks wether they are local or connected to the internet, I have an acer 7720 laptop. HELP!!!

---

### Post by t0mppa on 2009-05-19
> **jsternberg said:**
> My hunch is the combination of installing the backports (whatever those are), plus disabling Roaming and then re-enabling Roaming in the Network Manager app, somehow did the trick.

Backports are essentially fixes that were done for latter versions of software than you have currently installed. For instance, suppose that the hex conversion problem was fixed on network manager 0.8, the fix could then be backported to version 0.7 as well.

[QUOTE=cgb223]thats weird because im having the exact oppisite problem[/QUOTE]

So, you can connect to WEP/WPA secured networks then?

---

