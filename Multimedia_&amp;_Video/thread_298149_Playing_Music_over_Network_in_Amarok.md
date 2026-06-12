---
title: "Playing Music over Network in Amarok"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Arkitekt on 2006-11-12
I am giving serious thought to switching over to Ubuntu. but i do have a couple questions (most i have posted in another thread) but this one question is a multimedia question specificly and i thought i would post it here.

what i want to do is get Amarok on my machine. I have a windows box and my windows box connected to the internet through a router, so they can be set up to see eachother (after a little playing around). what i want to be able to do is have amarok play music that is located on my windows box, essentially playing it over the network. my windows box has a 180 gb HDD whereas my linux box only has a 20 gb. so you see why i would want such a setup. also i plan on investing in a laptop in the near future and setting linux up on it , and would love to do the same thing. 

Is it possible? and if so how? i have tried and tried on fedora core and have gotten no where (very frustrating). i have tried using mt-daapd and just mounting the folder, neither worked sucsessfully. if it is possible can some provide me either with some instructions on how to do so, or a link to maybe a How-To.

Any and all help will be appreciated.

---

### Post by xlulux on 2006-11-12
the way that i do it is by mounting the windows shared out harddrive as a network drive then playing the songs. this worked for xmms but ymmv.

---

### Post by Arkitekt on 2006-11-12
well i am more interested in how to do it with amarok. i perfer it over anything else. can someone provide me with a howto or small guide?

---

### Post by comforteagler on 2006-11-13
you can play music in amarok from another computer in your network
by installing samba and sharing the music on your windows computer
using windows file sharing

now you can mount the shared mp3 folder from your windows machine in your ubuntu machine and use the settings of amarok to play music from this
folder

---

### Post by Arkitekt on 2006-11-13
thanx :) i will definatley try that. one thing, im not entirely sure on how to mount, im gonna search around for a guide somewhere, however if you have one or know of a great one please let me know :)

---

### Post by fvboegeld on 2006-11-14
I used the following commands and it works without a prob

mkdir /mnt/**network**
chmod 0777 /mnt/**network**
mount -t cifs //**windows_name**/**windows_share** /mnt/**network** -o user=**windows_user**,password=**windows_password**

networks : just give it a name
windows_name : IP Adres or name of your windows station
windows_share : Name of your windows share (or d$)
windows_user : Windows username
windows_password : Windows username password

---

### Post by Arkitekt on 2006-11-14
great thanx, :D hopefully that works. One thing though, if the windows users do not have passwords do i just type in 'password=' or should i not even include that in the line?

---

### Post by lazyart on 2006-11-14
If there is no password then just eliminate the -o and everything after it.  I just did this yesterday with Exaile, which is about equivalent to amaroK, but for gnome.

---

### Post by mrvgarg on 2006-11-14
The easiest way to do is to set up itunes on windows and use rhythmbox or banshee on Linux. But all the songs must be mp3 format.

---

### Post by Arkitekt on 2006-11-14
i will check out Exaile, but i use amarok in Gnome though, only depenancie i think is kdelibs. but i could be wrong.

personally i dont like rhythmbox, but its all preferance. and all my songs are mp3 format. thanx for the help guys really appreciate it.

---

### Post by cdinoz on 2006-11-15
Sorry to hijack (slightly) a thread - mrvgarg - I used to to stream my mp3's from my windows box using rhythmbox - but since upgrading from dapper to edgy - this method no longer seems to work - I point the player at the shared files in windows - but rythmbox simply crashes continually now 

Any suggestions?](*,)

---

### Post by Arkitekt on 2006-11-15
not a hijack at all :) may not be about amarok but still an issue regarding networked music. Hopefully someone can answer you. :)

---

### Post by billputer on 2006-11-15
> **cdinoz said:**
> Sorry to hijack (slightly) a thread - mrvgarg - I used to to stream my mp3's from my windows box using rhythmbox - but since upgrading from dapper to edgy - this method no longer seems to work - I point the player at the shared files in windows - but rythmbox simply crashes continually now 

Any suggestions?](*,)
Have you tried using a different player to play the files?  That might narrow down where the problem is.

---

### Post by Arkitekt on 2006-11-22
> **fvboegeld said:**
> I used the following commands and it works without a prob

mkdir /mnt/**network**
chmod 0777 /mnt/**network**
mount -t cifs //**windows_name**/**windows_share** /mnt/**network** -o user=**windows_user**,password=**windows_password**


I did that and this is the output

```
jboyd@jboyd-desktop:~$ sudo mount -t cifs //tara/Downloads /mnt/network
mount: wrong fs type, bad option, bad superblock on //tara/Downloads,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

i then tried to dmesg output and got

```
jboyd@jboyd-desktop:~$ dmesg | tail
[17195158.564000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[17195158.564000] ide: failed opcode was: unknown
[17195158.640000] cdrom: failed setting lba address space
[17195160.208000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17195160.208000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[17195160.208000] ide: failed opcode was: unknown
[17195160.256000] cdrom: failed setting lba address space
[17195164.132000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17195166.212000] ISOFS: changing to secondary root
[17391971.132000]  CIFS VFS: cifs_mount failed w/return code = -22
```

any ideas guys??

---

### Post by gbesso on 2006-11-22
Try using smbfs instead of cifs

---

### Post by Arkitekt on 2006-11-22
> **gbesso said:**
> Try using smbfs instead of cifs

same issue

```

jboyd@jboyd-desktop:~$ sudo mount -t smbfs //tara/Downloads /mnt/network
mount: wrong fs type, bad option, bad superblock on //tara/Downloads,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jboyd@jboyd-desktop:~$ dmesg | tail
[17195158.564000] ide: failed opcode was: unknown
[17195158.640000] cdrom: failed setting lba address space
[17195160.208000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17195160.208000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[17195160.208000] ide: failed opcode was: unknown
[17195160.256000] cdrom: failed setting lba address space
[17195164.132000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17195166.212000] ISOFS: changing to secondary root
[17391971.132000]  CIFS VFS: cifs_mount failed w/return code = -22
[17464197.916000] smb_fill_super: missing data argument

```


EDIT: i have installed smbfs from apt-get and it seemed to mount. ill see if amarok can read it now. thanx for the help guys

Edit V2: IT WORKED! thanx for all your help guys, i can now play music from my other comp on this one :). now only to turn another box into a pure music/file server

---

### Post by eriefisher on 2006-11-22
VLC has the ability to catch and stream all media. It is also cross platform, Linux,Windows,Mac. Just another option.

---

### Post by Arkitekt on 2006-11-28
ok new problem, i got everyhting to mount alright, but now when i restart its all gone, i have to mount it again... why? and how can i have it be permenant, add it to startup?

---

### Post by 5h4rk on 2006-11-29
Can I play music remotely using SSH in a remote Windows based station?

---

### Post by amadeus266 on 2008-01-10
> **gbesso said:**
> Try using smbfs instead of cifs

thanks for that tip. it fixed my network music woes!

---

