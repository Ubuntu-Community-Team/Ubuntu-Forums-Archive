---
title: "realtek RTL8191"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by sakala on 2010-02-03
just installed ubuntu 9.1 on my Toshiba L450 can't seem to have wireless internet connection.wireless driver on my machine is realtek RTL8191se.need help please anyone

---

### Post by jsampaio57 on 2010-03-14
> **sakala said:**
> just installed ubuntu 9.1 on my Toshiba L450 can't seem to have wireless internet connection.wireless driver on my machine is realtek RTL8191se.need help please anyone

you need to install the rtl819x driver. Pick it here [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true")

untar it, and compile with:
sudo su
make
make install

then reboot

cheers...
jorge

---

### Post by chili555 on 2010-03-14
In order to compile this, you also need to:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by rushing1 on 2010-03-16
I followed the above instructions and have a working Kubuntu 9.10 installation using WPA2 and the network manager.  Adding the Linux driver worked on my Toshiba L555D-2005, dual-booting with Windows 7.

However, the wireless failed when I applied the 186 bug fixes since the iso image that were reported by kPackageKit.  I spent a day trying to fix my wireless, then noticed the kernel had been updated from 2.6.31-14 to 2.6.31-20.

I tried to make uninstall, make clean, then re-make and install in the 2.6.31-20 kernel. The wireless network would show, but network manager would not connect. I spent most of the day trying to resolve this issue.

I gave up, and re-installed from the iso disk this morning, added the driver and my wireless was working again.

I applied all bug-fixes except the 4 entries for the update from 2.6.31-14 to 2.6.31-20, rebooted, and my wireless kept working.

I applied the kernel update, uninstalled the driver and rebooted.

I compiled and installed the driver against the new kernel and rebooted, My wireless still was visible but would not connect.

At this point, I uninstalled the driver, rebooted to 2.6.31-14 using grub, re-compiled, re-installed the driver and have a working system.

I hope this helps others looking at this issue.


Is there a step I missed in re-compiling to the new kernel, or is there a way to find out why I could not get the driver to work in the newer kernel?

---

