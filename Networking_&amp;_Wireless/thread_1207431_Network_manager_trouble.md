---
title: "Network manager trouble"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by benh13 on 2009-07-08
i am new to ubuntu, and while trying to set up a static ip, i uninstalled network manager and have no internet connection on that computer. however, many people say this was bad advice and i can't re install it. is there any way to reinstall network manager gnome without internet connection? 
 
i have tried setting up the static ip address but it won't give me permission to save the file now that i have edited the network interface.
 
is there anything i can do?
thanks

---

### Post by aysiu on 2009-07-09
You can go to the Ubuntu Packages website:
[http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=all&section=all)

On an internet-connected computer, download the *network-manager* and *network-manager-gnome* .deb packages for your appropriate Ubuntu release (9.04 is Jaunty, 8.10 is Intrepid, 8.04 is Hardy).

Transfer them to the desktop folder of your Ubuntu computer (via USB stick, I guess).

Then, in [the terminal](http://www.psychocats.net/ubuntu/terminal), type ```
cd ~/Desktop
sudo dpkg -i network*.deb
```

---

