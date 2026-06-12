---
title: "Mounting an SMB share to my server"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by patlabor on 2009-04-01
I have a problem getting an smb share that i am running on an nslu 2.0 to mount on my ubuntu server 8.10

the share is a 1TB USB Harddrive formattet with NTFS. i can access it from all my windows machines, but i want to mount it directly to my server which i use to do the heavy livting. the two are connected via ethernet but the rest is connected via wlan. so when i want to copy something from the server to the nslu i have to use a third pc and transfer it over wlan with abouth 0.7MB/s

i tried
mount -t cifs -o username=xxx //Slug/HDD_1_1_1 /test

but i get this error
mount error: could not find target server. TCP name Slug/HDD_1_1_1 not found
No ip address specified and hostname not found

using nmblookup Slug i get
quering Slug on 192.168.178.255
192.168.178.22 Slug<00>

replacing the "Slug" with the ip address in the mount command i get promptet for the password of the share and then:
mount error 101 = Network is unrechable

using smbclient //Slug/HDD_1_1_1 i can access the share without problems

hopefully anyone can help me

thanks in advance.

---

### Post by dmizer on 2009-04-01
Well, I was going to say "check the second link in my signature" but it appears to be missing at the moment, so try this instead: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by patlabor on 2009-04-02
thanks for your fast reply.
finally i had time and just gave your tutorial a try.

after editing the nsswitch.conf i could finally mount the share, but now i cant access the folder. i used /test where i had full access. 

after mounting my share there suddenly i dont have any access anymore. suddenly the owner changed from root:root to 501:501 and the x bit missing, so i can not cd into the dir.

i was trying chmod and chown to get access there but even with sudo chmod i got a permission denied.

sadly i am stuck again.

---

### Post by dmizer on 2009-04-02
What was the exact command you used to access the SLUG after following my howto?

---

### Post by mpsii on 2009-04-02
to my knowledge you need two (2) forward slashes (//) between the hostname and folders

---

### Post by patlabor on 2009-04-03
> **dmizer said:**
> What was the exact command you used to access the SLUG after following my howto?


i was following your tutorial and was using 

sudo mount -t cifs //Slug/HDD_1_1_1 /test -o username=whatever,password=exactly,file_mode=0777,dir_mode=0777

i skipped the utf8 part cause i dont have any utf8 encryptet filenames but gave it right now a try with that option too, again same result

---

### Post by dmizer on 2009-04-03
Okay, try this:
```
sudo mount -t cifs //Slug/HDD_1_1_1 /test -o username=whatever,password=exactly,uid=501,gid=501,file_mode=0777,dir_mode=0777
```
If that doesn't work, do you get errors?

---

### Post by patlabor on 2009-04-04
> **dmizer said:**
> Okay, try this:
```
sudo mount -t cifs //Slug/HDD_1_1_1 /test -o username=whatever,password=exactly,uid=501,gid=501,file_mode=0777,dir_mode=0777
```
If that doesn't work, do you get errors?


just gave that a try, but still no change.

no error messages, but access denied whatever i try to do with the /test dir

---

### Post by dmizer on 2009-04-05
After mounting, what is the output of:
```
sudo ls -la /test
```

---

### Post by patlabor on 2009-04-06
dont remember the exact error message, but was something about "access denied" or "not allowed"

i had to undo the changes i made in the nsswitch.conf, since after that changes according to your tutorial, apt-get was broken. something about could not resolve archive.de.ubuntu.com.
but ping was still working from the server, and i could browse archive.de.ubuntu.com from my windowsmachine

---

### Post by dmizer on 2009-04-06
In /etc/nsswitch.conf, Did you make sure that "wins" was before "dns" as shown in the tutorial? If not, you are likely to have browsing problems.

Please try again, and run the following command after you've mounted.
```
sudo ls -la /test
```
I need the EXACT output of this command as it will give me information that will help me determine what your problem is.

---

