---
title: "Error 255 cannot convert name &quot;Everyone&quot; to a SID"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by ccslive on 2009-07-06
I am trying to make a simple home network with samba. the problem is that I can't share any folders because of the error 

"net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter"

There has been a couple post about it but the non of the work arounds have worked any help would be greatly appreciated
](*,)
I'm using ubuntu  9.04

---

### Post by Iowan on 2009-07-06
I've seen this issue before... but I'll need to search for similar threads (or you can... ;) )

---

### Post by ccslive on 2009-07-06
I have spent the last couple days looking and this is my last ditch effort. I appreciate the help.

---

### Post by swerdna on 2009-07-07
Maybe a thorough look would help:

Please post the [global] stanza of smb.conf so we can check your "usershare" setup.

Also, can you show us the permissions on one of the offending shares -- suppose the share abcde is located at /path_to/abcde, run this terminal command and post back: > ls -l /path_to/ That will show us the perms on the share. Then run this: > ls -l /path_to/abcdeThat will show us the objects inside the share.

Then finally, show us the config file for the shared directory abcde by running this terminal command:> cat /var/lib/samba/usershares/abcde

---

### Post by ccslive on 2009-07-07
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup

# server string is the equivalent of the NT Description field
    server string = MEADIA SERVER

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


the other info I think you want is...


[printers]
    comment = All Printers
    browseable = yes
    path = /var/spool/samba
    printable = yes
;    guest ok = yes
;    read only = no
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[Videos]
    comment = Videos
    path = /home/mathew/Videos
    writeable = yes
    browseable = yes
    guest ok = yes

---

### Post by swerdna on 2009-07-07
Your [global] contains no reference to usershares which causes it to default to these values:
```
        usershare allow guests = No
        usershare max shares = 0
        usershare owner only = Yes
```
That will cause pronlems so you should edit smb.conf and insert these alternate lines underneath [global]:
```
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```

You can open the file for editing in a superuser editor with this terminal command:
```
gksu gedit /etc/samba/smb.conf
```

Also, please post back the other three pieces of information that I asked for. I'll repeat in case u aren't quite sure:

> ..........show us the permissions on one of the offending shares -- suppose the share abcde is located at /path_to/abcde, run this terminal command and post back: ```
ls -l /path_to/
``` That will show us the perms on the share. Then run this: ```
ls -l /path_to/abcde
```That will show us the objects inside the share.

Then finally, show us the config file for the shared directory abcde by running this terminal command:```
cat /var/lib/samba/usershares/abcde
```

---

### Post by MinonBer on 2009-07-09
Hello linux noob here  
I'm in the same boat as the original poster  I'm using Ubuntu 9.04  details requested as follows  
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = bcast host lmhosts wins

# User Entered Settings by me Hubris
	usershare allow guests = Yes
;	usershare max shares = 100
	usershare owner only = False

	netbios name = hubris
	map to guest = Bad User
	os level = 33
;	printing = cups
	printcap name = cups
;	printcap cache time = 750
	cups options = raw
	use client driver = yes
;	local master = yes
	preferred master = yes

   other details from smb.conf  

 [Installs]
	path = /media/Media/Installs
;	writeable = no
;	browseable = yes
	guest ok = yes

hubris@Hubris-study:~$ ls -l /var/lib/samba/usershares/
 total 8 
-rw-r--r-- 1 hubris hubris 82 2009-07-03 12:07 installs 
-rw-r--r-- 1 hubris hubris 80 2009-07-03 12:07 movies  
 
hubris@Hubris-study:~$ ls -l /var/lib/samba/usershares/installs
-rw-r--r-- 1 hubris hubris 82 2009-07-03 12:07 /var/lib/samba/usershares/installs   

hubris@Hubris-study:~$ cat /var/lib/samba/usershares/installs 
#VERSION 2 
path=/media/Media/Installs 
comment= 
usershare_acl=S-1-1-0:R 
guest_ok=n    

OK that's all I think which has been asked for I followed Swerdna's tutorials on how to set up the network between ubuntu and windows. Thanks by the way, it was the most clearly written of all the networking guides I found.  
Also currently I cannot see any other computers on the network, including windows and ubuntu computers (ubuntu PCs set up as a non-Preferred Local master browsers), but as I do not know much about ubuntu yet I'm not sure that this is even related to the above error.  
-whenever I open the network browser and try to open the network listed (windows network) it fails to mount, this behaviour changes when i switch to a dynamic IP address i can open the network then but nothing shows  other things that have been suggested i try include disabling the firewall, which makes no difference and when enabled i've made sure the the required ports were open for samba 
 and findsmb only shows my ip address if thats important 

 I've decided to mention it in case it relates. Sorry if this steals the thread from the original poster. Its not my intention hopefully any solution for me helps or sheds light for them.  

Remember noob linux user here so be kind 

 Cheers

---

### Post by swerdna on 2009-07-09
@MinonBer
Does this > I'm in the same boat as the original poster mean that you are getting this error:> net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter? Should I be focusing on the same error for you? While you answer that, here are a few comments:

Take the comment (semicolon) off this line: > **[COLOR="Red"];[/COLOR]** usershare max shares = 100

You have shared "installs" two ways, once in the classical fashion by adding a stanza to smb.conf, and once using the sharing tool in Nautilus (which generates a "usershare" in /var/lib/samba/usershares). These are different styles. Choose one or the other, not both.

And what do you get when you run this command: ```
sudo /etc/init.d/samba status
```and this command:```
sudo ufw status
```

Check that the workgroup name you've used here is the same on all Linux machines and also on the win boxes.

Reboot your network hardware (routers and switches etc). Then when they settle, reboot all the workstations in sequence, not simultaneously, allowing each to settle before rebooting the next. (I know that sounds extreme, but you'd be surprised what it can shake loose.)

---

### Post by Janeleaper on 2009-07-09
Hi.  I'm getting the same error message as above and need some advice.

My situation is as follows.  I'm trying to file-share between two dell Inspiron computers.  One has Ubuntu 8.10 and the other 8.04.

The 8.10 is the older machine.  Previously I tried to get it to file share with a computer running Windows XP using Samba but without success, but I suspect that whatever I did then is causing the problem now.

Neither machine currently has Samba installed.  I've successfully set up a shared folder on the new 8.04 machine.  The 8.10 machine can see it.  When I try to set up a shared folder on the 8.04 machine I get the message:

"net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter."

What do I do?

---

### Post by Janeleaper on 2009-07-09
I should add that I need talking through it.  I don't know what a stanza of smb.conf is, for example.  Sorry.

---

### Post by swerdna on 2009-07-09
> **Janeleaper said:**
> I should add that I need talking through it.  I don't know what a stanza of smb.conf is, for example.  Sorry.
This order:


Step 1: Install Samba. System --> Administration --> Synaptic Package Manager and install samba and samba-common and smbclient and nautilus-share and libsmbclient

Step 2: Have you got these three lines in your samba config file, smb.conf, located at /etc/samba/smb.conf:
```
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```

Step 3: check exists directory /var/lib/samba/usershares

Step 4: reboot

---

### Post by Janeleaper on 2009-07-09
I've installed Samba.  I've searched for a file called samba/smb.conf.  I get the message "no files found"

---

### Post by Janeleaper on 2009-07-09
I've checked.  The other applications you told me to install are intalled.

---

### Post by Janeleaper on 2009-07-09
Sorry.  I've found the file now.  I didn't realise the "etc" meant something.

The file does not have the three lines you mention.  It has:

usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

---

### Post by Janeleaper on 2009-07-09
Do I replace those lines or just add the ones you gave me?  

I do have the directory.

---

### Post by Janeleaper on 2009-07-09
I'm also being told I don't have the permissions necessary to save the file.

---

### Post by MinonBer on 2009-07-10
just to clarify 
I'm in the same boat as the original poster means that i am having the same error
"net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter"
when i try to share files in nautilus (right click->sharing options->share)

sorry if i was not clear

sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running

sudo ufw status
To                         Action  From
--                         ------  ----
6542                       ALLOW   Anywhere
2049                       ALLOW   Anywhere
135/tcp                    ALLOW   Anywhere
Samba                      ALLOW   Anywhere


"samba" as above is listed in the gui of the firewall as 137,138 udp
and 139, 445 tcp

Swerdna if you could focus on the same error as the original poster for me that would be great. The only reason i brought up my other problems was in case they were related. As i am new to linux I can't tell if they are related.


and Janeleaper ubuntu saying that you don't have permisssions to edit the file means that you need to open the file as a superuser

first you should backup the file
open the terminal under the application menu->accessories->terminal

enter
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
it might ask for a password (this is your root password)

and then to edit smb.conf the terminal and enter
sudo gedit /etc/samba/smb.conf

this will open smb.conf and allow you to edit and save it

Janeleaper you may find this link extremely useful (i know i did)
it is a fairly good walkthrough setting up a home network
[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by Janeleaper on 2009-07-10
Thanks to both of you.  I suspect I'm being particularly dense about this, but I'm still confused.  I'm not trying to set up a Microsoft Windows - Ubuntu network, only Ubuntu - Ubuntu, so I shouldn't need Samba at all -- I think.  

But -- my problems seems to be caused by having attempted to set up a MS -- Ubuntu network in the past using Samba.  Even having uninstalled Samba I seem to have a lot of Samba files on my system.  

I really don't know what to do now.  I'm going to sleep on it and try again tomorrow.

---

### Post by swerdna on 2009-07-10
> **Janeleaper said:**
> Sorry.  I've found the file now.  I didn't realise the "etc" meant something.

The file does not have the three lines you mention.  It has:

usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

You open the file for editing as a superuser, then you'll be able to save the file after editing. Use this terminal command to get it open as a superuser:```
gksu gedit /etc/samba/smb.conf
```

regarding these lines:
> usershare allow guests = yes
username map = /etc/samba/smbusers
security = user
; guest ok = no
; guest account = nobody
leave them as they are and add these two:
```
usershare max shares = 100
usershare owner only = False
```

---

### Post by swerdna on 2009-07-10
> **Janeleaper said:**
> Thanks to both of you.  I suspect I'm being particularly dense about this, but I'm still confused.  I'm not trying to set up a Microsoft Windows - Ubuntu network, only Ubuntu - Ubuntu, so I shouldn't need Samba at all -- I think.  

But -- my problems seems to be caused by having attempted to set up a MS -- Ubuntu network in the past using Samba.  Even having uninstalled Samba I seem to have a lot of Samba files on my system.  

I really don't know what to do now.  I'm going to sleep on it and try again tomorrow.

No you don't need Samba -- you can use it but insteda you can use NFS. So, good luck with that.

---

### Post by swerdna on 2009-07-10
> **MinonBer said:**
> just to clarify 
I'm in the same boat as the original poster means that i am having the same error
"net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter"
when i try to share files in nautilus (right click->sharing options->share)

sorry if i was not clear

sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running

sudo ufw status
To                         Action  From
--                         ------  ----
6542                       ALLOW   Anywhere
2049                       ALLOW   Anywhere
135/tcp                    ALLOW   Anywhere
Samba                      ALLOW   Anywhere


"samba" as above is listed in the gui of the firewall as 137,138 udp
and 139, 445 tcp

Swerdna if you could focus on the same error as the original poster for me that would be great..............
Sure. Haven't heard back from the OP, so over to you: The firewall looks good. If you removed the semicolon and undid one or the other type of sharing, and rebooted all, you could try it again. What's the situation now?

---

### Post by MinonBer on 2009-07-10
Swerdna - I removed the semicolon on
usershare max shares = 100

and removed the nautilus sharing method from the installs folder
installs folder is now only shared one way in the smb.conf
i restarted my computer

when i entered the network browser i still have the same behavior
intially the  network complains that it cannot mount
and on the second try it enters the network share and nothing shows

also i tried on a seperate folder the nautilus sharing method and i still am getting the intial error that the original poster complained of

---

### Post by swerdna on 2009-07-10
Well lets get the classical version going first. Just to be sure it's not the firewall, run this command to shut the firewall: > sudo ufw disable and see if you still get the errors you mentioned:> intially the network complains that it cannot mount
and on the second try it enters the network share and nothing showsOf course, we assume the share is not empty.

Does that change anything with the firewall down?

If not then run the smb.conf through the testparm filter and post back the result. The filter is called by running this command in a terminal: ```
testparm -s
```

---

### Post by Janeleaper on 2009-07-10
I re-installed Samba.  Made the amendments you suggested.  Rebooted.  Same error message - 255.  

Since my problem is with Ubuntu to Ubuntu file sharing, not MS to Ubuntu, I started another thread, but have had no reply.

The problem seems to have been caused by the fact that I installed Samba in the past -- which I now deeply regret.  Is there anyway of completely cleaning Samba from the system, not just uninstalling it?

---

### Post by MinonBer on 2009-07-10
disabling the firewall changes nothing

hubris@Hubris-study:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[Installs]"
Processing section "[Duchess]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = HUBRIS
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	preferred master = Yes
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	cups options = raw
	use client driver = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[share]
	path = /media/Media/share
	guest ok = Yes

[Installs]
	path = /media/Media/Installs
	guest ok = Yes

[Duchess]
	path = /home/hubris/Desktop/Duchess
	guest ok = Yes

---

### Post by swerdna on 2009-07-11
> **Janeleaper said:**
> I re-installed Samba.  Made the amendments you suggested.  Rebooted.  Same error message - 255.  

Since my problem is with Ubuntu to Ubuntu file sharing, not MS to Ubuntu, I started another thread, but have had no reply.

The problem seems to have been caused by the fact that I installed Samba in the past -- which I now deeply regret.  Is there anyway of completely cleaning Samba from the system, not just uninstalling it?
run this in a terminal: ```
sudo locate samba
```Then uninstall samba samba-common and so on.

Then reinitialise the database by running this: ```
sudo updatedb
```Then run this again: ```
sudo locate samba
```or put a copy on your desktop with this:```
sudo locate samba > /home/yourname/Desktop/big_job_ahead.txt
```then you have alist for rooting out the remnants -- but caustion don't delete anything u really need.

---

### Post by swerdna on 2009-07-11
@MinonBer
There's too much stuff in your smb.conf to discuss. I suggest you back it up e.g. with this terminal command: ```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```and then 
```
replace the text in the existing with this:
[global]
workgroup = WORKGROUP_NAME
netbios name = HUBRIS
server string = %h server (Samba, Ubuntu)
name resolve order = bcast host lmhosts wins
map to guest = Bad User
os level = 33
preferred master = yes
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes

[share]
path = /media/Media/share
guest ok = Yes

[Installs]
path = /media/Media/Installs
guest ok = Yes

[Duchess]
path = /home/hubris/Desktop/Duchess
guest ok = Yes
```
and change the WORKGROUP_NAME to whatever it should be. Also re-add users to the samba user database. reboot and try browsing again.

I also assume that you didn't set your other machine/s to seek out a wins server (if u don't know what I'm talking about, then you didn't).

---

### Post by swerdna on 2009-07-11
Just a quick thought while reading the paper Sunday with coffee -- the forum intruded -- gacht!

Anyway, you must have a connection tracker turned on in the ufw firewall for shares to be seen properly in Samba. You can check with this command in a terminal:```
cat /etc/default/ufw | grep netbios
```This is the correct response:> IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"The important bit is "nf_conntrack_netbios_ns". FFI see here:[Opening the Firewall for Samba]("hhttp://ubuntu.swerdna.org/ubulanprimer.html#firewall")

OK back to the real coffee.

---

### Post by MinonBer on 2009-07-11
swerdna you have just made someones day
thankyou very much
everything works now
i'm able to access other pcs on the network and no more error on trying to share folders through nautilus

---

### Post by swerdna on 2009-07-11
> **MinonBer said:**
> swerdna you have just made someones day
thankyou very much
everything works now
i'm able to access other pcs on the network and no more error on trying to share folders through nautilus
fabulous!
So was it the smb.conf or the firewall thing?

---

### Post by MinonBer on 2009-07-11
it was smb.conf

also strangley enough i dont' even get  a response when i enter
cat /etc/default/ufw | grep netbios
in the terminal

---

### Post by swerdna on 2009-07-12
> **MinonBer said:**
> it was smb.conf

also strangley enough i dont' even get  a response when i enter
cat /etc/default/ufw | grep netbios
in the terminal

Don't worry about the "cat etc etc | grep etc" thing. I was just curious. As I recall you had samba allowed in the firewall by rule "sudo ufw allow samba", which doesn't need attention to the connection tracker.

Regarding the fix for smb.conf. It seems to me that you and Janeleaper and the OP ccclive all had the same deficit in the [global] stanza of smb.conf and it is likely that the fix that worked for you would work for them.

Thanks for the reply.
Be well
swerdna

---

### Post by Janeleaper on 2009-07-19
I've decided to re-visit this problem.  I decided not to try to clean Samba from my system.  After uninstalling Samba there are still many Samba files and I do not know which ones I need to keep.

So -- I re-installed it on my 8.10 and installed it for the first time on my 8.04.  I altered the smb.conf file as you (swerdna) advised minonbeer, on both computers.  Now I have this:

The 8.10 computer can "see" the 8.10 computer and see the shared folder, but can't open it.  

If I got to Network in nautilus I get two icons.  One is "Hubris" - name of 8.04 computer.  The other is "Windows Network".  If I select Hubris I get files labelled Duchess, Installs, Print, Public, Share.  If I select Public I get the password prompt but when I give the password it is not recognised.  It just reappears.  I am using the user password for the Hubris computer.  The password and user name is the same for both computers anyway.

If I choose Windows Network I get a network icon labelled "Network-Name".  If I select that I get Hubris again.

I'll do another post to explain what happens on the 8.10 computer.

---

### Post by Janeleaper on 2009-07-19
Actually _exactly_ the same thing happens on the 8.10 computer.  

I've tried selecting Samba from the administration panel.  I get a message "starting Samba" in the bottom panel but then it disappears.

---

### Post by martinbaselier on 2009-07-19
It seems, you now have a working samba configuration, but there's an issue with the rights.  When you check the properties of the folder (right click; properties) in nautilus, check if others have reading rights on it.

I have a directory called shared in my personal home directory for sharing samba files: My user name is tin.
In a terminal it should show something like this: 
```

ls -dal ~/shared
drwxr-xr-- 3 tin tin 4096 2009-04-28 12:27 shared

```

---

### Post by Janeleaper on 2009-07-19
thanks for replying

By "rights" do you mean "permissions"?

When I go to "properties" "permissions there are three types: owner, group and others.  For each I can change folder access, but there is also a file access option and I find I cannot change that.  At the moment it just reads "..."

Folder access is set to "read and write" for others, so it is not that.  Do you know what group should be set to?  I don't know what "group" is.

---

### Post by Janeleaper on 2009-07-19
In terminal I get "command not found" in response to "ls -dal ~/shared"

---

### Post by Janeleaper on 2009-07-19
jane@Hardy:~$ ls -dal ~/shared
ls: cannot access /home/jane/shared: No such file or directory
jane@Hardy:~$

---

### Post by swerdna on 2009-07-19
> **Janeleaper said:**
> I've decided to re-visit this problem.  I decided not to try to clean Samba from my system.  After uninstalling Samba there are still many Samba files and I do not know which ones I need to keep.

So -- I re-installed it on my 8.10 and installed it for the first time on my 8.04.  I altered the smb.conf file as you (swerdna) advised minonbeer, on both computers.  Now I have this:

The 8.10 computer can "see" the 8.10 computer and see the shared folder, but can't open it.  

If I got to Network in nautilus I get two icons.  One is "Hubris" - name of 8.04 computer.  The other is "Windows Network".  If I select Hubris I get files labelled Duchess, Installs, Print, Public, Share.  If I select Public I get the password prompt but when I give the password it is not recognised.  It just reappears.  I am using the user password for the Hubris computer.  The password and user name is the same for both computers anyway.

If I choose Windows Network I get a network icon labelled "Network-Name".  If I select that I get Hubris again.

I'll do another post to explain what happens on the 8.10 computer.
There is an issue with permissions that is easy to fix.

Let's just focus on Hubris to start with. You have shared it either:
(a) using the Nautilus sharing tool
OR
(b) by creating the share in the file smb.conf.

The permission issue depends on which method you used.

If you used method (a) the Nautilus tool, there were three boxes:
[LIST=1]
[*]share the folder
[*]allow others to write to the folder
[*]allow guests (ppl without accounts)
[/LIST]
If you ticked 1 and 2 but not 3, then you must add users to the samba user database, which sounds a lot like your problem.

If you don't want to add users to the Samb user daytabase, you must tick the third box and allow guests (no accounts).

Is method (a) the issue? Or is the issue from method (b) [if you created the share by editing smb.conf]? I need to know which way to advise you.

---

### Post by martinbaselier on 2009-07-20
@JaneLeaper.

You would have to replace shared with the name of your shared folder. As I said above it, I have a folder called shared on my machine. If you don't it will only show the file doesn't exist. 

The samba rights/permissions for the folder seem in order though, you can change for all the files in the folder, that's were the second option is for. I won't show, cause it can be different for each file. You could make some files read only, some invisible and give write access to other. 

Best to follow the steps by swerdna.

---

### Post by Janeleaper on 2009-07-20
Hi Swerdna.  Thanks for replying.  Sorry for the delay in responding.  

By using the Nautilus sharing tool, I assume you mean right clicking on the folder icon and choosing sharing options.  This is what I did.  I don't know how to do method (b).  

The File Manager - Folder Sharing shows all three boxes ticked: that is "share this folder", "allow other people to write in this folder" and "guest access".

---

### Post by Janeleaper on 2009-07-20
My shared file is called "public":

jane@Hardy:~$ ls -dal ~/shared
ls: cannot access /home/jane/shared: No such file or directory
jane@Hardy:~$ ls -dal ~/public
ls: cannot access /home/jane/public: No such file or directory
jane@Hardy:~$

---

### Post by Janeleaper on 2009-07-20
But:
jane@Hardy:~$ ls -dal ~/Public
drwxrwxrwx 2 jane sambashare 4096 2009-07-18 11:53 /home/jane/Public
jane@Hardy:~$

---

### Post by swerdna on 2009-07-20
> **Janeleaper said:**
> I've decided to re-visit this problem.  I decided not to try to clean Samba from my system.  After uninstalling Samba there are still many Samba files and I do not know which ones I need to keep.

So -- I re-installed it on my 8.10 and installed it for the first time on my 8.04.  I altered the smb.conf file as you (swerdna) advised minonbeer, on both computers.  Now I have this:

The 8.10 computer can "see" the 8.10 computer and see the shared folder, but can't open it.  

If I got to Network in nautilus I get two icons.  One is "Hubris" - name of 8.04 computer.  The other is "Windows Network".  If I select Hubris I get files labelled Duchess, Installs, Print, Public, Share.  If I select Public I get the password prompt but when I give the password it is not recognised.  It just reappears.  I am using the user password for the Hubris computer.  The password and user name is the same for both computers anyway.

If I choose Windows Network I get a network icon labelled "Network-Name".  If I select that I get Hubris again.

I'll do another post to explain what happens on the 8.10 computer.
Let's concentrate on going to the 8.04 computer from the 8.10 computer. i.e. we talk about the setup on the 8.04 computer. I've become lost so we should go through the steps from the beginning.

First the samba software, run this terminal command: sudo /etc/init.d/samba status. Here's mine:
```
john@ubuntu904:~$ sudo /etc/init.d/samba status
[sudo] password for john: 
 * nmbd is running
 * smbd is running
john@ubuntu904:~$ 
```
Check that you get two daemons labelled "running".

Second the software, run this command to check the software installed: dpkg -l | egrep "samba|smbclient|nautilus-share"
You could copy/paste that into a terminal. Here's what I get:
```
john@ubuntu904:~$ dpkg -l | egrep "samba|smbclient|nautilus-share"
ii  libsmbclient     2:3.3.2-1ubuntu3     shared library for communication with SMB/CI
ii  nautilus-share   0.7.2-4ubuntu1       Nautilus extension to share folder using Sam
ii  samba            2:3.3.2-1ubuntu3     SMB/CIFS file, print, and login server for U
ii  samba-common     2:3.3.2-1ubuntu3     common files used by both the Samba server a
ii  smbclient        2:3.3.2-1ubuntu3     command-line SMB/CIFS clients for Unix
john@ubuntu904:~$ 
```
So paste here what you get.

Now there's a bit of a question as to which shares are usershares and which are not. You've got the following shared resources: Duchess, Installs, Print, Public, Share
Let's see which shares are usershares, run this command: cat /var/lib/samba/usershares. Here's what I get:
```
john@ubuntu904:~$ ls -l /var/lib/samba/usershares
total 4
-rw-r--r-- 1 john john 83 2009-07-12 15:57 music_share
john@ubuntu904:~$
``` 
That shows one configuration file for the shared directory "music_share". Paste here what you get.

Finally let's look into your samba config file for any shares that might have strayed there, run this command and post back the results, it's just one word with the attached option -s: testparm -s. Here's what I get:
```
john@ubuntu904:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[ubufiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = SWERDNA
	server string = 
	map to guest = Bad User
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	usershare allow guests = Yes
	usershare owner only = No
	cups options = raw
	use client driver = Yes

[ubufiles]
	path = /home/john/Desktop/ubufiles
	force user = john
	read only = No
	guest ok = Yes
john@ubuntu904:~$ 

```That shows my smb.conf file after it's been cleaned up by the testparm program to just show the important stuff.
Paste here what you get.

A final question: you have all these shares: Duchess, Installs, Print, Public, Share. Which ones would you like to keep and which ones would you like to turn off?

We'll proceed to the next step after we see what your situation is so far.

---

### Post by Janeleaper on 2009-07-24
My apologies for not responding.  I've run out of time to deal with this.  The other computer is continuously in use.  Thanks for your help.

---

### Post by neilhnz on 2010-09-21
Hi All,

I quite new to Linux so please forgive me for not being overly technical in my solution.

I was also having issues with the above error "Error 255 cannot convert name "Everyone" to a SID" I tried all the solutions mentioned in this post but none of them worked.

Tonight I went into Samba and went into Preferences then Server Settings. 


I the last entry was set to "No Guest" I changed it to "Guest". 

After changing this I then used Nautilus to share a folder that I have been trying for months to share, but always got the above error. This time however it worked. So for all of you that have had trouble you might want to try this solution. I hope it helps.

Neil...

---

### Post by miguelongo on 2010-10-14
I had the same prolem...

check the usershares folder permissions (1770) , owner (root) and group owner (usershare) making that not the problem.

so, I moved the smb.conf and used the original one (with testparm -s, so deleted the comments) and now I can use the nautilus share.

smb.conf.original.testparm :

```

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
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

```

as soon as I found the problem I coment it

---

### Post by briansz123456 on 2010-12-27
I finally figured this out on my Mint Linux 10 system.  

*Control Center > Samba > Preferences > Server Settings > Security*

Ensure that authentication mode is set to 'User' and that your typical Linux user account is selected as the Guest account.

Ensure that the shared folder entered into your smb.conf file has unrestricted permissions, i.e. *chmod -R a+rwx /home/USERNAME/SHARENAME*

This is probably only good for LAN use as it's not particularly secure, but what the heck, it actually works.  I can now see the Samba shares from the Linux host machine as well as Windows client machines on the local network.

---

