---
title: "Need a new wifi card.. looking at edimax EW-7711USN,"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by dux666 on 2013-03-07
need a new Wifi card that works out of the box on most Linux systems, I am looking at the edimax EW-7711USN, does this work out of the box? no need to install crap? if not, then what should i be looking at? 
[http://wikidevi.com/wiki/Edimax_EW-7711USn](http://wikidevi.com/wiki/Edimax_EW-7711USn)

---

### Post by kurt18947 on 2013-03-07
I have two that work out of the box.  TrendNet TEW-649UB uses a RealTek 8192SU chipset, Netgear WNA1100 uses an Atheros AR9271 chipset.  Do not make the mistake of thinking any Netgear adapter will work.  Some Netgear models cannot be made to work with any amount of expertise.  There are other models that work equally well, these are the ones I have experience with.  I read somewhere that the Ralink RT2800usb module that drives your linked device works best on 12.10 and later.  I have a device on the way that uses this chipset.  I'll post if it's easy to get working.

I've posted in the past the Dlink's DWA-131 is plug 'n' play.  Mine is, it's a twin of the TrendNet TEW-649UB.  However there is a new version out that is *not* plug 'n' play so buying that model would be playing roulette; v.1x works, v.2 does not.  I hate when manufacturers do that but it's common.  Windows users probably don't notice the difference, linux users certainly do.

---

### Post by tjeremiah on 2013-03-07
I have the edimax ew-7811un and it functions better than in Windows IF you install the updated Realtek drivers which is detailed how to do somewhere on the internet. On Windows its CRAP but in Ubuntu, once you install the Realtek drivers, just plug it in and it will function well. It will wake up from standby with no problem and be on when you log into Ubuntu (after every kernel update though I have to reinstall the driver which is annoying). One important note is that even though its dirt cheap being at $10, you [COLOR="#FF0000"]must point it towards the router[/COLOR] for it to function well. I am currently 1 floor away from my old Netgear wireless a/b/g router (7 yrs old :( ) and manage to get an average speed of 7mbps down, 2 up which gets the job done. I assume when I finally upgrade router to take advantage of its wireless N, things will be a lot better.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091)

---

### Post by itrogers on 2013-03-07
Here are some Kernel supported hardware & drivers.
[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

---

### Post by kurt18947 on 2013-03-07
I just received and installed this cheapie.  It is not as good as the Edimax referenced by the O.P. but much to my surprise it was plug 'n' play.  The Edimax needs the RealTek drivers.
[http://ubuntuforums.org/showthread.php?t=2123313](http://ubuntuforums.org/showthread.php?t=2123313)

---

### Post by dux666 on 2013-03-07
can anyone tell me if the  [SIZE=1][COLOR=black][FONT=sans-serif]RT2870, RT3070 drivers are in ubuntu? [/FONT][/COLOR][/SIZE]

---

### Post by kurt18947 on 2013-03-09
Oops, I misread the O.P.s first post, sorry if I caused any confusion.  The Edimax EW-7**8**11Un uses a RealTek rtl8188CUs chip and requires the manufacturer's driver to work correctly.  I don't know about the EW7711Un.  I know the cheapie adapter I posted above uses a Ralink RT5370 chip and 'just works' in the latest Ubuntu releases, 12.04 and later.  I do recall the RT3070 caused some issues a while ago but haven't read much about it lately so it's possible that those issues are in the rear view mirror.

---

### Post by QIII on 2013-03-09
*Moved to** Networking & Wireless***

Hello and welcome to the forums!

If you are replacing a card anyway, you might look [here.]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux").

You'll probably save some headaches that might be worth the few extra bucks you'll pay.

The RT28xx driver is included.  Add it to your modules file and it will be loaded at startup.  The other I don't know.

Best wishes!

---

### Post by dux666 on 2013-03-19
it cost 100 for that wifi? why it cost so much? everyone else is 20.

---

