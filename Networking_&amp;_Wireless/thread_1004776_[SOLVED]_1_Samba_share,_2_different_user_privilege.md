---
title: "[SOLVED] 1 Samba share, 2 different user privileges"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2008-12-07
I am setting up a samba share but I am confused about one thing, how can I setup 2 different types of user access privileges on the same Share?

_For Example:_
I am sharing a media folder to an XBMC box with the username xbox, that I want to only have READ privileges (NO WRITE).  But I also on that same share want myself user basskozz to have full access (READ & WRITE).  How can I set this up in smb.conf?

---

### Post by BassKozz on 2008-12-07
**UPDATE**
I found out about "read list" & "write list": [http://oreilly.com/catalog/samba/chapter/book/ch06_02.html](http://oreilly.com/catalog/samba/chapter/book/ch06_02.html)

and I've modified my smb.conf file like so:
```
[RAID-Storage_Media]
        comment = Unicorn-NAS Media Folder on RAID5
        read only = yes
        valid users = xbox basskozz
        read list = xbox
        write list = basskozz
        path = /media/RAID-storage/Media
        browsable = yes
        available = yes

```

I added the user 'xbox':
```
sudo useradd -d /dev/null -s /sbin/nologin -g sambashare xbox
```
*Note: 
"-d /dev/null" tells ubuntu not to create a /home/ directory for this user
"-s /sbin/nologin" tells ubuntu not to let the user login to shell (or ssh)
"-g sambashare" adds the user to the 'sambashare' group

I then added the user to the smbusers:
```
sudo smbpasswd -a xbox
```

But I still can't login to the share via the 'xbox' user, althou logging in via my useraccount (basskozz) works just fine and I have RW permission (as I should)...

PLEASE HELP[-o<, what am I missing to get access via the user account 'xbox'
TiA,
-BassKozz


**EDIT**: Here are two screenshots of what happens when I try and login to the samba share using 'xbox' on the same machine that the share resides:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/nautilus-smblogin.png[/IMG][IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/smb-unabletomount.png[/IMG]
Again, I can login fine using 'basskozz' but not 'xbox'

---

### Post by mgmiller on 2008-12-07
Try installing the package:
```
sudo apt-get install system-config-samba
```

Once it's installed, find it in System > Administration > Samba

This gui will let you set up and configure shares.  Although I haven't tried to set up more than one for a given directory, in theory you could simply set up a share for one user with write access and another share to the same folder for a different user without write access.

---

### Post by BassKozz on 2008-12-07
Thanks for the suggestion mgmiller,

I installed the gUI and I setup two separate shares like you recommended and now here is what my */etc/samba/smb.conf* looks like:
```
[RAID-Storage_Media]
	comment = Unicorn-NAS Media Folder on RAID5
	writeable = yes
	valid users = basskozz
	path = /media/RAID-storage/Media
;	browseable = yes
;	available = yes

[Xbox]
	comment = Unicorn-NAS Xbox Share
	path = /media/RAID-storage/Media
;	writeable = no
;	browseable = yes
	valid users = xbox

```
but I still can't seem to login as user 'xbox' on the newly created 'Xbox' share even from localhost. :confused:
Could it have something to do with the actual folder permissions of */media/RAID-storage/Media*, because I can login as my local account 'basskozz' but not 'xbox' I think that might be the reason, what can I set the folder permissions to to allow multiple users access?

---

### Post by mgmiller on 2008-12-07
Does the user "xbox" exist on the machine that is hosting the share?  I wonder if you have to set up an account for that user before you can share something for "him".  I realize you added all sorts of xbox as user things to samba, but did you create the actual user account xbox?

You can navigate to the folder using a root browser:
```
gksu nautilus
```Then right click the folder and select permissions and allow read for everyone.

---

### Post by mgmiller on 2008-12-07
Here is another thought.
Go into the samba gui and at the top, click Preferences > Server Settings
Select the Security tab.
In the "Guest Account" drop down, change it from "No Guest Account" to "xbox".

See if that works....

---

### Post by BassKozz on 2008-12-07
> **mgmiller said:**
> Does the user "xbox" exist on the machine that is hosting the share?  I wonder if you have to set up an account for that user before you can share something for "him".  I realize you added all sorts of xbox as user things to samba, but did you create the actual user account xbox?
Yes that was part of this line in a previous post:
```
sudo useradd -d /dev/null -s /sbin/nologin -g sambashare xbox
```
That added a Unix user 'xbox', then I also added a samba user 'xbox' with the following:
```
sudo smbpasswd -a xbox
```
> **mgmiller said:**
> 
You can navigate to the folder using a root browser:
```
gksu nautilus
```Then right click the folder and select permissions and allow read for everyone.
Did that, still won't let me login as 'xbox' :(
> **mgmiller said:**
> Here is another thought.
Go into the samba gui and at the top, click Preferences > Server Settings
Select the Security tab.
In the "Guest Account" drop down, change it from "No Guest Account" to "xbox".

See if that works....
Tried it, nope still won't let me login as 'xbox' :(

---

### Post by BassKozz on 2008-12-08
Well I've been trying a million different things to try and get this working:
[LIST]
[*]I deleted the 'xbox' user and recreated it
[*]I removed the 'xbox' share and recreated it
[*]After the above didn't work I reinstalled all the samba packages using Synaptic Package Manager
[*]Then I created a new user 'xbmc' (without the options-"-d /dev/null -s /sbin/nologin -g sambashare") and a new share 'xbmc' 
still nothing :(, so I removed both of those
[*]Tried good 'ol xbox user & share again by manually editing */etc/samba/smb.config*
[/LIST]
And after all this I am still STUCK ](*,)


A couple of things I noticed;
[LIST=1]
[*]When I try and change the permission of the shared folder (even using 'gksudo nautilus') it just reverts back to it's previous settings:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/Screenshot-MediaProperties.png[/IMG] The blanked out 'owner' is my real login, but for all-intents-and-purposes let's call it 'basskozz'
So if I enter **Others > File Access = Read Only**, and apply, and re-open it reverts back to it's previous setting "---"


[*] Also I've been researching the "encrypted passwords = true" setting of */etc/samba/smb.conf*, apparently this usually goes hand-in-hand with another setting **smb passwd file = /etc/samba/smbpasswd** according to this post: [http://ubuntuforums.org/showthread.php?t=76647&p=442015](http://ubuntuforums.org/showthread.php?t=76647&p=442015)

But I can't find that setting in my */etc/samba/smb.conf* :confused:
Is this required? or has that been depreciated with the latest version of samba?  Could this be causing my problems?[/list]
PLEASE HELP [-o<

---

### Post by mgmiller on 2008-12-08
> But I can't find that setting in my */etc/samba/smb.conf* :confused:
Is this required? or has that been depreciated with the latest version of samba?  Could this be causing my problems?

The uncommented line  "encrypt passwords = true" exists in my [I]/etc/samba/smb.conf and I didn't add it. 

The line "[/I]**smb passwd file = /etc/samba/smbpasswd**[I] " does not exist in my smb.conf

Note also that the file /etc/samba/smbpasswd does not exist on my system.


It also says at the beginning of the smb.conf file:
"Samba has a huge number of configurable options most of which 
 are not shown in this example"

Have you tried running the command:
[/I]```
testparm
```
to check that you have not made any basic syntactic errors?

One change that I make to all my machines that use samba is to edit the area that says:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

```

So that the last line looks like this:
  ```
name resolve order = lmhosts wins bcast host

```
notice I have removed the ; and changed the resolve order

The final thing that I can think of is have you restarted the samba service since making these changes?
```
sudo /etc/init.d/samba restart
```

---

### Post by BassKozz on 2008-12-08
> **mgmiller said:**
> 
One change that I make to all my machines that use samba is to edit the area that says:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

```

So that the last line looks like this:
  ```
name resolve order = lmhosts wins bcast host

```
notice I have removed the ; and changed the resolve order

The final thing that I can think of is have you restarted the samba service since making these changes?
```
sudo /etc/init.d/samba restart
```
Ok I changed my "***name resolve order***" to look like yours restarted samba and still no good :(
> **mgmiller said:**
> 
Have you tried running the command:
```
testparm
```
to check that you have not made any basic syntactic errors?
I don't think there are any syntax errors because I reinstalled all the samba packages and overwrote the **smb.conf** file when I re-installed and setup everything via the GUI, but anyways here are the results for testparm:
```
testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[RAID-Storage_Media]"
Processing section "[Xbox]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts wins bcast host
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[RAID-Storage_Media]
	comment = Unicorn-NAS Media Folder on RAID5
	path = /media/RAID-storage/Media
	valid users = basskozz
	read only = No

[Xbox]
	comment = Unicorn-NAS Xbox Share
	path = /media/RAID-storage/Media
	valid users = xbox
```

Thanks for all the help mgmiller I really appreciate it.
I just wish I could get this thing working, I can't figure out what is wrong here.

---

### Post by mgmiller on 2008-12-08
You're welcome.  

Is user "xbox" able to work with any shares on your server?  Try setting up a new folder that is only shared by xbox and see if he can access it.  If so, look closely at smb.conf for a clue as to why xbox can see one folder, but not another.  If you can't get any shares working for xbox, it's probably a system wide permissions thing, perhaps, xbox not being in the right groups.
I only wish I could figure out what your problem is.  Beyond this, I'm stumped.

If I think of something else, I will post back here.

If you do figure it out, please post here so I can see the solution also.

---

### Post by BassKozz on 2008-12-09
Just an update:
I've renamed the /Media/ directory to /media/ (thinking the cap "M" might have been the culprit), nope still broken :-(
I've "sudo chown 777" my folder that is being shared, didn't fix it :-(
I created a completely new folder and setup a new share (named "Xbox"), and still Broken :cry:
I also have been reviewing my /var/log/samba folder and I've narrowed down the exact error message:
```
[2008/12/08 23:58:24,  0] smbd/service.c:make_connection_snum(1152)
  '/media/RAID-storage/media' does not exist or permission denied when connecting to [Xbox] Error was Permission denied

```
After doing a google search for "smbd/service.c:make_connection_snum(1152)" it looks like quite a few people have had similar issues, but I have yet to find a definitive solution...
I'll post back when I learn more.
Thanks Again

_**Edit, another Update:**_
I learned how to login to smb shares via the command line (so I am not using Nautilus any more to try and access them, to rule out Nautilus as the culprit) here are the results:
```
basskozz@Unicorn-NAS:/var/log/samba$ smbclient //Unicorn-NAS/RAID-Storage_Media/
Enter basskozz's password: 
Domain=[UNICORN-NAS] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Sun Dec  7 16:23:43 2008
  ..                                  D        0  Mon Dec  8 23:47:50 2008
  Test                                A        0  Sun Dec  7 16:20:12 2008
  14 - I Wish You Well.mp3            A 11021582  Sun Dec  7 16:23:44 2008

		58682 blocks of size 8388608. 55674 blocks available
smb: \> exit
basskozz@Unicorn-NAS:/var/log/samba$ smbclient //Unicorn-NAS/Xbox/
Enter basskozz's password: 
Domain=[UNICORN-NAS] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_ACCESS_DENIED
basskozz@Unicorn-NAS:/var/log/samba$ smbclient //Unicorn-NAS/Xbox/ -U xbox
Enter xbox's password: 
Domain=[UNICORN-NAS] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
basskozz@Unicorn-NAS:/var/log/samba$ 

```

On the first login above I logged into my working share that uses my login.
On the second login I tried to login to the 'xbox' share using my main login account which didn't work ***AS EXPECTED*** because 'basskozz' is not a valid user for that share
On the third login I tried to login to the "Xbox" share using user 'xbox', still not working but now I have a new error to look into: **NT_STATUS_BAD_NETWORK_NAME**

---

### Post by BassKozz on 2008-12-09
SOLUTION FOUND !!! \\:D/
FINALLY !!! =D>

I must give credit to this post: [http://www.linuxquestions.org/questions/showthread.php?p=3189392#post3189392](http://www.linuxquestions.org/questions/showthread.php?p=3189392#post3189392)
> Had the same problem ... spent the better part of a day trying to work through it. For me, the error message set me up for failure by leading me down the wrong path looking for a solution. The real underlying problem was directory permissions two directories above in the path.

Be sure the entire path has at least golbal 'read' permissions set!
The problem was that the perant directory /media/**RAID-storage** had it's "others" folder access set to "none" ](*,)

I am up and running now, THANK GOD that's over. :lolflag:
I am so excited right now, Thanks for all the help mgmiller ):P

---

### Post by mgmiller on 2008-12-09
Hooray!  The solution actually makes sense.  

This is a valuable lesson, the whole path has to have the correct permissions, not just the target folder.

Glad it's finally working.....):P

---

