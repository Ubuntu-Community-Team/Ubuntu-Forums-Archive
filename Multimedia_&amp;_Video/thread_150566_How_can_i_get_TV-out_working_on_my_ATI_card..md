---
title: "How can i get TV-out working on my ATI card."
date: 2006-03-26
forum: Multimedia &amp; Video
---

### Post by UbuntuJohan on 2006-03-26
Hi,

I've  compiled and installed the 8.23.7 ATI drivers by following this post
[http://ubuntuforums.atiorg/showpost.php?p=423584]("http://ubuntuforums.atiorg/showpost.php?p=423584") 

The installation was succesful and I can e.g watch DVD's on it.

My problem starts when I try to use my tv on TV out.
It kind of works.
When I power on the PC the bios splash image displays correct but only in black and white also the grub menu displays but then the TV just flickers until gnome is started. Then the TV displays gnome correctly but still only in black and white.

I've tried to edit xorg.conf to get it working but nothing I've tried has helped.

The cables and tv can handle this since i'm able to display properly from a windows laptop.

The TV uses PAL-B and I'm connected via a s-vhs to scart adapter.
The graphics card is a RADEON X550.

I'm depending on TV-out since it's a mythtv box I'm trying to build. ](*,) 

any ideas on what to do?

Cheers
//Johan

---

### Post by UbuntuJohan on 2006-03-26
I managed to solve this myself.
After some more googling I understood that ATI driver 8.23.7 and TV-out often leads to problems.

Many stated that 8.20.8 was the last version where TVout worked fro them.

So I downloaded that driver
(Copy the link for newest ATI driver and edit it to fetch 8.20.8 instead.

Then after some struggle I managed to get rid of the 8.23.7 driver.
For a while not even vesa was working so i was stuck with terminal.

I "compiled" the driver like in the same way as stated in the link in the first post.

I took a while until I realized that the deb files ended up in /tmp
Then I installed them rebooted and now vesa was working again.
ran fglrxconfig and rebooted again. And this time the fgrlx drivers where used.
The only thing was that fglrxinfo stated mesa instead of ATI.
I turned out that one of the 8.23.7 deb files still was in /usr/src
So removed that and did 
m-a i-a fglrx
And after that everything is working fine

I hope this helps if someone ends up in the same situation.

Cheers
//Johan

---

