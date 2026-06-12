---
title: "[SOLVED] Torrent download speeds too low? Software?"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by Ben Page on 2008-12-18
Hello!
After resolving that internet "lockup" issue...

Linux renew ip command
The -r flag explicitly releases the current lease, and once the lease has been released, the client exits. For example, open terminal and type the command:

$ sudo dhclient -r

Now obtain fresh IP:

$ sudo dhclient

...i finaly got stable internet connection, resolved locking up, and I have no need for network restart anymore! BUT!
Now i have noticed a significantly lower average dnld speeds in torrent clients (I have tried Wine microtorrent, Deluge, Jaber, Ktorrent and even Opera torrent download manager). Is this due to software or is it a hardware thing. In Winblows, microtorrent has average speed, for example 25 kbps, but in Ubuntu any of these torrent clients have avg of 15 kbps on same torrent! Is this incompatibility between Win and Lin peers?

But internet connection works in same speeds when browsing pages through Opera or FF, and now I am downloading open SUSE 11.1 via HTTP and it is downloading in full speed in Ubuntu.

Is this torrent client issue or something else? Is there a good lightweight torrent cl that works fine, is there a setting that I can fiddle with to get full speed in Ubuntu torrent cl.?

router: AolYnk, Realtek integrated, dynamic IP.

---

### Post by Ben Page on 2008-12-21
bump! :)

Now i'm in Linux Mint 6, but its the same thing as Ubuntu 8.10 (network at least), and I have experienced the same internet "lockup" problems, solved them in the same manner, with couple of logouts and suspends after typing the code, BUT the problem with torrents presists, everithing else internet related works fine, surfing, email, http downloading, package downloading, updating...I have tried every torrent software available for linux and trough Wine, all were in default settings, any clue?

---

### Post by superprash2003 on 2008-12-21
which port does your torrent client use?? check to see if that port is open using this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by Ben Page on 2008-12-21
All my torrent client use 6881 by default, I never changed that, or any settings in any OS. The site is saing that this port is not working, could this be the problem? I have some download speed, but its 40% slower than dnld speed in Win. What port range should I try? Or what port?

---

### Post by djbushido on 2008-12-21
It doesn't really matter what port you need to do, just try random port numbers (above 1024 - for some reason lower doesn't work at all for me), until something works using the above site.

---

### Post by Ben Page on 2008-12-22
no go! :(

I have scaned 500 ports, and non of them is working (I checked those recomended, too). I dont really understand this port thing, but I did everithing the site and you people say. Is this a problem with something else? Its strange that souch large range of ports are not working at all...:confused:

---

### Post by superprash2003 on 2008-12-23
it has something to do with port forwarding.. login to your router and check under virtual server if you have port forwarded properly. if possible post a screenshot of that page.. and post output of ifconfig from the terminal.. and also output of sudo iptables -L

---

### Post by Ben Page on 2009-01-08
Just to make a note on this issue, it solved by it self by installing Ubuntu in its own partition and in its own file-system (ext3). Internet works perfectly (same as in win) now, while in Wubi install it had some serious issues (but that's tolerable since it was only virtual install).

---

