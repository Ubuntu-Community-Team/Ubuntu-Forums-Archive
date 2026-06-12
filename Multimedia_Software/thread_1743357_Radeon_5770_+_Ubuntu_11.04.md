---
title: "Radeon 5770 + Ubuntu 11.04"
date: 2011-04-29
forum: Multimedia Software
---

### Post by pszpak on 2011-04-29
I'm trying to get unity working smoothly with my Radeon 5770. So far I've had great difficulty getting good performance. The restricted driver Ubuntu provided provided horrible frame rates and the open source driver is leaving all kinds of visual artifacts on the page.

I was wondering if anyone has had any success with this card? It worked fine with 10.10, but things have obviously changed.

I'm trying out this here:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

And will post if things work out. Otherwise I'd love to here other people's outcomes with the 5770 and 11.04.

Update: Didn't work. Got stuck on the aticonfig command, which returned bad command. So now I'm running with no compositing at all. The installation seems to have done nothing but bork the system.

Update 2: I used the provided ubuntu drivers and downloaded the compizconfig settings manager. Then I went to the general settings and clicked on OpenGL and then unclicked the setting called Sync to Vblank. This cleared up the the low frame rates. The system now has compositing and is work OK (not super, but ok).

---

### Post by Accidental on 2011-04-30
I'm having the same issues. Are your performance issues during playback of HD video content? I did the same trick you recommended by turning OFF the 'Sync To VBlank' and received better [reference] framerates in my HD videos. Though, I now get vertical sync issues during fast-changing scenes. Do you experience the same issue?

Any additional help would be much appreciated.

Perhaps this is a n00b question, but are the ATI/AMD Proprietary drivers in the 'Additional Drivers' utility the same as the current drivers available on the ATI website (Catalyst - 11.4)?

(I'm on 11.04 + have the Sapphire 5770. 8GB memory. i5-2500K. SSD)

---

### Post by josepaul on 2011-04-30
I am having this same problem, performance is ridiculously poor for such a high end card.

---

### Post by josepaul on 2011-04-30
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2738396.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2738396.html)

Others seem to have this same problem.

---

### Post by josepaul on 2011-04-30
> **Accidental said:**
> Perhaps this is a n00b question, but are the ATI/AMD Proprietary drivers in the 'Additional Drivers' utility the same as the current drivers available on the ATI website (Catalyst - 11.4)?


Just tried it, I installed the one from the website. Similar results. No use.

---

### Post by sikander3786 on 2011-04-30
This solved the issue for many users.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by 4Orbs on 2011-04-30
Using Xubuntu 11.04 with xfce compositing turned on, performance is much better than when I had Unity and compiz. Turning off the xfce compositing improves HD video performance slightly. But I still get occasional video tearing whether playing HD video or standard avi movies. Except for the tearing, video quality is good with compositing either on or off. Monitor is 23 inch lcd connected with hdmi cable. Have some minor audio problems. Still, I'm happy and hoping an update will clear up the video tearing and audio glitch soon. I'm using the proprietary driver from Ubuntu repositories.

---

### Post by pdkta on 2011-06-16
Worked for me!!!! so simple solution to such a big issue!!!! (Post #6)

---

### Post by oscarivera9 on 2011-09-15
Yes, indeed!!!  Post #6 worked for me too!  Click on the link and follow the instructions they give you there, and reboot!  They don't mention to reboot (unless you read the comments on that page), but you have to reboot after you do what they suggest.

Most awesome!!!

---

