---
title: "NAS Files hidden in terminal suddenly."
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by mensfort on 2011-07-03
Problem: Most directories and files are suddenly hidden in my NAS, even read-only directories. How is this possible???  This means, with terminal they are invisible but with Nautilus I have access. It started when I lost 10 years of e-mails.

What I did before it happened;
- I changed from /etc/fstab CIFS to .gvfs because the speed of my NAS is 4x faster. (4MB/sec now is 18MB/sec.)
- I opened my e-mails remote from a laptop and let it run thunderbird until the battery was empty. 

Only the e-mail directory OUR MAIL is still visible with terminal, the rest is hidden... but with Nautilus I still have access to the files. 

2 ACTIONS:
- Backup of e-mails, software etc to local drive asap with nautilus.
- ask people what can cause this???

---

### Post by capscrew on 2011-07-03
> **mensfort said:**
> Problem: Most directories and files are suddenly hidden in my NAS, even read-only directories. How is this possible???  This means, with terminal they are invisible but with Nautilus I have access. It started when I lost 10 years of e-mails.

What I did before it happened;
- I changed from /etc/fstab CIFS to .gvfs because the speed of my NAS is 4x faster. (4MB/sec now is 18MB/sec.)
- I opened my e-mails remote from a laptop and let it run thunderbird until the battery was empty. 

Only the e-mail directory OUR MAIL is still visible with terminal, the rest is hidden... but with Nautilus I still have access to the files. 

2 ACTIONS:
- Backup of e-mails, software etc to local drive asap with nautilus.
- ask people what can cause this???

What command are you using to view the files in the terminal?  Explain what you mean by: I "changed from /etc/fstab CIFS to .gvfs....

Nautilus uses ~/.gvfs to mount SMB shares.  This might be why you can still see the files using Nautilus.

---

### Post by Morbius1 on 2011-07-03
> Explain what you mean by: I "changed from /etc/fstab CIFS to .gvfs....That would be my handiwork I'm afraid. In an earlier post instead of trying to find out why an fstab automount is slower than a nautilus mount I suggested he use Gigolo. Gigolo will issue the following command whenever  the remote share is available:
```
gvfs-mount smb://server/share
```As you stated it will mount to ~/.gvfs/share-name on server-name just as doing it manually  in Nautilus does. I also suggest a symlink to a "non-hidden" directory if this was an issue with any of his applications.

I am not sure how the terminal is being used with Thunderbird in this context.

---

### Post by tgalati4 on 2011-07-03
I think it is a user permission issue.  .gvfs is hidden because it is supposed to be used by the system (root privilege) to allow easy searching and mounting of network shares.  When you mount it manually, then it is still root permission, but then users can't get access because it was not mounted by the automounter in gnome virtual file system (gvfs).  Does that make sense?  So your files are probably still there, but have a root read-only attribute that needs to be changed back to default.

I have noticed the speed improvement as well, and I was tempted to set up some manual file shares as well, wondering what the consequences would be.  Well, you found one of them!

The speed goes from "Dog-Slow" to OK, and perhaps limited by network bandwidth and switchgear.  A 100BaseT network is doing well to achieve consistent 18 MB/sec transfers.  Remember, it is sharing the network with potentially 254 other devices.

---

### Post by capscrew on 2011-07-03
> **tgalati4 said:**
> I think it is a user permission issue.  .gvfs is hidden because it is supposed to be used by the system (root privilege) to allow easy searching and mounting of network shares.  When you mount it manually, then it is still root permission, but then users can't get access because it was not mounted by the automounter in gnome virtual file system (gvfs).  Does that make sense?  So your files are probably still there, but have a root read-only attribute that needs to be changed back to default.

Says who?  My .gvfs directory is owned by me.  See here```
capscrew@tools:~$ ls -al|g .gv
dr-x------  2 capscrew capscrew      0 2011-07-03 16:54 .gvfs

```The directories mounted on that directory are also owned by me.  These were mounted via Nautilus```
capscrew@tools:~/.gvfs$ ll
total 4
dr-x------  3 capscrew capscrew    0 2011-07-03 16:54 .
drwxr-xr-x 53 capscrew capscrew 4096 2011-07-03 16:54 ..
drwx------  1 capscrew capscrew    0 2011-06-08 14:01 backup on trucks

```The share is //trucks/backup> 

I have noticed the speed improvement as well, and I was tempted to set up some manual file shares as well, wondering what the consequences would be.  Well, you found one of them!

The speed goes from "Dog-Slow" to OK, and perhaps limited by network bandwidth and switchgear.  A 100BaseT network is doing well to achieve consistent 18 MB/sec transfers. 
The conversion is 8 bits = 1 bite.  12.5 Megabytes = 100 Megabits.  The protocol 100BaseT (Fast Ethernet) operates at max 100 Megabits per second (100 Mb/sec or 12.5 MB/s). You can do the calculation yourself [**_here_**]("http://www.matisse.net/bitcalc/?input_amount=100&input_units=megabits&notation=legacy") > 
 Remember, it is sharing the network with potentially 254 other devices.
If you are using a switched network (no hubs) then all devices have a 1 to 1 conversation end to end.  There is no collision domain.  The only concern is end to end bandwidth.  How many devices are on any segment is only tangentially important.

---

### Post by mensfort on 2011-07-05
> **capscrew said:**
> What command are you using to view the files in the terminal?  Explain what you mean by: I &quot;changed from /etc/fstab CIFS to .gvfs....

Nautilus uses ~/.gvfs to mount SMB shares.  This might be why you can still see the files using Nautilus.

 let me explain some detail: In my /etc/fstab I put following line : //192.168.1.40/Volume_1 /home/nas cifs  username=mensfort,password=zhongguo,uid=1000,gid-100,rsize=57344,wsize=57344 0 0  In /home/nas, there I can see all directories and all files. However, in following directory i only see 2 directories from thunderbird, the last program used before all trouble start: ~/.gvfs/volume_1 on ch3mnas/  with Nautilus however, ~/.gvfs/volume_1 on ch3mnas/ also shows all files and directories.  Normal software and terminal can only see 2 directories in ~/.gvfs/volume_1 on ch3mnas/, but in /home/nas I can see all.... but slower.  does this help?  (btw. most friends don't know .gvfs... is there maybe an alternative. I also don't like the hidden directory .gvfs)

---

### Post by mensfort on 2011-07-05
> **capscrew said:**
> Says who?  My .gvfs directory is owned by me.  See here```
capscrew@tools:~$ ls -al|g .gv
dr-x------  2 capscrew capscrew      0 2011-07-03 16:54 .gvfs

```The directories mounted on that directory are also owned by me.  These were mounted via Nautilus```
capscrew@tools:~/.gvfs$ ll
total 4
dr-x------  3 capscrew capscrew    0 2011-07-03 16:54 .
drwxr-xr-x 53 capscrew capscrew 4096 2011-07-03 16:54 ..
drwx------  1 capscrew capscrew    0 2011-06-08 14:01 backup on trucks

```The share is //trucks/backupThe conversion is 8 bits = 1 bite.  12.5 Megabytes = 100 Megabits.  The protocol 100BaseT (Fast Ethernet) operates at max 100 Megabits per second (100 Mb/sec or 12.5 MB/s). You can do the calculation yourself [**_here_**]("http://www.matisse.net/bitcalc/?input_amount=100&input_units=megabits&notation=legacy") 
If you are using a switched network (no hubs) then all devices have a 1 to 1 conversation end to end.  There is no collision domain.  The only concern is end to end bandwidth.  How many devices are on any segment is only tangentially important.

  Hi friend, For me, I am lucky that /etc/fstab can see all files and directories... maybe you should also try to add the NAS to that file. My network is 1000MB, but that doesn't mean I can do 90MByte/second... that would be awesome.

---

### Post by mensfort on 2011-07-05
I add following in the configuration startup programs:  gvfs-mount smb://server/share  then with terminal I could do for 1 month:  cd ~/.gvfs/volume 1 on ch3mnas/backup   now I go back to the old (slow) situation (with line in /etc/fstab):  cd /home/nas/backup  Still wondering why .gvfs is very fast compared to /fstab. Even windows is faster, that should not be allowed.

---

### Post by capscrew on 2011-07-05
> **mensfort said:**
> let me explain some detail: In my /etc/fstab I put following line : //192.168.1.40/Volume_1 /home/nas cifs  username=mensfort,password=zhongguo,uid=1000,gid-100,rsize=57344,wsize=57344 0 0  In /home/nas, there I can see all directories and all files. However, in following directory i only see 2 directories from thunderbird, the last program used before all trouble start: ~/.gvfs/volume_1 on ch3mnas/  with Nautilus however, ~/.gvfs/volume_1 on ch3mnas/ also shows all files and directories.  Normal software and terminal can only see 2 directories in ~/.gvfs/volume_1 on ch3mnas/, but in /home/nas I can see all.... but slower.  does this help?  (btw. most friends don't know .gvfs... is there maybe an alternative. I also don't like the hidden directory .gvfs)
Can you provide the output of this:```
smbclient -L 192.168.1.40
```

---

### Post by capscrew on 2011-07-05
> **mensfort said:**
> Hi friend, For me, I am lucky that /etc/fstab can see all files and directories... maybe you should also try to add the NAS to that file. My network is 1000MB, but that doesn't mean I can do 90MByte/second... that would be awesome.
I'm sure your network is not 1000MB more likely is 1000 Mb aka Gigabit (B=byte b=bit). Network speeds are measured in bits not bytes.  We are daling with a bitstream not a byte-stream.

---

### Post by capscrew on 2011-07-05
> **mensfort said:**
> I add following in the configuration startup programs:  gvfs-mount smb://server/share  then with terminal I could do for 1 month:  cd ~/.gvfs/volume 1 on ch3mnas/backup   now I go back to the old (slow) situation (with line in /etc/fstab):  cd /home/nas/backup  Still wondering why .gvfs is very fast compared to /fstab. Even windows is faster, that should not be allowed.

Not sure myself.  But then again I'm not sure how you defined the share on the NAS.  Do you have spaces in the share definition?  Like this //server/my share ? Are you using quotes ("") to surround the share definition?

---

### Post by mensfort on 2011-08-08
> **capscrew said:**
> Can you provide the output of this:```
smbclient -L 192.168.1.40
```

Here the reply for smbclient -L 192.168.1.40
Domain=[HOUKES] OS=[Unix] Server=[Samba 3.0.28]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

---

