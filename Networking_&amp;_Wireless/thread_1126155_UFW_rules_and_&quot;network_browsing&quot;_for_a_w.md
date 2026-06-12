---
title: "UFW rules and &quot;network browsing&quot; for a windows share query."
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-04-15
Hi there,
I installed Ubuntu 8.10 on a machine last week and all is going well with my home network and Internet connection. I have a directory on a networked XP machine which I have set to share so accessing those windows files is pretty routine in Uubuntu . I just go to ->Places->Network on my top panel and I see my "Windows Network" icon in the browser and click, then click on MSHOME and my shared XP directory icon comes up and I can access those files. All very straightforward. Being security conscious I decided to enable the UFW firewall on my Ubuntu box. Initially I set all rules to deny and then enabled the firewall with the intention of fine tuning as desired.
```

$ sudo ufw default deny
$ sudo ufw enable

```

I added  rules to allow ssh (port 22) and vnc (port 5900). All very straightforward. I could ssh and vnc from my XP machine to Ubuntu. Unfortunately, with the firewall enabled I no longer had access to my XP shared directory from my Ubuntu box. There is definitely a firewall rules issue because when I disabled UFW I could access my XP shared directory with no problems. So which ports need to be allowed in UFW rules for me to browse my XP share ? 137, 138, 139 and 445 ? 


****UPDATE*****

With the firewall ENABLED I fire up a terminal on command line and when I run the command :

```


$ smbclient -L //***.***.***.***


```

I get a listing showing my XP details and the name of directory which is shared. I can login to the xp share on command line by issuing the smbclient command :

```

$ smbclient //***.***.***.***/xpshare
.................
 smb: \> 


```

At the smb prompt I can "ls" and "get" files. So I am now even more confused as to why when using command line I can get into my xp share and when using "network browsing" gui I cannot ??!!



Cheers,
uc

---

### Post by Mordac85 on 2009-04-15
You probably just need to open the SMB ports so you can communicate with the XP box.  I believe  [http://ubuntuforums.org/showthread.php?t=806000](http://ubuntuforums.org/showthread.php?t=806000) covered the same thing you are seeing.

---

### Post by uncle-c on 2009-04-15
Thanks Glenn, 
I have found some additional info. With UFW  ENABLED if I go --> Places --> "Connect to Server" and connect to "Windows Share" I can access the XP share ( after logging in with my XP password), so your suggestion has confused me even more.
Anyway, I can access my XP share and the fact I have to enter a password to prove my credentials is fine.

So with UFW ENABLED I could not connect to XP share via the --> Applications --> Networks method. The share did not show in the browser.
However, I could connect by --->Applications ---> Connect to Server (login in with XP Password). 

With UFW DISABLED I could connect using the ---> Application ------ >Network method and not be asked for a password. 

It would be interesting to know why this is such.


uc

---

### Post by Mordac85 on 2009-04-15
Well, I guess I'm in the same boat... confused.  I didn't realize you were being prompted for credentials and I don't know why the two paths to connecting give you different results.  I may have to actually build a ubuntu box and play with that one. ;)

---

### Post by uncle-c on 2009-04-16
Sorry Glenn, I just tried ( with firewall enabled) the
 ---->Places --->Connect to server  method. It asked me for login credentials but I could access the XP share by entering nothing. I am still confused as to why I cannot access the XP share via the ---->Places--->Network method ??!!! Would be very intrigued by your findings !!!


uc

---

### Post by superprash2003 on 2009-04-16
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325745](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325745)

---

### Post by k23 on 2010-12-08
I found a solution :popcorn:

```
sudo ufw allow from any app Samba to "yourlinuxboxIP"
```

---

