---
title: "Ati Mobility Radeon 9700 white screen (fglrx)"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by Udziuolo on 2007-11-02
Hello!

For the past few months I've been facing a major problem with my ATI Mobility Radeon 9700 video card. Whenever I install official ATI's drivers (fglrx) I'm getting the "white screen of death".
Here's a short brief of which I've resarched about my issue.
ATI's drivers install ok, without problems. But after restarting the whole system, the lcd turns white. The computer is still operational, I can login, but I don't see what I am doing.
I've read google links couple of times and the problem lies in a switched LCD and external CRT settings. The drivers (or Xorg itself) switch edid information from the lcd and the external crt connected via vga port. In fact, when there's no CRT attached, the edid information is corrupted and that's why the lcd can't display the image. If I connect the external CRT and do ctrl+alt+backspace - the problem is solved. Even so, carrying an external monitor with my notebook is extremly uncomfortable smile
The problem is discussied on gentoo forums (the solution is to change to open source drivers, which I've already done. But those drivers are extremly slow in 3d).
I didn't mention earlier, that custom modelines to my monitors are propably completly ignored.
The option "IgnoreEDID" is only valid to open source drivers.
There was a sollution on gentoo wiki (adding a line to ~/.xprofile which would restart the monitors) but it doesn't work.

The problem is discussied over here:
[http://gentoo-wiki.com/Talk:HOWTO_ATI_D](http://gentoo-wiki.com/Talk:HOWTO_ATI_D) … ite_screen
[http://forums.gentoo.org/viewtopic-t-516271.html](http://forums.gentoo.org/viewtopic-t-516271.html)


Can someone help me with installing fglrx?

---

