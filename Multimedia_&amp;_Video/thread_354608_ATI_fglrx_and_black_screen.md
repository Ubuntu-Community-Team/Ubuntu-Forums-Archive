---
title: "ATI fglrx and black screen"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by moimies on 2007-02-06
I've tried to install Ati drivers from repositories and binary, both time ending up with black/blank screen. I've read many threads and howtos but nothing helps. And I don't want to try every trick I find because I had to do hard reset when it jams :(. My card is 9800, so it's supported.

I've found out that this isn't a rare problem, so does anyone have any solution?

---

### Post by moimies on 2007-02-09
No one knows?

---

### Post by dmitry_roslyakov on 2007-02-09
The same thing :(

---

### Post by sssp on 2007-02-09
I am having the same problem. I have tried the directions from the ati website too and no luck. I also have a radeon 9800 pro.
This card seems to give alot of people problems.

---

### Post by barney_1 on 2007-02-09
I had this same problem with an ATI 9800 AIW Pro card running on an ASUS K8V SE Deluxe motherboard.  After tearing my hair out for a couple of months I discovered that I didn't have the most up-to-date bios.  Everthing worked just right after upgrading the BIOS to current.

---

### Post by nomad00 on 2007-02-09
I'm having the same problem w/ a 9600 :( 

Could someone point me to how to revert to default drivers so i can get the gui loaded? :P

---

### Post by moimies on 2007-02-10
Boot in the recovery mode and run command "dpkg-reconfigure xserver-xorg". Then take vesa drivers from the list.

Post here if you're having a same problem, so we'll see how big issue this is.

I have the newest bios on my Asus A7V266, but it doesn't help.

---

### Post by nomad00 on 2007-02-10
Thanks! Was able to get back into the GUI and re-followed the guide incase i was missing something.....but no.

Sad part is i had this working fine, playing World of Warcraft thru Wine, but then I ran Envy to try to keep my drivers as up to date as possible...and I can't get it back to the state it was in before.

---

### Post by moimies on 2007-02-11
Yeah, I got it working \o/. I followed [these]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") instructions. But I did this:
> Note: An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc.

Then I added "Option   "MonitorLayout" 	"TMDS, AUTO"" in Device section in xorg.conf. That I found from [here]("http://www2.ati.com/drivers/linux/linux_3.12.0.html#173165").
I have an LCD monitor connected in DVI. And no black screen, X and 3D-acceleration are working.

---

### Post by Dark X Dragon on 2007-02-11
I have a problem like this, not sure if it's the same thing.
Games will load but with just a black screen.


After some tracking down I found this:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6.html)

Which refers to this:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge)

---

