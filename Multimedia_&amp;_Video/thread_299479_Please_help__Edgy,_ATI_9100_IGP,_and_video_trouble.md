---
title: "Please help:  Edgy, ATI 9100 IGP, and video troubles"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by ford42 on 2006-11-14
A while back, I built a MythTV box using an Asus Pundit-R.  I first installed Breezy.  I had minimal problems with the install, and once installed, it worked great.  I recently upgraded to Dapper.  All is still working well.  This last weekend, I decided to back it up, then do a fresh install of Edgy.  IVTV was pretty easy.  Lirc was pretty easy.  But, then came video and TV out.  I was able to get that working fairly easily, but when I played any video, it seemed slow and dragging.  I realized that I had to set VideoOverlay to use the Xv Extension instead.  Once I did that, the video was smooth, but the bottom 1/3 (roughly) of the video is cut off.  I am using the fglrx driver from the Edgy repository.  The latest ATI binary drivers no longer support the ATI 9100 card.  The older binaries don't support Xorg 7.1.

With the Edgy fglrx, fglrxinfo shows Mesa.  I tried many suggestions that are on this message board and elsewhere, and I could not fix that.  My dapper install also showed Mesa, but the video (with Xv) had no problems.

Can anyone give insight/help into how I can get the video smooth and the right size.  If it involves somehow hacking older ATI binary drivers to work with Xorg 7.1, I am up for that.  If it involves getting the flgrxinfo to show ATI and not Mesa, I hope someone can help.  Just looking for insight and help because I spent many hours over the weekend trying to get this working.

Thanks for any help.

---

### Post by belly917 on 2006-11-14
I have the exact same problem as you..

Ubuntu Edgy (server)
ATI fglrx 8.30.3
Xv enabled
Mesa result of fglrxinfo
bottom 1/2 of video missing

I also had the same problem with dapper and previous fglrx drivers.

I have been looking all over the place for a fix, but the only advice I have seen was to install a ati fglrx driver 8.22 or older.  But I doubt this will work with the Xorg version included in edgy.

I think I may be selling my ATI card and getting an Nvida instead, since I don't see a fixed driver coming from ATI anytime soon.

---

### Post by ford42 on 2006-11-15
I actually have the TV OUT working without problems in Dapper, but fglrxinfo shows Mesa.  I really don't care if it does show Mesa, as long as it is working for what I want.  Because of that Xv extension (VideoOverlay) problem, I can't get the same results in Edgy.

---

