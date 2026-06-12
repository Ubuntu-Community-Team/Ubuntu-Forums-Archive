---
title: "What will an x1650 work with?"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by Pethegreat on 2007-12-06
I have a computer with ATI x1650 PCI-express video card. When I installed ubuntu 7.10 I used whatever came with the OS to get the ATI drivers. I can no longer boot into ubuntu without getting a black screen. I read about this problem and what I got from the threads was to not use 7.10 with the x1650. 

Will the x1650 work with any version of ubuntu? If you tell me a version, can you give me a download link so I can burn another CD? I also need easy to understand instructions on how to install the drivers. I have only had linux for about a week(2 days working) so I don't understand any of the commands in the terminal.

---

### Post by mouseboyx on 2007-12-06
Someone got it working here:
[http://youtube.com/watch?v=oyoNCqwZX38](http://youtube.com/watch?v=oyoNCqwZX38)

They installed gusty then did not install any updates, then went to the ati website, downloaded the driver, installed it rebooted then it worked.  My brother has this same card and its the only reason he is not upgrading to Ubuntu.  Ati needs to get off their a$$ and make some good drivers. Or just make the dang thing opensource so it can become better than it could ever be if they made it.

---

### Post by Shakkaa on 2007-12-06
I have that same card and I've had it working with everything for a very long time right now.  I wont say it's easy, but who said free software was easy in the first place.  You can download the new ATI driver which is version 7.11.  you will have to install it manually by downloading it and then typing sudo sh ./"DRIVER" where driver is the exact name of the driver you downloaded. Make sure you are within the path where you run it in.  If  compiz doesn't work for you enable composite on your xorg.conf which is in /etc/X11/xorg.conf, just change the 0 to 1 or enabled.  Personally I have better luck with kubuntu.  It works way better with this card on Gutsy 7.10.  You can install it by typing sudo apt-get install kubuntu-desktop.

Anywho, jsut keep searching in the forums.  Everything is here, you just need to be patient and read a lot.

---

### Post by Pethegreat on 2007-12-07
I need to get rid of the not working drivers before I try the 7.11's With windows, I am used to the newer install of drivers overwriting the old ones. I need to delete the non-working ones so I can get my desktop back. How do I delete the files through the terminal? I also got all the updates for 7.10. Would I be better off by starting with a fresh install? Or can I leave the updates and just remove the drivers?

I looked at compiz since I never used it or even knew about it. It looks nice, but I am happy with my 2d desktop. So getting that to work is not important for me.

---

