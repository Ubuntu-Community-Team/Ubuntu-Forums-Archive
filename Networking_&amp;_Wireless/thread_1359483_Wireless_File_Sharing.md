---
title: "Wireless File Sharing"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by BennieBlount on 2009-12-19
I have two PCs with Ubuntu 9.10 connected to one wireless router. I have the MUSIC folder on both PCs shared. I used this to install Samba:

apt-get install samba

When I click on "network" on either PC it goes to Windows Network and then to WORKGROUP. And it stops right there at WORKGROUP with a message that it is unable to mount WORKGROUP.

How do I view the shared folders on either PC?


Thanks,

Bennie

---

### Post by some-what-Gnu-2-networks on 2009-12-19
From places: Connect to Server   
select "Windows share" instead of public FTP
 enter the IP address of the pc to connect to 
   Enter the user name and password of the user of the pc you are trying to connect to

---

### Post by BennieBlount on 2009-12-19
Thanks, but, what is the server address of the other computer? These 2 PCs are sitting side-by-side.

And, like Windows XP, shouldn't I be able to see these shared folders on the network?

---

### Post by Thocrun on 2009-12-19
are they in the same workgroup?
what connection? (pc to pc or..dhcp router)

---

### Post by BennieBlount on 2009-12-19
Both are connected to the same wireless router, which I suppose means they are in the same workgroup?

---

### Post by some-what-Gnu-2-networks on 2009-12-19
Go to router's page by entering it's Ip in your browser. it should show the Ip's of attached PCs.

---

### Post by BennieBlount on 2009-12-19
OK, I'll be back...

---

### Post by some-what-Gnu-2-networks on 2009-12-19
my old router had the IP on the bottom of the device, the new one has it in the manual.
Should be similar to 192.168.5.1 Just a sample IP

---

### Post by some-what-Gnu-2-networks on 2009-12-19
> **some-what-Gnu-2-networks said:**
> Go to router's page by entering it's Ip in your browser. it should show the Ip's of attached PCs.
In your _web_ browser, sorry.

---

### Post by BennieBlount on 2009-12-19
> **some-what-Gnu-2-networks said:**
> Go to router's page by entering it's Ip in your browser. it should show the Ip's of attached PCs.


I got address but it and took your steps but I still get a "failed to connect to windows share" error

Thanks, I'll close this up for tonight.

Bennie

---

### Post by some-what-Gnu-2-networks on 2009-12-19
only other idea is you may have the samba server installed but not client. Try apt-get install smb.:confused:

---

### Post by some-what-Gnu-2-networks on 2009-12-19
have you selected folders to share? Right-click folder and choose "Sharing options"

---

### Post by inobe on 2009-12-20
> **BennieBlount said:**
> I got address but it and took your steps but I still get a "failed to connect to windows share" error

Thanks, I'll close this up for tonight.

Bennie

once you have installed samba you need to configure shares in smb.conf

[https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html)

to open smb.conf in terminal do

```
gksu gedit /etc/samba/smb.conf
```

remember to change the default example **path** to the correct path !

example 

```
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```


the **path =** should be a directory like **/home/username/music** or whatever that directory is actually named, replace user name with actual user name.

you must have a valid path before you can edit your smb.conf, you can make one or use an existing path, here how to make one.

```
mkdir /home/username/shares
``` replace user name with your actual username, the shares at end of path is an example an can be what ever name you desire.

follow the steps to configure smb carefully, review the settings in the link for further configurations, if their is something you don't understand let us know.

---

### Post by wootah on 2009-12-20
Sorry if I missed this... but I thought I recall the release for Samba for 9.10 having problems with SMB.

Are you connecting to Windows 7? I thought I saw XP up above?

---

