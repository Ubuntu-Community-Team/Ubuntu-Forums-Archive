---
title: "Hp Proliant Ml115 Video Problems"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by holdenrs on 2008-03-15
I have installed 7.10 server program.  the display will not configure to anything but 640 x 480. it has an integrated  nvidia controller.  i have older AMW monitor.  any help would be great.

---

### Post by eskimodigger on 2008-04-27
Your video driver is based on a Matrox G200 and has only 2MB of memory, limiting it to text display only. I don't know what you are intending to use your Proliant for, but I use mine strictly as a server. It sits on the network storing photos, music, backups, etc. It isn't connected to a display or a keyboard, and I administer it using ssh and webmin. If you are intending to run X then I would suggest a cheap graphics card for about $30/40. I use the x64 version of ubuntu server, and I have just upgraded from v7 to v8 with no problems. You will find many other distributions will hang on bootup, this is to do with the NMI wihch is a keyboard hardware interrupt. You can get around this if you need to, or use ubuntu! Good luck!

---

