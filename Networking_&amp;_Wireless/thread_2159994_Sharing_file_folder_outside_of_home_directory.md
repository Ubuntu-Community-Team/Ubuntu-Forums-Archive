---
title: "Sharing file folder outside of home directory"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by yandex232 on 2013-07-05
I have two hard disks one ssd where my **kubuntu **is on and one 500GB hard disk with ext4 filesystem. Samba is installed.
I have shared a folder in my home directory simple with dolphin and it can be viewed via my android phone. Then i tried the same on my 500GB Harddisk and it does not work Now my Question.
How can i share a folder outside of my home directory on my 500GB Hard Disk???   :(
Thanks alot for answers :D

---

### Post by Morbius1 on 2013-07-05
[COLOR=#0000cd]*Note: I don't know KDE so I don't know how far I can help you with this but...*[/COLOR]
> I have shared a folder in my home directory simple with dolphin and it can be viewed via my android phone.
That sounds like a Samba Usershare to me so please post the output of the following command:
```
net usershare info --long
```
If I'm wrong about usershare please post the output of this one - actually you might want to post it anyway:
```
testparm -s
```
> Then i tried the same on my 500GB Harddisk and it does not work 
What does that mean exactly? You couldn't create the share in Dolphin or you couldn't access it once it was created?

---

### Post by SeijiSensei on 2013-07-05
Do you own the folder, or is it owned by a user like root?  If you own it, you might be able to share it using the same procedure you used with the folder in your home directory.  If you don't own it, you'll need to change the permissions on the folder like this:
```

sudo chown -R username:username /path/to/some/folder

```
Replace "username" with your own.

You can also define a folder to be shared in /etc/samba/smb.conf.  Here's an example of a publicly-accessible share definition from the [Samba Server Guide]("https://help.ubuntu.com/community/Samba/SambaServerGuide"):

```

[public]
        comment = Public Share
        path = /path/to/share/point
        read only = no
        guest only = yes
        guest ok = yes

```

There are GUI tools to manage Samba, but I've never used them.

---

### Post by Morbius1 on 2013-07-05
> sudo chmod -R username:username /path/to/some/folder
I think you mean chown not chmod?

---

### Post by TheFu on 2013-07-05
I would want to know if there are any errors inside the system and samba log files. Are there?

---

### Post by SeijiSensei on 2013-07-05
> **Morbius1 said:**
> I think you mean chown not chmod?

Sorry!  Of course.  I've fixed the original.

That will teach me to post here without having my morning cup of coffee first!

---

### Post by yandex232 on 2013-07-09
Thanks alot for the answers and your time. I thought there was some foolproof solution which i could not see but anyway i have put an usb stick into my Technicolor Modem. It now acts as a Fileserver which can be seen by my phone and my PC. :lolflag:

> Then i tried the same on my 500GB Harddisk and it does not work

I was not correct. In my pc is one Harddisk with three partitions. 2 20GB for Win XP (Adobe PDF Pro and some Games) and Kubuntu. I wanted to transmitt some gamecube roms from my android phone to the pc but the 20GB where too full so i thought share a folder on the third partition (ext4). But the phone saw the folder but could not open it because i had no authorization but sharing a folder in the home directory with the same method worked. 

> There are GUI tools to manage Samba, but I've never used them.

A Samba GUI i tried did not see the third partition but yeah i think with a Samba Gui would work

---

