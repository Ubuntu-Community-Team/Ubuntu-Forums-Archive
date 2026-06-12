---
title: "DVD player problems"
date: 2010-11-23
forum: Multimedia Software
---

### Post by G. Kay on 2010-11-23
I'm new to Ubuntu, having installed it a few days ago on my Toshiba Satellite laptop (64 bit) after a malicious virus made it impossible to continue with Windows 7. So far I love it, with one exception; I cannot get DVDs to play. I've tried Movie Player, VLC, Dragon Player, and KM Player with the same results. The disk will fire up in its drive, most of the players show its title, but none of them will actually play it. I've tried several DVDs in case of a faulty disk, but none work. How can I resolve this issue? Any help would be greatly appreciated!

Thanks

---

### Post by tommcd on 2010-11-23
Have you enabled the **medibuntu** repository and installed **libdvdcss2**? If not, then see this:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then just install libdvdcss2. Enabling the medibuntu repo will also allow you to install the Windows codecs. To install the Windows codecs, just install the **w32codecs** (if you are using 32bit Ubuntu) or the **w64codecs** (if you are using 64bit Ubuntu).
After you install libdvdcss2, you can install **xine-ui**, which is an excellent media player for DVDs.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

