---
title: "Sharing works only in one way (first time YOU see this!)"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by nandelbosc on 2009-05-15
Hi to all! ;)

I have a little LAN with two computers with a fresh install of Ubuntu 9.04, connected to a ADSL router with 4 LAN ports.

The Hard is the same for every computer.

PC1 > hostname: ferran, ip: 192.168.1.5, username: ferran
PC2 > hostname: florens, ip: 192.168.1.10, username: florens

Ping work perfectly from ferran to florens and florens to ferran.

I can ssh from ferran to florens and florens to ferran.

But see what happens when I try to move documents between computers (all of this happens with GUI too (gnome) but I used the console for post here!)... 

All firewalls inactive...

```
ferrran@ferran:~$ sudo ufw status
[sudo] password for ferran: 
Status: inactive

florens@florens:~$ sudo ufw status
[sudo] password for florens: 
Status: inactive
```

All have read/write permisions to shared folders...

```
ferrran@ferran:~$ ls -l Escriptori/
drwxrwxrwx 11 ferran ferran    4096 2009-05-14 20:22 compartit

florens@florens:~$ ls -l Escriptori/
drwxrwxrwx 11 florens florens    4096 2009-05-14 20:33 factures
```

Shared's are listed ok...

The shared here is **factures**
```

ferrran@ferran:~$ smbclient -L //florens -U florens
Enter florens's password: 
Domain=[FLORENS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (florens server (Samba, Ubuntu))
	HL-5040-series  Printer   Brother HL-5040 series
	Epson-Stylus-Photo-RX510 Printer   Epson Stylus Photo RX510
	factures        Disk      
Domain=[FLORENS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	MACIAS               FLORENS
```
and...

The shared here is **prova**
```
florens@florens:~$ smbclient  -L //ferran -U ferran
Enter ferran's password: 
Domain=[FERRAN] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (ferran server (Samba, Ubuntu))
	Stylus-Photo-RX520 Printer   EPSON Stylus Photo RX520
	EPL-5900L       Printer   EPSON EPL-5900L
	Brother-HL-5040 Printer   Brother HL-5040
	prova           Disk      
Domain=[FERRAN] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	MACIAS               

```

I can get files from florens to ferran...

```
ferran@ferran:~$ smbclient //florens/factures -U florens
Enter florens's password: 
Domain=[FLORENS] OS=[Unix] Server=[Samba 3.3.2]

smb: \Factures 2004\1-Gener\> get 04004-FRI-SUF-08.01.04.doc 
getting file \Factures 2004\1-Gener\04004-FRI-SUF-08.01.04.doc of size 24576 as 04004-FRI-SUF-08.01.04.doc (5999,9 kb/s) (average 6000,0 kb/s)
```

but i can't put files...

```
smb: \> put temp.jpg
^C

*********** I wait for more than 30 seconds anmd don't work, I stopped it with ctrl+c

smb: \> ls
  .                                   D        0  Fri May 15 07:54:12 2009
  ..                                  D        0  Fri May 15 07:28:45 2009
  temp.jpg                            A        0  Fri May 15 07:54:12 2009
		48811 blocks of size 1048576. 29343 blocks available

```

the files it's writed but with no content.

	
upside down...


I can put files from florens to ferran...

```
florens@florens:~/Escriptori$ smbclient //ferran/prova -U ferran
Enter ferran's password: 
Domain=[FERRAN] OS=[Unix] Server=[Samba 3.3.2]
smb: \> ls
  .                                   D        0  Fri May 15 07:25:31 2009
  ..                                  D        0  Fri May 15 07:26:58 2009

		46936 blocks of size 1048576. 28897 blocks available
smb: \> put temp.jpg
putting file temp.jpg as \temp.jpg (10484,8 kb/s) (average 10484,8 kb/s)
```

But i can't get...

```
smb: \> get temp.jpg
^C
************* wait for more than 30 seconds and don't work, I press ctrl+c


florens@florens:~$ ls -l
-rwxr-xr-x  1 florens florens     0 2009-05-15 07:48 temp.jpg

************* the has been write but with no content
```


Ok, you think... nandelbosc, you have a samba problem, but NO! The logs don't show nothings, a here another clue... SSH and NFS file transferd don't work too!!!

See that...

From ferran I can't copy files to florens...

```
ferran@ferran:~$ scp temp.jpg florens@florens:/home/florens/
florens@florens's password: 
temp.jpg                                                                                                                   100%  651KB 651.3KB/s   00:00    
^C

*************** wait more than 30 second but don't work, I stopped it with ctrl+c
```

the files it's created but with no content (like smb before, remember?)...
```

ferran@ferran:~$ ssh florens@florens
florens@florens's password: 

florens@florens:~$ ls -l
-rw-r--r--  1 florens florens     0 2009-05-15 07:55 temp.jpg
```

I back mode...
```

ferran@ferran:~$ scp florens@florens:/home/florens/temp.jpg temp1.jpg 
florens@florens's password: 
temp.jpg                                                                                                                   100% 5169KB   5.1MB/s   00:01    

ferran@ferran:~$ ls -l
-rw-r--r-- 1 ferran ferran 5293056 2009-05-15 07:57 temp1.jpg
```

work's ok!


from the other computer...

I can copy files from florens to ferran...

```
florens@florens:~$ scp temp.jpg ferran@ferran:/home/ferran/
ferran@ferran's password: 
temp.jpg                                                                                                                   100% 5169KB   5.1MB/s   00:00    

```

But I can't copy from ferran to flores...

```
florens@florens:~$ scp ferran@ferran:/home/ferran/temp.jpg ./temp.jpg
ferran@ferran's password: 
temp.jpg                                                                                                                     0%    0     0.0KB/s - stalled -
^C
*************** I wait for more than 30 seconds and don't 
work, I stopped it with ctrl+c
florens@florens:~$ ls -l
-rw-r--r--  1 florens florens     0 2009-05-15 08:01 temp.jpg

```

What's the hell happens?!?!

I don't know what search for, or what logs. dmesg, syslog amb samba logs of either computer don't nothing!

Thank's i advance!

---

### Post by superprash2003 on 2009-05-15
you need to check the folder's permissions , not the samba folder permissions , but the original folder permissions , right click on folder and click on properties and check permissions.. does it say root for everything?

---

### Post by nandelbosc on 2009-05-15
Thank's for reply.

The folder permisions are ok...

```
florens@florens:~$ ls -l Escriptori/
-rwxr-xr-x 1 florens florens 476 2009-05-12 19:58 factures

```


The problem was very stupid... the router has the #2 LAN port damaged. After connect to other port, all works ok!

very strange, but went well

thank's for your time

---

