---
title: "DNS in Ubuntu 12.04 and VPN"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by 3wheels1life on 2013-03-13
I hope you are all well. Here's my problem (I'll explain how I got here):
  I was running ubuntu 10.04, and I got [Mullvad]("http://mullvad.net") , a VPN service because it is anonymous and cheap.
  Mullvad VPN service installed perfectly on 10.04 and I have used it for about 1-2 months, without an issue. 
  Finally, in January I installed Ubuntu 12.04 via upgrade from 10.04, leaving mullvad installed. Everything still worked properly.
  Recently, however, with no changes to the software (as far as I know  other than Ubuntu updates, Mullvad wasn't working correctly. It would  say it was connected, but without the green checkmark indicating this  that was previously displayed in 12.04 and 10.04. I could still browse the internet..until about 2 days ago.
  My subscription expired, and I started up Mullvad (but without the  option to block connections on failure, because I was not a subscriber).  I still left Mullvad installed however. Later, I restarted my computer,  and this time did not start Mullvad/VPN at all.
  I could no longer access domain names, except for by typing in IP  addresses of sites. I searched via startpage, and I found a couple  articles. Apparently, I was supposed to move /etc/resolvconf. 
  I did this and now cannot access DNS. 

Thank you in advance.

---

### Post by jdthood on 2013-03-15
See: [http://askubuntu.com/questions/265376/problem-with-dns-in-ubuntu-12-04-and-mullvad-vpn](http://askubuntu.com/questions/265376/problem-with-dns-in-ubuntu-12-04-and-mullvad-vpn)

---

### Post by 3wheels1life on 2013-03-30
The post you linked to, I also authored, but could not reply to you directly.
Here's my edit and comments from [there]("http://askubuntu.com/questions/265376/problem-with-dns-in-ubuntu-12-04-and-mullvad-vpn").

EDIT: I followed the post [here]("http://askubuntu.com/questions/164342/internet-connection-not-working-although-it-says-it-is-connected") and did this:  sudo mv /etc/resolv.conf /etc/backup.resolv.conf  I did this and now cannot access DNS. Thank you in advance.

Hi, Thank you for the advice. I did this and  the terminal gave the following error: resolvconf:Error:  /etc/resolv.conf isn't a symlink, not doing anything. Please help.

Thank you for the advice @jdthood. I followed  your advice, and the terminal gave me an error:  "resolvconf:Error:/etc/resolv.conf isn't a symlink, not doing anything."  I think It has to do with what I did. I edited my question, because I  had used the following code (which was missing from the original post):  "sudo mv /etc/resolv.conf /etc/backup.resolv.conf" Thank you!

-3wheels1life

---

### Post by 3wheels1life on 2013-03-30
If you could help me with this after reading what I just wrote, I would really appreciate it!

-Thank you...

---

### Post by gordintoronto on 2013-03-31
Are you on a wired connection or wireless? DHCP or static?

---

### Post by 3wheels1life on 2013-04-03
DHCP wireless sometimes, wired other times

---

### Post by jdthood on 2013-04-03
To restore the symbolic link at resolv.conf, do "sudo ln -nsf ../run/resolvconf/resolv.conf /etc/resolv.conf".

---

### Post by 3wheels1life on 2013-04-04
I'm away from my desktop for a while, but when I'm back I'll let you know if that worked for me.
Thank you.

---

### Post by 3wheels1life on 2013-04-07
It works now! Thank you for all your help!

By the way, does Mullvad still have this problem on the new version?
[URL="https://www.mullvad.net/en/download.php"]
https://www.mullvad.net/en/news.php[/URL]
[https://www.mullvad.net/en/download.php](https://www.mullvad.net/en/download.php)

Thank you everyone!!

---

