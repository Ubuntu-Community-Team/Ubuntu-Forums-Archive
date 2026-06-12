---
title: "USB Wi-Fi Adaptor for MAC Address Change"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by kirb3 on 2010-06-10
My laptop has an internal Broadcom wireless adaptor.  It works fine for basic Internet access, but I cannot change the MAC address with ifconfig.  I would like to be able to change my MAC address.  Since this is a laptop, the only option for me to do this is a USB wireless adaptor.  But compatibility is very hit-or-miss.  I've already tried two USB adaptors that had been stated to be compatible with Linux, and while both worked for basic functionality, neither allowed me to change the MAC address.

For whatever reason, this information seems very, very difficult to find.  I have spent upwards of ten hours cumulatively searching forums (including this one) and other resources, and have found only vague, outdated, or outright false information regarding USB adaptors that support this.  I believe I will be doing a great service to other users like myself by getting this question directly and conclusively answered for once, and the more responses, the better.

Questions:

Do you have (or know of) a USB wireless adaptor that actually allows you to change the MAC address?

If so, what is the specific brand and model number, and what steps were necessary to install the drivers?  (Even posting just a link or brief summary would be helpful.)

Preferably something cheaper than $60, but honestly I've already expended so much time and frustration on this by now that I could hardly care less what it costs.  Ideally something that can be purchased from a physical store as opposed to online in case something is screwed up and I have to return it, but again, any information is better than none.

Thanks for viewing!

---

### Post by kirb3 on 2010-06-11
Bump!  I know this is an issue a lot of people have had trouble with -- I even know a couple personally.

Surely there is at least one USB wireless adaptor that allows you to spoof its MAC address through ifconfig.

---

### Post by pricetech on 2010-06-11
Honestly, I can't think of anyone who would want to spoof a wireless MAC address for anything other than malevolent reasons.

---

### Post by cariboo on 2010-06-11
> **pricetech said:**
> Honestly, I can't think of anyone who would want to spoof a wireless MAC address for anything other than malevolent reasons.

+1, if the op can't come up with a compelling reason, this thread will be closed.

---

### Post by kirb3 on 2010-06-12
Privacy.  I don't like the idea of having my university track my every move online.  I'm not trying to hack into someone's network -- if I cared that much I'm sure there would be other approaches possible, such as buying a cheap laptop with a compatible card and using any one of the myriad other MAC-spoofing threads on this forum for instructions.

Aside from privacy reasons, I've heard of people wanting to be able to avoid 20-minute delays from their ISPs when switching between devices, doing network testing, etc.  Wanting to spoof a MAC address is hardly prima facie evidence of ill intentions.  This isn't just a personal request -- as I mentioned, I've spent a lot of time looking for this information, which makes me suspect that other people might also be searching for it.

Lastly, there are tons of threads here about changing MAC addresses.  It's clearly not an unusual request, nor is that information terribly difficult to find.  There are just none that I can find about doing so specifically with a USB adaptor.

Examples:

[http://ubuntuforums.org/showthread.php?p=9443910]("http://ubuntuforums.org/showthread.php?p=9443910")
[http://ubuntuforums.org/showthread.php?t=1348058]("http://ubuntuforums.org/showthread.php?t=1348058")
[http://ubuntuforums.org/showthread.php?t=1478937]("http://ubuntuforums.org/showthread.php?t=1478937")
[http://ubuntuforums.org/showthread.php?t=1168210]("http://ubuntuforums.org/showthread.php?t=1168210")
[http://ubuntuforums.org/showthread.php?t=94891]("http://ubuntuforums.org/showthread.php?t=94891")
[http://ubuntuforums.org/showthread.php?t=1319981]("http://ubuntuforums.org/showthread.php?t=1319981")
[http://ubuntuforums.org/showthread.php?t=1437632]("http://ubuntuforums.org/showthread.php?t=1437632")
[http://ubuntuforums.org/showthread.php?t=1433877]("http://ubuntuforums.org/showthread.php?t=1433877")
[http://ubuntuforums.org/showthread.php?t=1426083]("http://ubuntuforums.org/showthread.php?t=1426083")

I hope this helps clarify things a bit -- I realize I left out some information in my initial post.

---

### Post by kirb3 on 2010-06-12
Bump!  As I've stated, I want to do this for perfectly legitimate reasons, and there are tons of threads for using internal wireless adaptors -- just none for USB hardware specifically.

I'm relatively sure someone has at some point spoofed a MAC address on a USB Wi-Fi adaptor, so there must be answers out there.  If you've done it, what brand/serial number adaptor did you use?

---

### Post by pricetech on 2010-06-13
If there were that many people doing it, whatever the line of reasoning, there would be solutions.

Check the manufacturer's website for information about the adapter you have.

Your wireless router has the MAC your ISP is looking for, not your NIC.

---

### Post by kirb3 on 2010-06-13
Yes, that's what I had hoped, but I didn't see much unfortunately.  Otherwise I wouldn't have started a thread.  Manufacturer websites haven't mentioned ifconfig MAC spoofing compability on Ubuntu -- it's a rather narrow topic given that most people are primarily worried about whether a given adaptor will allow them to access the Internet using Linux at all.

Ordinarily, yes, the ISP would be interested in the router MAC and anyway activity would be traceable from the switch port on the other end.  However, since I'm at a university, the university owns the routers and individual activities would be tracked by NIC MAC addresses.  Ergo, spoof the NIC MAC and privacy is restored.

If you are reading this post and you have a USB wireless adaptor, would you please run the following for that interface and post the model number, whether the operation succeeded, and whether you could connect to the Internet afterward?

[INDENT]```
sudo ifconfig <interface name> down
ifconfig <interface name> hw ether <new MAC>
ifconfig <interface name> up
```[/INDENT]

It should take maybe 30 seconds max, and you'd be helping to collect data on an apparently very little-known issue.  Thanks!

---

### Post by pricetech on 2010-06-15
Sounds like a dandy research project.  Purchase numerous USB wireless adapters and try each of them to see which ones will allow you to change the MAC and still function under Ubuntu / Linux.  Then post the results for the benefit of others.

---

