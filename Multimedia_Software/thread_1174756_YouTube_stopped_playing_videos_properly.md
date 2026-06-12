---
title: "YouTube stopped playing videos properly"
date: 2009-05-31
forum: Multimedia Software
---

### Post by arepaking on 2009-05-31
Hi Everyone,
Youtube used to work flawless before, but since three days ago I can't play videos even though I am able to see the first frame; but when clicking the "Play" button then it freezes.

Does anyone knows or at least have an idea about what could be causing this issue? Last thing I remember I installed was the logmein client but I already uninstalled it and the issue with youtube remains.

Thanks in advance for your guidance,
AK

Update: Sites such as Hulu.com and SouthParkStudios works fine. Both of them uses Flash Player 10. I am having this issue just in YouTube and Facebook videos.

---

### Post by arepaking on 2009-06-01
any ideas?

Updates: I just realized that Pandora.com has the same issue... I can hear the song starting but 1 sec later.. it stalls.

---

### Post by arepaking on 2009-06-01
Issue Solved!!!!!

Ok, this is what I found. Three days ago I installed the "Simple Backup" program and it had been backing up a lot of stuff during the next three days. It was pretty much taking over my /var/ folder and I think it affected the /var/tmp at some point because I was not able to perform system updates due to the lack of space.

I uninstalled this app, then deleted all the backup files.. rebooted and everything started to work again!!!

I hope this post can help anyone out there.

---

