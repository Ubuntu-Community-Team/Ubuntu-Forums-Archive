---
title: "Front-end unresponsive after intrepid upgrade"
date: 2009-02-08
forum: Mythbuntu
---

### Post by jaymzh on 2009-02-08
All,

I recently upgraded to interpid[1] and since then the mythtv front-end has been completely unresponsive to any input. The frontend logs show nothing useful. It says it can't run cdrecord or setup SIP, but that shouldn't an issue.

An strace shows it cycling on select() of fd 22 and getting EAGAIN.

An ltrace shows it cycling on _ZN10MythUIType5PulseEv(0x7f0980043480, 0x7f0983a1bbd0, 0x7f098001eba0, 0, 0x7f098001dbb8) = 1

The Xorg log shows nothing of interest.

The backend log shows nothing resembling an error except for:
  QDateTime::fromString: Parameter out of range

If I ssh in and run mythtv-setup, it works fine over ssh's X forwarding.

[1] The box is a brand-new install, but everytime I tried to install the mythbuntu intrepid CDs I got cd read errors mid-installation (tried 2 downloads and 3 cdrs), so I installed hardy ran through mythtv-setup and then did an apt-get upgrade to intrepid. Since then the frontend has been completely unresponsive.

Any help would be appreciated.

Thanks,
- Phil

---

