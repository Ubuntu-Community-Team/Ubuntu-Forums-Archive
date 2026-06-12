---
title: "Sharing External Harddrive to XP/Vista Machines"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Zintha on 2010-03-11
Evening,  An introduction, I'm a completely new, unknowing and eager to learn Ubuntu 9.10. In all the posts i've searched on these forums about this problem i've either come across people using older versions and it doesn't apply or trying to fix other problems or people who are trying to do something completely over my head.  So, my problem:  I've got a Seagate 1TB External hard drive that i've used to store a whole variety of things that i've had shared on my home network since the day I got it.  Since i've started to use Ubuntu 9.10 i've not found a way of sharing it over the network, not even been able to see this computer over the network from any Windows machines.   I've looked into Samba a little bit but all I can find documentation wise that makes any sense to me is about printer sharing and I can't, myself, work out how I could apply it to the hard drive.  There is no rush on this, i've got my hard drive running off my Vista laptop in the mean time, however if I could get it running off this computer it would make things a lot easier for me.  Keep in mind, with the solutions, i'm new to this. Even some of the more basic things that everyone else seems to understand without a question leaves me firing it off to Google and sifting through another 50 topics just to understand.

---

### Post by Morbius1 on 2010-03-11
Plug your external drive into the Ubuntu machine

It should automount to something like: /media/Seagate

Open Nautilus and right click on /media/Seagate > select "Sharing Options" > click on all three boxes > select "Create Share"

There's only one tiny problem. Assuming this external drive is formatted in NTFS or FAT32 then it will mount to /media/Seagate with access permissions to you only and not your remote users. The easiest way to fix this is like this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your ubuntu login user name.*[/COLOR]

Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**

What this will do is create a mask that will convert the remote user's identity to yours - for that share.

---

### Post by Zintha on 2010-03-11
Right now my external is getting using quite a bit so I won't be able to switch it over yet.

As soon as I can I will try out what you're suggesting. 

Although, whats Nautilus and how do I go about getting it?
Will sudo apt-get install Nautilus work?

Sorry, still very new to Ubuntu.

edit: 
sudo apt-get install nautilus only told me it was already the current version yet I can't find it in applications or System menu?

---

### Post by Morbius1 on 2010-03-12
Nautilus is the name of the file manager in Gnome. When you click on your "Home" folder it will bring up nautilus.

Since you're going to be in the Terminal anyway just type: **nautilus**

---

### Post by jedispork on 2010-03-13
I just wanted to say thanks.  I used
```

usershare owner only = false
```

When I tried sharing the ntfs folder I received a error telling me to add that to the global section. Much simpler than I expected it to be.

---

### Post by sinkyboy2000 on 2010-03-16
> **Morbius1 said:**
> Plug your external drive into the Ubuntu machine
 
It should automount to something like: /media/Seagate
 
Open Nautilus and right click on /media/Seagate > select "Sharing Options" > click on all three boxes > select "Create Share"
 
There's only one tiny problem. Assuming this external drive is formatted in NTFS or FAT32 then it will mount to /media/Seagate with access permissions to you only and not your remote users. The easiest way to fix this is like this:
 
Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**
 
Add the following line to the [COLOR=blue][global][/COLOR] section of smb.conf:
```
force user = morbius
```[COLOR=blue]*Change morbius to your ubuntu login user name.*[/COLOR]
 
Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**
 
What this will do is create a mask that will convert the remote user's identity to yours - for that share.
 
This looks like the answer to my problem.  My windows machines see the folder, but I can't get access.  Thanks a lot!

---

### Post by sinkyboy2000 on 2010-03-17
> **sinkyboy2000 said:**
> This looks like the answer to my problem. My windows machines see the folder, but I can't get access. Thanks a lot!
 
 
:D:D:D:D
Tried it out and it worked. Thanks again!!!

---

### Post by WEIR_SJ on 2010-09-25
WHOOOOOP!! this work for me too...

Thanks
Stu :)

---

### Post by Terryfab24 on 2012-12-04
I have a similar problem but where under the global section should I add "force user = myusername"? Because it doesn't seem to be working for me..

> **Morbius1 said:**
> Plug your external drive into the Ubuntu machine

It should automount to something like: /media/Seagate

Open Nautilus and right click on /media/Seagate > select "Sharing Options" > click on all three boxes > select "Create Share"

There's only one tiny problem. Assuming this external drive is formatted in NTFS or FAT32 then it will mount to /media/Seagate with access permissions to you only and not your remote users. The easiest way to fix this is like this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your ubuntu login user name.*[/COLOR]

Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**

What this will do is create a mask that will convert the remote user's identity to yours - for that share.

---

### Post by wildmanne39 on 2012-12-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

