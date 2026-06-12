---
title: "New drive installed but cannot  access share"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by mcoops on 2010-06-23
Hi,
 
I have just built 2 Ubuntu Desktop machines with a 2TB drive in each.
 
The machines are to sit on a Windows network one as media storage the other to as backup for the first.
 
I have shared a folder on each machine and all the shares can be accessed from the other Ubuntu machine and from the windows machines.
 
**The problem**
 
I have installed another 2TB hard drive in each machine and formatted as ext4 file system.
 
I then created a folder on each machines new hard drive and shared as usual. The shared folders can be seen on the network but cannot be accessed by network machines.
 
The error is "Unable to Mount location" "Failed to mount Windows Share"
 
Hope this is clear
 
TIA Mark

---

### Post by mcoops on 2010-06-24
Wow... there certainly are more questions than answers on this forum.
 
Does antone monitor these postings?

---

### Post by sikander3786 on 2010-06-24
Hi.

Are you trying to access shares from a windows machine?

How have you configured your smb.conf file?

Can you post it for a few references?

Regards.

---

### Post by mcoops on 2010-06-24
Hi Thanks for the reply,
 
I can access shared folders on the new ubuntu desktop machines from any linux or windows box. 
 
My problem is that i have installed a new 2tb hdd in the linux box using the same ext4 filesystem and shared some folders on that drive. I can access these folders from the linux box the drive is installed in but although i can see the folders over the network on the linux and windows machines i cannot access them.
 
I get the error "unable to mount location" "Failed to mount windows shares"
 
Hope this is clear
 
Mark

---

### Post by Morbius1 on 2010-06-24
As a follow-on to sikander3786's question, in order to properly answer you question we need to know what method of samba sharing you're using ( there are 2 ), how the shares are set up, and what are the permissions of the target folder. Please post the output of the followin commands:

```
net usershare info 
sudo net usershare info
testparm -s
ls -al /path-to-mountpoint-of-2TB-drive
```

---

### Post by mcoops on 2010-06-25
[FONT=Times New Roman][SIZE=3]Hi, Thanks for the reply[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]This is the output of the commands[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]The Data folder is on the first drive and can be accessed by both Windows and Linux machines, the Mediadata folder is on the new drive and can be seen but not opened on the windows and linux machines[/SIZE][/FONT]
 
 
**[FONT=Times New Roman][SIZE=3]mark@media-server:~$ sudo net usershare info[/SIZE][/FONT]**
 
[FONT=Times New Roman][SIZE=3][sudo] password for mark: [/SIZE][/FONT]
 
 
**[FONT=Times New Roman][SIZE=3]mark@media-server:~$ net usershare info[/SIZE][/FONT]**
 
[FONT=Times New Roman][SIZE=3][data][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]path=/home/mark/Data[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]comment=[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]usershare_acl=Everyone:F,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]guest_ok=y[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3][mediadata][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]path=/media/Data2/mediadata[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]comment=[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]usershare_acl=Everyone:F,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]guest_ok=y[/SIZE][/FONT]
 
 
 
 
**[FONT=Times New Roman][SIZE=3]mark@media-server:~$ testparm -s[/SIZE][/FONT]**
 
[FONT=Times New Roman][SIZE=3]Load smb config files from /etc/samba/smb.conf[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Processing section "[printers]"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Processing section "[print$]"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Loaded services file OK.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Server role: ROLE_STANDALONE[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][global][/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]server string = %h server (Samba, Ubuntu)[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]map to guest = Bad User[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]obey pam restrictions = Yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]pam password change = Yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]passwd program = /usr/bin/passwd %u[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]unix password sync = Yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]syslog = 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]log file = /var/log/samba/log.%m[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]max log size = 1000[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]dns proxy = No[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]usershare allow guests = Yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]panic action = /usr/share/samba/panic-action %d[/FONT][/SIZE]
 
 
 
[FONT=Times New Roman][SIZE=3][printers][/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]comment = All Printers[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]path = /var/spool/samba[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]create mask = 0700[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]printable = Yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]browseable = No[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]browsable = No[/FONT][/SIZE]
 
 
 
[FONT=Times New Roman][SIZE=3][print$][/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]comment = Printer Drivers[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]path = /var/lib/samba/printers[/FONT][/SIZE]
 
**[FONT=Times New Roman][SIZE=3]mark@media-server:~$ ls -al /media/Data2/mediadata[/SIZE][/FONT]**
 
[FONT=Times New Roman][SIZE=3]total 8[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]drwxrwxrwx 2 mark sambashare 4096 2010-06-23 16:26 .[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]drwx------ 4 mark mark 4096 2010-06-23 16:09 ..[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]-rw-r--r-- 1 mark mark 0 2010-06-23 16:26 new disk[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]mark@media-server:~$ [/SIZE][/FONT]

---

### Post by AfrikaDietmar on 2010-06-25
> [FONT=Times New Roman][SIZE=3]drwxrwxrwx 2 mark sambashare  4096 2010-06-23 16:26 .[/SIZE][/FONT]r  which is read which is 4
w which is write which is 2
e which is execute which is 1

drwx|rwx|rwx
Samba Owner (you) drwx is 7, you can read, write and execute
rwx is 7, group can read, write and execute
rwx is 7, others can read, write and execute

> [FONT=Times New Roman][SIZE=3]drwx------ 4 mark mark 4096  2010-06-23 16:09 ..[/SIZE][/FONT]I suppose that this is your /home/mark folder ? Thats you, here drwx is 7, you can read, write and execute, group and others dont have access rights.

> [FONT=Times New Roman][SIZE=3]-rw-r--r-- 1 mark mark 0  2010-06-23 16:26 new disk[/SIZE][/FONT]I suppose that this might be your external drive.
[FONT=Times New Roman][SIZE=3]-rw-|[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]r--[/SIZE][/FONT]|[FONT=Times New Roman][SIZE=3]r--
[FONT=Verdana][SIZE=2]**-rw-** is you, its set on 6, you have read and write access.
**r--** is group, its on 4, there a group only has read access, thats why you can see it in your network
**r--** thats the last part of the group bits, here its set on read bit, which is 4, likewise in your network you can see only the drive.

Try this in your terminal:
[/SIZE][/FONT][/SIZE][/FONT]```
sudo chmod 777 -R /media/'new disk'
```I suppose this would be the path to your USB drive.
[FONT=Times New Roman][SIZE=3][FONT=Verdana][SIZE=2]-R is for recursivley changing all your files and folders as well.
[/SIZE][/FONT][/SIZE][/FONT]
Maybe this helps, i have mentioned quite a few times "suppose" - that is because i'm not totally sure, still learning like you - anyone is welcome to disect what i mentioned.

For me ACL and eiciel don't work in my Ubuntu 10.04 so i set all the permissions with the terminal and i used simple samba sharing and edited all details in the smb.conf. I don't think yours above is complete ? (maybe i'm mistaken)
Did you also input the Work Group name ? (But you can see your USB drive in the network anyway...)

---

### Post by mcoops on 2010-06-25
Hi AfrikaDietmar,
 
Thanks for the reply, It seems to have worked.  I can now access the folder from Windows and Linux boxes.
 
I can now refine this for different users
 
I set the permissions to the new drive using the terminal
 
**sudo chmod 777 -R /media/Disk2/mediadata**
 
as you suggested and it worked.
 
I learned not to use the GUI and to stick with terminal
 
Thanks everyone for your help on this.
 
Cheers, Mark

---

### Post by AfrikaDietmar on 2010-06-25
Hi Mark, 

happy to hear that it worked out.

What really helped me was this doc: 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Its quite handy and you will always from time to time come accross file permission issues, especially across the network. I have this always next to my computer, until one day its branded in my mind :)

You can also assign folders/files to an owner and a group with:
```
sudo chown -R username:groupname /home/foldername/foldername
```Here again the -R is for recursive.

I usually create the users/groups with System > Administration > Users and Groups

Don't forget that if you create users, in order for them to work across the network you also need to set them for samba.

```
sudo smbpasswd -a user1
```
(I don't use the same password i assigned the user in order to login  onto the computer.)

To delete the samba user:
```
sudo userdel user1
```


So in this way, by giving ownership you don't always need to chmod 777 because here you allow everyone access.

I usually give the owner a 7, the group a 7 and others just 5 and if i want to make a folder more restricted, i assign it to an owner or a group where i make owner 7 group 5 and others 5. In a network, before you are logged in, you dont have access rights, so you would be considered as "others" so you would still need to be able to see and execute the command to login, so thats where i understand it as such that others still need to see and execute so its a 5 (read 4 + execute 1).
Well it depends, you need to play around with chmod and test a lot what works best. 
But after a while you'll see that it makes a lot of sense. 

For editing your smb.conf file I found this tutorial very useful:
[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)
[http://ubuntu.swerdna.org/ubusambaserver.html#shares](http://ubuntu.swerdna.org/ubusambaserver.html#shares)

Now that your problem is solved you can mark the forum thread as "solved" on the thread tools pulldown menu.

c u

---

### Post by Morbius1 on 2010-06-25
AfrikaDietmar, mcoops is using Nautilus-shares as you can see by his posts. The links on how to edit smb.conf are for Classic-share and would just mess things up for him.

They are also both guest shares so he doesn't need to create any samba users.

Finally he has one more problem. Every time a remote guest saves a file to his shares it will save with owner:group = nobody:nogroup. That means that "mark" will be able to read the file but not write to it. Perhaps that's what he wants it to do. I don't know.

One way to have solved the original problem and this reoccuring nobody:nogroup problem is to add the following line in the [global] section of smb.conf:

```
force user = mark
```And then restart samba.

---

### Post by mcoops on 2010-06-25
Hi Morbius1, AfrikaDietmar,
 
Would you recommend changing to Samba? I just happen on Nautilus and not sure how. I shared the file using the GUI.
 
Samba seems to to be the most used, how would I change over?

---

### Post by Morbius1 on 2010-06-25
Nautilus-share is samba. It's been part of samba for years. The big difference is that the shares in nautilus-share are not located in smb.conf. They are in /var/lib/samba/usershares.

I don't have a religious affiliation with either method but I would suggest you use one method or the other. The old way of doing samba is Classic-shares and there are may howto's out there but only a handful are correct. Of the two that  were mentioned above this one is a standard:
[http://ubuntu.swerdna.org/ubusambaserver.html#shares](http://ubuntu.swerdna.org/ubusambaserver.html#shares).

[COLOR=Blue]**EDIT:**[/COLOR] If you plan to convert to Classic-shares you might want to "unshare" the nautilus-shares just so the two will never conflict with one another. If you have guest access in nautilus-share and only allow one user to access it in classic-share you could see how Samba would get confused.

---

### Post by Morbius1 on 2010-06-25
You know I just looked at swerdna's HowTo again - it's been a while.

He goes through this part about "os levels" and changing "local master", and using samba to control printing, etc.... 

If you have nautilus-share working as it is you don't need to do any of that. Samba is already set up correctly and working. Just go to his part about share creation.

The biggest difference between the two methods is control of individual shares. Nautilu-shares allows you to have a mix of guest and authenticated shares. Classic-shares also allows you to have a share accessible by only one remote user. When nautilus-share creates an authenticated share it's available to anyone who has a samba password.

---

