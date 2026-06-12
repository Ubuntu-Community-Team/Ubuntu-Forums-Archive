---
title: "Ralink RT5370 problem! HELP!"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by lJ9%3MR&gt;sa on 2012-03-30
I'm running Xubuntu 11.10 and I'm having issues with my generic Ralink RT5370 usb wifi.

I'm trying to make it load itself on startup. I have to type this manually to start the wifi:
modprobe rt2800usb
sudo -s
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id
exit

Can you please help me! I've tried adding something to /etc/modules or something like that but to not success. help...:p

---

### Post by lJ9%3MR&gt;sa on 2012-03-31
Bump. Do you need more info!? PLEASE HELP ME SOLVE THIS PROBLEM!:mad::mad::mad::mad::mad::mad:

---

### Post by lJ9%3MR&gt;sa on 2012-03-31
I've figured it out! Don't post to this post... By the way, can a moderator please close it or tell me how?

---

### Post by kurt18947 on 2012-03-31
> **faxmanloveswaffles said:**
> I've figured it out! Don't post to this post... By the way, can a moderator please close it or tell me how?

Being the thread originator, you can mark it solved using 'thread tools' at the top of the page.  Documenting how you solved your problem is a help to others who search and find your thread.  Reading "solved" threads is oftentimes helpful.

---

### Post by colorprint on 2012-05-01
> **faxmanloveswaffles said:**
> I've figured it out! Don't post to this post... By the way, can a moderator please close it or tell me how?

I have the same problem. How have you resolved this?

---

### Post by chili555 on 2012-05-01
Please see post #6 and following here: [http://ubuntuforums.org/showthread.php?p=11861862](http://ubuntuforums.org/showthread.php?p=11861862)

---

### Post by colorprint on 2012-05-01
I have found some solution here:  [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

---

### Post by colorprint on 2012-05-01
> **chili555 said:**
> Please see post #6 and following here: [http://ubuntuforums.org/showthread.php?p=11861862](http://ubuntuforums.org/showthread.php?p=11861862)
oh, thanks for your solution too!

---

