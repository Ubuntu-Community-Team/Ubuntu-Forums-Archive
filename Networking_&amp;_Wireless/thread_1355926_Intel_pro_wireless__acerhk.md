---
title: "Intel pro wireless / acerhk"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by skeetwood-mac on 2009-12-15
Alright so after hours of searching and reading through threads I figured out how to install the acer hk driver. Every time I restart though my wireless stops working again and I have to run.

```
sudo -s 
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessle
```

how can I get around this?

---

### Post by chili555 on 2009-12-15
Add this:```
acerhk
```to */etc/modules*, and this:```
echo 1 > /proc/driver/acerhk/wirelessle
```to */etc/rc.local* right above 'exit 0.' I assume it's actually wirelessle[COLOR="Red"]d[/COLOR].

---

### Post by skeetwood-mac on 2009-12-15
> **chili555 said:**
> Add this:```
acerhk
```to */etc/modules*, and this:```
echo 1 > /proc/driver/acerhk/wirelessle
```to */etc/rc.local* right above 'exit 0.' I assume it's actually wirelessle[COLOR="Red"]d[/COLOR].

Thanks for the quick reply. I should have mentioned that I'm a total noob.

Im not exactly sure how to add acerhk to /etc/modules or  echo 1 > /proc/driver/acerhk/wirelessled to /etc/rc.local right above 'exit 0.'

This is only the second time I've had ubuntu. The first time was over a year ago,and I was starting to figure out some of the code. But then I got a mac. Well I just got a crappy old laptop and put ubuntu on it so I'm slowly learning again. 
A little more insight into how to write that code would be aweome.

---

### Post by chili555 on 2009-12-16
Open a terminal (Applications -> Accessories -> Terminal) and please do:```
sudo gedit /etc/modules
```The text editor will open and show the contents of the file. Yours probably looks like this:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
Edit it to look like this:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

acerhk
Proofread twice, save and close. Now do:```
sudo gedit /etc/rc.local
```Make the last part read like this:> # By default this script does nothing.

echo 1 > /proc/driver/acerhk/wirelessled

exit 0Proofread twice, save and close gedit. If you do not have gedit, use nano, kate or vim.

Again, may we assume you really mean wirelessle[COLOR="Red"]d[/COLOR]? Post back if you need more help, and, especially, to report if these steps do the trick.

---

### Post by skeetwood-mac on 2009-12-17
WOO that worked thanks so much! I'm starting to get the hang of this linux stuff. I'm still a little confused about the file system but I'll figure it out. Now I just gotta figure out why my computer goes to sleep when I plug in or un plug the power cord. I just changed it to shut off the monitor so it's not a big deal but seems a little weird. Anyways..thanks for the help I really appreciate it.

---

