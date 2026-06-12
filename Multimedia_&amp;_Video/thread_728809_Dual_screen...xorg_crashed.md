---
title: "Dual screen...xorg crashed"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by Mishal on 2008-03-19
I was trying to set up dual screens using my laptop and my roommate's monitor and I failed.

Anyway, while I was doing that, I disabled my laptop monitor and enabled my roommate's monitor. Once I was done with it, I couldn't revert back to my laptop monitor.

Now when I log in to Ubuntu, it gives all sorts of error messages. I am stuck with the command line.

If I type 'startx', it gives me more error messages.

My guess is that I have to change xorg.conf somehow. But I don't know what to change in the file. Please help.

---

### Post by Mishal on 2008-03-19
Could someone please help? :)

---

### Post by Mishal on 2008-03-20
No one?

---

### Post by perhhk on 2008-03-20
1.try windows

2.restore xorg from an ubuntu livecd (I think t has a generic configuration)

---

### Post by mattk132 on 2008-03-20
no.  To reconfigure xorg you can use this command (without quotes):  Sudo dpkg-reconfigure xserver-xorg.  Go through the setup and there you go.:)

---

