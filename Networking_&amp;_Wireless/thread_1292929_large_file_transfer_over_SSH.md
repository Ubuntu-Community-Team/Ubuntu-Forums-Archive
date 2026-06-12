---
title: "large file transfer over SSH"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by TheBuzzSaw on 2009-10-16
I use my laptop to connect to my desktop through SSH over my router (wireless). Everything works great, but I recently noticed that I struggle transferring large files. The transfer rate is extremely high, but it suddenly stalls, and I have no connection for a while. Is this an SSH thing? Or my router? I figured it might be my DoS protection, so I turned that off. It still stalls. I disabled my router's firewall entirely, and the transfer still stalls.

The file is ~500MB.

Ideas? :(

---

### Post by jonobr on 2009-10-16
Im figuring the best approach would be to setup an Ftp server temporarily.

Try copying the file using ftp and see if you get the same stalling action.

If that shows the same result, I would try using a different machine if you have one handy. 
Also, if its wireless, have you tried with wired to see if makes a diff?

---

### Post by sprouty on 2009-10-16
If i was you i would split the file into smaller chunks. You'r isp might be doing somethng funny if you use to much badwidth at once.

Information on the split command:
[http://www.computerhope.com/unix/usplit.htm](http://www.computerhope.com/unix/usplit.htm)

you can use cat to put it all back togerther :-D

---

### Post by jonobr on 2009-10-16
I was thinking that going laptop to desktop was within your own network and not going across the ISP,
is that a wrong assumption?
Are you going to a desktop in work / Univ or other through the internet?

Thanks

---

### Post by TheBuzzSaw on 2009-10-16
It's not going over my ISP. >_>

My desktop is plugged into the router. My laptop is connected over wireless.

---

### Post by aesis05401 on 2009-10-16
How are you set up? Are you using an SSH file-system or just logging in and attempting to perform the action?

Edit: Look here: [http://ubuntuforums.org/showpost.php?p=3767474&postcount=11]("http://ubuntuforums.org/showpost.php?p=3767474&postcount=11")

Poster says that he optimized max transfer unit on wireless card by observing ping response times.  Lowering MTU resulted in many fewer dropped packets and allowed transfer of very large files.  I can't vouch for the solution, but it might be worth a shot.

---

