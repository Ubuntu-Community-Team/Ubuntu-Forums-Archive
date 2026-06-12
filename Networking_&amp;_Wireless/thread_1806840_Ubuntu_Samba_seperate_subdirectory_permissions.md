---
title: "Ubuntu Samba seperate subdirectory permissions"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by dglad4 on 2011-07-18
Okay so I decided to turn my NAS over from Windows Server 2003 to Ubuntu 11.04 Desktop. This was a big leap for me as I'm still quite new to Linux, but I thought it'd be worth it. I've got everything working pretty good such as Apache2, SSH and converting my disks to ext4.

My problem however is Samba. I've got it to share out my hard drives okay but haven't got effective permissions just yet. All drives and the documents storage folder have write permissions by everyone at the moment but I'm the only one that really uses them in the LAN. What I need to do is be able to do what can be done on Windows Server, create a share, set who can access it (user or group) and then under Windows Explorer change folder permissions so say Elliot can access the share and folder Stuff but Sandra can access the share and not Stuff.  Which is easy enough on Windows but I need the folders under that share to work the same with Samba. Here is how the drives are mounted and where the documents folder is located:

"Samba share name" at "mount/folder"
"datastore1" mounted at "/srv/ds1"
"datastore2" mounted at "/srv/ds2"
"datastore3" mounted at "/srv/ds3"
"documents$" located at "/srv/ds1/userdata"

All drives mounted with full read/write permissions. I need the separate users folders in the documents folder only accessible by root and that user. I managed to do this with chown and chmod in the terminal but this only applies to the local system and not Samba. I was thinking separate shares for the users but if I wanted to create a folder somewhere in the data drives such as "Administrators" then I would need separate folder permissions under that share.

Anyone got any ideas?

Thanks,
dglad4.

---

### Post by dglad4 on 2011-07-21
Still no one? Damn.

---

### Post by jmoorse on 2011-07-21
> **dglad4 said:**
> Still no one? Damn.

You might want to move this to the server forum, it is not really a networking problem.

---

### Post by capscrew on 2011-07-22
> **dglad4 said:**
> Okay so I decided to turn my NAS over from Windows Server 2003 to Ubuntu 11.04 Desktop. This was a big leap for me as I'm still quite new to Linux, but I thought it'd be worth it. I've got everything working pretty good such as Apache2, SSH and converting my disks to ext4.

My problem however is Samba. I've got it to share out my hard drives okay but haven't got effective permissions just yet. All drives and the documents storage folder have write permissions by everyone at the moment but I'm the only one that really uses them in the LAN. What I need to do is be able to do what can be done on Windows Server, create a share, set who can access it (user or group) and then under Windows Explorer change folder permissions so say Elliot can access the share and folder Stuff but Sandra can access the share and not Stuff.  Which is easy enough on Windows but I need the folders under that share to work the same with Samba. Here is how the drives are mounted and where the documents folder is located:

"Samba share name" at "mount/folder"
"datastore1" mounted at "/srv/ds1"
"datastore2" mounted at "/srv/ds2"
"datastore3" mounted at "/srv/ds3"
"documents$" located at "/srv/ds1/userdata"

All drives mounted with full read/write permissions. I need the separate users folders in the documents folder only accessible by root and that user. I managed to do this with chown and chmod in the terminal but this only applies to the local system and not Samba. I was thinking separate shares for the users but if I wanted to create a folder somewhere in the data drives such as "Administrators" then I would need separate folder permissions under that share.

Anyone got any ideas?

Thanks,
dglad4.

If you want to have separate users data using Samba then use the [homes] share parameter in the /etc/samba/smb.conf file.  That's exactly what it's for.  See "The [homes] section" [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for more information.  Google gets you [homes]+samba&btnG=Go!"]**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.google.com/search?q=).

---

### Post by capscrew on 2011-07-22
> **jmoorse said:**
> You might want to move this to the server forum, it is not really a networking problem.

I used to wonder why Samba was considered networking (it's not connectivity for sure), but I go with the flow.  Most of us know that Samba is discussed in both forums.  :-)

---

### Post by jmoorse on 2011-07-22
> **capscrew said:**
> I used to wonder why Samba was considered networking (it's not connectivity for sure), but I go with the flow.  Most of us know that Samba is discussed in both forums.  :-)

Fair enough, not a big samba man here.  I am just waiting for the day someone asks about bgp... :)

---

### Post by dglad4 on 2011-07-24
> **capscrew said:**
> If you want to have separate users data using Samba then use the [homes] share parameter in the /etc/samba/smb.conf file.  That's exactly what it's for.  See "The [homes] section" [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for more information.  Google gets you [homes]+samba&btnG=Go%21"]**_[COLOR=DarkSlateGray]this[/COLOR]_**]("http://www.google.com/search?q=).

EXCELLENT! Talk about think outside the square! I get it now and never would have thought of it! Use the Samba logons to connect home directory, and using the magic of Linux create a soft link in the users home directory to the drives, which allows Linux permissions to take over. Mapping network drives couldn't be harder than one more directory deep in the share.

Brilliant:popcorn:

Thankyou very much. I'll report back when I've applied the changes and tested them. :D

---

### Post by dglad4 on 2011-07-27
Yep, did the trick nicely. Samba is now sharing out to the LAN at \\192.168.1.100 with \username then their home directory shown. I managed to get the correct permissions on the drives where a group "admin" can write and users only read. I'm the server owner so I get the ownership and permissions set at 775 for all data, 770 for administrators folders and the userdata folder as 755 so only I and root can create new folders for users. All user folders are chown to me:user with chmod 770 to lockout guests. The magic of soft links allowed me to create ds1/2/3 in each of the users home folders which then allowed a simple Windows batch logon script of

net use Z: \\192.168.1.100\%USERNAME%\ds1
and so on

The redirected user shell folders on the Windows clients were set to

\\192.168.1.100\%USERNAME%\ds1\userdata\%USERNAME%\My Documents
etc

Everything works perfectly. Very happy with my Ubuntu server now especially as its getting a hardware upgrade soon. 8GB of RAM will give plenty of VM play ;)

Once again thanks all and hopefully this helps someone else in the future aswell.
dglad4.

---

