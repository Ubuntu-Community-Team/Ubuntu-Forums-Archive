---
title: "File Server"
date: 2008-08-06
forum: Mythbuntu
---

### Post by 1337ferret on 2008-08-06
Hey guys,

Got another quick question I can't seem to find.
I am new to linux and loving every minute of it so far, I recently did part of my network+ in Redhat, My intention with this htpc was to also have it as a samba file server, like in redhat, with my other pc's in the house, as it will have a 1TB hard drive which I want to store the majority of the media in the house.

Is there a way to do this, I trawled through the services and package manager coming out more confused than I was beforehand.

Any help would be appreciated, Thanks again

-FeRReT

---

### Post by tamoneya on 2008-08-06
samba sounds like a pretty good choice to me.  It will ensure compatibility with the windows systems. 

In general samba is pretty easy to setup:[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Moridin333 on 2008-08-06
I have a shared partition on my htpc here at home.  at the end of my /etc/smb/smb.conf I have these options.

[Data]
path = /media/Data
available = yes
browsable = yes
public = yes
writable = yes

my windows pc has the drive mounted using the username and password and my other linux computers have this entry in fstab

//192.168.1.11/Data /media/Data cifs rw,username=,password= 0 0
I took out the username and password.

if you want to be able to read and write to the files don't forget to chmod 777 -r <path to shared partition or folder> on your server

---

### Post by 1337ferret on 2008-08-06
Thanks guys, Just trying to remember where the templates etc are =D.

I am going to go dig up that old linux book, thanks a heap for the help guys.

---

