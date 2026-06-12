---
title: "Configure aspect ratio and resolution"
date: 2008-04-13
forum: Mythbuntu
---

### Post by TheConsultant on 2008-04-13
Hi.
With MYTHBUNTU 8.04 and MYTHTV 0.21 I have trouble with the aspect ratio.
My TV is a SONY wide screen monitor with 1024x1024 resolution.  If I configure the resolution with the mythbuntu control centre as LCD TV 102x768 it's look like good, but my recorded videos with a aspect ratio of 16:9 are showing a letterbox instead full screen. If I switch to a aspect ratio 4:3 while watching a recording - it is ok.

If I switch the mythbuntu control centre the resolution to LCD 1024x768 with activated "widesccreen", the 1024x768 is changed to 1280x720 but this is to much for my television.

By the way. Why shows the xserver-xorg tool only PC monitors and not television entries too? 

Where is my mind error?

Best regards
Martin

---

### Post by gobbles414 on 2008-04-13
> **TheConsultant said:**
> Hi.
With MYTHBUNTU 8.04 and MYTHTV 0.21 I have trouble with the aspect ratio.
My TV is a SONY wide screen monitor with 1024x1024 resolution.  If I configure the resolution with the mythbuntu control centre as LCD TV 102x768 it's look like good, but my recorded videos with a aspect ratio of 16:9 are showing a letterbox instead full screen. If I switch to a aspect ratio 4:3 while watching a recording - it is ok.

If I switch the mythbuntu control centre the resolution to LCD 1024x768 with activated "widesccreen", the 1024x768 is changed to 1280x720 but this is to much for my television.

By the way. Why shows the xserver-xorg tool only PC monitors and not television entries too? 

Where is my mind error?

Best regards
Martin

I don't doubt your figures; I've done some research online. But 1024x1024 equals a square. I find it odd that any manufacturer would use a square resolution for a widescreen display. That's just asking for trouble. ](*,)

Anyway, I have a 1280x1024 monitor connected to one of my PCs. That's equivalent to 5:4. All full screen (4:3) videos look like they are widescreen because of the difference in aspect ratios. Perhaps you're encountering a similar issue...? Also, try restarting and then go to *System => Administration => Screens and Graphics*. Maybe you can choose the correct resolution from there...? Finally, you might restart, press the *escape button* on your keyboard, choose the *Rescue Mode* for your latest kernel, and *type sudo dpkg-reconfigure xserver-xorg*.

Do any of these ideas help you?

---

### Post by TheConsultant on 2008-04-13
Hi gobbles414

Only the max resolution is 1024 x 1024, but with 1024x768, the tv is working well.
In the past (mythtv 0.20) there was a page to change between a 4:3 or a 16:9 televsion. With this switch was mythtv working well with the aspect ratio.
Now in 0.21 I'm missing this switch. It's seems that mythtv is looking for the aspect ratio of the driver.

dpkg-reconfigure xserver-xorg is not working well with hardy. With gutsy the tool was detect my tv as well and was updating grub. Now it's switch to a high resolution of 1280x1024 without to ask me. It's updating grub and if make a reboot, the tv is flicker, becaus the resolution for the spalsh screen is to high.

Can be the dpkg-reconfigure xserver-xorg finds PC monitors, but fails with televsions. So dpkg-reconfigure xserver-xorg is not usable to me.

More tipps?

Best regards
Martin

---

### Post by gobbles414 on 2008-04-13
> **TheConsultant said:**
> Hi gobbles414

Only the max resolution is 1024 x 1024, but with 1024x768, the tv is working well.
In the past (mythtv 0.20) there was a page to change between a 4:3 or a 16:9 televsion. With this switch was mythtv working well with the aspect ratio.
Now in 0.21 I'm missing this switch. It's seems that mythtv is looking for the aspect ratio of the driver.

dpkg-reconfigure xserver-xorg is not working well with hardy. With gutsy the tool was detect my tv as well and was updating grub. Now it's switch to a high resolution of 1280x1024 without to ask me. It's updating grub and if make a reboot, the tv is flicker, becaus the resolution for the spalsh screen is to high.

Can be the dpkg-reconfigure xserver-xorg finds PC monitors, but fails with televsions. So dpkg-reconfigure xserver-xorg is not usable to me.

More tipps?

Best regards
Martin

Interesting... The only thing that I can add to my original post is that 1024x**1024** is probably your monitor's "native resolution". My guess is that your PC is trying to match that native resolution when it goes to 1280x**1024**. I'm out of ideas. Sorry...

---

### Post by TheConsultant on 2008-04-13
Thanks a lot gobbles414

---

### Post by gobbles414 on 2008-04-13
> **TheConsultant said:**
> Thanks a lot gobbles414

Sorry that I wasn't able to help... Perhaps someone else in the forums can be of more assistance.

---

### Post by tgm4883 on 2008-04-14
Can you post the make/model of your TV?  perhaps it's an EDID issue.

---

### Post by TheConsultant on 2008-04-15
Hi tgm4843

It's not a trick, it's a SONY ;)

The type is a KE-42TS2E 42 inch plasma model with 1024 x 1024 pixel resolution.

This model is able to play HDTV with 720p, but have no HDMI port. The PC is connected via RGB BNC components connectors (5 connectors).

Best regards

Martin

---

### Post by gobbles414 on 2008-04-15
> **TheConsultant said:**
> The PC is connected via RGB BNC components connectors (5 connectors).

Well, that explains a lot! I'm honestly surprised that your TV ever worked with your PC. **Have you tried to connect using your S-Video connection?** Many laptops have an S-Video out, and adapters are available for desktops.

I'm sure that you paid a lot of money for your TV if you purchased it new in 2003. But even a review from that time I found on the web calls the connections on your TV "slightly disappointing". HDMI wasn't very mature at that time. And VGA is still a luxury for TVs. But Sony should have at least included a DVI connection on your TV! Heck, I've seen CRTs from 2001 with DVI inputs!

---

