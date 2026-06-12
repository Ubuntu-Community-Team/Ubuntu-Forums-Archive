---
title: "Authorization Dialog for Windows XP Share help"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by eduardoeltortuga on 2009-08-09
Why does the Authorization Dialog box keep popping up? What user name and password is it talking about? I've set up samba before but I've never had so many problems. I thought if I added a user and password in the samba con.f file it would take care of the Authorization Dialog. I also added mshome workgroup to the file.
  Ubuntu is networking with XP just fine. Do I have to set-up a password in my XP machine? I've been working on this all weekend!](*,)

---

### Post by dmizer on 2009-08-09
Take a look at the 6th link in my sig.

If that doesn't help, please post your current /etc/samba/smb.conf file.

Also, are you trying to connect from Windows to Ubuntu or from Ubuntu to Windows?

---

### Post by eduardoeltortuga on 2009-08-10
Both. I can open Kubuntu shares in Windows, but I keep getting asked for user/pass while trying to get Windows shares from Kubuntu. I can sometimes open the shares and the files inside but then I start getting asked for user/password. I've set up samba before and I've never had any problems.

---

### Post by the_mouse on 2010-02-15
Have you managed to find a fix this issue?

I remember a year ago I was able to browse seamlessly the shared folders of my winxp machine but now it can't even connect if I type smb://winxp-machine-name (dolphon says "Can't connect to winxp-machine-name").

If I type smb://192.168.1.101 I can see the list of shared folders but if I open some of them I get asked for username and a password. If I try to browse the same shares from another winxp machine there's no authorization dialog... :(

I'll take a look at [Fix samba browsing!!!]("http://ubuntuforums.org/showthread.php?t=1169149") (10x  dmizer) and see if it works.

However I'm very suprised of this issue, since I haven't changed my configuration, only the Kubuntu version:
8.10 - no issues woth samba
9.40 and 9.10 - authorization dialog keeps popping out :(

---

### Post by eduardoeltortuga on 2011-03-12
Hello
No, I still can't connect to my windows xp shares from Kubuntu. I've searched the internet hi and low but still don't know how to fix this issue. I want to embrace Kubuntu, but this issue keeps me holding me back. By the way, I can open XP shares with Ubuntu.

---

### Post by the_mouse on 2011-03-13
Well, apparently is a Kubuntu / Dolphin / Samba issue.
The interesting part is that sometimes I can browse through shared folders without any problem at all, and sometimes after I go through a few folders, the auth. dialog appears :(.

---

