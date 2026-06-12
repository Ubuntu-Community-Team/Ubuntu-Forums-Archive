---
title: "Failed to retrieve share list from server"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2011-07-31
Hi all.

My flatmates just set up a windows server to share media.
If I use nautilus, I can see something called "Windows Network". But if I click on it, or try to open it, I get the error message:
> Failed to retrieve share list from server

I have nautilus-share and smb installed.

How do I now actually connect to a windows shared folder?

---

### Post by Morbius1 on 2011-07-31
Access it directly by ip address:
```
nautilus smb://192.168.0.100
```
Change 192.18.0.100 to the ip address of the Windows server.

---

### Post by jibal on 2011-11-23
> **Morbius1 said:**
> Access it directly by ip address:
```
nautilus smb://192.168.0.100
```Change 192.18.0.100 to the ip address of the Windows server.

That's not helpful.

---

### Post by dandnsmith on 2011-11-23
This one's a bit tricky without more detail, but you could see what the response to *sudo smbtree* (in a terminal window) is.
You may well be foundering on a firewall (probably at the Windows end).

---

### Post by red40y on 2011-12-20
i read this hoping for help, however, i got an idea when i read about firewall issues. on my windows computer i had to allow sharing over the network.(it was set to not share over the network even with homegroup set up) after i did that i was able to connect to windows through browse network tab in home folder. 

browse network-->windows network-->workgroup-->choose computer. 

it asked me for user name and password fore workgroup and i was in. i can now transfer from ubuntu to windows. but not windows to ubuntu. but no matter, it works for me for now. i hope this helps you, good luck.

---

### Post by spin498 on 2011-12-30
I'm having similar issues. I'm confused by the fact that if I try to get on my network, I see 2 icons for my Mac, no icons for any of my Win7 machines or my Amahi file server. When I run smbtree it does show the Win 7 machines and this error message for each "cli_start_connection: failed to connect to 'whichever'PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL" Again no listing for the Amahi server.

---

### Post by ianchai on 2012-02-22
I found a solution that works for me -- it's a bug in the /etc/samba/smb.conf file in Ubuntu 11.10

Need to add "name resolve order = bcast host" to that file and restart Samba.

I found the solution at [http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

---

### Post by capscrew on 2012-02-22
> **ianchai said:**
> I found a solution that works for me -- it's a bug in the /etc/samba/smb.conf file in Ubuntu 11.10

Need to add "name resolve order = bcast host" to that file and restart Samba.

I found the solution at [http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)
It's NOT a "bug".  You can configure the method the Samba "node" responds on the network.  Using bcast first makes this a B-node (it broadcasts its IP address and netbios name).

---

### Post by ame82 on 2012-09-10
> **capscrew said:**
> It's NOT a "bug".  You can configure the method the Samba "node" responds on the network.  Using bcast first makes this a B-node (it broadcasts its IP address and netbios name).

plz guys we just starting more details , how can i do that?
i have problem and my ubuntu 12.4 can never acces shared folder in another 12.4 what a shame , simple task taking forever

---

### Post by itpro007ca on 2012-12-06
> **ame82 said:**
> plz guys we just starting more details , how can i do that?
i have problem and my ubuntu 12.4 can never acces shared folder in another 12.4 what a shame , simple task taking forever

Post you smb.conf file and we'll go from there.

I'm running Ubuntu Server 12.04,have 1 Windows XP Home PC and one Win7 Laptop and Samba works both ways for me,with one exception.This time I can click on workgroup computers in XP and access the 'allshares' folder I set up,but it doesn't show up in Network Places(it did on the last install),but on Win7,they all show up fine,so does the 'public' folder I 'shared',so Samba does work.

---

### Post by asifmohtesham on 2013-02-08
Thank you! It worked! :-)

---

