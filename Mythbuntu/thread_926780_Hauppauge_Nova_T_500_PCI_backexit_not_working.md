---
title: "Hauppauge Nova T 500 PCI back/exit not working"
date: 2008-09-22
forum: Mythbuntu
---

### Post by niciliketo on 2008-09-22
Hi,

I am unable to use the back/exit button on my Hauppage Nova T 500 PCI remote control.

This is very frustrating as it prevents me doing away with my keyboard and mouse.

I have trawled the 'net looking for resolutions, and have found loads of advice, but none of it has resolved my issue because:
1. The other remote buttons continue to work, despite any changes I make to my remote control settings (either through Mythbuntu control panel, or the lirc config files).
2. I am unable to get irw working (log states it cannot get file information for /dev/lirc0

How is this possible?  I would be a bit more confident in trouble shooting if I was even able to stop my remote control from working (I would know I was changing the correct files).

Any advice gratefully received.  Many thanks in advance.

---

### Post by SiHa on 2008-09-23
I had exactly the same issue with the same card - changing files had no effect whatsoever. Turns out LIRC wasn't configured properly and was doing nothing. Apparently, there is a common-kernel support built in to ubuntu that interprets common keypresses, like up / down, etc.

Can you test one thing for me?

Press 'Mute' when Myth is not running - if you get the speaker icon popup, then you have kernel support, nothing more.

Try Garry Parkers guide: [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

Note that the NovaT 500 LIRC device is usually /dev/input/event*n*, so that would explain why you have no /dev/lirc0.

Once you can get an output from irw, you can run```
sudo mythbuntu-lirc-generator
``` to create your .lircrc, which is the file that maps the keypresses to the various programs.

Hope this helps,

Simon

---

### Post by niciliketo on 2008-09-24
Thank you so much Simon.  This resolved my problem. I now have a working lirc and am really happy.

---

### Post by SiHa on 2008-09-24
Glad to help - could you mark it as solved please? (Thread tools > mark as solved)

Thanks,

---

