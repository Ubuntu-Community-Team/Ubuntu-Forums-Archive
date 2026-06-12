---
title: "&quot;Mapping a Network Drive&quot;"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by Burky on 2009-09-27
I have an external drive on my desktop that has all my music and stuff on it. When I had a windows laptop I was able to make a drive on the laptop that was the external drive on my desktop and it was just like I had the external drive on my laptop. So I was wondering if I could do the same with my Ubuntu laptop?

Thanks

---

### Post by Burky on 2009-10-01
When I do smbtree I get this

```
david@nx9010:~$ smbtree
Password: 
MSHOME
	\\JAUNTY         		
		\\JAUNTY\IPC$           	IPC Service ()
		\\JAUNTY\MyFiles        	
		\\JAUNTY\print$         	
	\\HEWLETT        		New
	\\COMPAC         		Compaq
		\\COMPAC\WEEKLY         	
		\\COMPAC\YOUROWN2       	
		\\COMPAC\Faucets        	
		\\COMPAC\Insurance      	
		\\COMPAC\PRESARIO (C)   	
		\\COMPAC\Prom 08        	
		\\COMPAC\lexmark8       	Lexmark 8300 Series
		\\COMPAC\MONTHLY        	
		\\COMPAC\School Work    	
		\\COMPAC\House Stuff    	
		\\COMPAC\Furniture Warranty	
		\\COMPAC\YOUROWN        	
		\\COMPAC\CALENDAR       	
		\\COMPAC\Pictures       	
		\\COMPAC\POSTER         	
		\\COMPAC\Dave           	
		\\COMPAC\EXTERNAL (J)   	
		\\COMPAC\SharedDocs     	
		\\COMPAC\print$         	Printer Drivers
		\\COMPAC\IPC$           	Remote IPC
		\\COMPAC\pmw            	
		\\COMPAC\DOCUMENT       	
		\\COMPAC\Boulevard S83 Printable Brochure_files	

```

I want to make the External boot at startup so I added this line to the fstab

```
//COMPAC/EXTERNAL (J)  /media/external  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

After doing this ```
sudo mount -a
``` I get this ```
[mntent]: line 15 in /etc/fstab is bad
```

I'm not sure what's wrong, anyone care to help me out a bit?

---

