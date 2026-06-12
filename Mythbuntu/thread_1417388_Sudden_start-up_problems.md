---
title: "Sudden start-up problems"
date: 2010-02-27
forum: Mythbuntu
---

### Post by zaurus on 2010-02-27
Hello there.

I have a Muthbuntu 9.10 installed with 2 DVB cards, Terratec c-1200 cable and HVR-4000. It was working prety well for a couple of monthes. Suddenly it started behave rather strange with start-up. I have a login prompt instead of X-window as it was before. If I do nothing at prompt the Xwindow starts anyway after some minutes. I check my DVB cards. Only Terratec is detected, but no drivers are loaded. I manipulated a bit with Lirc setup and removed apparmor. That is what I was doing between normal sturt-up and when the proble began. I saw at prompt some error related to apparmor. Ok, I installed it again, but it does not help. I run 2.31.19-generic kernel on AMD 64-bit.
Please help to sort out the source of problems. Where should I check what is wrong to begin with? And maybe someone has a solution ready.
Yor advices are very appreciated?

N.B.
I am so unwilling to re-install the whole system again!

---

### Post by blackoper on 2010-03-03
Did you upgrade your packages? I'd just try reinstalling the video packages and making sure your driver is current and beign loaded. For the login issue, I'd try turning back on autologin.

---

### Post by zaurus on 2010-03-03
I upgraded to Mythtv 0.23 and it helped with this issue but create others. But it is in another tread.
It is not a good solution but works at least.

---

