---
title: "ATI Radeon 9200 Pro + monitor Flatron L1715S"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by Matthai on 2006-06-09
As described in subject, I have ATI Radeon 9200 Pro and Flatron L1715S monitor

Graphical install is not working. I press Esc, and have to install by live vga=771 option.

After Installation computer cannot be started - I have to go to Recovery mode. In fact, it is started, but I receive "input signal out of range" error on the monitor.

BTW: In recovery mode I become root immediately - without password. I think that is dangerous...

Then I install xorg-driver-fglrx, and follow the rules as described in wiki (sudo depmod, sudo aticonfig --initial, sudo aticonfig --overlay-type=Xv)
I also changed default screen, and after reboot (or /etc/init.d/kdm restart) things still do not work. The same "input signal out of range" error!


I also tried to manually put HorizSync and VertRefresh into /etc/X11/xorg.conf (Section "Monitor": HorizSync 30.0 - 95.0, VertRefresh 50.0 - 160.0)

that is quite strange. I upgraded this machine from Hoary, where everything worked perfectly...

---

### Post by Matthai on 2006-06-09
Holly shit!

I just runned
sudo dpkg-reconfigure xserver-xorg

and pressed "enter" all the times, and now it works!

---

