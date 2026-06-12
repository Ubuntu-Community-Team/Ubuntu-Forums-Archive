---
title: "VPN can not access web site hosted by Ubuntu"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by 2ndPlaceFinish on 2009-01-28
I have successfully set up VPN on my home network allowing others to connect to one of my computers. However when trying to access an internal website there are a few issues.

First, when going to the default page (192.168.0.12), Ubuntu serves it to the computer connected to the VPN just fine. However if I try to access any of the TRAC pages (ex. 192.168.0.12/projects/test) I have hosted on the server, it can not access the page. Does this have something to do with the authentication I have set up on the page? 

I can connect to the TRAC pages fine when I am on my network, just not when connected via VPN. When connecting from within my network it asks for my authentication credentials.

Any help or ideas would be appreciated.

---

### Post by 2ndPlaceFinish on 2009-01-29
I should also note that it does ask for my user name and password on the projects page, but I am unable to access any of the specific TRAC projects.

I am not sure if this has something to do with the VPN client/server I am using (both windows machines), but because I can connect to the basic website at 192.168.0.12 it makes me believe it is something to do with Ubuntu's configuration (I could be wrong though).

---

### Post by jms1989 on 2009-01-29
well, i believe, for a server to read normal users files they have to be 755 for the directories and 644 for the files. they must be world readable for it to work.

---

### Post by 2ndPlaceFinish on 2009-01-29
I am pretty sure I have all the permissions set correctly on the server. All TRAC directories are owned by www-data and set to 755. Thanks for the help though. Any more options?

---

### Post by 2ndPlaceFinish on 2009-02-03
It seems to be the same thing with my SVN. Small updates or commits work ok, however anything more than a small text file and it freezes it up (looks like it is loading forever). 

I think this has something to do with some type of size issue as the very basic (text only pages) of my website will show up, however any page with images will not appear (it looks like it loads forever)

After reading some forums it suggested I change my MTU size from 1500 to 1400 on my windows machine (The VPN Client) but this did not work.

I really need to get this working so my friends and I can collaborate on projects without having to be on the local network.

Any help would be greatly appreciated.

Thanks in advance,
Shane

---

### Post by 2ndPlaceFinish on 2009-02-03
Apparently the Max MTU size that works with my VPN Connection is 1200. After I changed that on my VPN Client everything works fine. I guess this was not an issue with my server after all. Thanks for the help.

---

