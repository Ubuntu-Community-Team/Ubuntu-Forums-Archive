---
title: "abcde error (&quot;CDROM has not been defined or cannot be found&quot;)"
date: 2009-08-23
forum: Multimedia Software
---

### Post by Senuf on 2009-08-23
Hello.
To the point:
I want to backup many music CDs (starting with a beautiful Billie Holiday one). My goal is ripping each CD to a single **FLAC** file with a corresponding **CUE** file (then double backup them to DVDs). After searching for plausible solutions, I ended up with the famous "abcde" *thing*. Well, whatever I do with abcde I get the following message: "**CDROM has not been defined or cannot be found**". Even if I write just "abcde" and nothing else.

As far as I got to know, what I need for it to rip a CD in FLAC format was something like this:

[INDENT]**~$ abcde -1 -M -p -o flac**[/INDENT]

I **do** have a CDROM drive (well, a *DVD-RW* drive). And that drive works OK in Ubuntu whether I want to listen to some music, read backup CDs and DVDs, watching a movie, writing data, whatever you mention. Just **not** abcde.

Any hint?

Thanks in advance.

Senuf.

---

### Post by andrew.46 on 2009-08-24
Hi Senuf,

> **Senuf said:**
> 

```
~$ abcde -1 -M -p -o flac
```



This may not help but perhaps try:


```
~$ abcde **[COLOR="Red"]*-d /dev/cdrom*[/COLOR]** -1 -M -p -o flac
```

All the best,

Andrew

---

### Post by Senuf on 2009-08-24
Hi Andrew,

> **andrew.46 said:**
> Hi Senuf,

This may not help but perhaps try:

```
~$ abcde **[COLOR="Red"]*-d /dev/cdrom*[/COLOR]** -1 -M -p -o flac
```

All the best,

Andrew

Hmmmmm...
Didn't work.
All I got was the same line:
[INDENT][FONT="Courier New"][COLOR="DarkRed"][ERROR] abcde: CDROM device cannot be found.[/COLOR][/FONT][/INDENT]

Well, thanks anyway for stopping by.

Let's see if some other idea arises. As for me, I tried every combination I could find, but since I am not a *"power user"* I guess that there might be a solution lurking out there, somewhere out of my grasp.

Senuf

---

### Post by mc4man on 2009-08-24
run this to double check what /dev links your drive has, look for listing under  *-cdrom

```
sudo lshw -C disk
```

---

### Post by Senuf on 2009-08-26
> **mc4man said:**
> run this to double check what /dev links your drive has, look for listing under  *-cdrom

```
sudo lshw -C disk
```

First, thanks for passing by.
Now, to the point:
I did what you suggested.
The "answer" was this:
```
  *-disk:0                
       description: ATA Disk
       product: WDC WD800BB-00JK
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WCAMDA729442
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=de42de42
  *-disk:1
       description: ATA Disk
       product: WDC WD800JB-00ET
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 77.0
       serial: WD-WMAHL1373102
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=139b139b
  *-cdrom
       description: DVD writer
       product: DRW-1608P
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.59
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
```

Thanks in advance for any further hint.

Senuf

---

### Post by mc4man on 2009-08-26
Not all that familiar with abcde but using andrew's command as an example change to cdrom1
```
abcde -d /dev/[COLOR="Blue"]cdrom1[/COLOR] -1 -M -p -o flac
```

If you wish it's very simple to set that drive to /dev/cdrom, /dev/dvd, ect. which is what many apps will default to. 
(so by default abcde is looking for /dev/cdrom, but you're set as /dev/cdrom1

If so, then run and post this (use a maximized terminal so lines don't get jumbled, will take just a min or less to reset

 ```
cat /etc/udev/rules.d/70-persistent-cd.rules 
```

---

