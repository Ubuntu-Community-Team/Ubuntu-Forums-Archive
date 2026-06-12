---
title: "Can we have a &quot;Sticky&quot; for SAMBA config and issues?"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by emarkay on 2009-10-16
Not to be a whiner, and it's really not urgent, but, in 3 years or so have never been able to network 3 PC's in Ubuntu, when they are on Ubuntu, or Windows XP.  I know the network works, because I can get them connected in Windows XP.

I have "system-config-samba" and "Smbfs" installed.  I have confirmed my "workgroup" names are identical, and added the "netbios name" to all, also.

In "Samba Server Configuration" the specific folder is shared (indicated in Nautilus with share icon on folder) and is "Read/Write, Visible".

When I go to "Places > Network", "Windows Shares on <workgroup>" I click and eventually only see one machine - this one.

I have seen a "dbus error" occasionally but always get the infamous "Unable to mount location. Failed to retrieve share list from server" everytime otherwise.

Once, recently I did see one of the machine's names, but when I clicked on it I got the "share list" error.

All are Karmic (beta) updated machines, but this has been through Jaunty back to about Dapper.  Like I said, it's not critical, but annoying.

Thank you.

---

### Post by swerdna on 2009-10-16
> **emarkay said:**
> Not to be a whiner, and it's really not urgent, but, in 3 years or so have never been able to network 3 PC's in Ubuntu, when they are on Ubuntu, or Windows XP.  I know the network works, because I can get them connected in Windows XP.

I have "system-config-samba" and "Smbfs" installed.  I have confirmed my "workgroup" names are identical, and added the "netbios name" to all, also.

In "Samba Server Configuration" the specific folder is shared (indicated in Nautilus with share icon on folder) and is "Read/Write, Visible".

When I go to "Places > Network", "Windows Shares on <workgroup>" I click and eventually only see one machine - this one.

I have seen a "dbus error" occasionally but always get the infamous "Unable to mount location. Failed to retrieve share list from server" everytime otherwise.

Once, recently I did see one of the machine's names, but when I clicked on it I got the "share list" error.

All are Karmic (beta) updated machines, but this has been through Jaunty back to about Dapper.  Like I said, it's not critical, but annoying.

Thank you.
That error message is often seen when the UFW firewall is not configured for Samba. So maybe turn it off pro tem to see if things improve.

FFI: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubusambaserver.html#firewall")

For the broad config requirements:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home or Office LAN/Network]("http://ubuntu.swerdna.org/ubusambaserver.html")

---

### Post by emarkay on 2009-10-17
[SIZE=2][SIZE=1]So this is what I have to do, as I read these and others.  I will try this later today on both machines and see if they can then speak to each other.  Thanks.
[/SIZE] 
```
[SIZE=1]BACKUP ORIGINAL FILE:  [I]sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

[/I]1. [I]sudo ufw disable
[/I]
2. *gksu gedit /etc/default/ufw*
Find and change to this: *IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"*

3. sudo* ifconfig | grep Bcast*
Look for "inet addr: and replace last segment  of this IP address with  "0/24".  Now do:
[I]sudo ufw allow proto udp to any port 137 from 192.XXX.X.0/24
sudo ufw allow proto udp to any port 138 from 192.XXX.X.0/24
sudo ufw allow proto udp to any port 139 from 192.XXX.X.0/24
sudo ufw allow proto udp to any port 445 from 192.XXX.X.0/24
[/I]
4. Add a user to the Database or change an existing user's password (as root) with smbpasswd:
[I]sudo smbpasswd -a <username>
New SMB password: ######
Retype new SMB password: ######
[/I]
5. Confirm with:[I] sudo pdbedit -L
[/I]
6. Paste this stanza into smb.conf:
[global] 
[I]workgroup = WORKGROUP_NAME
netbios name = NETBIOS_NAME
server string =
name resolve order = bcast host lmhosts wins
preferred master = no[/I]

7. Restart Samba:* sudo /etc/init.d/samba restart*

8. Note: Each share is defined in a separate stanza in smb.conf.  
[ShareName]
[I]path = /path_to/shared_directory
read only = no[/I]
Then: *sudo chmod 1777 /path_to/shared_directory*

9. Configure for Printing. Include the theses into smb.conf.
[global]
[I]printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes[/I]

[printers]
[I]comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes[/I]

[print$]
[I]comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no[/I]

10. Enable and confirm: *sudo ufw enable | sudo ufw statu*s[/SIZE]              
```[/SIZE]

---

### Post by swerdna on 2009-10-17
Here's two more tips, one re firewall, one re making the machines talk to each other:
Make all the changes, then to make diagnosis of faults simpler, turn UFW off temporarily with "sudo ufw disable".
After all changes, reboot the involved machines consecutively, waiting for each to finish before starting the next one. Do this circuit twice.
When the sharing is working, then turn ufw back on with "sudo ufw enable".

Good luck

---

### Post by emarkay on 2009-10-17
Thanks.  Otherwise what I have here is "hunky-dory"?
I have been doing other things, but will add all these things to my PC's tonight to see if they will speak.  :)

---

### Post by emarkay on 2009-10-18
Well I have aWin XP and a Ubuntu Karmic Beta on the network and this Karmic Beta PC gives me:
"DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered."
when I click on "Network", after I clixk on "Windows Network".

Any other ideas??

---

### Post by swerdna on 2009-10-18
I Googled that error message -- many returns -- they relate to a bug. In one it seemed to go away if you wait for browse master elections to complete, circa 15 minutes. But you should read them yourself -- and maybe file a bug report if necessary.

---

### Post by emarkay on 2009-10-20
> **swerdna said:**
> I Googled that error message -- many returns -- they relate to a bug. In one it seemed to go away if you wait for browse master elections to complete, circa 15 minutes. But you should read them yourself -- and maybe file a bug report if necessary.

I saw those too.  I do file bugs, but there are so many variables with Ubuntu Networking, I wouldn't know what to offer other than what a lot of other people are saying: "It doesn't work." 

I will keep pursuing this, but all I can say is I am glad I am not trying to do anything productive on a network; and you will note, I haven't even tried to connect to to these when one or more is booted into XPSP3!

I will post a link to this thread on the Karmic Beta area, a bit late as it's almost RC day, but maybe...

Thanks, and any other ideas or suggestions welcomed!

---

### Post by screaminj3sus on 2009-10-25
This used to work out of the box in older versions of ubuntu, seriously wtf. I have tried all the suggestions and even turning off firewalle ect.. and get the failed to mount bs.

---

### Post by emarkay on 2009-10-26
Apparently there is are  legit bugs for some Samba applications in Karmic, but I have had no responses to the tests I am prepared to run on the bug I filed regarding configuration:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808)

---

### Post by swerdna on 2009-10-26
> **emarkay said:**
> Apparently there is are  legit bugs for some Samba applications in Karmic, but I have had no responses to the tests I am prepared to run on the bug I filed regarding configuration:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/456808)
Just want to check some things you said in yr bug dialogue & post #3. Can you post here the results of these commands:
[LIST]
[*]ls -l /var/lib/samba/usershares
[*]testparm -s
[*]sudo ufw status
[*]sudo pdbedit -L
[*]smbtree -N
[*]sudo /etc/init.d/samba status
[/LIST]

---

### Post by emarkay on 2009-10-26
Now note, this is a "virgin" Samba install - I have not even named the "Workgroup" to my Windows name.  I wanted this for the Bug to ensure that the config is pure and to document the steps.

[LIST]
[*]ls -l /var/lib/samba/usershares
[/LIST]
ls -l /var/lib/samba/usershares
total 4
-rw-r--r-- 1 <username> <username> 101 2009-10-23 17:14 <shared directory>

[LIST]
[*]testparm -s
[/LIST]
Load smb config files from /etc/samba/smb.conf
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
[INDENT]    path = /var/lib/samba/printers
[/INDENT]
[LIST]
[*]sudo ufw status
[/LIST]
Status: inactive

[LIST]
[*]sudo pdbedit -L
[/LIST]
nobody:65534:nobody
emarkay:1000:,username>,,,

[LIST]
[*]smbtree -N
[/LIST]
No display, just next command line.

[LIST]
[*]sudo /etc/init.d/samba status
[/LIST]
 * nmbd is not running
* smbd is running

Lert me know and if you can, post any relevant comments in the Bug report, also.

---

### Post by swerdna on 2009-10-26
Well the worst thing is that nmbd isn't working, So check in System --> Administration --> Services that samba is turned on (file sharing it's called iirc).

If it is already on, then check that the software is installed. Run this command:```
dpkg -l | egrep "samba|smbclient|nautilus-share"
```In 9.04 I get this:```
ii libsmbclient 2:3.3.2-1ubuntu3 shared library for communicatio.... 
ii nautilus-share 0.7.2-4ubuntu1 Nautilus extension to share fol.... 
ii samba 2:3.3.2-1ubuntu3 SMB/CIFS file, print, and login.... 
ii samba-common 2:3.3.2-1ubuntu3 common files used by both the S.... 
ii smbclient 2:3.3.2-1ubuntu3 command-line SMB/CIFS clients f....
```
What do u get? (and what version of Ubuntu are you installing?).

---

### Post by emarkay on 2009-10-26
We don't have "Services" anymore in Karmic! 
Bes I have is "System Monitor > Processes" and no, no "iirc" or "samba-anything" but I do see some Samba-daemon stopping..." or something when I shut down graphically.

your DPKG command gives: 
"ii  libsmbclient                          2:3.4.0-3ubuntu5                           shared library for communication with SMB/CI
ii  nautilus-share                        0.7.2-12                                   Nautilus extension to share folder using Sam
ii  samba                                 2:3.4.0-3ubuntu5                           SMB/CIFS file, print, and login server for U
ii  samba-common                          2:3.4.0-3ubuntu5                           common files used by both the Samba server a
ii  samba-common-bin                      2:3.4.0-3ubuntu5                           common files used by both the Samba server a
ii  smbclient                             2:3.4.0-3ubuntu5                           command-line SMB/CIFS clients for Unix
ii  system-config-samba                   1.2.63-0ubuntu4                            GUI for managing samba shares and users"

I thought I was clear - this is  Karmic 9.10 - RC installed a few days ago and updated as of now.

---

### Post by swerdna on 2009-10-26
Certainly your problem is the samba naming daemon nmbd. I haven't installed Karmic. You should report this as a bug. Under "Processes" surely there's something about file sharing or network sharing? What's there that's possibly related to windows networking or sharing?

---

### Post by emarkay on 2009-10-27
> **swerdna said:**
> Certainly your problem is the samba naming daemon nmbd. I haven't installed Karmic. You should report this as a bug. Under "Processes" surely there's something about file sharing or network sharing? What's there that's possibly related to windows networking or sharing?

Thanks for your and the others'  assistance.  
The submitted bug was killed - changed to a "question".

To quote a great philosopher:
"Well whatever, nevermind..."

---

### Post by mihow on 2009-12-24
If you killed the bug, what was the answer to the question? I am have the same issue.

---

