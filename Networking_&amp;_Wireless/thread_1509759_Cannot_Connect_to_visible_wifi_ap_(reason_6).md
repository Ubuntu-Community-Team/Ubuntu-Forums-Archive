---
title: "Cannot Connect to visible wifi ap (reason 6)"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Geneset on 2010-06-14
Hi folks, there seem to be alot of the same questions that dont give any information. I'm travelling currently so the last network i connected successfully to was my home wpa-psk network. I hadn't tried anything until i got to my accommodation that is an open network (that I'm on now on the Win7 partition on my laptop).

The network (and a similar archetypical 'linksys' open network, aswell as some protected local networks are correctly displayed in network-manager and upon selection, it happily spins around to its hearts content for a while before saying 'no chance boy'.

/var/log/syslog spills out the usual combination of wpa_supplicant and kernel messages, the most interesting of are that the kernel deauthentication reason 6 response. 6 apparently means class2FrameFromNonAuthStation...Client attempted to transfer data before it was authenticated.

Anyone seen anything like this? I've already tried going closer to the router to no avail. I don't remember seeing this any other time I've connected to a open AP, even if that AP is far away. (Signal strength for this AP is good, kismet says its around -57dBm, well above the threshold of -80dBm.

---

### Post by SaintDanBert on 2010-06-14
I have similar troubles when I'm gone walk-about.  I cannot comment about the "reason 6" details, but would like to know what that all means...

I found that I could use the win-dose side, get wifi connected, and then dance with the typical hotel/motel "use our network" web page
-- asks room number, or spews local adverts, or (shudder) asks for money. This almost always works straight away.  Linux connections don't seem to happen with similar ease.

[highlight]However[/highlight], once I've danced with win-dose, I found that in many cases I could connect with linux until the overnight refresh that many hotels enforce when the connection bounces.

I can only surmise that the access point and my hardware address become known good after win-dose use and then linux is able to do its thing. {That is all a guess on my part.}

COMMENTARY: Trouble shooting basic network troubles remains a blackest arcane art. The logs have too much chatty jargon that is meaningful only to bit-heads and super-geeks. Couple that with the large list of small parts that combine to make things happen and the road warrior has little chance beyond the mini-fridge ... and automatic, event-driven only makes things harder to find and follow and adjust.

~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-06-14
see [http://ubuntuforums.org/showthread.php?p=9461238#post9461238](http://ubuntuforums.org/showthread.php?p=9461238#post9461238)

---

### Post by Geneset on 2010-07-04
No go Dan; its literally on open router connected to an ADSL line; no fancy access control :D

I will try the WICD route tomorrow if i get a chance.

Thanks!

---

### Post by Geneset on 2010-07-07
After trying the wicd idea, it appears that its a signal to noise problem, as if I'm standing right by the AP, it works perfectly well. 
I'll admit that the environment that I'm working in is very noisy, but that doesn't explain why windows has no problem connecting from 2 floors up but Ubuntu can barely operate withn 15 ft!

---

### Post by Geneset on 2010-07-08
I solved this using the compat-wireless drivers, write up [here]("http://goo.gl/fb/93hJP"). Thanks!

---

