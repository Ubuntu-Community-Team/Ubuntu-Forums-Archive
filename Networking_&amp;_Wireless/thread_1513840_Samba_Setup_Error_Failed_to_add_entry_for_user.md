---
title: "Samba Setup Error: Failed to add entry for user"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by finny388 on 2010-06-20
I am trying to set up my Ubuntu 10.04 netbook to see my WinXP desktop's files and vice a versa.

I followed the steps in this tutorial thread: [HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

I got as far as "Time to add yourself as an samba user." at this point I keep getting the following error:

```
sudo smbpasswd -L -a WinXP_User_Name
New SMB password:
Retype new SMB password:
Failed to add entry for user WinXP_User_Name.

```

My WinXP machine has no password.

My conf file is here:

> [global]
    ; General server settings
; 
    netbios name = WinXP_Computer_Name
    server string =
; 
    workgroup = WinXP_WorkStation_Name
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
; 
    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

; 
[MyFiles]
; 
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
; 
    force user = WinXP_User_Name
; 
    force group = WinXP_User_Name

Can anyone tell me what I am doing wrong?

Thanks

---

### Post by alan34 on 2010-06-20
Here is how I do it. May not be the best or even correct but works for me.

**I have found that the username and password must be exactly the same for your linux user, samba user and XP user or your in trouble. Put the same username and password on your XP box**

TO ADD USER

sudo adduser --shell /bin/false 'name'
(no shell with this)
sudo adduser --shell /bin/bash 'name'
(shell with this)

sudo passwd 'name' 'new password'

sudo smbpasswd -a 'name'

Here is part of my /etc/samba/smb.conf

[alan]
	path = /home/alan
	force group = alan
	read only = No
	create mask = 0770
	force create mode = 0770
	directory mask = 0770
	force directory mode = 0770

To make the files available to other users you have to add them to the group "alan". I just edit /etc/group and add the users to the relevant line as

alan:x:1000:john,tom

Then

sudo service smbd restart

Should be good to go. Please note the bold text!

Here are some other examples

[jill]
	path = /home/jill
	force group = jill
	write list = +jill
	read only = Yes
	create mask = 0770
	directory mask = 0770
	guest ok = Yes

[jack]
	path = /home/jack
	valid users = +jack
	force group = jack
	read only = No
	create mask = 0770
	force create mode = 0770
	directory mask = 0770
	force directory mode = 0770
	

Yes there are many ways of doing it the more ways the easier it is to get wrong. Please note I am no expert so hope this works for you good luck.

---

### Post by finny388 on 2010-06-21
Thanks for the reply Alan but I can't have my user names and passwords all the same.

The instructions seem so simple. I can't understand what is wrong.

---

### Post by finny388 on 2010-06-21
^

---

### Post by alan34 on 2010-06-22
I believe your original error is because you have not added xp_user to your linux machine as a regular user 
eg
sudo adduser --shell /bin/false xp_user

sudo passwd xp_user

sudo smbpasswd -a xp_user      ## same password!!

sudo mkdir /home/samba

sudo mkdir /home/samba/xp_user

sudo chmod -R 777 /home/samba     

sudo chown xp_user.xp_user /home/samba/xp_user


in /etc/samba/smb.conf

[xp_user]
path = /home/samba/xp_user
force group = xp_user
read only = no
create mask = 0777
force create mode = 0777
directory mask = 0777
force directory mode = 0777
guest ok = yes

(Note this is as leaky as sieve so fine tune permissions once you get it to work. The above to 0770.) 


sudo vi /etc/group       $$ or whatever text editor you like

xp_user:x:1001:john,tom,alan     etc,etc


sudo service smbd restart


Go to your windows box and add a user xp_user with the same password and try. You can always create a test user just to try to get it working first then
experiment until you get the configuration you want.

Make a note of the IP address of your linux machine

ifconfig -a

say 192.168.0.10


Then on your windows machine Tools-Map Network Drive

\\192.168.0.10\xp_user

Can't be certain this is correct but should work - only use linux at home, linux/windows at work.

Keep trying you will get there. Make notes and backups before you edit files so you can go back.

Good luck.

---

### Post by Morbius1 on 2010-06-22
You've got three problems:

(1) Creating a samba user is a two step process. For example, if I want to give a remote user "mary" access to a share:

Open Terminal and type
```
sudo useradd -s /bin/true mary
```This will create a "mary" user that has no local logon capability and no home directory.
```
sudo smbpasswd -a mary
```This will add AND enable a "mary" samba account/password.

And they do not have to match mary's WIndows login username and password. Why would mary want to provide the server with her local login user name and password?

(2) Anyway you likely will have another problem and it has nothing to do with Samba:

If you created the folder /media/samba this way:
```
sudo mkdir /media/samba
```It had ownership = root and mode = 755 meaning root can read and write and everyone else could only read. You created a writeable share so this isn't going to work. Yo will need to modify the permisions on the shared folder. One way to do that is like this:
```
sudo chmod 0777 /media/samba
```(3) Ownerhip and permissions of mary's files on your share:
> [MyFiles]
; 
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
; 
    force user = WinXP_User_Name
; 
    force group = WinXP_User_Name                      When WinXP_User_Name saves a file it will be owned by her and you as the share owner will only be able to read the file and not write to it. Perhaps that's what you want it to do so you can keep track of what's the remote users files and what's yours. But if you want to write to those files you will have to change the force user to you ( the share owner ) not the remote user. Then all files will be writeable to both you and the remote user.

---

### Post by finny388 on 2010-06-23
Windows cannot find my share folder in Ubuntu.

These are all the steps I have followed to make things clear:

1 Install Samba:
```
sudo apt-get install samba
```
2 Stop Samba:
```
sudo /etc/init.d/samba stop
```
3 Back up /etc/samba/smb.conf
4 Paste contents of conf supplied in [thread]("http://ubuntuforums.org/showthread.php?t=202605") (as in 1st post in this thread)
5 Make the following edits:
> [global]
    netbios name = WinXP_Computer_Name
    workgroup = WinXP_WorkStation_Name
    wins support = no
[MyFiles]
    path = /media/samba/
    force user = WinXP_User_Name
    force group = WinXP_User_Name
6 Make share directory
7 Set permissions:
```
sudo chmod 0777 /media/samba
```
8 Start Samba:
```
sudo /etc/init.d/samba start
```  failed
found this command in forums; it worked:
```
sudo service smbd start
```
9 Add Samba user to Ubuntu (as per Morbius1)
```
sudo useradd -s /bin/true WinXP_User_Name
```
10 Add Samba user to Samba
```
sudo smbpasswd -L -a WinXP_User_Name
sudo smbpasswd -L -e WinXP_User_Name
```

All good on the Ubuntu side (thank you Morbius1), now on to Windows XP

The instructions say you must have static IPs to use WINS in Windows. Since I don't have that I set WINS to no in the conf and followed the WINS disabled section:

Map Network Drive:
> With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now.

For the IP I used "inet addr" from ifconfig.
I tried both:
```
//192.168.123.123/MyFiles
//192.168.123.123/media/samba
```
But Windows cannot find it: "the network path <path I entered> cannot be found" and this message comes up very quickly.

What am I missing that prevents WinXP from mapping this network drive?

thanks

---

### Post by Morbius1 on 2010-06-23
> [global]
[COLOR=Blue]     netbios name = WinXP_Computer_Name[/COLOR]
[COLOR=Green]     workgroup = WinXP_WorkStation_Name[/COLOR]
    wins support = no
[MyFiles]
    path = /media/samba/
    force user = WinXP_User_Name
    force group = WinXP_User_Name                      To be honest with you, since you're trying to map the linux share by ip address I don't know if that is going to be a problem or not but your "[COLOR=Blue]netbios name[/COLOR]" is not correct. The **netbios name **is the name of the Ubuntu box not the Windows box.  You need to fix that. Windows will short circuit if it sees itself on the network :p

As for the [COLOR=Green]workgroup =[/COLOR] , I assume you set it to [COLOR=Green]WORKGROUP[/COLOR] or whatever the workgroup name is on the Windows box.

> I tried both:
     Code:
     //192.168.123.123/MyFiles
//192.168.123.123/media/samba 
The second one will never work because it's not a share and I don't know if that's a typo but your slashes are going in the wrong direction in windows. It should be:
```
\\192.168.123.123\MyFiles
```If you don't have static ip address your map may not survive a reboot though. Maybe when you fix the **netbios name** you'll be able to browse to the share and use the ubuntu machine name from Windows.

[COLOR=Blue]EDIT: I just read through your original post again. You had that netbios name and workgroup parameter wrong from the beginning. Sorry I missed that [/COLOR]:oops:

---

### Post by finny388 on 2010-06-23
I corrected netbios to my Ubuntu machine name (via hostname in terminal)
Yes, workgroup is the WinXP's workgroup name.
Yes, the slashes were a typo so I'm using ```
\\192.168.123.123\MyFiles
```

I restarted samba with ```
sudo service smbd restart
```after editing the conf.

No change in result though.:(

> If you don't have static ip address your map may not survive a reboot though. Maybe when you fix the netbios name you'll be able to browse to the share and use the ubuntu machine name from Windows.
Reboot of Ubuntu?

It seems to be the same upon reboots. Am I using the wrong IP?

---

### Post by Morbius1 on 2010-06-23
>  		I corrected netbios to my Ubuntu machine name (via hostname in  terminal)
In smb.conf:
Change this:
>  [COLOR=Blue]     netbios name = WinXP_Computer_Name[/COLOR]
To this:
```
netbios name = ubuntubox
```
And restart samba.

The netbios name = parameter in smb.conf will override anything you do with hostname.

---

### Post by finny388 on 2010-06-24
> To this:
```
netbios name = ubuntubox
```

And restart samba.
 

If you meant literally to write 'ubuntubox' for netbios, I did, restarted, and it failed again.

If you mean that netbios name is arbitrary it should have worked anyway.

> The netbios name = parameter in smb.conf will override anything you do with hostname.

not sure what you mean here. I don't do anything with the hostname (computer name).

Sorry Morphius1, I probably don't understand something. :)

---

### Post by Morbius1 on 2010-06-24
> 
"The netbios name = parameter in smb.conf will override anything you  do with hostname. "                                
not sure what you mean here. I don't do anything with the hostname  (computer name).You wrote:
> I corrected netbios to my Ubuntu machine name (via hostname in   terminal)                      

---

### Post by Morbius1 on 2010-06-24
You know you've been at this for 4 days now and lord knows I'm not the smartest person in this forum but it may be time you consider starting over. I've been trying to work with your smb.conf file that in today's standard is just plain broke ( the HowTo you're following is very old ). There are parts and options missing and has features disabled. 

If you're interested here's a procedure to start from scratch:

**(1) Make sure the following file exists: **
/usr/share/samba/smb.conf

**(2) Make another backup of your current smb.conf**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD
```**(3) Start with a fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```**(4) Correct one mistake in the new one:**
Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = trueAnd add one more line to the [COLOR=Blue][global][/COLOR] section:
```
netbios name = ubuntubox
```[COLOR=Blue]*And yes I mean literally.*[/COLOR]

**(5) Restart samba**
```
sudo service smbd restart
```**(6) Use Samba Nautilus-share to create a guest share:**

Open Nautilus
Right click on /home/your_user_name/Documents
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete..", and "Guest access"
Select "Create Share"

It will ask you if you want it to modify permissions - you do.

**(7) Now go to XP's My Network or Network Places ( or whatever it's called on XP ) and see if you can see the documents share.**

There's two parts to samba: one is actual network recognition and connectivity and the other is share creation. A Nautilus-share guest share is very simple and eliminates the share creation issue from this problem. It also modifies permissions on the shared folder eliminating that as a possible source for problems. 

Anyway, it's just a suggestion.

---

### Post by finny388 on 2010-06-24
4 days indeed, but I've never set up a network before, I'm just grateful for the help. it's hard to be heard in this high traffic forum.

I started fresh as you outlined.

One thing I did in addition was specify workgroup as the name of the winxp box's workgroup name.

In Network Places in XP I see the XP workgroup under Microsoft Windows Network but there is nothing in it and I can't map to it (it just doesn't recognize my selection)

Most interesting though is upon reboot of XP, I'm getting this error before logon:
"a duplicate name exists on the network"

Googling, I find this means there are two computer with the same netbios name in a network. But, netbios is UbuntuBox here and... well I don't know what it is in XP but it's not ubuntubox.

the computer names are not the same,  workgroup is, and previously I created that disabled user with identical name as user on WinXP.

so confused. thanks again.

---

### Post by Morbius1 on 2010-06-24
In WinXP, Right click on "My Computer" > Properties > Computer Name.

What is:
Full computer name:
Workgroup:

And what does this mean?
> and previously I created that disabled user with identical name as user  on WinXP.[COLOR=Blue]EDIT: You might as well post the output of the following command again:[/COLOR]
```
 testparm -s
```

---

### Post by finny388 on 2010-06-24
> **Morbius1 said:**
> In WinXP, Right click on "My Computer" > Properties > Computer Name.

What is:
Full computer name:
Workgroup:

This is where I sourced the workgroup and computer name earlier. Full computer name is not even similar to my ubuntu's computer name.

> 
And what does this mean? and previously I created that disabled user with identical name as user on WinXP.

From you: [COLOR="Red"]sudo useradd -s /bin/true mary[/COLOR]    where mary is user name of winxp machine.

> You might as well post the output of the following command again:

testparm -s> 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = UBUNTUBOX
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

---

### Post by Morbius1 on 2010-06-24
> Most interesting though is upon reboot of XP, I'm getting this error  before logon:
"a duplicate name exists on the network"My first rule of thumb is to never accept Windows advice on a Linux forum. You've already violated that advice by following the HowTo you referenced above but in this case I don't know of anyway around the Windows error except to do something in Windows.

The "duplicate name" error happens when another computer on the  network has the same name or when one of the machines has a workgroup name that matches it' s computer name. Since you won't share that information I'm going to assume that it's different now but it may have not always been so. Windows never forgets so it may be associating your ubuntu machines ip address with a a duplicate machine name.

You can clear Windows memory of that by issuing the following commands in **Command Prompt** on WinXP:

```
ipconfig /flushdns
```Since Windows likes to be rebooted a lot you may want to do that as well.

---

### Post by finny388 on 2010-06-24
I ran ipconfig /flushdns, rebooted, still got the message.
Turned off the ubuntu box, rebooted xp, message gone.

If it helps, here are my computer names

XP
Computer Name = ander-wg007
Workgroup = ANDER-WGS
Username = Ander
IP = 192.168.100.102

Ubuntu
hostname = eee900-pc
username = finny
IP = 192.168.100.103

---

### Post by finny388 on 2010-06-25
Not sure at what point this happened but after a reboot or two, I can now see ubuntubox on my XP machine.

I can also see XP from Ubuntu.

Just one last hitch - on the xp machine I have no write permissions. (whereas in Ubuntu I can write to the XP machine)

Yet when I right-click my /home/finny folder (the one I set to share in Nautilus), all 3 check boxes are checked in Sharing Options.

Thanks so much for your help Morbius1, I wonder if we can jump this last hurdle.:p

---

### Post by Morbius1 on 2010-06-25
I don't mean to be difficult but what do you mean by "write".

When you shared /home/finny ( BTW, you really shouldn't be sharing your own home folder, that's why I wanted you to share only the Documents folder ) it would have set permissions to allow write to the remote samba user. But write means that the remote user would be able to add a file or folder to that share. It doesn't mean that the remote user would be able to write to a specific file or folder within that share.

Samba determines what a remote user MAY do.
Linux file permissions determines what a remote user CAN do.

Let's say you have a file within /home/finny called phone.txt. If you do a:
```
ls -l /home/finny/phone.txt
```You would likely get this output:
> -rw-r--r-- 1 finny finny"finny" can read(r) and write(w) to the file but everyone else can only read(r--).

One way around this in Nautilus-share is to add one more line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = finny
```Then restart samba.

This will act as a mask converting the remote guest to you as far as that share is concerned.

**NOTE:** The problem with this is that you're sharing your entire home directory and allowing guest access. That's insane. Even if you restricted it to those with a username and password - that's slightly less insane.

I would highly recommend that you share a folder within your home directory rather than your home directory itself.

---

### Post by finny388 on 2010-06-25
Sharing my home folder is insane for security reasons? (please elaborate a little, I'm sure it's naive, maybe b/c I am the sole user of this network that I don't get it)
 I did it because under finny I have
Documents
Downloads
Pictures
Music
Books
etc

and I wanted access to all of them but on XP I see the sea of hidden files and that is too messy.

I may have to share them one by one, if I put them under a grand subfolder a bunch of links will be broken.

So to be clear:

1. Yes I'd like to be able to write to (edit) files in the share as well as add files.

2. You are saying I must add force user to the conf file to do this.

3. You are saying stop being insane and share subfolders only.

correct?

---

### Post by Morbius1 on 2010-06-25
Let me be upfront, I'm old school. Even the suggestion of sharing one's home directory on a desktop OS makes me twitch. The home folder in Linux is sort of the same thing as "Documents and Settings" in Windows. It's more than just Documents, Pictures, Movies... It's all the "hidden" files which are in fact all the configuration files that makes you , you. Security is one caution, but carelessness is another ( and trust me I've been there ). Delete one of the "hidden" folders by accident and who know what might happen.

Having free access to all that just seems wrong to me. If you're the only user on the network then that's another matter I suppose. I would still be more comfortable with separate shares for Documents, Pictures, Movies,...

And yes you need to use the "force user" to overcome the write problem. There are alternatives but each one brings with it more complexity.

---

### Post by finny388 on 2010-06-25
force user worked like a charm and I'm setting up subfolders as share instead of the finny directory.

Cheers to you Morbius1, thanks for all your help.

I am now happily networked.:p

---

### Post by Morbius1 on 2010-06-25
Mark this as solved , it's under "[COLOR=Red]Thread Tools[/COLOR]" at the top of the page.

We win prizes based on the number of problems we solve  ... Ummm ...Don't we ? :p

---

### Post by finny388 on 2010-06-25
good practice, thanks

looking forward to the prizes...;)

---

