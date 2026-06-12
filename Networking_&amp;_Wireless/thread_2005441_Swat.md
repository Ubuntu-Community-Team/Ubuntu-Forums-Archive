---
title: "Swat"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by pauldmallett on 2012-06-17
Hi all,
 Ubuntu 12.04 server full reinstall,Samba works fine but and I quote from the only other reference to this problem that i have found.
 "I am able to login to swat (as root) and see all the categories - Global, Shares, Printers, etc... It is able to read from my current smb.conf when I go to the View category. It seems like the html form is broken because "commit changes" and Change View To: Basic or Advanced do absolutely nothing."
 Also Shares are not visible but printers are??
 I have had a good look at all the relevant files, restarted Samba & xinetd.
 All and any suggestions considered.

---

### Post by Morbius1 on 2012-06-17
swat is no longer maintained and hasn't been for some time. Also, swat destroys the original working smb.conf file and replaces it with something that I'm sure it considered workable in it's day.

IF you have a specific problem with your shares you might want to post the output of the following command:
```
testparm -s
```Note: I haven't used swat in a very long time but as I remember it it doesn't play nice with hand edited smb.conf files so you'll either have to find someone that remembers how swat works or remove swat and start editing smb.conf with a text editor.

---

