---
title: "Ubuntu 11.04 - Cannot Connect Wirelessly"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by MrHappyGoLucky12 on 2011-08-29
My network controller is a Broadcom BCM4311 and my PCI-ID is 14e4:4311.  The computer is a Dell Inspiron 1520.

I have tried every step on this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers) but nothing works.

This is a screenshot of what I see under Network Connections: [http://img845.imageshack.us/img845/3332/screenshotkf.png](http://img845.imageshack.us/img845/3332/screenshotkf.png) .

Should my wireless connection automatically appear under Network Connections or do I need to manually add it?  What other steps should I try?  :confused:

---

### Post by wildmanne39 on 2011-08-29
Hi, open synaptic and type in bcm then uninstall everything there with a green square, then reboot.

Then run this command
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
then disconnect your wired connection and restart your computer and it should work if not post back if it does please mark solved.
Thank you

---

### Post by MrHappyGoLucky12 on 2011-08-30
I had an extra USB wireless adapter here and plugged it in.  It  immediately identified my wireless network and I was able to connect.   However, my internal wireless adapter still works if I boot into another  operating system, so I know it's not broke either.  Weird...

---

### Post by wildmanne39 on 2011-08-30
Hi, have you tried what I mentioned in post 2?

---

### Post by MrHappyGoLucky12 on 2011-08-30
> **wildmanne39 said:**
> Hi, have you tried what I mentioned in post 2?

wildmanne39,

Great work!  Thanks for your help.  Works great!

John

---

### Post by wildmanne39 on 2011-08-30
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by mkintzel on 2011-09-16
I tried the two commands listed in the second post - still not working.

lspci | grep Broadcom
03:00.0 Network: Broadcom Corporation BCM4311 802.11 b/g WLAN (rev 01)

what else should I try?  Kinda new to all of this.  Thanks for any help you can provide.

---

### Post by dennis_matutina on 2011-09-16
Hi all, thank you for all the help and feedback in this thread and other posts elsewhere, I managed to connect my Ubuntu 11.04 using b43-fwcutter after 2 days of trying all the solutions I could find. But I only narrowed down the culprit just a few minutes ago why I cannot connect to wireless at home but can connect to my wifi at the office: *check if your router uses [COLOR="DarkRed"]WPA/WPA2[/COLOR] or [COLOR="DarkRed"]WPA2 only[/COLOR]. If it is the former, try changing it to WPA Only or ** WPA2 Only***. 

I am using a D-Link DIR-300 at home and that router has the WPA/WPA2 option, which the driver apparently does not like. Good luck to all who are still struggling with this :D ):P

---

### Post by mkintzel on 2011-09-16
Fixed by the following steps - thanks to the post by mangames at
[http://ubuntuforums.org/showthread.php?t=1785881](http://ubuntuforums.org/showthread.php?t=1785881)


[FONT=Arial][SIZE=3]This is solved.... I am all set now after trying the below steps :

1) Use below command to uninstall the default installed driver :

[COLOR=DarkRed]sudo apt-get remove bcmwl-kernel-source

[COLOR=Black]2) Once above step is done, download below driver for 32-bit/64-bit system respectively :

[/COLOR][/COLOR][/SIZE][/FONT][SIZE=3]For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/...untu5_i386.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb")[/SIZE]
[SIZE=3][URL="http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb"]
[/URL][/SIZE]
[SIZE=3]For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/...ntu5_amd64.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")[/SIZE]

[FONT=Arial][SIZE=3][COLOR=DarkRed][COLOR=Black]
3) Install the downloaded file and restart. Now the wireless networks will show up and you should be all set.

[/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-09-16
Hi, welcome to the forum! I am glad you have it working.

---

