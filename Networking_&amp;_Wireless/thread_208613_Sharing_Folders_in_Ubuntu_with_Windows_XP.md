---
title: "Sharing Folders in Ubuntu with Windows XP"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by DyWaN on 2006-07-03
Hi, i would like to ask questions regardring on managing users and their rights to my folder shared at Ubuntu.

I've managed to share a folder at Ubuntu by using this following command:
sudo smbpasswd -e myusername
entered the password & new password

sudo smbpasswd -a myusername
again entered new password

the questions is:

1. What is the difference between -e and -a switch?

2. Is there anyway I could manage users access and their rights using a simple way instead of using command line?

3. Regarding to adding users, does it mean eveytime i need a user from windows machine wants to access my shared folder, I have to create each username for them in the **System/Administration/Users & Groups** nad I have to execute the command line above so they can access my shared folder in my Ubuntu machine?

4. How can I manage each user's access rights bot in simple way if there's any and in command style way?

I would like to thank everybody here for supporting the growth of Ubuntu. Thank you

---

### Post by scxtt on 2006-07-03
1. -a adds "username" to the local smbpasswd file, -e enables an already existing user ...

brought to you by the friendly smbpasswd manpage ... :)

---

### Post by DyWaN on 2006-07-03
Thanks scxtt...

do you have any idea how to manage each user's access rights for each specific folders?

---

### Post by scxtt on 2006-07-03
i'm the only one who uses my computer - and the only one on my network (i experiment w/ samba/nfs using VMs), but i'm thinking you can edit /etc/samba/smb.conf to specify which users can access certain shares ... probably something as simple as (if you have 3 users - Bob, Jane, and Steve):
[indent][XP_share]
...
...
users = Bob, Steve
...
...[/indent]something like that would probably stop Jane from being able to use the share ...

note - it's possibly "valid users":
[indent]# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
    valid users = %S[/indent]don't forget to restart samba anytime you make changes to smb.conf ...

---

### Post by DyWaN on 2006-07-03
thank you very much for your detailed answers into this. :)

one final thing : how can I edit the file you mentioned above? using the terminal? if so, which set of command shall I use? again thank you very much for your answers and your time getting into this...

---

### Post by scxtt on 2006-07-03
you're welcome - always glad to help :) ...

i personally like to use vi(m) to edit config files ... so you can do:
[indent]sudo vim /etc/samba/smb.conf[/indent]and edit it that way ... you can also use any editor you want, like gedit:
[indent]gksudo gedit /etc/samba/smb.conf[/indent]if you're not familiar w/ vi(m) you can get the same results using gedit ...

---

### Post by DyWaN on 2006-07-03
ok, I will try to learn it first. If I came up with any problems I will post it again here. Thanks SCXTT ^_^

---

### Post by DyWaN on 2006-07-03
If I have made changes to the file, how can I save it? I can't find any "Save" option.....

---

### Post by scxtt on 2006-07-03
:wq

the colon is to get to "command mode", "w" is write and "q" is quit ...

---

### Post by blkc4us on 2006-07-03
using vi
cursor movement - h,j,k,l (left,down,up & right)
Delete charater - x
Delete line - dd
Mode toggle - ESC, Insert (or i)
Quit - :q
Quit without saving - :q!
Save file - :w
Text search - /

---

### Post by DyWaN on 2006-07-04
Hi guys, it's me again. I've downloaded and installed swat <-- was told to be much more easier to edit a smb.conf file. I read the manual using man swat from the terminal and it told e how to launch swat which is to start my browser and type : [http://localhost:901](http://localhost:901).

I've done so but the browser came up with an error. Do I have to do any configurations to make swat works? thanks guys, you've been very helpfull for newbie like me.

---

### Post by scxtt on 2006-07-04
it's using port 901 to make a connection to your box, i've never used that program - but try [http://127.0.0.1:901](http://127.0.0.1:901) and see if that works ...

---

