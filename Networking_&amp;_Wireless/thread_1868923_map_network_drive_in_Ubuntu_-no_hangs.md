---
title: "map network drive in Ubuntu -no hangs?"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by deckoff on 2011-10-25
I want to find the best way to mount my NAS drive to my laptop.  It is mounted most of the time, but sometimes the laptop is on the go.  my only problem is that when I am on the go, Krusader and nautilus hang  when trying to access the drive. Up till now, I used wicd(in Kubuntu  11.04) to run a post-connect and pre-disconnect scripts for the specific  connections. It worked well, but wicd is too buggy now in Ubuntu 11.10 and I  thing it even breaks hibernation...

this is the script I used to run to mount:

 	Code:
 	sudo mount -t cifs //192.168.1.106/Public /media/MyBookLive -o username=******,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777,soft,user,noperm 
Any ideas how to make this mount when reachable , and not hang when not  are welcome :smile:. I thing some good ideas for options when mounting might help.
I have tried autofs in the past, with no success, but I have not tried a lot, this might be an option, too. 
I have tried to put a script in /etc/network/if-up.d and if-down.d but the umount script will run when the connection is already down, and the system will still hang...
Strangely, this problem has been around for years, lots of people trying to solve it, with no good solution.
thank you

---

