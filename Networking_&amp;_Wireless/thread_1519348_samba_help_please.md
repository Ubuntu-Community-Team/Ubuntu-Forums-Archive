---
title: "samba help please"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by Eina1 on 2010-06-28
I've been battling for more than a week to get my network running. Here is what I've got.
Desktop with ubuntu 10.04
Laptop with win xp
desktop with ubuntu 8.04

I want the 10.04 desktop to be server for print and internet, with at least 1 file on each to be shared with al the other mashines.

I've read a lot but just get more confused.
If I put "http://localhost:901/viewconfig" in my browser I do get what I believe is swat but nothing is changeble there. 
SYSTEM - administation - samba, I get some server,klient and sharing of folders.

Should I try and uninstall and start over.
I am new to linux.

Thanks

---

### Post by tracyandskye on 2010-06-28
Drove me crazy when I first started.  Much searching led me to this method:

For a fully functional workstation that shares and receives resources on a small business workgroup or a home LAN, you need packages smbclient, libsmbclient, samba-common, nautilus-share and samba. All except package samba are installed by default.
Check Synaptic for these packages or:

You can install any missing packages via System --> Administration --> Synaptic Package Manager.
[In Kubuntu GoTo: System Settings --> General --> Add and Remove Software].

Setup Samba with this in the smb.conf file on the server:

```
sudo gedit /etc/samba/smb.conf
```

I replace everything in my **_servers_** Samba file with the following:

```
[global]
workgroup = "The name of your network - no quotes"
netbios name = "Your computer name"
name resolve order = bcast host lmhosts wins

map to guest = Bad User
local master = yes
preferred master = yes
os level = 65
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

wins support = no
```

and this in the smb.conf file on Ubuntu **_workstations_**:

```
[global] 
workgroup = "The name of your network" 
netbios name = "Your computer name" 
name resolve order = bcast host lmhosts wins 
server string = 
map to guest = Bad User 
local master = yes 
os level = 33 
usershare allow guests = Yes 
usershare max shares = 100 
usershare owner only = False 
```

If workstation is **_print server_**, include:

```
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
guest ok = no

```


Enter this in the terminal:

```
chmod -R 0777 "/path_to/share"
``` 

Note the space between the 7 & your path.

```
chown -R username:username "/path_to/share"
``` 

Folders will now be available to Windows & Linux machines, with nothing read only, though if files are created & saved on a workstation, then moved to the server (instead of being saved directly to the server), that chmod command will need to be entered again.

Then add samba shares through System>Administration>Shared Folders (or >Samba)

Restart Samba:  

```
sudo /etc/init.d/samba restart
```

---

### Post by Eina1 on 2010-06-28
thank you for the reply, it looked like everything worked great until the restart.

jaco@jaco-desktop:~$ chown -R jaco:jaco Documents/shared
jaco@jaco-desktop:~$ sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found
jaco@jaco-desktop:~$ 

there seems to be no samba files in the init.d directory.

this is also some of the line I see when I save the getit file

error: line 53471: bad flag vector alias
error: line 53473: bad flag alias index: 0
error: line 53473: bad flag vector alias
error: line 53474: bad flag alias index: 0
error: line 53474: bad flag vector alias
error: line 53475: bad flag alias index: 0
error: line 53475: bad flag vector alias
error: line 53476: bad flag alias index: 0
error: line 53476: bad flag vector alias

---

### Post by Morbius1 on 2010-06-28
Excuse the interruption,

For your 8.04 machine this should still work:
```
sudo /etc/init.d/samba restart
```For 10.04 it will not work becasue the "samba" service no longer exists and it's replacement ( nmbd and smbd ) is no longer in init.d. So to restart samba in 10.04 the command is:
```
sudo service smbd restart
```

---

### Post by pricetech on 2010-06-28
Actually Samba can be configured entirely through the GUI configuration tool now, (System - Administration - Samba) and you don't have to restart Samba after making changes there.

---

### Post by capscrew on 2010-06-28
> **Morbius1 said:**
> Excuse the interruption,

For your 8.04 machine this should still work:
```
sudo /etc/init.d/samba restart
```For 10.04 it will not work becasue the "samba" service no longer exists and it's replacement ( nmbd and smbd ) is no longer in init.d. So to restart samba in 10.04 the command is:
```
sudo service smbd restart
```

The daemons [FONT="Courier New"]**smbd **[/FONT]and [FONT="Courier New"]**nmbd **[/FONT]have always existed.  The daemon [FONT="Courier New"]**smbd **[/FONT]is the main part of Samba.  Name resolution for Samba is provided by [FONT="Courier New"]**nmbd **[/FONT].

What has changed is how these are called upon startup and from the command line now that Upstart is used in 10.04 (Lucid) instead of SysV init.

---

### Post by capscrew on 2010-06-28
> **pricetech said:**
> Actually Samba can be configured entirely through the GUI configuration tool now, (System - Administration - Samba) and you don't have to restart Samba after making changes there.

You don't even need to use any external tool.  Nautilus will configure shares via "usershares".

---

### Post by Eina1 on 2010-06-28
jaco@jaco-desktop:~$ sudo service smbd restart
[sudo] password for jaco: 
smbd start/running, process 3131
jaco@jaco-desktop:~$ 

looks like I've got something running:p.  I also changed the workgroup in system - admin-samba  and could see the change in swat - config, the swat config is not the same as the one I've created earlier:confused:.

So how do I get to see my files on the xp machine? I can not see the ubuntu machine from the xp either.

No luck with the ubuntu8.04 machine yeat, I've got no internet on the ubuntu 8.04 machine either so getting upgrades act is a problem, I was hoping of sharing the internet with the ubuntu 10.04.

Thank you all fer all the replies and help.

---

### Post by Morbius1 on 2010-06-28
swat is the most destructive samba utility known to man in my personal opinion. Swat doesn't edit an smb.conf it replaces it. At this point you are beyond the point of no return ( actually you can reset yourself back to the beginning).

If you wan't you can post the output of the following command so we can see how your samba server is set up:
```
testparm -s
```And just in case you're also using usershares ( aka Nautilus-share ) you might want to post the output of this one:
```
net usershare info
```

---

### Post by Charlietje on 2010-06-28
This is how I set up a samba server:


**Installing**

```
apt-get install samba samba-common smbfs smbclient

```


**Configuration**

File: /etc/samba/smb.conf
```
[global] 
  workgroup = WORKGROUP 
  server string = %h server (Samba, Ubuntu) 
  dns proxy = no 
  log file = /var/log/samba/log.%m 
  max log size = 1000 
  syslog = 0 
  panic action = /usr/share/samba/panic-action %d 
  security = user 
  encrypt passwords = true 
  passdb backend = tdbsam 
  obey pam restrictions = yes 
  unix password sync = yes 
  passwd program = /usr/bin/passwd %u 
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdate\ssuccessfully* . 
  pam password change = yes 
  map to guest = bad user 
  usershare allow guests = yes

[homes] 
  comment = Home Directories 
  browseable = yes 
  writable = yes 
[data] 
  comment = Data Share 
  path = /data/ 
  browsable = yes 
  valid users = carl 
  read users = carl 
  write users = carl writable = yes 
  writable = yes 

```

**DON'T FORGET**
in terminal:
```
smbpasswd -a carl
```


**Mount share**
```
smbmount //192.168.1.2/homes /home/carl/Desktop/share -o username=carl
```

---

### Post by Morbius1 on 2010-06-28
> **Eina1 said:**
> I've been battling for more than a week to get my network running. Here is what I've got.
Desktop with ubuntu 10.04
Laptop with win xp
desktop with ubuntu 8.04

I want the 10.04 desktop to be server for print and internet, with at least 1 file on each to be shared with al the other mashines.
You have very simple requirements. Did you ever try the obvious and use Nautilus-share ( aka usershares, that CAPSCREW mentioned )?

Here's the full HowTo on using Nautilus-share to create a Samba share:

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

This will create a public share that allows guest access. I would start with that just to see if you have other networking problems in your network. If you want to have a share that requires a username and password then Nautilus-share can do that to.

Did you try this method and it didn't work? Are you not using Gnome?

**[COLOR=Blue]EDIT: [/COLOR]**Since we don't know the condition of your smb.conf at the moment, if you want to use nautilus-share it requires that you have , at a minimum, two lines in the global section of smb.conf to pull this off:
  ```
usershare allow guests = yes
map to guest = bad user
```

---

### Post by Eina1 on 2010-06-28
jaco@jaco-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[shared-1]"
NOTE: Service shared-1 is flagged unavailable.
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = TUIS
    netbios name = JACO
    null passwords = Yes
    guest account = jaco
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    usershare owner only = No
    guest ok = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    read only = No
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = Yes
    browseable = No
    browsable = No

[shared-1]
    path = /home/jaco/Documents/shared
    read only = No
    guest ok = No
    browseable = No
    browsable = No
    available = No
jaco@jaco-desktop:~$

---

### Post by Eina1 on 2010-06-28
jaco@jaco-desktop:~$ net usershare info
[samba]
path=/home/samba
comment=
usershare_acl=Everyone:F,
guest_ok=n

[shared]
path=/home/jaco/Documents/shared
comment=
usershare_acl=Everyone:F,
guest_ok=n

[downloads]
path=/home/jaco/Downloads
comment=
usershare_acl=Everyone:R,
guest_ok=n

jaco@jaco-desktop:~$

---

### Post by Eina1 on 2010-06-28
I did as [Morbius1]("http://ubuntuforums.org/member.php?u=982144") suggested - did not at first know there is a easy way, it help to get the file shared but how do I acsess it from xp.

---

### Post by Morbius1 on 2010-06-29
**First,** your smb.conf seems to have a little bit of this and a little bit of that. Let's see if we can maneuver around it.

**Second, **do yourself a favor and use whatever tool or utility you used to create this share and remove it:
> [shared-1]
    path = /home/jaco/Documents/shared
    read only = No
    guest ok = No
    browseable = No
    browsable = No
    available = No[B]
Third:[/B] All of your shares require a username and password to gain access. Is that what you want? Or was it because the option to create a guest share was grayed out? 

If it's because it was grayed out it's because you're missing a line in that smb.conf of yours:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:[COLOR=Black]
[/COLOR]```
[COLOR=Black] usershare allow guests = yes[/COLOR]
```[COLOR=Black]



[/COLOR]

---

### Post by Eina1 on 2010-06-30
Places - network-tuis(my work group) - jaco-some shared folders.  This I get so this macgine is now workinh on the network. 
On the xp laptop, view workgroup computers I also get tuis(my work group) and in it small (laptop's name) and in it the laptops shared folders.

Both machines networking activate on start up and both connection's lights on the switch sometime flashes.
But I still can not see one another.

---

### Post by Morbius1 on 2010-06-30
I did not understand your last post.

---

### Post by Eina1 on 2010-06-30
Both machines connect to the network automatically at start up, and everyone shows itself and its shared folders on the network, but not the files of the other machine.

---

### Post by Morbius1 on 2010-06-30
So, for example, you can see "jaco-desktop"  then "downloads" but there are no files within "downloads" ? Or you get an error when you try to open "downloads" ?

---

### Post by Eina1 on 2010-06-30
On the ubuntu machine:  If I go to Places - network- I get a "folder that says " windows network" if I click on it it shows a network folder named "tuis"(my workgruop name) if I then click on it it shows a pc-like logo with the ubuntu machine's netbios name "jaco", if I then click on it it shows all the shared files for the ubuntu machine. It shows nothing from the xp laptop.

On the xp laptop: start - my network places ( shows the shared files on xp) then view workgroup computers, it shows the "tuis" (which is the work group name) and a pc loge named "small" (the laptops name), but again nothing from the ubuntu machine.

Every machine are just showing its own shared folders, both does have the workgroup name "tuis"

---

### Post by Morbius1 on 2010-06-30
From each of the linux machines post the output of the following command:
```
smbtree
```From the XP machine post the output of the following command from [COLOR=Blue]Command Prompt[/COLOR]:

```
net view
```Then:
```
net view \\name-of-each-machine
```

---

### Post by Eina1 on 2010-06-30
jaco@jaco-desktop:~$ smbtree
Enter jaco's password: 
TUIS
    \\JACO                   Samba 3.4.7
        \\JACO\samba              
        \\JACO\shared             
        \\JACO\downloads          
        \\JACO\IPC$               IPC Service (Samba 3.4.7)
        \\JACO\print$             
jaco@jaco-desktop:~$ 

I'll try and duplicate the xp's output.

net view
server name                                                Remark
---------------------------------------------------------------
\\SMALL                                                       small
The command completed successfully.



net view \\name-of-each-machine
for small
shows the printers and shared folders on xp (called small)
The command completed successfully.

for jaco (ubuntu machine)

System error 53 has occured

The network path was not found.


Could it be that the network settings on my xp are incorrect?

---

### Post by Morbius1 on 2010-06-30
On the XP side: The very first thing I would try is to disable whatever firewall you have on the XP machine and try it again.

On the Linux side: If you haven't done anything to the Linux firewalls you should be OK. But if you have added your own firewall rules to linux you need to disable these and try again.

---

### Post by Eina1 on 2010-06-30
I've never come across any firewall stuff on the ubuntu machine. I switched off firewalls in both windows and antivirus with no results.

I have not done much on the ubuntu machine - except trying - a few times to get samba working.  Would it not be a idee to reinstall ubuntu from fresh?

I'm just thinking that all the hassles of getting samba working that I my have messed something up?

---

### Post by Morbius1 on 2010-06-30
The only thing you've touched so far is samba so a complete reinstall seems drastic to me. If you wanted to reset yourself to the beginning with Samba here's how I would do it:

**(1) Make sure the following file exists:**
/usr/share/samba/smb.conf

**(2) Make a backup of your current smb.conf**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```**(3) Start with a fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```**(4) Correct one mistake in the new one:**
```
 gksu gedit /etc/samba/smb.conf
```
Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = [COLOR=Blue]true[/COLOR]**(5) Restart samba**
```
sudo service smbd restart
```**(6) Use Samba Nautilus-share to create a guest share:**

Start with something very simple at first:
Open Nautilus
Right click on /home/your_user_name/Documents
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete..", and "Guest access"
Select "Create Share"

It will ask you if you want it to modify permissions - you do.

**(7) Now go to XP's My Network or Network Places ( or whatever it's called on XP ) and see if you can see the documents share.**

---

### Post by Eina1 on 2010-06-30
I do not know how I can thank you for you're help and patience. 
Here is what I did.
Follow the steps in post 25
On windows changes all the tcp/ip ect setting I could get to automatic
I've also activated all the firewalls again 
and viola

I can now access all the shared docs on ubuntu from xp, but not visa versa yet.

I would like to know how I can set up the machines to use the printer and INTERNET over the network?
I now also have 2 workgroups on both pc registerd, one called workgroup and one called tuis, will this be a problem in future.

Thank you for all you're help.

---

### Post by Eina1 on 2010-06-30
I fixed the 2 workgroup problem on xp by changing the xp's work group to "workgroup" 
Networks on ubuntu still shows 2 workgroups but I get the following error when I try to access the xp machine

Unable to mount location
Failed to retrieve share list from server

---

### Post by Morbius1 on 2010-06-30
> Unable to mount location
Failed to retrieve share list from server     In a Terminal type:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the WinXP machine.*[/COLOR]

If it connects and you can see your XP shares "Bookmark" it:
In Nautilus > Bookmarks > Add Boobmark
It will show up under places on the left panel just like a "mapped drive" does in Windows.

---

### Post by Eina1 on 2010-06-30
I've got the printer sorted
Just had to install a new printer in xp

---

### Post by Eina1 on 2010-06-30
The INTERNET is also sorted - just had to tell Firefox to use network instead of modem.

I really appreciate all the help, thank you

---

### Post by casals on 2010-07-10
0

---

### Post by Morbius1 on 2010-07-10
While I would agree that osx sometimes gets confused by something other than an ip address it can work with a machine name:

ipp://MACHINE_NAME:631/printers/Linux-Printer-Name

BTW you might want to enable the "Advanced" printer ICON in OSX:
[http://swiss.ubuntuforums.org/showpost.php?p=9521970&postcount=9](http://swiss.ubuntuforums.org/showpost.php?p=9521970&postcount=9)

Using it from the IPP icon always gave me problems.

---

### Post by casals on 2010-07-11
0

---

### Post by Morbius1 on 2010-07-11
You do have the printer on the Linux box "shared" and "published" through CUPS right?

*Enable Sharing for that Printer.*
Administration  > Printing > Right Click the attached printer > Properties >  Policies
Check Enabled, Accepting Jobs, and Shared

*Enable Publishing of the Shared Printer*
Administration >  Printing > Server > Settings > Check "Publish Shared Printers  connected to this system"

---

### Post by casals on 2010-07-12
0

---

### Post by casals on 2010-08-26
Here's what worked for me.

Setup: 6-year-old PC with HP Laserjet 6L plugged into the parallel port; ethernet cable into Linksys WRT54G router, cable internet. 2 Mac Laptops, one Windows netbook, want the PC to be a print server over wifi. 

First I got rid of Ubuntu 10.04 and installed Debian Lenny instead. I don't think this should make any material difference at all. 

I used a guide by Ian Ward called "Debian and Windows Shared Printing 
mini-HOWTO" [http://www.ibiblio.org/pub/linux/docs/HOWTO/other-formats/pdf/Debian-and-Windows-Shared-Printing.pdf]("http://www.ibiblio.org/pub/linux/docs/HOWTO/other-formats/pdf/Debian-and-Windows-Shared-Printing.pdf"). If you google the title there are copies of it all over the place. 

I followed all the directions (skipped the part about Printing to Windows PCs). The crucial things, I think, were the settings for CUPS and Samba, and especially the step of creating a no-password account and user in Samba. Also crucial is permissions: printing didn't work at first, and so I had a look at

/var/log/samba/log.<my laptop>

and saw that my laptop didn't have permission to write to the spool file in the new no-password account. (By the way, go look at these log files, they will actually tell you what Samba and CUPS are seeing, unlike the dreadful Mac print queue panels.) So I went to /home and did

chmod 777 smbprint

(that's the name of the new account). I added the printer on Mac OS X 10.5.8 using the "Advanced" button, select Windows, then type smb://servername/printername for URL, then specify the driver. (I think it will also work to add it as a regular Windows printer.) I'm asked for a password every time I print, and I click the Guest radiobutton. 

I added the printer on a WinXP netbook; browsing for the printer didn't seem to work, but when I put in \servername\ it popped up with the printer name in the dialog to specify the printer location manually. 

I know this isn't very secure, and it can be done in different ways, but this worked for me. 

Like many others in this situation, I'm appalled that it should take so long (in my case, on-and-off fiddling since for 2 months) and be so frustrating to do something that every home user will want to do, 2 minutes after they have installed Ubuntu or Debian or whatever.

---

### Post by Morbius1 on 2010-08-26
casals, That HowTo you referenced really takes you back doesn't it?

I would argue that if you're going to use samba to connect to an Ubuntu attached printer 5 conditions need to be met:

(1) The Ubuntu attached printer should be installed and workable from Ubuntu itself

(2) The Ubuntu printer should be be set to "Shared" and the CUPS server should be set to "Publish shared printers"

(3) For guest access without a password prompt on the client only one modification needs to be made to the default smb.conf:
From this default [printers] section:
> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
[COLOR=Blue]   guest ok = no[/COLOR]
   read only = yes
   create mask = 0700To this:
> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
[COLOR=Blue]   guest ok = yes[/COLOR]
   read only = yes
   create mask = 0700Now the next 2 conditions are because of upstart bugs introduced in the 10.04 Ubuntu release:

(4) You must make sure that the cups service starts before the smbd service starts. You will know it hasn't if you issue the following command and no printers show up in the list:
```
smbtree
```(5) You must make sure that the nmbd service is running or else your entire ubuntu machine will not appear on the network. To find out it's running:
```
sudo service nmbd status
```Steps (1) and (2) are pretty much the same thing you'd have to do if the printer was on Windows. Step (3) is a samba thing. And Steps (4) and (5) are because of bugs in how services are started these days and may or may not affect everyone. There may be other reasons connecting to a printer fails , firewalls, apparmor, name resolution, etc.., but these 5 conditions must be met.

The HowTo's requirement that you set security to share and create a "guest account = smbprint" ( with it's own home directory, no less ) when there already is a "guest account = nobody" created by default is convoluted in my opinion.

I have no doubt that it works for you but I don't think the average user needs to go though all that to access a shared printer.

---

### Post by casals on 2010-09-01
Excellent! That did it. I reinstalled 10.04.1. Made sure the printer worked. Used Synaptic Package Manager to load Samba (see first post: this isn't loaded by default). Modified /etc/samba/smb.conf as above. Added the printer on Mac OS X 10.5.8 as a standard Windows printer. Print; check Guest as the password. It worked! Sharing worked too! But.....

Here's what really catches the unwary: when you reboot, it doesn't work any more. That's what kept killing me the first time around. The problem is the "CUPS starts after Samba" problem. At least on my system, the standard installation of 10.04 doesn't ensure that CUPS starts first, and since it doesn't, Samba doesn't see the printer to share, and so it doesn't. The fix that worked for me is [here]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141/comments/18"). The actual fix is simple. You want to change a single line in /etc/init/smbd.conf, from 
> start on local-filesystems
to
> start on (local-filesystems and stopped rc)

One last puzzle. Whenever I print from Mac OS X 10.5.8, I'm asked for the password, and every time I check Guest. This dialog will remember a user name/password, but it won't remember Guest. Is there a way to get it to remember?

And one last "not quite": adding the printer on my wife's 10.5.8 iMac had to use the Advanced button, type is Windows, then machine/printer in URL after the smb://, then select the driver. Otherwise fine.

---

### Post by casals on 2010-09-03
Um, nope. When I boot up the Ubuntu machine and wait for a half hour, > smbtree
shows nothing at all, not the printer, not the share. I know there's some little thing I've been doing that gets Samba to find its shares, but isn't there a way to tell Samba to get going on its own? Is this the wrong way to fix the start order issue?

---

### Post by Morbius1 on 2010-09-03
It looks like your hitting every single one of the upstart bugs in one install.

Now what you have is the "nmbd starts before samba starts" problem:

Insert a line to /etc/init/nmbd.conf so that it looks like this
> description "NetBIOS name server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

pre-start script
[COLOR=Blue]    mkdir /var/run/samba[/COLOR]
    NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null`

    [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script

exec nmbd -DWithout nmbd running there are no "names" for anyone to see so smbtree outputs nothing.

[COLOR=Blue]EDIT: Just in case you thought I was smart enough to come up with that it was a workaround (#7) in a bug report:[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064)

---

### Post by casals on 2010-09-08
Thanks for that. It didn't seem to be my problem, though (as elegant as it would have been!). I looked through the list of comments on:

 [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064)

and found a reference to another:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410)

and did two things mentioned there: use Synaptic Package Manager to load samba-common-bin; then (a) add pre-released updates (Lucid proposed) as a software repository, and (b) reinstalled Samba. Now nmbd and smbd and cups seem to start in the right order, and I get my printer and my share. Yay!

Boring details: I did change nmbd.config. Annoyingly enough, nmbd HAD started correctly; but after the change and a reboot, it didn't. I took the change out again, reboot, still nmbd didn't start. I checked the logs and found:

in /var/log/daemon.log:
> Sep  7 11:36:59 mymachine init: nmbd pre-start process (1250) terminated with status 1

and in /var/log/samba/smbd.log
> [2010/09/07 11:36:57,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/07 11:36:57,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/07 11:36:57,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/07 11:36:57,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
also, when I tried to manually start nmbd using > sudo service nmbd start I got a message (I don't have it in front of me any more) like "Start failure". That's the point where I went to the second of the two pages mentioned above.

As some of the comments on bugs.launchpad.net said, this strikes me as a very critical thing for Samba and Upstart -- however fiddly the problem is, it has been in my way since June, and I have the luxury of being fairly persistent in trying to fix it. Is there somewhere it would be appropriate to express this concern?

---

