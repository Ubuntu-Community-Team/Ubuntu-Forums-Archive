---
title: "Cannot figure out how to get online!"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by HollyThornton on 2009-10-12
I just received a computer from someone on Freecycle and it is operating on Edubuntu. I am totally new to this operating system and since it was given to me by a stranger, there really isnt anyone that I can ask for help from. I am using a direct internet connection but when I attempt to go to google or any other website, I am told that it cannot find the site. It says that either i misspelled the website or need to check my Network or DNS settings. I do not know how to find these settings and even if i do, im not sure what the settings should be. This is my first personal computer (we have been using the PS3 to go online) and I have no idea how to hook it up to the internet properly. Do I need a DNS code or something? Please help!

---

### Post by viper250 on 2009-10-12
you need to check and see what  your broadband connection requires
for example dsl by default uses dhcp  and linux usually sets up with dhcp by default.
but some  network modems use a static ip address.
you also need to check the properties of the network connection
wired network would be listed as eth0 wireless would be listed as eth1
 I will research this a bit more for you and get back to you a bit later:P

---

### Post by HollyThornton on 2009-10-12
Thanks a bunch. I know I was using dhcp and eth0. Any help you could give would be greatly appreciated. I can find anything on Windows but it seems like Linux is so hard to navigate.

---

### Post by viper250 on 2009-10-12
found a download site so i can check out the distro but I need to know what version you have

---

### Post by HollyThornton on 2009-10-12
Its Edubuntu 8.10

---

### Post by blur xc on 2009-10-12
> **HollyThornton said:**
> Thanks a bunch. I know I was using dhcp and eth0. Any help you could give would be greatly appreciated. I can find anything on Windows but it seems like Linux is so hard to navigate.


First off, I feel that I just need to point out how funny thread titles like, "I can't get online!" look, when obviously you had to get online to post it...  

Linux isn't any harder to navigate than windows, it's just different.  If are looking for a control panel- you aren't going to find it.  You've been using windows for a long time, and that's why you know it so well.  If you had used linux all those years instead of windows, and sat in front of a windows computer, you'd more than likely feel like it was hard to navigate.  It just takes a few months to learn something new.

Good luck, and have fun with it...

BM

---

### Post by viper250 on 2009-10-12
checked out 6 ubuntu distros and all setup eth0 as dhcp automatic virtually all linux distros setup eth0 the same.
 although there are some that do not set up automatic they still detect them.
anyhow click on the system menu , select administration, select networking. when the box pops up click on wired network and click on properties. make sure that the connection is enabled.

---

### Post by Iowan on 2009-10-13
I skipped 8.04 and 8.10 desktops (and have never used Edubuntu), so I'm kinda running blind...
DNS settings are usually stored in the file */etc/resolv.conf*. Ordinarily, Network Manager or the DHCP client (dhclient) gets that information.

---

