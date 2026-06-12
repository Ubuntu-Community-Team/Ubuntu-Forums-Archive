---
title: "Realtek RTL8111E linux network driver not working"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by technel on 2013-05-24
I am running a fresh install of Ubuntu 12.04 LTS on my desktop with a Gigabyte GA-Z68A-D3H-B3 motherboard, which (unfortunately) uses the Realtek RTL8111E LAN chip. It's a well documented issue that the network cuts in and out or runs very slowly on Linux—I'm experiencing this as well.

I downloaded the [official Realtek driver](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8168E/RTL8111F) (r8168-8.035.00.tar.bz2) and successfully ran "sudo ./autorun.sh".

If I run this script while my network is non-functional, it will fix it. However, inevitably, a couple minutes later, the network will cut out again until I re-run the script.

I'm not sure exactly what's going on. Realtek did not respond to my support request, I have tried numerous online tutorials for older versions of the driver/kernel, and I attempted to make the switchmod script work. I didn't have success with any of them. (Note: Unlike [this guy](http://ubuntuforums.org/showthread.php?t=2138125), my motherboard does not support IOMMU, so that's not a viable solution either.)

If someone could help offer suggestions or troubleshoot this issue, I would *really* appreciate it! Thanks!

---

### Post by varunendra on 2013-05-29
> **technel said:**
> If I run this script while my network is non-functional, it will fix it. However, inevitably, a couple minutes later, the network will cut out again until I re-run the script.
As soon as you get it fixed by running the script, please post-
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
dmesg | grep -iE 'r81|eth|network'
```

Then, when it cuts out again, do -
```
ifconfig
dmesg | grep -iE 'r81|eth|network'
cat /var/log/syslog | grep -iE 'r81|eth|network'
```

As soon as it cuts off, also take a look at -
```
cat /var/log/syslog | tail -40
```
and post its output too if there are any relevant messages in it that are not covered in the last command output above.

---

### Post by technel on 2013-05-29
> **varunendra said:**
> As soon as you get it fixed by running the script, please post-
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
dmesg | grep -iE 'r81|eth|network'
```

Then, when it cuts out again, do -
```
ifconfig
dmesg | grep -iE 'r81|eth|network'
cat /var/log/syslog | grep -iE 'r81|eth|network'
```

As soon as it cuts off, also take a look at -
```
cat /var/log/syslog | tail -40
```
and post its output too if there are any relevant messages in it that are not covered in the last command output above.

Hi there!

I appreciate your help, but I didn't think I was going to get a response, so I already bought a new network card... Thanks anyway!

---

### Post by varunendra on 2013-05-29
Yeah, a response 4 days later.., I wasn't hoping for a response either.

Hope the new card is happy with Linux :)

Feel free to post back anytime if you need to get the onboard one working as well. I can't promise, but I'll try my best :)

---

