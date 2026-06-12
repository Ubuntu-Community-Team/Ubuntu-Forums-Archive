---
title: "Questions considering samba, lmhosts and firestarter"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by phanyx on 2009-08-26
Hello,

I have 3 problems:

1# Every reboot samba seems to delete its file `/var/run/samba/unexpected.tdb'. When I try to `smbtree -d 3', it dumps me lots of `tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory' messages. What's funny, when I manually 'touch /var/run/samba/unexpected.tdb', it stops to complain about it, but, as I said, after a reboot the file magically disappear again, causing garbage everytime I smbtree again. Can something be done with it ?

2# I found out, that I can make less garbage in my LAN by resolving netBIOS names by `lmhosts' file rather than broadcasting the LAN. So I created /etc/samba/lmhosts and filled it with IPs and netBIOS names of all computers in my LAN (enormous amount of 3). It works perfectly in smbtree (it dump precisly, that it uses lmhosts and is happy with it) and nmblookup but, when I try to browse samba shares on Dolphin or Firefox with `smb://netbios-name' method, it fails. The second method `smb://ip' works normally though. The strange thing is, that when I remove the lmhosts file, browsing with smb://netbios-name method works just fine (besides of garbaging LAN, what I'm trying to avoid). What do I wrong ?

3# In Firestarter when I have `Edit > Preferences > Firewall > Advanced Options > Block broadcasts from external network' checked, firewall blocks broadcast queries from my LAN (192.168.1.0/255.255.255.0). I have to uncheck this option to make the firewall to accept and respond broadcast queries from LAN. Suprising thing is, that, when I check `Edit > Preferences > Firewall > Advanced Options > Block broadcasts from *internal* network' option, broadcasts from LAN aren't blocked. Is it misnaming of the options or what ?

I hope I won't make `tl;dr' spam. Thanks for any responds

---

