---
title: "Surf's Up! and down :-("
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by 3.2.1 Penguins on 2005-12-14
Hello,

It's the weidest thing.  Some pages I can go to sometimes.  I got here!  But sometimes I can't.  Some pages I can't get to at all.  I'm running Gnome in Ubuntu 5.10.  I can Ftp, I've downloaded programs from add applications.  I can ping Yahoo! from terminal, but I can't surf there.  I can't get to Google, nor search from the toolbar.  E-mail won't work either.  I have DSL and a Linksys BEFSR41 between my computer and the DSL Modem.  I'm using Mozilla Firefox that came with Ubuntu.  It's weird.  Any suggestions???

Thanx and,

MERRY CHRISTMAS!

---

### Post by imrumpf on 2005-12-14
Try unhooking the router and plugging your ubuntu system directly into the internet. If things work that means that there is a problem with the router. I was going to suggest port forewarding or something similar to that to see what happens.

---

### Post by 3.2.1 Penguins on 2005-12-14
Oh Yeah... I forgot to mention that I tried taking the Linksys out of the loop with no change in performance.  I even rebooted with Linksys out of the loop with no change.  I've reinserted it into the loop with no change in performance.    I read somewhere else on this forum (I believe) about finding the router's address and pinging that, and pinging IP addresses on the net, and pinging web URLs.  All the pings check out!  The poster said if all is well in terminal, the problem is probably the program.  In this case, Firefox and the e-mail program.  However, I have changed, rechanged, and put back all kind of settings in Firefox with no change, so I don't know.  Ubuntu also wiffed on my sound card, and it took me two days to get Ubuntu to "see" my video card.  The good news is, the dual boot is working beautifully, so my Windows set-up is still working great.  Plus, all these Linux problems help me to learn!  (right?)  :smile: 

Thanx again for any help from the brain trust!

---

### Post by imrumpf on 2005-12-14
I had a few other suggestions:

1) Did you try installing a different browser such as opera or mozilla? Doubt it would help but doesn't hurt to try.

2) For the life of me I cannot find the post where I read this but there was an example somewhere of a person who used ubuntu at school and he got blasklisted because the windows servers didn't recognize the ubuntu protocols, and automatically assumed there was a virus, as thing's "weren't right" for the Windows Servers. A quick call to the IT dept. fixed the issue. Maybe call your ISP and tell them what you are experiencing, as it could very well be that you are on some sort of blacklist.

Quick question...does everything work fine as far as the internet with windows? if so that would be a better supporting argument for #2 mentioned above.

---

### Post by 3.2.1 Penguins on 2005-12-14
Thanx for the idea!  I will call Quest Communications and see if they have any suggestions.  Yes, the Internet is working great in Windows, so #2 is more likely.  To support that even more... after I pinged Yahoo! and then tried to surf there in Firefox, I got a "connection refused" from Yahoo!.  I was thinking they didn't appreciate the ping, recognized my IP Address, and refused me.  Maybe it's part of an Ubuntu looking like a virus thing.  However, to refute that, sometimes when I surf here, I'm in right away.  Other times I have to wait, or even close the browser and try again...  Things that make you go hmmmmm.

Thanx again for the ideas!

---

### Post by Lambert on 2005-12-14
Look into ipv6 also. It's enabled in ubuntu by default and has caused problems.

Go [here]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide") and in the trouble shooting steps section towards the end there's a small bit on ipv6 and how to disable it.

---

### Post by 3.2.1 Penguins on 2005-12-14
Thank You Lambert!  It Worked!

ipv6 is now off in Firefox and it surfs like it should.  Now I'm gonna follow the rest of the wiki instructions on how to make it systemwide.  Hopefully that'll fix the e-mail problem.  Thank you all for your help.  Next I tackle the sound problem.  Maybe I should consult the wiki on that too!  :D 

Thanx again y'all.

MERRY CHRISTMAS

---

