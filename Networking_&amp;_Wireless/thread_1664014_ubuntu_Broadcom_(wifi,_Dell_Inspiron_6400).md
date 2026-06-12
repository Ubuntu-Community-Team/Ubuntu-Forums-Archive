---
title: "ubuntu Broadcom (wifi, Dell Inspiron 6400)"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by woundedtiger40 on 2011-01-10
Dear Members,

I have installed ubuntu on my Dell Inspiron 6400, and it has Broadcom  for using wifi, First time I connected with internet through LAN cable,  and installed the broadcom driver successfully and used wireless  internet. But when I restarted my laptop I had to repeat the procedure  again (i.e. connect to lan and download the broadcom driver and install  and use the wireless), and everytime when I have to use wireless  internet I have to do the same thing. What should I do? Please help me.

Thanks in advance.

Best regards.

---

### Post by howefield on 2011-01-10
Moved to Networking and Wireless.

---

### Post by PatchesTheCaveman on 2011-01-11
Please reboot, and complete the following steps **before** you try and install the STA driver again.

Go to Applications > Accessories > Terminal on your top panel.  Then, type the following command and press Enter:
```
sudo modprobe wl
```
You will be asked for password.  Type it in and press Enter.  It won't show stars or dots or anything, but it will work.

After that, click on the network icon and see if you can connect to your wireless networks now.  If so, run this command to make the above fix permanent:
```
sudo bash -c "echo wl >> /etc/modules"
```

If not, run these commands:
```
lsmod
lshw -C network
dpkg-query -s bcmwl-kernel-source
```
and copy/paste the output to a reply to this thread, and we'll see what else we can do.

---

