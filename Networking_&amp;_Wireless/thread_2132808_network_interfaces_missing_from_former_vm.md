---
title: "network interfaces missing from former vm"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by hsartoris on 2013-04-05
I have extracted a heavily customized version of ubuntu from a virtual machine and set up a computer to boot it from an external hard drive.

Everything works fine, except that there don't appear to be any networking drivers whatsoever. I wouldn't expect it to, having previously been a virtual machine, but what is really getting me is that I can't successfully install any drivers. Thus far, I have installed the official linux drivers (the card is a realtek RTL8188CE) and used ndiswrapper to try both debugging and the windows drivers. Neither of these processes has had any success in terms of getting the interface to show up in iwconfig, which outputs only lo and eth0, neither of which have wireless extensions. Incidentally, only lo shows up in ifconfig.

When I use ndiswrapper to install the drivers, everything goes as normal until ```
modprobe ndiswrapper
``` which shows nothing whatsoever. ```
ndiswrapper -l
``` returns successfully.

I have removed the vmware config files from /etc/modprobe.d. What else can I do?

---

### Post by wildmanne39 on 2013-04-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

You should know that the driver for your device is problematic before we go any further.
Thanks

---

### Post by hsartoris on 2013-04-06
After some hassle with windows character encoding, here it is.

---

### Post by wildmanne39 on 2013-04-06
There is lot of information that should be there but is not, did you do a minimal install when you created the vm? or a server install?

Let's check if network manager or wicd is installed:
```
ps aux | egrep 'Network|wicd'
```
please try:
```
sudo modprobe rtl8192ce
```
You also have two drivers instlled for your eithernet connection.
Thanks

---

