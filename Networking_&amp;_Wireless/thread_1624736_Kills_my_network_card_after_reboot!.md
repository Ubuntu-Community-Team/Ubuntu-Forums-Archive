---
title: "Kills my network card after reboot!"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by rob444 on 2010-11-18
Hello!

I recently downloaded and installed Ubuntu LTS through wubi.
So now I have both Windows 7 and Ubuntu.

When I got into Ubuntu the first time everything worked except the network. I checked everything and Ubuntu detected my onboard network card just fine. I couldn't figure out what the problem was, it was like the cable was unplugged.
After a few hours of tampering with no success, I decided to boot back to Windows 7 so I would be able to google around about my problem. That's when I noticed Windows said that my cable was unplugged. So I decided to check my cable in my end and up to my router's end and everything looked OK.
I had no idea what the hell was going on so I tried the cable on my older machine and the cable was fine!
Then it occurred to me that Ubuntu must have left my network card in a weird state so I powered off my machine and then booted it back up. The problem was still there. So I powered it down again and cut the power. I powered it up after there was no more power in the motherboard (there's a red LED light on the motherboard) and I got into Windows and it could detect my cable again.
I thought it was odd so I tried to reproduce the error by booting Ubuntu again and Ubuntu didn't boot this time, it threw me into a console and I just typed reboot and tried again, and it worked this time.
When I got into Ubuntu I had a working network connection, I was reminded of all the hours I spent trying to fix it and chuckled a bit.

So it all works now but the problem is still there. So I have to shutdown and cut the power everytime I want to have my network card detect the cable in Windows.
Odd but a bit annoying, you guys heard of something like this before?


My motherboard is a  Gigabyte GA-P55A-UD3 with a RTL8111E chip.

Thanks :)!

---

### Post by bcbc on 2010-11-18
> **rob444 said:**
> Hello!

I recently downloaded and installed Ubuntu LTS through wubi.
So now I have both Windows 7 and Ubuntu.

When I got into Ubuntu the first time everything worked except the network. I checked everything and Ubuntu detected my onboard network card just fine. I couldn't figure out what the problem was, it was like the cable was unplugged.
After a few hours of tampering with no success, I decided to boot back to Windows 7 so I would be able to google around about my problem. That's when I noticed Windows said that my cable was unplugged. So I decided to check my cable in my end and up to my router's end and everything looked OK.
I had no idea what the hell was going on so I tried the cable on my older machine and the cable was fine!
Then it occurred to me that Ubuntu must have left my network card in a weird state so I powered off my machine and then booted it back up. The problem was still there. So I powered it down again and cut the power. I powered it up after there was no more power in the motherboard (there's a red LED light on the motherboard) and I got into Windows and it could detect my cable again.
I thought it was odd so I tried to reproduce the error by booting Ubuntu again and Ubuntu didn't boot this time, it threw me into a console and I just typed reboot and tried again, and it worked this time.
When I got into Ubuntu I had a working network connection, I was reminded of all the hours I spent trying to fix it and chuckled a bit.

So it all works now but the problem is still there. So I have to shutdown and cut the power everytime I want to have my network card detect the cable in Windows.
Odd but a bit annoying, you guys heard of something like this before?


My motherboard is a  Gigabyte GA-P55A-UD3 with a RTL8111E chip.

Thanks :)!
try this link [http://ubuntuforums.org/showthread.php?t=1548422](http://ubuntuforums.org/showthread.php?t=1548422)

---

### Post by rob444 on 2010-11-18
Wow! Sweet find!

I'll give this a try when I get home from work.

Thank you!

Solved!

Thank you :).

---

