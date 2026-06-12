---
title: "Alienware m17/Ubuntu no network devices found on fresh install"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by RobAmesquita on 2013-08-30
Just installed ubuntu and had no Wi-Fi interfaces recognized so tried wired and still Ubuntu does not recognize any network devices at all. I'm sure if I could get online I could fix the Wi-Fi issue but cannot connect in any way, shape or form. I have my alienware resource cd but it's packaged in .exe if that's any help

---

### Post by chili555 on 2013-08-30
Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
lsb_release -d
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by javahollic on 2013-09-11
I just had this exact problem, Id paste the result but it doesnt even see my USB key.

I have:
- 08:00.0 Ethernet Controller [0200]: Qulacomm Atheros Killer E2200 Gigabit ethernet Controller [1969:e091] (rev 10)
- 0a:00.0 Network Controller [0280]: Broadcom Corporation Deveice [14e4:43b1] (rev 03)

release:  Ubuntu 13.04 (off a freshly burned ISO image retrieved today

---

### Post by chili555 on 2013-09-11
Here is the answer for your wireless: [http://askubuntu.com/questions/251163/is-there-a-way-to-get-broadcom-802-11ac-wifi-43b1-working-on-ubuntu-12-10](http://askubuntu.com/questions/251163/is-there-a-way-to-get-broadcom-802-11ac-wifi-43b1-working-on-ubuntu-12-10)> Of course, you could buy a cheap USB wireless device and wait. – chili555 Feb 4 at 16:17And here is your ethernet: [http://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200](http://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200) See post #4. As you can see, it's an involved process that involves a lot of downloads; hard to do without an internet connection.

If it were my computer, I'd borrow or buy a USB wireless and get the ethernet going. I'd wait on future developments for your wireless; it may take a few months.

---

### Post by jlope001 on 2013-09-20
Hi,  I also have an alienware 14 that I purchased the a few days ago.  Same issue, no working ethernet or wireless with the same specs you mentioned.  

```

$ lspci | grep E2200
08:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 10)

```

Wireless drivers
```

0a:00.0 Network controller: Broadcom Corporation Device 43b1 (rev 03)
```
 

After a few hours of searching I found a post that mentioned that the kernel 3.10 had working ethernet drivers for E2200

[http://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working](http://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working)


I used the page below and followed the instructions (on a different machine, I downloaded the three repos).  Copied them over to the alienware machine and ran the commands in the post.  
[http://ubuntuhandbook.org/index.php/2013/08/linux-kernel-3-10-10-released-install-upgrade-in-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/08/linux-kernel-3-10-10-released-install-upgrade-in-ubuntu-13-04/)

Restarted the computer and ethernet worked like a charm!  I still don't have wireless, but thats' another issue i'll tackle later.

---

