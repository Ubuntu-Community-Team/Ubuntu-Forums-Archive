---
title: "Wireless not staying connected"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by vDub2000 on 2013-02-20
I've been having this problem every time I've tried installing and using Ubuntu 12.10 but I have not been able to find a solution for the problem.

I have a USB wireless network adapter that shows up as a "Realtek RTL8188CU Wireless LAN 802.11n USB Network Adapter" in Device Manager in Windows, but I've forgotten how to look that stuff up in Linux since I haven't used it in a while.

Anyway, Ubuntu is able to find my network and I'm able to put in my password, however it simply will not connect and it'll frequently re-prompt me for the password even though it is correct. The last time I booted into Ubuntu, it was connected for a few seconds before it disconnected and would not re-connect.

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by vDub2000 on 2013-02-20
I think I may have misunderstood one of the steps in that post you linked me to because now it can't find my network at all.

I blacklisted the things that you specified in your post and added "8192cu" to the end of /etc/modules and rebooted my computer to implement the changes that were made, which is when I noticed there was a problem.

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by vDub2000 on 2013-02-20
Nope, I downloaded the driver for my actual device. *lol*

I'll give it another go and let you know whether it succeeds.

---

### Post by vDub2000 on 2013-02-20
Okay, I made sure to download the driver for the 8192CU and the file downloaded was the same one I downloaded the first time and despite having followed your steps, it's still not seeing my network anymore.

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by vDub2000 on 2013-02-20
I get a couple of make errors at the end, but it seemed like it was due to a missing directory.

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by vDub2000 on 2013-02-22
When I ran the command "sudo lshw -C network" it says driver="rtl8192cu" which is the driver I downloaded from Realtek's website.

---

### Post by vDub2000 on 2013-02-25
so I guess no one else is able to help me? :-(

---

### Post by vDub2000 on 2013-02-25
*sigh* I guess I'll be avoiding Linux for a little while longer then...

---

### Post by vDub2000 on 2013-03-02
Still holding out for some more assistance with this...

---

