---
title: "Troubles with WPA"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Riona on 2006-06-04
Having trouble getting WPA to work. I followed  the below posting :
followed the post by geocritters

1. install wpa_supplicant
2. install Network-manager-gnome
3. Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5. Reboot
6. Select your network in the NM icon
7. Follow the prompts for password, type, etc.
8. Choose password for keyring (you'll be prompted).
9. Away you go! 

Well For me this doesn't work. it fails to find the network connection. 
 In theory this should work I got wep working. 
uninstaling WPA supplicant' doesn't help I tried it.

Any ideas ?? 
where are the log files located for this?
Thanks.

---

### Post by shamrock_uk on 2006-06-04
Can't help you with the logs, but there is a little walkthrough included in the book that comes with Dapper. 

Find it at:

/usr/share/example-content/book-toc.html

and you want chapter 6. There's a little bit on WPA supplicant, including paths to example configurations.

---

