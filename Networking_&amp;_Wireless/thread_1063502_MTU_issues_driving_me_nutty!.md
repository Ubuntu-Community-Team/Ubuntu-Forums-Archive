---
title: "MTU issues driving me nutty!"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by maximinus_uk on 2009-02-07
Hi all

My new internet connection works just fine under windows, and almost works just fine under Linux. I can browse google and that's about it!

However, a little research on this site and I have found that the problem is the MTU on the ADSL modem router is set to 1500. What I have to do is change this to 1492.

But I have a no-name Chinese ADSL modem (since I live in China) and I have no way of changing that setting.

Does anybody know of any way that I can make things work from only the Linux end? I'm having to post this from XP!

Thanks

---

### Post by maximinus_uk on 2009-02-08
Solved it after a good few attempts.

Basically, it helps if you have another OS that works. I ran windows and from a command prompt did:

ping -l SOME_NUMBER [www.google.com](www.google.com)

With some number starting at 1592 and counting down. You want to find the highest value at which google responds. This was 1452 for me. Now reboot into linux, go to the terminal and type ifconfig. You should see at least 2 connections: the eth0 and ppp0. Enter this command:

sudo ifconfig ppp0 mtu 1452

replacing 1452 with whatever value you got from the first part. Problem solved!

---

