---
title: "Autodetecting X config on bootup"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by freakymousemats on 2006-09-18
Hello

I've setup a Dapper install on a USB hard disk and I'd like to be able to boot it up on multiple machines. It works fine in all but one respect... X won't run when the video hardware doesn't match the machine it was set up on.

I know it's possible to do a dpkg-reconfigure to manually update the configuration when using it on a new system, but this isn't really what I'm after.

Is it possible to have the X configuration automatically detected and generated each time the system boots, much like the LiveCD does?

Thanks
Steve

---

### Post by freakymousemats on 2006-09-18
Dug down into the various filesystem images on the LiveCD and found out how it sets up X automatically each time. Turns out dpkg-reconfigure was the answer after all....

dpkg-reconfigure -fnoninteractive xserver-org

Forces a reconfigure without asking any questions. So I've added it to my /etc/init.d/gdm script. If anyone thinks there's a better place to put it or a nicer way of doing it, I'd love to hear it.

Steve

---

