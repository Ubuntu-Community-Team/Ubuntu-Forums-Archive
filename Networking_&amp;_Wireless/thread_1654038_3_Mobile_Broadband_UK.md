---
title: "3 Mobile Broadband UK"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by dESAI on 2010-12-27
Season greetings everyone!

I have a new laptop with Ubuntu and Win7 installed. I recently bought a Mobile Broadband USB Modem from the UK mobile provider known as "3".

This is the device I purchased: [http://direct.tesco.com/q/R.207-7408.aspx]("http://direct.tesco.com/q/R.207-7408.aspx")

Can this be used with Ubuntu? The software provided is only for WIN/OSX.

I have searched the forums and the most recent post that I could find about this was made in 2008, so I assume that the info in them is obsolete.

I still love Ubuntu, but are my hands tied to Win7 on this issue?

Thanks all!

---

### Post by dESAI on 2010-12-27
Update. According to windows this is the modem I'm using: 

ZTE Proprietary USB Modem

---

### Post by Linicks on 2010-12-28
Yes, I am on one now, they work great, and pretty bloody fast in the UK.

Put the sim card in, plug it in, then you need to right click on the icon that appears on the desktop and 'eject' the drive.  Then use network manager wizard for 3 internet - accept defaults. Then just connect from the network applet.

Search in these forums for 'zte mf112 cdrom eject' for instructions to do this automatically.

Nick

---

### Post by dESAI on 2010-12-28
Cool I'll give it a try right away.

Cheers dude!

---

### Post by Linicks on 2010-12-28
Once you are online, got to 'three.co.uk' and just visit the 'mythree' account link - it will automatically log you in, so you can then view usage, top-up etc. etc.

By the way, have a read of my message here -> [http://ubuntuforums.org/showthread.php?t=1653593](http://ubuntuforums.org/showthread.php?t=1653593) see if you have same issues.

Nick

---

### Post by dESAI on 2010-12-28
> **Linicks said:**
> Yes, I am on one now, they work great, and pretty bloody fast in the UK.

Put the sim card in, plug it in, then you need to right click on the icon that appears on the desktop and 'eject' the drive.  Then use network manager wizard for 3 internet - accept defaults. Then just connect from the network applet.

Search in these forums for 'zte mf112 cdrom eject' for instructions to do this automatically.

Nick

I'm online already! :D

That was AMAIZINGLY EASY!!!

When I connected the modem nothing appeared on the desktop... so I went to my WIFI icon on the panel and was shocked to see Mobile Broadbank already there. I clicked it, selected my country, selected "3" and then I was online! 

I'm a little ashamed that I didn't try that already before. It was so damn easy! 

Ubuntu is just getting better and better eh. I'm almost ready to use it more than Win, I just need to figure out a cool way to use Photoshop in Ubuntu.

I have had some issues accessing Gmail using 3-MB and Win7 (only works with Google Chrome). And I'm a little surprised that I also have this issue with ubuntu. I'll could try another browser rather than FF, which I hate to do..... Did you have any issues with Gmail?

Thanks for your help and all the best for the new year and beyond!
:KS

---

### Post by Linicks on 2010-12-28
I don't use gmail, but if you do, please read my post I linked, that sorts out issues with 3internet.

BTW, I got rid of MS about 8 years ago, but have been using GNU/Linux for over 10 years.  It is a breathe of fresh air.

Also, secretly, I think that hardware manufacturers (like 3internet, O2 etc.) do support GNU/Linux now but do not announce it (as usually MS tie them done to only use their stuff) - hence why most gadgets do work 'out of the box'.

Nick

---

### Post by dESAI on 2010-12-28
> **Linicks said:**
> I don't use gmail, but if you do, please read my post I linked, that sorts out issues with 3internet.

BTW, I got rid of MS about 8 years ago, but have been using GNU/Linux for over 10 years.  It is a breathe of fresh air.

Also, secretly, I think that hardware manufacturers (like 3internet, O2 etc.) do support GNU/Linux now but do not announce it (as usually MS tie them done to only use their stuff) - hence why most gadgets do work 'out of the box'.

Nick

Mate you are a :KS

I now have access to my gmail. Just one small issue, there are no toolbars showing in Epiphany, also Javascript is not working. Luckily I set Gmail as my home page and used the shortcuts to access the site.

Like your good self, I also need to use other Goolge services, such as Analytics. Without the toolbars and js it'll be a bit of a pickle. Hopefully it'll be easy to get sorted.

Thanks for your help, getting online with Ubuntu/MB has made my day!

Stay cool.

---

### Post by Linicks on 2010-12-28
Then do the second fix - change the APN in the 3internet connection to 'three.co.uk' instead of '3internet'.  The only difference is here is that you will have a NAT ip address via 3internet as opposed to a real IP address ~ according to my tests today, speeds are about the same.

I researched, and there is not a lot of difference - and by using 'three.co.uk' firefox can access and function properly to google services.

Why it doesn't work though on 3internet APN is another question...

Nick

---

### Post by dESAI on 2010-12-28
> **Linicks said:**
> Then do the second fix - change the APN in the 3internet connection to 'three.co.uk' instead of '3internet'.  The only difference is here is that you will have a NAT ip address via 3internet as opposed to a real IP address ~ according to my tests today, speeds are about the same.

I researched, and there is not a lot of difference - and by using 'three.co.uk' firefox can access and function properly to google services.

Why it doesn't work though on 3internet APN is another question...

Nick

Nick you RULE!

---

### Post by Linicks on 2010-12-28
No I don't ~ this is what free open source software et al is all about - people sharing :)

Happy New Year my friend, enjoy a MS free future :)

Nick

---

### Post by dESAI on 2010-12-28
> **Linicks said:**
> No I don't ~ this is what free open source software et al is all about - people sharing :)

Happy New Year my friend, enjoy a MS free future :)

Nick

Hey dude it's me again :)

Sorry to bother you again... You said you work on the web, so I'm wondering, do you ever use the cPanel control panel provided by most Linux based shared hosts?

I ask because I am trying to access one myself now, but it keeps kicking me out, telling me my IP has changed. 

I'm only asking you because I'm wondering that it may be something to do with my current connection. 

Stay ms-free!

---

### Post by dESAI on 2010-12-28
> **dESAI said:**
> Hey dude it's me again :)

Sorry to bother you again... You said you work on the web, so I'm wondering, do you ever use the cPanel control panel provided by most Linux based shared hosts?

I ask because I am trying to access one myself now, but it keeps kicking me out, telling me my IP has changed. 

I'm only asking you because I'm wondering that it may be something to do with my current connection. 

Stay ms-free!

FTP is also not working with "three.co.uk".

I just changed the "three.co.uk" back to "3internet" and now FTP and the cPanel are working fine.

So, I've made a second connection in the con-manager, one for each of the two config's, so I can switch easily when I need to use gmail or the cPanel.

Not super convenient, but I'm still happy :)

---

### Post by Linicks on 2010-12-29
Yeah, it is because when you connect via 'three.co.uk' APN your connection is via 3's network and get assigned a NAT address, whereas '3internet' APN assigns 'real' ip addresses.

So the issue you see was that.

I will still investigate why googlemail etc. doesn't work with firefox and '3internet' APN though.

Nick

---

