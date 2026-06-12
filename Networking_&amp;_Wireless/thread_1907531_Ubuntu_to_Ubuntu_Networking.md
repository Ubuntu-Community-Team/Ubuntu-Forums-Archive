---
title: "Ubuntu to Ubuntu Networking"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by cirelosborn on 2012-01-11
I've been everywhere and tried everything and have gotten nowhere.

I have three Ubuntu machines (running 11.10) and have been trying to network them together through a router.  I've tried samba and I still can't set anything up.  I've used the sharing option in ubuntu and still nothing.  I can't see the other computers on the network from any other computer.

I've been working this for about a week.  Can someone please tell me how in the world to network these three machines together and share two external drives hooked up to one of the machines with the other two?

---

### Post by SeijiSensei on 2012-01-11
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by JRV on 2012-01-11
Check out my tutorial on Ubuntu to Ubuntu networking:

[http://ubuntuforums.org/showthread.php?t=1900551](http://ubuntuforums.org/showthread.php?t=1900551)

---

### Post by Morbius1 on 2012-01-11
If you are still interested in Samba here's my 10 minutite HowTo on browsing issues:

> 92.48% ( I made that number up ) of all the "failed to retrieve.." errors are caused by these 4 problems:

[1] Services on the server (desktop) aren't running.

So start them:
```
sudo service smbd start
sudo service nmbd start 
```[2] Firewalls are in the way.
If you haven't done anything to your firewalls then you're fine. If you  have done something with it disable them. We can fix it later.

[3] Your hostname is too long.

Run the following command and count the number of characters:
```
hostname 
```[COLOR=Blue]* If it's 15 characters or less then you're good to go. If it's 16 characters or more then here's how to fix it:*[/COLOR]
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf 
```In the [global] section - right under the workgroup line - add the following line:
```
netbios name = something 
```[COLOR=Blue]*"something" has to be 15 characters or less in length*[/COLOR]

[4] Rearrange the order of how samba resolves names to ip addresses by  putting the only method that works by default first. Again in the  [global] section add the following line:
```
name resolve order = bcast host lmhosts wins 
```After you do [3] or [4] restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart 
```Wait 5 minutes - no kidding - and then see if your client (laptop) can access the server's shares.If all of that does zip then post the output of this command:
```
smbtree
```

---

