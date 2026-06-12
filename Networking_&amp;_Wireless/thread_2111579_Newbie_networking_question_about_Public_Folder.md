---
title: "Newbie networking question about Public Folder"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by Bartender on 2013-02-02
I've got two Ubuntu 12.04 PC's on a home network.  Netgear WNDR3800 router in between them.

I'm a newb at networking.  Followed online instructions to install Samba and configure the Public Folder Share settings.  Although I didn't use [this tutorial]("http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/"), the steps I took are identical to the first part.  

This morning I tried to play an .mp3 that was stored in Computer "B" from Computer "A".  No permission.  I tried moving the song from "B" to "A".  Nope, no permission.  I tried changing the Public Folder permissions (right-click on the Folder, go into the Permissions Tab, change all parameters to "Read & Write", then click the button below) but the changes won't stick.

The second part of the above tutorial describes "Personal File Sharing", with some downloads and a few steps.  Do I need to go thru those steps in order to move files from one PC to another, or to play .mp3's that are stored on one PC from a different PC?  Or are there better ways?

---

### Post by Morbius1 on 2013-02-02
I can't imagine why anyone would share the public folder using 2 different protocols especially since "Personal File Sharing" really doesn't work.
Anywho,
> This morning I tried to play an .mp3 that was stored in Computer "B"  from Computer "A".  No permission.  I tried moving the song from "B" to  "A".  Nope, no permission. *[COLOR=Blue] I tried changing the Public Folder  permissions (right-click on the Folder, go into the Permissions Tab,  change all parameters to "Read & Write", then click the button  below) but the changes won't stick.[/COLOR]*First, nautilus-share which is what you are using to share the folder in Nautilus should have changed permissions automatically.

Second, The fact that you cant change permissions is not a good thing. Any chance this Public folder is a mount point for an NTFS partition?

Post  the output of the following command:
```
ls -dl $HOME/Public
```You might want to post the output of these as well just in case this is a samba issue:
```
testparm -s
net usershare info --long
```

---

### Post by Bartender on 2013-02-02
Well, I admitted right up front I was a newbie at networking.  I'm not quite sure what you mean by two different protocols?  If you have a superior suggestion that isn't too geeky I'd uninstall Samba.

Both of these PC's are ext4.  Well, one of them's a dual-boot, but I'm not messing with the NTFS partition on PC "A".  I just want to be able to share data across my LAN, and I've put off learning how for way too long.

It'd be great to plug a W7 laptop into the LAN every once in a while.  I read that SSH is better than Samba, but that's not an option if there are any Windows PC's in the LAN (?)


```
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ ls -dl $HOME/Public
drwxrwxrwx 2 hammer hammer 4096 Feb  1 15:19 /home/hammer/Public
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ net usershare info --long
[Public]
path=/home/hammer/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ 

```

The outputs from the three commands you gave me.  Any help much appreciated!  I guess I should run the same three on the second PC.

---

### Post by Bartender on 2013-02-02
Here's the output from PC "B"...

```
ding@ding-desktop:~$ ls -dl $HOME/Public
drwxrwxrwx 3 ding ding 4096 Feb  2 06:08 /home/ding/Public
ding@ding-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
ding@ding-desktop:~$ net usershare info --long
[Public]
path=/home/ding/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

ding@ding-desktop:~$ 

```

---

### Post by Morbius1 on 2013-02-02
> Well, I admitted right up front I was a newbie at networking.  I'm not  quite sure what you mean by two different protocols?  If you have a  superior suggestion that isn't too geeky I'd uninstall Samba.My comment wasn't directed at you but the author of the HowTo. Sorry about that. One of the things you will find out is that most HowTo's about samba are wrong.

Your smb.conf looks textbook correct.
Your userhsare definition looks correct.
And your permissions are correct.

In fact the only thing I see that's a problem is this:
>  hammer@**[COLOR=Blue]hammer-HP-Compaq-dc7800-Convertible-Minitower[/COLOR]**[B][COLOR=Blue]
[/COLOR][/B][COLOR=Blue][COLOR=Black]Samba uses the host name for the netbios name it uses on the network but it has to be 15 characters long or less. Didn't do an exact count but yours is way more that 15 characters long. I'm surprised the other machine can see it. THe easiest way to fix this for network purposes is this way:

[1] Edit  smb.conf as root:
[/COLOR][/COLOR]```
gksu gedit /etc/samba/smb.conf
```[COLOR=Blue][COLOR=Black]
[2] Add a line under your workgroup line that looks like this:
[/COLOR][/COLOR]```
netbios name = hammerhp
```[COLOR=Blue][COLOR=Black]
[COLOR=Blue][I]Doesn't have to be that exact name but keep it 15 characters or less in length
[/I][COLOR=Black][3] Restart samba:
[/COLOR][/COLOR][/COLOR][/COLOR]```
sudo service smbd restart
sudo service nmbd restart

```Note: WHen you restart samba the network has a fit so wait a few minutes before you try to access the share.
[COLOR=Blue][COLOR=Black]
[COLOR=Blue]**EDIT**[/COLOR]: If there is still an issue post the output of this diagnostic command:
[/COLOR][/COLOR]```
smbtree
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][B][COLOR=Blue]
[/COLOR][/B]

---

### Post by Bartender on 2013-02-02
Morbius1, I appreciate any help.  I'm very gunshy about guessing once I'm in terminal.  Here's a chunk of language from that Samba config file... is this the right part?

```
#======================= Global Settings =======================

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
;   name resolve order = lmhosts host wins bcast

#### Networking ####
```

And is this what you're suggesting?

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   [COLOR="Blue"]netbios name = hammerhp[/COLOR]

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)



I never would have guessed that the name was too long.  Since we're not actually changing the name of the HP, I don't understand how this would make the LAN work, but willing to give it a shot.    

I dunno, it just seems that building a basic home network oughta be easier!

EDIT: After posting, I went back to Home Folder and tried accessing both PC's.  PC "B", named "ding", went right to PC "A", the one with the long-winded name (hammer etc.).  But when I went to PC "A" and asked it to look at PC "B"'s Public folder, I got an error that said something like "smb/Public can't be read" and askesd what application I wanted to use.  I tried 3 or 4 times, and then it started working again.  I would have grabbed a screenshot of the error message but it went away.  Sorry.

After your post about the long name, I woulda thought that "B" would have troubles with "A", but it was the other way around.  "A" (long name) couldn't see "B".

---

### Post by Morbius1 on 2013-02-02
[1] Create a file as root:
```
gksu gedit /etc/avahi/services/samba.service
```[2] Add this to the file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
    <name replace-wildcards="yes">%h SMB</name> ## Display Name
    <service>
        <type>_smb._tcp</type>
        <port>445</port>
    </service>
</service-group>
```[COLOR=Blue]**Note**: The very first line cannot have any spaces in front of it when you paste it into gedit. So remove any you find there.

[COLOR=Black]That's it. Do that on both machines. See if you can now see the machines when you browse for them.[/COLOR]
[/COLOR]

---

### Post by Bartender on 2013-02-02
OK, Morbius1, I hope *you* know what *I'm* doing :)

The network view from the Home Folder is different now.  Please see attachments.

hammer.jpg is the view from PC "A" (the HP with the long name) looking at PC "B".

ding.jpg is the view from PC "B", looking at PC "A".

Both views have new entries.  From PC "B", I clicked on HAMMER-HP-COMPA, not the other one with the really long name, and it went to PC "A"'s Public Folder no problem.  I'll try several times over the next few days and see if they both behave.

I'm online with PC "A".  I put the GIMP screenshot from PC "B" into its Public folder, then accessed the screenie via PC "A" in order to attach it to this post.  Copy/pasted it to the "A" desktop.  I'm so impressed with myself!

I don't know what kind of wizardry you did, but it appears to be working.  Will definitely be holding on to the code you sent.  If there's a need to add a 3rd Linux PC to the mix, would you say that I should be able to simply repeat what I did so far on my own, then create that file and plug your code into it?

And where did you learn this stuff!!??

---

### Post by Morbius1 on 2013-02-02
I am going to explain a few things only because the "Network" display does get confusing.

** When you create a share the way you did you used samba which uses netbios names.
** You seem to be having issues with netbios name resolution in your network.
** The "samba.service" file actually uses a protocol called mDNS ( In OSX and Windows it's called Bonjour. In Linux it's called Avahi ).

Avahi goes back to using the host name not the netbios name so we really haven’t fixed anything we just used an improved ( my opinion ) way of resolving names.

If everything was working as it should you would see multiple entries for every machine. For example:

ding-desktop = The pure Samba way of doing this via netbious name.
ding-desktop SMB = The avahi way of doing this though a mDNS qualified host name. Any host showing up with an SMB at the end would be from Avahi.

> If I want to add a 3rd  Linux PC to the mix, would you say that I should  be able to simply repeat what I did so far, then create that file and  plug your code into it?Yes.

---

### Post by Bartender on 2013-02-02
Thank you very much for the guidance.  

Do you mess around with Lubuntu at all?  PC "B" is an old Pentium 4.  I've been running the Lubuntu DE instead of Unity.  Logged back into Ubuntu 12.04 the last couple of days while trying to figure out the LAN.

When I log off of Unity and back into Lubuntu, there is no network listing at all in the left-hand column of the Home Folder.  I googled search terms like "lubuntu home folder no network" but didn't see anything that seemed to address the issue.

Would prefer to run Lubuntu on PC "B".  Hopefully I'm just missing something obvious?

---

### Post by Morbius1 on 2013-02-02
I don't use Lubuntu but I do use Xubuntu and it's file manager also has that problem. I fixed it by running ( thunar is XFCE's file manager ):
```
thunar network://
```And then bookmarking it so it shows up in the left side panel. Maybe pcmanfm can do the same thing.

---

### Post by Bartender on 2013-02-02
OK, I think I got it working by following [these directions]("http://ubuntuforums.org/showthread.php?t=1623346")

I had to download some of the packages he listed.  Some were already there.

I went back to PC "A", found its IP address, then typed 

```
smb://192.168.1.2
```

into pcmanfm's "address bar" on PC "B".  It found a print folder, and the Public Folder on "A".  Then I was able to make a bookmark.

Going back to PC "A", I thought I was in trouble again.  ding didn't show up.  For lack of a better idea, I clicked on "Windows Network", then "WorkGroup", and found ding.  The Public folder opened.  Kind of odd that I had to go thru "WorkGroup" but it worked!!

I wonder if the file and text you had me build has any impact on the process when I'm in Lubuntu?

---

