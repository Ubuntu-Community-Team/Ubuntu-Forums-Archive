---
title: "2 Sound Cards, can't set one Default!!!"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by joegiampaoli on 2006-11-18
Ok, here's a good one, ubuntu 6.10 "Edgy", I have two sound cards, one VIA (integrated) the other Audigy (PCI), I can't set Audigy as default, it always chooses VIA as default, I did "sudo asoundconf set-default-card Audigy", then I reboot, and nothing:confused: , still VIA, I need to use both cards on my system, I only want Audigy as default...:rolleyes:

---

### Post by joegiampaoli on 2006-11-23
Ok, I solved it with this guide by LordRaiden (thnks)
Sometimes the answer is right on front of us.

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

Hope this helps future users.

---

### Post by Phulerock on 2006-11-23
Hello Joe Giampaoli,

I wiil show you the simple way to set the default sound device

1. go to sound item in Preferences menu
2. go to Sounds tab, you will see default sound card item
3. re-login after setting
finished !

Hope this help.

---

### Post by joegiampaoli on 2006-11-23
Thx Phulerock actually that was what I was having problems with, because when I rebooted my box it would switch the devices, specially since I use one for voip and the other as default audio, it was driving me crazy, the guide I point at the top works for the whole system even after reboot and affects all accounts. So I did do it the way you explain for a while on three different accounts I have on the box, but now I managed it to work system-wide with the help of that guide.

Thanks again. Cheers.8)

---

