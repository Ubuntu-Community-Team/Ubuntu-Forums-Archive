---
title: "Wireless issues - anything being done about it?"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by KaYnemO on 2010-06-03
I see a lot of people experience wireless problems after upgrade to Lucid - me as well - wifi drops and won't reconnect, wimax needs terminal push to get up, NetworManager won't auto connect. Also flash plugin is crashing when trying to watch video of some sites (comedycentral.com for instance). Some sites report missing Flash Plugin !!??!! All of this is very annoying. Forums don't seem to supply answers - only a million of questions. I am sorry to see this, since I've been a linux user for many years and love it through bad times and good mainly for friendly forum support. Any help? Anything is being done to fix these problems? I would really love NOT to backgrade to Karmic. THanks

Got 10.04 on Acer Aspire 5670 (Intel Pro [Golan] network card)

---

### Post by arvevans on 2010-06-03
In my own case I noticed that the upgrade turned off access to several repositories, including some that contain drivers for WiFi hardware.  If the administrator does not subsequently re-activate needed repositories, some hardware may not come up automatically.

Obviously this is problematic if one depends on WiFi based Internet access for downloading WiFi hardware drivers.  The chicken-and-the-egg situation becomes a frustrating roadblock.

---

### Post by cossack on 2010-06-03
> **KaYnemO said:**
> I see a lot of people experience wireless problems after upgrade to Lucid - me as well - wifi drops and won't reconnect, wimax needs terminal push to get up, NetworManager won't auto connect. Also flash plugin is crashing when trying to watch video of some sites (comedycentral.com for instance). Some sites report missing Flash Plugin !!??!! All of this is very annoying. Forums don't seem to supply answers - only a million of questions. I am sorry to see this, since I've been a linux user for many years and love it through bad times and good mainly for friendly forum support. Any help? Anything is being done to fix these problems? I would really love NOT to backgrade to Karmic. THanks

Got 10.04 on Acer Aspire 5670 (Intel Pro [Golan] network card)
Your problem with your upgrade makes me hold off on upgrading my 9.1 ubuntu.
I have heard that is best to get the live cd and test it with your hardware and if all is well then do a clean install and forget the upgrade procedure. I tryed doing the upgrade from 9.04 to 9.1 and what a mess, no wi-fi and my wireless broadband would not work. I had to get a live cd and do a clean install then all worked well. This time I will get a new hard drive and do a 10.04 install and if it is a problem I can put my old hard drive back.

---

### Post by KaYnemO on 2010-06-04
Actually, the problem (according to hours of internet research by yours truly) seems to be with conflicts in IRQ or whatever between the wifi drivers and radeon module. I have disabled KMS by adding radeon.modeset=0 in GRUB and the wifi is stable since, however, some sites still crash with video streaming (like comedycentral.com), while others work stable like youtube.com. I am sure the issue is being looked at - have to wait until then, I am just way to lazy to downgrade to 9.1 :) I just hope they will announce the problem solved once they do :)

---

### Post by SteveGerry on 2010-06-04
I agree - I am having similar issues with Ubuntu 9.04 from a CD I bought from Canonical that included Firefox - connects to home wireless network but Firefox won't work.  I posted 4 days ago ([http://ubuntuforums.org/search.php?searchid=73593031](http://ubuntuforums.org/search.php?searchid=73593031)) and 6 days ago details.
 
It's a problem for the whole Linux concept if the forums are places where everyone posts problems or possible solutions that don't actually work.  Some for the advice posts have taken hours and seem very knowledgable and it seems people are trying to fix something that just isn't fixable due to underlying bugs.
 
I would love to tell people "forget Windows and just get Ubuntu" but it seems pretty vital that a laptop should connect to Internet, especially if it says it is connected to the network.
 
When I go to the Canonical website I can buy support - but really they shouldn't sell a product which seems to be unworkable.

---

### Post by KaYnemO on 2010-06-05
Well - I've been fully on Linux for the past 6 years or so, so I remember worse user days then now, so this little bug wouldn't throw me off the Linux - I have survived all this time with ATI Radeon card (not a pretty task :) ). But it would have been good if the forum would turn back to the days when there was fast help to the whines of likes of me :)

P.S. The latest kernel update seems to have helped - maybe it's placebo, I dunno - I removed the radeon.modeset=0 line from GRUB after the kernel update and the system is ok, sorta... Still no flash plugin support in Chrome (no matter what I do), so using Firefox, which works fine - no idea why. Also still no automatic connection with a wimax usb modem, but I am used to using terminal :)

Good luck !

---

