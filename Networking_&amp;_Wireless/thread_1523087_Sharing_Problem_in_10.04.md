---
title: "Sharing Problem in 10.04"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2010-07-03
I did a fresh install of Lucid alongside Vista on my laptop, a Toshiba Satellite A205-S5804. When I went into "Personal File Sharing" under System > Preferences, it said that the necessary packages were not installed. Using the documentation at this link:

[https://help.ubuntu.com/10.04/internet/C/networking-shares.html](https://help.ubuntu.com/10.04/internet/C/networking-shares.html)

I went into a terminal, opened shares-admin, and as promised it told me that I didn't have the right software installed, and allowed me to check both NFS and SMB to install. I did so, installed, and at the end, it said everything was successful. After exiting the dialog, the window asking me to install NFS/SMB appeared again. I selected to install, it dissappeared, and then reappeared. It did this repeatedly, until I decided to close it out. I then went back to the guide, and went to add a new share. But the drop down box would not allow me to choose Windows share, only Unix (NFS). How do I enable Windows Filesharing? Is this a unique problem, or is everyone having this? If so, this was a bad decision for a Long Term Support release. I have used Ubuntu in the past and have gotten it to share with Windows computers flawlessly. Now, it appears that this essential (for me) functionality is broken. Does anyone have any idea what's wrong? Thanks in advance to those who offer any advice.

Anxiously awaiting a reply,

ShinHadoken

---

### Post by ShinHadoken on 2010-07-03
Bump, por favor.

---

### Post by Morbius1 on 2010-07-03
> When I went into "Personal File Sharing" under System > Preferences,  it said that the necessary packages were not installed. Using the  documentation at this link:

[https://help.ubuntu.com/10.04/intern...ng-shares.html]("https://help.ubuntu.com/10.04/internet/C/networking-shares.html")The HowTo link talks about Samba. "Personal File Sharing" has nothing to do with samba. If you want to get "Personal File Sharing" to work you need to install the following packages:
```
Apache2.2.bin
libapache2-mod-dnssd
```It doesn't work very well but your experiences may be different from mine.

[COLOR=Blue]EDIT: I should note that "Personal File Sharing" allows you to share only one directory: /home/user_name/Public[/COLOR]

As for Samba use the Nautilus-share method to share folders:

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

---

### Post by ShinHadoken on 2010-07-03
All I really want to do is share files/folders with Windows PCs. As far as I know, that's accomplished by Samba. Am I in error, or in order to share with Windows must I use the "nautilus-share" method?

---

### Post by ShinHadoken on 2010-07-03
I have done as you said following the nautilus-share method, and I could not see the share from my Windows computer. When I entered Network on my Ubuntu computer, I saw the name of my computer, j****-linux, and Windows Network. Clicking on my machine shows two folders, one is the Documents folder I shared, and the other is print$. Clicking on the documents folder results in an error message, "Unable to mount location. Failed to mount Windows share." Clicking print$ brings up a password dialog, asking for username (mine is given by default), domain (WORKGROUP is given for default), and password (which is blank, awaiting my input) followed by options on how long to remember my password. I put in my account password, which apparently didn't work, because the dialog reappeared asking for my password again. Going back to where it showed my machine and Windows Network, this time I entered Windows Network. I see two folders, one MSHOME and another WORKGROUP, the former which I recognize as the workgroup for all the Windows PCs on my network. I click on it, and get an error: "Unable to mount location. Failed to retrieve share list from server." So, I click on WORKGROUP, and I see just my machine. I go in, and get the same results as before.

---

### Post by ShinHadoken on 2010-07-04
Is anyone else having this issue? Or am I completely missing how to share with Windows in Ubuntu Lucid?

---

### Post by ShinHadoken on 2010-07-04
Very discouraged at the lack of interest in my post...

While apparently out of date, I did follow this guide:

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

I set up an addition share in /srv/test. The results are I can now see the other Windows computers on my network and access them. YAY! They can also see me. However, when I try to access my Ubuntu pc from Windows, it comes up with a username/password prompt. I tried entering in my login details to no avail. Shouldn't the shares be available without any username required? Someone please help, I'm almost there!

Although, I'm still EXTREMELY disappointed that this did not work out of the box. Need to go onto Launchpad and do some complaining. I should be able to configure all this from within a GUI, not have to hand-edit configuration files at the command line.

---

### Post by Morbius1 on 2010-07-04
> All I really want to do is share files/folders with Windows PCs. As far  as I know, that's accomplished by Samba. Am I in error, or in order to  share with Windows must I use the "nautilus-share" methodNautilus-share is Samba. It's just a way of doing it through the Nautilus file manager like the way you can do it in Windows.
> Clicking on my machine shows two folders, one is the Documents folder I shared, and the other is print$. Clicking on the documents folder results in an error message, [COLOR=Blue]"Unable to mount location. Failed to mount Windows share."[/COLOR] That sounds like a permissions problem which is unlikely if you're using nautilus-share on your own home folder....

The best thing to do now is provide the output of the following commands so we can see how you're set up:

```
net usershare info
sudo net usershare info
testparm -s

```One more command that we need to see the output from:
```
ls -dl /home/username/Documents
```[COLOR=Blue]*Changing "username" to whatever your login username is.*[/COLOR]

---

### Post by ShinHadoken on 2010-07-04
> **Morbius1 said:**
> Nautilus-share is Samba. It's just a way of doing it through the Nautilus file manager like the way you can do it in Windows.
That sounds like a permissions problem which is unlikely if you're using nautilus-share on your own home folder....

The best thing to do now is provide the output of the following commands so we can see how you're set up:

```
net usershare info
sudo net usershare info
testparm -s

```One more command that we need to see the output from:
```
ls -dl /home/username/Documents
```[COLOR=Blue]*Changing "username" to whatever your login username is.*[/COLOR]

```

james@james-linux:~$ net usershare info
[documents]
path=/home/james/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/james/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

james@james-linux:~$ sudo net usershare info
[sudo] password for james: 
james@james-linux:~$ sudo net usershare info
james@james-linux:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = MSHOME
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[test]
    comment = Testing SAMBA sharing in Ubuntu
    path = /srv/test
    read only = No
    create mask = 0755
    guest ok = Yes
james@james-linux:~$ ls -dl /home/james/Documents
drwxrwxrwx 2 james james 4096 2010-07-02 20:11 /home/james/Documents
james@james-linux:~$ 

```

---

### Post by Morbius1 on 2010-07-04
I'm going to focus on the Nautilus-shares first:
> [documents]
path=/home/james/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[pictures]
path=/home/james/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y
There is absolutely nothing wrong with these
At first glance there is nothing in your smb.conf that would prohibit this from working - i.e., remote access without password prompt.

The only thing I can think of at first blush is if your entire path doesn't have the execute bit turned on. That would be unusual because it's on by default but let's take a look:

Post the output of :
```
ls -dl /home/james
```

---

### Post by Jonners59 on 2010-07-04
Guys
Not alone.  I have been using Ubuntu for a while now and network sharing, especially with Windows does work but can be temperamental and difficult to get running.

I am very interested in the info below and will be trying it all out. Points I note are:

1. It is temperamental even when you have got it going, works one minute and not the next.
2. Permissions is not easy to change if the drive is owned by root - I have not been able to find a way yet.
3. Installing the share is also not obvious and I get it on some machines but not others.

That all said I do have some answers that may be of help....  I have just left some on a different thread

[http://ubuntuforums.org/showthread.php?t=1523906](http://ubuntuforums.org/showthread.php?t=1523906)

I'll be keeping an eye on this, looks interesting

---

### Post by Morbius1 on 2010-07-04
As for your Classic-share:
> [test]
    comment = Testing SAMBA sharing in Ubuntu
    path = /srv/test
    read only = No
    create mask = 0755
    guest ok = Yes
This may be a permissions problem depending on what you did to /srv/test itself. One way to allow guset access is by changing permissions on the target shared directory:
```
sudo chmod 0777 /srv/test
```[COLOR=Blue]EDIT: I should have explained that better:[/COLOR]

If you did a **sudo mkdir /srv/test** it would have created a directory owned by root with read / write acces to root and read only access to everyone else. Since you specified write access to guest this share will not work as desired. You'll have to either set permissions to 777 which would allow read / write access to everyone including the remote guest or you can change ownership to "nobody" which is what the remote user will be identified as when he tries to access the share. There are many more ways around this permissions problem ...

---

### Post by metalguy639 on 2010-07-04
I too have an issue with mine. I have 4 PC's all are on linux and I have to have them share or else I'm stuck and going back to windows again :( 

```
net usershare info
[@@@@@@]
path=/media/FreeAgent Drive/@@@@@
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[backups]
path=/media/My Book/BACKUPS
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[ftp]
path=/media/My Book/[FTP]
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[@@@@@@]
path=/media/My Book/[@@@@@@@]
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

[graphics]
path=/media/My Book/GRAPHICS
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

```

The above is only showing this particular PC's drives that are shared. I have things shared on the other pc's but its not showing up here. 

2nd Item:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
```

3rd Item:

```
drwxr-xr-x 11 name name 4096 2010-07-04 17:31 /home/name/Documents

```

Also I had uninstalled Samba after installing it and now when I click on the network link I get an error message saying it cannot open it.

---

### Post by Morbius1 on 2010-07-04
metalguy639, Please start your own thread. This one is complicated enough.

Your problem seems simple enough:
(1) Reinstall samba
(2) Add the following line to the [global] section of smb.conf:
```
force user = morbius
```
*[COLOR=Blue]Change morbius to your own login user name[/COLOR]*
(3) restart samba

If you have problems please start your own thread.

---

### Post by ShinHadoken on 2010-07-04
Did as you suggested, and restarted computer to restart Samba (by the way, know an easier way of doing this, without having to do a hard reboot?)

```

james@james-linux:~$ ls -dl /home/james
drwx------ 31 james james 12288 2010-07-04 22:11 /home/james
james@james-linux:~$ sudo chmod 0777 /srv/test
[sudo] password for james:
james@james-linux:~$

```

Results are: still no dice. Windows still asks for a username/password, my login does not work. I still cannot access any of the shares from Ubuntu itself, failing on the same error, with the exception of /srv/test, but I believe that one was working before, and I simply forgot to tell you all so. Whether it was or not, it is now, but like I said, only from within Ubuntu.

I used to be able to read permissions, but I haven't used Ubuntu in quite a while, so I'm not certain whether or not the execute bit is present, but the output is given above. Still doesn't seem to be linked to the Windows prompt issue, because we set the permissions of /srv/test, and it still asks.

---

### Post by Morbius1 on 2010-07-05
> **ShinHadoken said:**
> Did as you suggested, and restarted computer to restart Samba (by the way, know an easier way of doing this, without having to do a hard reboot?)
  Finally an easy question :wink:. To restart Samba:
```
sudo service smbd restart
```Here is the problem with your Nautilus-shares:
> james@james-linux:~$ ls -dl /home/james
drwx------ 31 james james 12288 2010-07-04 22:11 /home/jamesOnly one person has any kind of access to your home directory and that's "james". You can tell samba to allow guest access and it will try to comply but the linux file permissions itself will not allow it.

From a Terminal
```
sudo chmod 0755 /home/james
```This should reset those permissions to the default. 


Actually you might want to go one level up and make sure that /home itself has the correct permissions. An "ls -dl /home" should look like this:
> [COLOR=Blue]drwxr-xr-x[/COLOR] 5 root root 4096 2010-06-25 14:23 /homeIf it's not that then make it that:
```
sudo chmod 0755 /home
```I can't imagine how permissions on those two directories could have changed from the default.

---

### Post by normh on 2010-07-05
Yes, I am having exactly the same problem.  Look forward to some advice.  I don't know how to uninstall or rollback what I have done so I can start again

---

### Post by Jonners59 on 2010-07-05
I sometimes find it easiest to go in to Synaptic Package Manager, find the app, do a complete un-install of it (Mark for Complete Removal), reboot and then reinstall it again.  Clears out all the old dead wood and you may find it works under default settings.

---

### Post by ShinHadoken on 2010-07-05
> **Morbius1 said:**
> Finally an easy question :wink:. To restart Samba:
```
sudo service smbd restart
```Here is the problem with your Nautilus-shares:
Only one person has any kind of access to your home directory and that's "james". You can tell samba to allow guest access and it will try to comply but the linux file permissions itself will not allow it.

From a Terminal
```
sudo chmod 0755 /home/james
```This should reset those permissions to the default. 


Actually you might want to go one level up and make sure that /home itself has the correct permissions. An "ls -dl /home" should look like this:
If it's not that then make it that:
```
sudo chmod 0755 /home
```I can't imagine how permissions on those two directories could have changed from the default.
Well, good news--I can access Documents and Pictures now!!! Bad news: Windows STILL comes up with a username/password prompt.

I noticed my print$ share also asks for username and password, could these somehow be linked? If I somehow enabled print$ to be accessed by anyone, would this solve the Windows issue?

I also have a theory regarding the permissions of the /home/james/* shares. I have an encrypted home folder. It is decrypted and mounted when I enter my login password. Is it possible that it is mounted to give only me permission to access it?

SOOOO CLOSE!! Please help me get there guys! And thanks for all the help, especially Morbius. The Ubuntu community never lets me down.

---

### Post by Morbius1 on 2010-07-06
> I also have a theory regarding the permissions of the /home/james/*  shares. I have an encrypted home folder. It is decrypted and mounted  when I enter my login password. Is it possible that it is mounted to  give only me permission to access it?An encrypted home folder? Yes that will definitely cause a problem. Any reason why you left that out in your original description of the problem? :mad:. Just kidding.

To be honest I've never attempted to remotely access an encrypted share so I don't know if this will work:

Open a terminal and type:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [COLOR=Blue][global][/COLOR] section:
```
force user = james
```Save the file, exit gedit, and back in the terminal type:
```
sudo service smbd restart
```I'm guessing the decryption of your home folder happens early in your login process so that by the time anyone tries to access your shares it's already accessible to you. The "force user" will convert all remote users to "james" as far as those shares are concerned.

Another alternative is to create a completely different ( non-encrypted ) directory structure for the things you want to share. For example:

Create a separate home folder called "Shared":
```
sudo mkdir /home/Shared
```Take possession of the directory so you can use Nautilus-share:
```
sudo chown james:james /home/Shared
```Use Nautilus to share the folder so that a **net usershare info** yields this share definition:
```
[shared]
path=/home/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Jonners59 on 2010-07-06
Morbius1
Thanks for this.  After my advise, I then suddenly found my networking days were suddenly over!  Panic then set in.  I could not get anything on smbtree either.  I then went step by step through the bits below, but your last thread made it reliable and fast - I do not use encrypted directories.

So many thanks.  I need to test it over the next few days to see if it really worked or is just a moment thing.

Interesting though....  smbtree still does not show other network users, though I can connect via "network" and "connect to server" in "places"
> jonathan@jonathan-laptop:~$ smbtree
Enter jonathan's password: 
WORKGROUP
JONATHANECHIARA
    \\SERVER                 server
cli_start_connection: failed to connect to SERVER<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\LOCALHOST              Vigor 2820 Samba Server
        \\LOCALHOST\music              
        \\LOCALHOST\dcim               
        \\LOCALHOST\share              
        \\LOCALHOST\documents          
        \\LOCALHOST\videos             
        \\LOCALHOST\desktop            
        \\LOCALHOST\pictures           
        \\LOCALHOST\IPC$               IPC Service (jonathan-laptop server (Samba, Ubuntu))
        \\LOCALHOST\print$             Printer Drivers
    \\JONATHAN-LAPTOP        jonathan-laptop server (Samba, Ubuntu)
        \\JONATHAN-LAPTOP\music              
        \\JONATHAN-LAPTOP\dcim               
        \\JONATHAN-LAPTOP\share              
        \\JONATHAN-LAPTOP\documents          
        \\JONATHAN-LAPTOP\videos             
        \\JONATHAN-LAPTOP\desktop            
        \\JONATHAN-LAPTOP\pictures           
        \\JONATHAN-LAPTOP\IPC$               IPC Service (jonathan-laptop server (Samba, Ubuntu))
        \\JONATHAN-LAPTOP\print$             Printer Drivers
    \\CHIARAPC               Chiara'sPC
cli_start_connection: failed to connect to CHIARAPC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

---

### Post by ShinHadoken on 2010-07-07
Thanks Morbius, figured it out!

In smb.conf, in order for guest access to work correctly, you have to have "security = share" instead of "security = user", which is the default in the configuration file. Now that that's done, my Windows computer sees me, and I see my Windows computers. They have access to each other's shares, and I have access to the printer in my room on Ubuntu now. Thank you so much for the help, and from what I can judge from the other posts, I'm not the only one with gratitude!

---

### Post by Jonners59 on 2010-07-07
Morbius1

Could you please take a look at a Thread I opened the other day.  No one has suggested anything and it may be up your street.  It's a major problem as it is the PC I run everything off of for the family.  I am currently still using Vista until I get the system fully functional on Ubuntu

[http://ubuntuforums.org/showthread.php?t=1523933](http://ubuntuforums.org/showthread.php?t=1523933)

---

### Post by Morbius1 on 2010-07-07
> **ShinHadoken said:**
> In smb.conf, in order for guest access to work correctly, you have to have "security = share" instead of "security = user", which is the default in the configuration file. Now that that's done, my Windows computer sees me, and I see my Windows computers.
  Unfortunately the fact that you are forced to use "security = share" is a bug ( one of many ) : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

"security = share" has been deprecated. From O'Reilly's Samba Book:
> What About the Other Two Security Modes?

    The remaining two security modes, security= share and security=server , are historical artifacts from past releases. Both of these implementations are remnants of authentication models primarily used by Windows 9x and earlier hosts. Neither security mode offers functionality beyond that provided by the three recommended security values covered in this chapter. Furthermore, in many instances, **[COLOR=Blue]the deprecated modes[/COLOR]** suffer from severe protocol limitations. For this and other reasons, there is a high chance that both will be removed from Samba at some future time. It is strongly suggested that you avoid these two values when building new servers.On the other hand I'm a firm believer in "whatever works" :wink: 

I do admire your persistence - 4 days at this.[INDENT][LEFT]
[/LEFT]
[/INDENT]

---

### Post by capscrew on 2010-07-07
> **Morbius1 said:**
> Unfortunately the fact that you are forced to use "security = share" is a bug ( one of many ) : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

This is not a bug.  It may be a bitch of some, but it's just how Samba works.  Samba is not exactly the same as *"Windows Sharing" *.  It is is a separate (and sometimes differing) implementation of the SMB/CIFS protocol. > 

"security = share" has been deprecated. From O'Reilly's Samba Book:[QUOTE]The remaining two security modes, security= share and security=server , are historical artifacts from past releases. Both of these implementations are remnants of authentication models primarily used by Windows 9x and earlier hosts.

[/QUOTE]This is a rather unfortunate quote.  To begin with the book is discussing this issue from the perspective of Samba v2, not v3 and later.  The book itself is out of date.  Hindsight is always better than foresight and current perspective we can see now that this statement not fully correct.  

I believe that when read in context the statement can be seen as being directed to those who were/are running Samba servers on domain type networks, not to those using ad hoc or simple local network LAN sharing.  The individual not running a domain style network still has to use share or user type security.

Samba has had it's twists and turns but to this day the default setting is still *SECURITY = USER*.  Read the section titled "NOTE ABOUT USERNAME/PASSWORD VALIDATION" and the SECURITY section of the current documentation [**_here _**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for greater detail

---

### Post by Morbius1 on 2010-07-07
I've always found the term "deprecation" to be rather odd. The dictionary meaning of the word: 
> 1.to express earnest disapproval of.
2.to urge reasons against; protest against (a scheme, purpose, etc.).
3.to depreciate; belittle. Then why is it an option. What's worse, as late as 3 months or so ago it's still being tweaked even though it appears they'd really like to remove it ( [http://lists.samba.org/archive/samba/2010-March/154737.html](http://lists.samba.org/archive/samba/2010-March/154737.html) ):
> On Mon, Mar 29, 2010 at 09:45:06PM +0200, Cassian Braconnier wrote:
>[I] Hi,
[/I]>[I] in "Using Samba" by G. Carter, J  Ts and R. Eckstein, 3rd edition, on  
[/I]>[I] chapter 5, page 113, I ses that the security = share option is  
[/I]>[I] "deprecated". It is said that "there is a high chance that ... will be  
[/I]>[I] removed from Samba at some future time".
[/I]>>[I] I find that security = share is extremely useful for many small non  
[/I]>[I] critical networks.
[/I]>[I] Is it still the case that this option is considered "deprecated" ? and  
[/I]>[I] if so what is supposed to replace it and to give the same functionality ?
[/I]
[COLOR=Blue]Well you can replace security = share with the correct "map to guest"
options, so it really isn't useful in the way you think. Having said
that we haven't (yet) removed it, and I just refactored the code
that implements it, so it'll probably be around causing us trouble
for a while yet [/COLOR]:-).

Jeremy.
Maybe it will take Samba4. Either way, all of what this user wanted to do should have been achievable with security = user.

---

### Post by capscrew on 2010-07-07
> **Morbius1 said:**
> I've always found the term "deprecation" to be rather odd. 
 
Then why is it an option. 
Why is what still an option?  There is a lot of code that if could be rewritten would be very different.  It is what it is.
> 

What's worse, as late as 3 months or so ago it's still being tweaked even though it appears they'd really like to remove it ( [http://lists.samba.org/archive/samba/2010-March/154737.html](http://lists.samba.org/archive/samba/2010-March/154737.html) ):

[QI have found that anybody can have an ***opinion*** and create an issue where there is none.  Nothing is immutable when it comes to computing, certainly not programing code. Everything can be restated (and usually is). 

As I understand it there is a difference between ***user ***and ***share ***security.  User security means you have to be authenticated where share relies on the underlaying FS permissions.   They may end up the same functionally for *"guests"*, but they are fundamentally different notions.
> 
Maybe it will take Samba4. Either way, all of what this user wanted to do should have been achievable with security = user.
I feel that there is a larger view of this.  I feel that as we are posting on a ***public forum***, we should be accurate for the readers that may follow later on (sometimes much later on).  While the this user should be answered directly, there should be some acknowledgement of future searchers who find this thread.

This is another reason that one should have individual threads for users questions.  This is not to say that ***side issues*** can't be addressed at all.  I wonder though, what positive purpose is served with a thread having the length and variety of the questions addressed here.

---

### Post by Morbius1 on 2010-07-07
ShinHadoken, My apologies for hijacking this thread. It appears you have resolved the issue to your satisfaction so I hope you don't mind if I indulge myself. 

capscrew, In the interest of accuracy since this is a public forum I take issue with your description of user level security:
> User security means you have to be authenticated where share relies on the underlaying FS permissions. They may end up the same functionally for "guests", but they are fundamentally different notions. To a new user that first line implies that one must explicitly create a samba user to gain access when using user level security. That is not true. I agree that an authentication is taking place but it's not explicit or obvious to the user. And both methods rely on the underlying FS permissions being in sync with the share authorization. You can't create a guest share and set permissions = 770 - it won't work.

In this particular case we have everything in place for guest access to work using user level security ( except for his encryption of his home directory ):

From his earlier posts he has the following option in his smb.conf:
> map to guest = Bad UserSince he hasn't explicitly stated otherwise the guest account has been specified for him in the default:
> guest account = nobodyWhen the remote guest user attempts to gain access he will be converted to the guest account: nobody. His share allows guest access so he should be allowed in assuming the Linux permissions are set to allow it. Had he deleted the "nobody" account on the server or if he had created a samba user with the same name as a windows client login name but a different password then it might mess things up. There should have been no reason to resort to share level security.

Now ShinHadoken has been working on this for 4 days and you have to admire his tenacity. Assuming he comes back to read any of my follow up rants at all, I'm betting he's in no mood to change what is currently working for him. :wink:

---

### Post by capscrew on 2010-07-07
> **Morbius1 said:**
> ShinHadoken, My apologies for hijacking this thread. It appears you have resolved the issue to your satisfaction so I hope you don't mind if I indulge myself. 

capscrew, In the interest of accuracy since this is a public forum I take issue with your description of user level security:
To a new user that first line implies that one must explicitly create a samba user to gain access when using user level security. 
Why should I have to look at the system as a new user does?  The documentation clearly states: *"When clients connect to a share level security server, they need not log onto the server with a valid username and password before attempting to connect to a shared resource (although modern clients such as Windows 95/98 and Windows NT will send a logon request with a username but no password when talking to a security = share server)."*  In other words: ***no authentication***.> 

That is not true. I agree that an authentication is taking place but it's not explicit or obvious to the user. And both methods rely on the underlying FS permissions being in sync with the share authorization. You can't create a guest share and set permissions = 770 - it won't work.

As I said the control is in the hands of the system administrator.  With security =share **the only control **is the FS permissions.> 

In this particular case we have everything in place for guest access to work using user level security ( except for his encryption of his home directory ):

I assume you mean the OP.> 

From his earlier posts he has the following option in his smb.conf:
Since he hasn't explicitly stated otherwise the guest account has been specified for him in the default:
When the remote guest user attempts to gain access he will be converted to the guest account: nobody. His share allows guest access so he should be allowed in assuming the Linux permissions are set to allow it. Had he deleted the "nobody" account on the server or if he had created a samba user with the same name as a windows client login name but a different password then it might mess things up. There should have been no reason to resort to share level security.

Now ShinHadoken has been working on this for 4 days and you have to admire his tenacity. Assuming he comes back to read any of my follow up rants at all, I'm betting he's in no mood to change what is currently working for him. :wink:

Nor was I suggesting that he should.

---

### Post by Acce-ss on 2010-08-18
I have managed to make shares with nautilus-share, but the thing OP mentioned in the first post is still bothering me. Many tutorials showed that you do shares with shares-admin. I cannot select the SMB share when adding a share there. 
Why wasn't shares-admin removed, if nautilus-share is supposed to take its job?

---

### Post by capscrew on 2010-08-18
> **Acce-ss said:**
> I have managed to make shares with nautilus-share, but the thing OP mentioned in the first post is still bothering me. 
Are you referring to the "personal sharing"?  That has nothing to do with Nautilus sharing in Samba.  @Morbius1 has discussed this in other threads.> 

Many tutorials showed that you do shares with shares-admin. I cannot select the SMB share when adding a share there.

That is an old tool for editing the /etc/samba/smb.conf file.  >  
Why wasn't shares-admin removed, if nautilus-share is supposed to take its job?  Perhaps the supporting libs have changed.
Two things -- (1) I believe it was removed in 8.04 (Hardy).   (2) The tool ***nautilus-share ***does not take the place of  ***shares-admin***.  The shares created by Nautilus are *usershares *and are stored at /var/lib/samba/usershares.  The Samba-Admin used to be a GUI editor for the smb.conf file.

I use VIM to edit the file, but you can use gedit if you have a desktop running.

---

