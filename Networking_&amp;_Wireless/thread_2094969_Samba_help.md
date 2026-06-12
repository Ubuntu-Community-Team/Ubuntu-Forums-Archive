---
title: "Samba help"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by keysys on 2012-12-15
Hi,

I'm New for this Forum.before posting this i would like to say that I'm not a expert in Linux,

as my Company File Server need to migrate to Linux Server platform.So i have Successfully Joined Linux OS to windows 2003 Domain Environment and integrated active directory.but i need to verify some basic couple to questions regards Samba File Sharing Between Linux and windows (as my company has different   windows Environments such as Windows 7/XP/2000).

My Question is ..

1. MY Domain Name is ABC
2. Active Directory Users are User01 , User02 , Admin-(Its Me) rest of users are normal Domain Users
3. Linux File /media

 1 have declare bellow case in my Smb.conf file in order to access my samba share to above users & my requrirment is user01 has full access and User02 should be as read only permissions
                
[media]
        Comment = MY MEDIA
        Path = /media
        Writeable = yes
        public = no
        Valid Users = ABC\User01
        read list = ABC\User02
after done the sharing path i checked access permission on above users client Pc & Found user01 has full permissions on shared directory but User02 doen't have read permissions :o

MY Linux file Permissions is drwxrwxrwx for shared Directory.

Hope you can understand my point and think i will reach good answer for this file sharing

Thank You Very Much.

---

### Post by keysys on 2012-12-15
can you any body give a suggestion on regards ???

---

### Post by xmanhattan on 2012-12-16
Hello keysys,

I am new to ubuntu but I have used samba on other linux setups.
This is a pretty good site for some more info on samba.
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba#.UM22xayQmBo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba#.UM22xayQmBo)

From my experience there are a few things that have to be checked:
Can the users access the linux system other than what you are trying to share?
I think that the xp users need to have a password embedded into the registry.

From this line > Valid Users = ABC\User01 I always used lowercase for all parameters.  I don't know if you really have to use the ABC\ as I always used the user names separated by a space.  Also the user name you show has a capital letter so I assume that is the format of the names as well.

Have a look at that link, recheck your settings and let's see what happens.

---

### Post by keysys on 2012-12-16
[COLOR=SandyBrown][COLOR=Black]Hi [xmanhattan]("http://ubuntuforums.org/member.php?u=1766451"),

Appreciated your help regards,

as my samba server everything  is working perfelly except read only permissoin.my only concens is how to i assign a Read only Permission to specific user.

as per Google findings when assing read list on smb.conf as read list = MYDOMAIN\USER.then user will not be able to modify the contents on the shared folder,

that what im expecting at the right moment.but still im not received good answer.

also note that my smb.conf security is ADS

[B]Security = ads



[/B]


[/COLOR]
[/COLOR]

---

### Post by xmanhattan on 2012-12-16
Here is what I did for a user and a shared directory:
> 
[pab]
    comment = User Directory
    path = /
    browseable = yes
    writable = yes
    available = yes
    public = no
    only user = no
[tmp]
    comment = Share Directory
    path = /tmp
    valid users = pab kmb
    browseable = yes
    writable = yes
    available = yes
    public = yes
    printable = no


I haven't used ADS so I can't answer you on that one.
[https://wiki.samba.org/index.php/Samba_&_Active_Directory](https://wiki.samba.org/index.php/Samba_&_Active_Directory)

Hope it helps

---

