---
title: "Lenovo W510 (NTK29MS) - Intel WiFi Link 6200 - random disconnects"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by PugTheBlack on 2010-05-12
Sorry for posting another "Wireless disconnects" post, but I did a search to see if I could find anything about this problem on hardware similar to my own, and didn't find anything. 

Like many other people seem to be experiencing my wireless connection also seem to disconnect from time to time... It's actually starting to get a bit annoying.. 

Running Ubuntu 10.04 x64 - Core i7-820QM CPU - 12GB RAM - Intel WiFi Link 6200 WLAN card, machine is new and my time for troubleshooting has been limited so I haven't really gotten around to see if this is something I can work out myself.. 

Any help or hints are appreciated though, and I will provide info as needed (when I get home from work) 

-M-

---

### Post by peepingtom on 2010-05-12
I've had a pretty good experience with my 6300 in my T510. I haven't read the changelogs to see if this would work, but you should try enabling the backports repositories in synaptic or Software Sources and then install the wireless backports modules.

Also: post the output of dmesg and maybe a smart guy will find a quick fix for you!

---

### Post by PugTheBlack on 2010-05-12
Will do some tests with Wicd instead of NetworkManager too - some people have reported that uninstalling NetworkManager and using Wicd instead has solved the problem for them.. 

-M-

---

### Post by Krsnajinana on 2010-05-12
I have the same problem, but different hardware. I have just installed backports, and I'm waiting to see if it works or not, but until then I'd like to report my experience, because maybe it can help people figure out what the problem is. My wireless disconnects, sometimes all the wireless networks disappear from my network manager, and I can't reconnect until I restart my computer. I'm using an ACER 5520 laptop. I was fine with Karmic Koala, although I remember that very occasionally this problem would appear, like once a month. But now it is very frequent, it could be between 10 minutes or 2 hours, and then it disconnects.

I don't know if it's relevant or not, but when I was using Karmic Koala, I wasn't using Evolution for my e-mail. Now, I have set up Evolution, and also Gwibber. And it seems to me, although I haven't done a really stringent test on this, that when I open these programmes, the problem occurs, or at least occurs more rapidly than it normally does. The other thing I did was set up OpenDNS in order that Gwibber would work properly with Facebook. Basically, what I'm trying to say is that after setting up OpenDNS, Evolution and Gwibber, I really started to notice the problem, although it may be coincidental, and the upgrade may be the real culprit.

Well, having installed the backports wireless files, I am going to open Evolution, and work for a while, and I'm going to see if the problem appears again.

---

### Post by Krsnajinana on 2010-05-12
Installing backports worked really well. I've been going all day, and the connection hasn't dropped once.

---

### Post by aot2002 on 2011-11-23
FYI this happens on same laptop with 6200 with windows 7 as well. Starting to think this is related to the 6200 it's all over the internet with this problem :(

---

