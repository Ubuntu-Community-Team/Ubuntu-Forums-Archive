---
title: "Install Samba on Xubuntu 13.04"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2013-05-25
Hi all

Just looking for the correct command to install Samba (and the GUI) on a brand new install of Xubuntu 13.04.

I've found conflicting commands, the first of which **sudo apt-get install samba4** took ages to run and had loads of things about creating DNS partitions, which seemed a bit over the top!  Seemed like it was turning my entire machine into a server!

Then I tried **sudo apt-get install samba system-config-samba cifs-utils** which seemed to work and gave me a GUI to create some shares, which I could access from another computer and my phone.

However, within the GUI there was a weird error which related I think to the weird things from that earlier samba4 command.

And so, I had a bit of a panic and did **sudo apt-get remove --purge samba**, followed by **sudo apt-get install samba system-config-samba cifs-utils** again but then the GUI wouldn't start at all.

So I did another **sudo apt-get remove --purge samba** and have left it at that since.

So all I need are the simple lines to install samba with the GUI to share my music & video folders.

Many thanks as ever!

Dave

---

### Post by Merrattic on 2013-05-26
Not sure if this is still up to date, but appears to do the trick:

[http://www.unixmen.com/how-to-configure-samba-using-a-graphical-interface-in-ubuntu/](http://www.unixmen.com/how-to-configure-samba-using-a-graphical-interface-in-ubuntu/)

(Installing **samba4** is an option, just **samba** will do in most situations!). You may need to un-install samba4 ?)

---

