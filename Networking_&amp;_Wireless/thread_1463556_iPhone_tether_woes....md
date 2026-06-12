---
title: "iPhone tether woes..."
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by Mr-Roboto-wants-to-party on 2010-04-27
So I can't get the bluetooth tethering to work still!  I have been trying for about 2 weeks.    The phone pairs, in blueman I set the phone as a trusted device and click network access point.  It then flashes up on the iPhone tethered with the blue banner. Blueman says it is connected.

But no net access.  

Network connections shows no new connections either.  Weird, I thought it would appear in there.

Is there anything I can do to force it to add the bluetooth link as a network connection?:KS

---

### Post by Mr-Roboto-wants-to-party on 2010-04-27
no ideas?:popcorn:

---

### Post by pdc on 2010-04-28
[http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html)

any use?

---

### Post by griffin30007 on 2010-05-01
I'm having the exact same issue.  This is the one last thing I would need to swap my new netbook entirely to ubuntu.

I'm using a Asus EEE T91MT, Ubuntu 9.10 if that helps.

---

### Post by AlanR8 on 2010-05-01
My understanding is that with Mr Jobbs phone you have to PAY to tether. In the UK it's a meagre £17.00 per month!

That's why my phone's PRIMARY function is connectivity, not looking at a small screen, but connected to the laptop as a modem. 

The Nokia Navigator does just that and is 3.5G so is quick when the signal's right! My package includes unlimited web access and therefore costs nothing to browse when I'm away from home. 

I refuse to pay hotel prices to connect.

---

### Post by steveneddy on 2010-05-01
I didn't think that iPhones sold in the US were even allowed to tether - although I know it can be done through a careful hack.

---

### Post by griffin30007 on 2010-05-01
Yes, you're supposed to pay extra for the tether but every iPhone 3.0+ can be cracked to just use the built in tether.  You are already paying for an UNLIMITED data connection, so you might as well use it.  I've used the connection through bluetooth on windows xp and 7 many a time and its even got me out of a couple jams when wifi wasn't available.

Again one of the main reasons I haven't swapped my new micro-tablet to ubuntu entirely yet.

Pretty sure these are the same exact instructions to crack the iphone for tethering.
[http://www.blogsdna.com/3610/how-to-enable-mms-3g-tethering-on-iphone-os-30-gm-build-7a341.htm](http://www.blogsdna.com/3610/how-to-enable-mms-3g-tethering-on-iphone-os-30-gm-build-7a341.htm)

---

### Post by Oliphant on 2010-05-04
I have a jailbroken 3g.  I ended up paying the $10 for iPhonemodem3.

I setup a network connection with the SSID: iphonemodem and used ad-hoc fired the app up on the iphone and had a connection with no problem. 

It won't show you are connected on the iphone and on some linux users it will indicate there is no connection.  This worked for me with no problems, it may or may not goes as smooth for others.  

I'm also using Lucid if that helps anyone.  I figured paying the $10 for one time was better than getting an aircard and paying for another data connection.

---

### Post by griffin30007 on 2010-05-04
There's only 3 problems with that.
1. You have to jailbreak your phone.  Not that I'm against this, I just against having to reorganize all my music on the phone.
2. Having to pay for a program on the jailbreak is kind of contradictory to the point to jailbreaking.
3. I've used the iPhone modem program in the past and not only did it not work with ubuntu but it didn't work with the windows side as well.  As it currently stands the phone can tether perfectly through bluetooth (also advantageous over Ad-Hoc since no one can jump on your connection) and it seems like the blueman app on Ubuntu has it close, real close, to having an actual answer.

---

### Post by stadniks on 2010-05-05
Try to do the following:

 		To make bluetooth tethering work in Ubuntu 10.04 (Lucid Lynx),  right-click on the Blueman icon, select Plugins. Enable NMPANSupport  plugin, press Ok.
Now everything should work.

---

### Post by griffin30007 on 2010-05-05
Ubuntu 10.04 does not work properly on the EEE T91MT because of the legacy drivers needed for the graphics.

But...
GOOD NEWS EVERYONE!
I updated to Blueman 1.21 (from 1.10) today and I'm currently running off my iPhone's internet connection through bluetooth tether to make this post.
[http://blueman-project.org/downloads.html](http://blueman-project.org/downloads.html)
Follow the instructions.  Works GREAT!  Thanks Blueman!

---

### Post by lastdeadmouse on 2010-05-05
> **griffin30007 said:**
> There's only 3 problems with that.
1. You have to jailbreak your phone.  Not that I'm against this, I just against having to reorganize all my music on the phone.
2. Having to pay for a program on the jailbreak is kind of contradictory to the point to jailbreaking.
3. I've used the iPhone modem program in the past and not only did it not work with ubuntu but it didn't work with the windows side as well.  As it currently stands the phone can tether perfectly through bluetooth (also advantageous over Ad-Hoc since no one can jump on your connection) and it seems like the blueman app on Ubuntu has it close, real close, to having an actual answer.

1. You don't have to reorganize music.
2. You don't have to pay for any jailbreak apps, as they're available cracked too.  Of course, if they're worth the $5, why not help keep them available.
3. MyWi is awesome and has worked flawlessly for me.  Actually uses the wifi chipset in the phone to create a managed network so you can connect any wifi devices to tether 3g.

Seriously, jailbreak.  It'll take all of 5 min tops, and who doesn't want a terminal on their phone?

---

### Post by griffin30007 on 2010-05-05
1.  Jailbreaking does wipe the phone unless they've changed it.
2.  I plan on jailbreaking later this summer when I have free time.  Its just not a top priority.
3.  I now have tethering on Ubuntu without paying for another app or jailbreaking the phone.  GG uninstall.

---

### Post by lastdeadmouse on 2010-05-06
No, jailbreaking doesn't wipe the phone.  Just download blackra1n, run it, jailbroken.  Takes all of 30 seconds (the longest part would probably be booting windows to run it if you still have it installed anywhere, lol). Install cydia, and away you go.  It seriously takes the iphone from pretty good to the most featured phone on the market.

---

### Post by DarkCanis on 2010-05-12
This worked for me, thank you! I was obtaining the DHCP address manually before after tethering.

> **stadniks said:**
> Try to do the following:

         To make bluetooth tethering work in Ubuntu 10.04 (Lucid Lynx),  right-click on the Blueman icon, select Plugins. Enable NMPANSupport  plugin, press Ok.
Now everything should work.

---

