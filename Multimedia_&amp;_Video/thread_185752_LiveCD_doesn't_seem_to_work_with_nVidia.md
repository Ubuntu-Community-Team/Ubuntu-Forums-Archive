---
title: "LiveCD doesn't seem to work with nVidia"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by ZephyrXero on 2006-06-01
I had a very frustrating time trying to install the Dapper Release Candidate on my brother's computer the other day. It seems the only option for desktop installation is now thru the LiveCD/Espresso, and after booting, the screen was just a big garbled mess. I had already seen similar problems a few months ago with my ATI based laptop, and I could easily fix it with either mesa or theproprietary drivers, except for the fact I can't edit the xorg.conf on a CD, let alone install new drivers. I really hope this gets fixed in the next couple hours before 6.06 goes final...but somehow, I'm doubtful.

For anyone having similar troubles, here's how to get around it, though it is a little bit of a pain and a time sink...

Download the server install disc, which is still text based, and do an install. After booting you'll need to "sudo apt-get ubuntu-desktop." Then after you do that, do a reboot and I'd suggest installing the proper Linux kernel for you system architecture too (for example, linux-686). So after that point, you will basically have the same thing as what you would have gotten with the regular install, if only it had *Just Worked* in the first place :/

---

### Post by ZephyrXero on 2006-06-01
Hmm....it appears the "alternate" installer available may be the tradition text based installer, so perhaps I went thru all that crap for nothing...anyway, the problem still remains AFAIK.

---

