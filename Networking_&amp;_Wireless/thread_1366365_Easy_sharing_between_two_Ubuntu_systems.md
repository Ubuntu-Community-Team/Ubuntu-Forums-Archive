---
title: "Easy sharing between two Ubuntu systems?"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by WolfRage on 2009-12-28
I just want to **[SIZE=5]EASILY[/SIZE]** share files from one Ubuntu to Ubuntu system, my networks is secure and I feel I should be able to do this easy? Please tell me how. I have tried to enable sharing on both computers and they both say that sharing is enabled and samba is installed; both can see one another and I can see the $Print and Public folder but I get unable to mount Public from both Ubuntu computers. Both are 9.10 installs.

---

### Post by doas777 on 2009-12-28
are you using the same username/passwd on both pcs?
have you logged into both PCs? are you using network-manager or the interfaces file to configure your network settings?

---

### Post by WolfRage on 2009-12-28
Network Manager has configured the network. Two separate users on two separate systems. I am currently trying to use Samba to connect the two. Yes I realize this adds extra processing that is meant for accessing a windows system. I am able to mount the vista machine. But I am trying to convert my wife to Ubuntu; then I hit this wall of not being able to share between the two systems even though I can share with a Windows system?

---

### Post by doas777 on 2009-12-28
post the output of this command from both pcs:
```

sudo testparm /etc/samba/smb.conf

```

at what point exactly is the sharing failing? are you unable to login, or is the folder just not being shared at all?

---

### Post by Morbius1 on 2009-12-28
What method of sharing are you using?

**sudo testparm** will show share definitions using classic samba

**net usershare info** will show share definitions if you're using nautilus-share ( as in Right Click Folder in nautilus > Sharing Options > Share this Folder )

---

### Post by WolfRage on 2009-12-28
This is from my computer.
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public1]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
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

[Public1]
    path = /home/<user>/Public
    read only = No
    guest ok = Yes
```
I can access the computers via smb://192.168.*.*/ but when I choose to mount Public it states that it failed to mount the windows share.

```
net usershare info
[public]
path=/home/<user>/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```
I guess I am trying to use both and hoping that I can get one or the other to work.

---

### Post by WolfRage on 2009-12-28
From the other machine. Again this is a different user login.
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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

```
net usershare info
[public]
path=/home/<user2>/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Morbius1 on 2009-12-28
Well, first off, on one PC you're using both methods so you need to decide which one you want to use.

If you want to use "Classic" samba you need to go into nautilus and "unshare" Public.

 If you want to stay with nautilus share you need to remove:
> [Public1]
    path = /home/<user>/Public
    read only = No
    guest ok = Yesand restart samba: In a terminal **sudo samba restart samba**

All your shares allow guest access so that's not a problem. Fix this computer first and see if the other can now access it.

---

### Post by doas777 on 2009-12-28
> **Morbius1 said:**
> Well, first off, on one PC you're using both methods so you need to decide which one you want to use.

If you want to use "Classic" samba you need to go into nautilus and "unshare" Public.

 If you want to stay with nautilus share you need to remove:
and restart samba: In a terminal **sudo samba restart samba**

All your shares allow guest access so that's not a problem. Fix this computer first and see if the other can now access it.


I think that should be:
```
**sudo service restart samba**
```
or ```
sudo /etc/init.d/samba restart
```

your right, I've never had any luck mixing the system and userspace (gui) models. pick one and stick with it to the death. I always go with the system space, since it avoids some limitations (user must be logged in, etc).

---

### Post by Morbius1 on 2009-12-28
Sorry it's [B]sudo service samba restart

[/B]> I always go with the system space, since it avoids some limitations (user must be logged in, etc).

Did not quite follow that one. Nautilus-share does not require a user be loged on for shares to be accessible if that's what you're refering to.

---

### Post by WolfRage on 2009-12-28
OK "sudo testparm /etc/samba/smb.conf" returns:```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
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
Net UserShare Info returns: ```
net usershare info
[public]
path=/home/<user>/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

But when I try to access this computer from the other I still get Unable to Mount Windows Share.
Thank you both for your help so far. I am hoping that this is an anomaly, but I have never successfully shared between two Linux Systems.

---

### Post by Morbius1 on 2009-12-28
Is /home/<user>/Public just a folder in your home directory or is it a mount point to another partition?

Do a **ls -dl  /home/<user>/Public** to see if somehow nautilus-share didn't reset the permissions properly.

The only other thing I can think of is the firewall. If you have done anything since the install to the firewall you could try to disable it just to see if it's getting in the way.

And it that's not it then let's go digging for error messages:

Open **Terminal**
Type **smbtree**
Type **findsmb**

---

### Post by WolfRage on 2009-12-28
It is just a directory with in my home. Returned out put from Terminal: ```
drwxrwxrwx 4 <user> <user> 4096 2009-12-28 14:59 /home/<user>/Public
``` With so many read, write, execute, I am not sure what that means. But I think that means Owner/Group/Others all have read/write/execute permissions.
smbtree returns: ```
WORKGROUP
    \\WRW-LAPTOP-UBUN        WRW-laptop-Ubuntu-9 server (Samba, Ubuntu)
\\WRW-LAPTOP-UBUN\public             
        \\WRW-LAPTOP-UBUN\Deskjet-F4100-series    HP Deskjet F4100 series
        \\WRW-LAPTOP-UBUN\IPC$               IPC Service (WRW-laptop-Ubuntu-9 server (Samba, Ubuntu))
        \\WRW-LAPTOP-UBUN\print$             Printer Drivers
    \\LEISHA-DESKTOP-U        leisha-desktop-ubuntu server (Samba, Ubuntu)
        \\LEISHA-DESKTOP-U\public             
        \\LEISHA-DESKTOP-U\IPC$               IPC Service (leisha-desktop-ubuntu server (Samba, Ubuntu))
        \\LEISHA-DESKTOP-U\print$             Printer Drivers
    \\FAKE-XP-2              
cli_start_connection: failed to connect to FAKE-XP-2<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
```
Fake xp 2 is a virtual machine on the Desktop. Not to concerned with that at the moment.

findsmb returns: ```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.101   WRW-laptop-Ubuntu-9.local [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.102   LEISHA-DESKTOP-+[WORKGROUP] [Unix] [Samba 3.4.0]
``` This took several seconds to generate a response.

---

### Post by Morbius1 on 2009-12-28
If this were a Windows / Linux network your netbios names are too long. So let's assume the same thing happens with linux / linux.

It has to be 15 characters or less. The easiest way is to set up a netbios name in smb.conf:

On each machine:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

add a line [COLOR=Blue]EDIT: in the [global] section[/COLOR] to each that looks like this:
[B]netbios name = something_15_characters_or_less

[/B]No spaces please.

Save the file, exit gedit and issue a **sudo service samba restart** on each machine.

---

### Post by doas777 on 2009-12-28
check /var/log/samba, and see what files were updated recently. they may contain useful diagnostic information. you can view them with the log file viewer at System->Administration->LogFileViewer

---

### Post by WolfRage on 2009-12-28
I was hoping that was it, but still not able to mount each other. Going to restart both. Also I noticed that for my system logs under administration, Samba is not in there so I will have to view that manually.

---

### Post by doas777 on 2009-12-28
> **WolfRage said:**
> I was hoping that was it, but still not able to mount each other. Going to restart both. Also I noticed that for my system logs under administration, Samba is not in there so I will have to view that manually.

yeah, you have to go to File->Open to show the smbd logs. pay special attention for a file in there called log.<hostnameOfFailingClient> that was updated very recently. samba keeps a log file for each client, so the messages there should be pertinent to the failing clients connections.

---

### Post by WolfRage on 2009-12-28
This is what was in one of the log for the New Name change of the Desktop on my computer the laptop. ```
[2009/12/28 20:50:04,  0] smbd/service.c:1009(make_connection_snum)
  '/home/wolfrage/Public' does not exist or permission denied when connecting to [public] Error was Permission denied
``` And from Previous attempts with a different bios name the one that was too long. ```
[2009/12/28 14:15:29,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2009/12/28 14:15:29,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2009/12/28 16:34:02,  0] smbd/map_username.c:140(map_username)
  can't open username map /etc/samba/smbusers. Error No such file or directory
[2009/12/28 16:35:17,  0] smbd/map_username.c:140(map_username)
  can't open username map /etc/samba/smbusers. Error No such file or directory
```

Also this log is from when I try to connect to myself through the nautilus shares. ```
[2009/12/28 22:00:03,  0] smbd/service.c:1009(make_connection_snum)
  '/home/wolfrage/Public' does not exist or permission denied when connecting to [public] Error was Permission denied
```

---

### Post by doas777 on 2009-12-28
hmmm. 
looks like the remote user does not have read access to the shared folder. 
what is the output of 
```
ls -l /home/wolfrage/Public
``` (also is it public or Public? doesn;t matter which as long as it's consistent).

my guess is that you will either have to change the owner group, or give the "other" group read access. you can do that with
```
sudo chmod -R o+r /home/wolfrage/Public
```

---

### Post by Morbius1 on 2009-12-28
If appears to be a known bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

You might try the recommendation in post #17

Open **Terminal **
Type **gvfs-mount smb://netbios_name/share_name**

If it connects, Bookmark it !

---

### Post by doas777 on 2009-12-28
> **Morbius1 said:**
> If appears to be a known bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

You might try the recommendation in post #17

Open **Terminal **
Type **gvfs-mount smb://netbios_name/share_name**

If it connects, Bookmark it !

I'm not sure I concur that this is an example of that bug, since there is no evidence of the endpoint error message, and because the issue is in hitting a discrete share, not the workgroup container itself (and it appears to be a problem in nautilus, not samba itself).

---

### Post by WolfRage on 2009-12-28
Ahh but I think I do agree with him, because I was previously receiving those requests for user name and password. But i saved the lack of password to my key chain. So now it has stopped requesting me to enter them, but I still fail to mount the drives.
So knowing that this is possibly a bug. I would like to know is Karmic using Samba 4?

@doas777 out put from terminal ls:```
total 326156
-rw-r--r-- 1 wolfrage wolfrage   2028640 2009-12-06 23:04 sp1aexpress_usa.exe
drwxrwxrwx 3 wolfrage wolfrage      4096 2009-10-18 00:25 Themes
-rw-r--r-- 1 wolfrage wolfrage    104062 2009-12-07 12:21 tuxperience-1024x768.jpg
-rw------- 1 wolfrage wolfrage 331805736 2009-12-06 22:33 windowsxp-kb936929-sp3-x86-enu_c81472f7eeea2eca421e116cd4c03e2300ebfde4.exe
drwxrwxrwx 9 wolfrage wolfrage      4096 2009-12-05 23:53 XPActivator Pack
```

The gvfs-mount did not work, it to yielded that it failed to mount the windows share.

---

### Post by doas777 on 2009-12-28
> **WolfRage said:**
> Ahh but I think I do agree with him, because I was previously receiving those requests for user name and password. But i saved the lack of password to my key chain. So now it has stopped requesting me to enter them, but I still fail to mount the drives.
So knowing that this is possibly a bug. I would like to know is Karmic using Samba 4?

@doas777 out put from terminal ls:```
total 326156
-rw-r--r-- 1 wolfrage wolfrage   2028640 2009-12-06 23:04 sp1aexpress_usa.exe
drwxrwxrwx 3 wolfrage wolfrage      4096 2009-10-18 00:25 Themes
-rw-r--r-- 1 wolfrage wolfrage    104062 2009-12-07 12:21 tuxperience-1024x768.jpg
-rw------- 1 wolfrage wolfrage 331805736 2009-12-06 22:33 windowsxp-kb936929-sp3-x86-enu_c81472f7eeea2eca421e116cd4c03e2300ebfde4.exe
drwxrwxrwx 9 wolfrage wolfrage      4096 2009-12-05 23:53 XPActivator Pack
```The gvfs-mount did not work, it to yielded that it failed to mount the windows share.

how about the same command on /home/wolfrage/ ? some of your files would be readable, and others not (those with -------r-- are readable), but I'm not sure about the Public folder itself. 

you are right, this may be a bug. I hadn't realized you were working with lucid until Morbius pointed it out.

---

### Post by WolfRage on 2009-12-28
SO I am really seriously considering going to Samba4 I did this with a 9.04 install because it was misbehaving on the network and Samba4 seemed to make it all better. What are your thoughts; both of you?

---

### Post by doas777 on 2009-12-28
if it already isn't working, then you have a great opportunity to try something new and interesting, at no cost, so go for it. let us know how it works out for ya

---

### Post by WolfRage on 2009-12-28
Out put for ls on home directory limited to the line for Public: ```
drwxrwxrwx  4 wolfrage wolfrage    4096 2009-12-28 14:59 Public
```
I am using Ubuntu Karmic 9.10 on both machines; not Lucid.

---

### Post by doas777 on 2009-12-28
> **WolfRage said:**
> Out put for ls on home directory limited to the line for Public: ```
drwxrwxrwx  4 wolfrage wolfrage    4096 2009-12-28 14:59 Public
```I am using Ubuntu Karmic 9.10 on both machines; not Lucid.

that should work. I'm not sure what to tell you on the permission denied.

just to clarify, you aren't being prompted for a password are you?

---

### Post by WolfRage on 2009-12-28
Not recently but I have been in the past. However I either canceled, because that worked for the vista machine or entered something like pass.

---

### Post by WolfRage on 2009-12-28
Samba4 on both machines and I still get unable to mount windows share. Why? WTF? Guess I will tell her she can use Vista until Ubuntu comes back up to par. How sad.

Why are both computers showing next to the windows network under network. But there is no longer a workgroup withing windows network?

smbtree yields zero output since the upgrade. findsmb seems to result in a bit of a loop.```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.101   WRW_LAPTOP     [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.101   WRW_LAPTOP     [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.101   WRW_LAPTOP     [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.101   WRW_LAPTOP     [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.102   LEISHA_DESK    [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.102   LEISHA_DESK    [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.102   LEISHA_DESK    [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.102   LEISHA_DESK    [WORKGROUP] [Unix] [Samba 3.4.0]

```The logs do not seem to be getting updated.

Is there a way that i can delete a saved password from my key chain or whatever it is called? I was able to browse my printer which makes me wonder if I just need to actually use a user name and password. It's not ideal for what I wanted, but it is more secure and as long as I can share.

---

### Post by Morbius1 on 2009-12-28
We need something that bypasses nautilus. I'm a little rusty at this but try this if for no other reason than to see another set of errors that will help diagnose this phenomenon.

In a terminal
Type **smbclient //ip_address/sharename **
You should end up with a prompt in the terminal that looks like this: 
[COLOR=Blue]**smb:\>**[/COLOR] 
Type **ls**

You should get a listing of the contents of the folder.

NOTE: When you're done working in the terminal type quit i.e., 
[COLOR=Blue]smb:\>[/COLOR] [B]quit

[/B]BTW. It's not like I've spent 20 years at this or anything but I've never seen duplicates on findsmb. I'm trying to figure out under what circumstances that is even possible.

---

### Post by doas777 on 2009-12-28
here are some instructions on clearing your keyring. having a bad password in there would cause the symptom you have described.

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)
you should probably reboot after doing it.

---

### Post by WolfRage on 2009-12-29
@morbius1 the smbclient command with the IP address of the other computer and it's share returned. ```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```@doas777 just deleted the ring; restarting. Will edit with results.

Well now when I connect to WorkGroup it asks me for a password, and will not go beyond that point. So it is the bug. What can I do about it?

If I can't fix this do you two recommend SSH or NFS?

---

### Post by Morbius1 on 2009-12-29
I did a quick google search of **NT_STATUS_BAD_NETWORK_NAME **and it found something in this forum:

[http://ubuntuforums.org/showthread.php?p=6335168#post6335168](http://ubuntuforums.org/showthread.php?p=6335168#post6335168) Look at post #13.

The whole path to /home/wolfrage/Public has to have at least "read" enabled in it's permissions which is something doas777 mentioned 14 hours ago.

If you do an **ls -dl /home/wolfrage** does it at least have an r in all 3 sections:

> d[COLOR=Red]r[/COLOR]wx[COLOR=Red]r[/COLOR]-x[COLOR=Red]r[/COLOR]-x 79 wolfrage wolfrage

---

### Post by doas777 on 2009-12-29
ssh/scp/sftp is a good option for secure transport, though it is likely overkill for a firewalled internal network, so it will be slower than samba.

to use scp, just install openssh-server, and after that, find and edit your sshd_config to set "PermitRootLogin = no". then save and restart sshd.

after that, all you have to do, is go to another linux pc, open nautilus, and put in the address bar "ssh://<serverNameOrIP>" and it will open a nautilus window to the servers / . 
if you are using a windows client, you will have to use WinSCP. 

very easy, just slow.

---

### Post by WolfRage on 2009-12-29
Doas777 & Morbius1 I ran the command and no, it does not have read access in all three locations. How do I fix it. I think I know and I am going to try and change it. I will post back I hope that will fix this.

Edit you guys rock! That was it because there was not read permissions at each level! OK now why was the read access not set correctly when I choose to share that folder? I mean why was my home directory not setup by Ubuntu? Shouldn't every one experience this problem?

---

### Post by WolfRage on 2009-12-29
Ok so there is still a problem, not major, but seems like something is broke. The laptop is no longer showing any computers in the network area. So what do you think caused the problem?

Some extra information. I did delete my key ring. Now when I choose windows network, I do not see "WorkGroup". So  when I type in smb://workgroup/ I get prompted for my password, but it will not accept any password or aborting, simply continues to ask for my password.
But when I type findsmb After awhile the other computer shows up as being under the WORKGROUP but not the laptop it's self.

---

### Post by Morbius1 on 2009-12-29
> So when I type in smb://workgroup/ I get prompted for my password, but it will not accept any password or aborting, simply continues to ask for my password.All these shares are still set for guest access right?

What you're describing has happened to me only once and it was between windows and linux because of a peculiarity of how windows accesses remote shares. Are you using the same username on both machines AND did you ever give that username an smbpasswd on box that has the share you're trying to access.

Note that it's asking for authentication at the Workgroup level not the share level.

If it follows the same pattern you should be able to gain access by giving the following when it asks for authentication:

[B]User Name: guest
Password: NULL  [COLOR=Blue]<-- leave it blank.

[/COLOR][/B][COLOR=Black]The ultimate answer was to either change someones username or remove the smbpasswd from that user.[/COLOR][B][COLOR=Blue]
[/COLOR][/B]

---

### Post by WolfRage on 2009-12-29
So I tried the guest user name with no pass and it accepted it but now states "Could not display "smb://workgroup/".  "Error: Failed to retrieve share list from server
Please select another viewer and try again."

---

### Post by doas777 on 2009-12-29
> **WolfRage said:**
> So I tried the guest user name with no pass and it accepted it but now states "Could not display "smb://workgroup/".  "Error: Failed to retrieve share list from server
Please select another viewer and try again."

there can be many causes to that problem. if you want to browse the workgroup itself, I think you need a domain master, to store the workgroups share list. computers fight to determine who is the primaru master browser (the computer with the full list of shares), and the election process can cause problems.  

can you still get to discrete shares if yo8u call them by their full names?

---

### Post by WolfRage on 2009-12-29
If you mean can I access the shares by netbios or IP then yes I can and that is what I have been doing. So how do I put just one machine in charge?

---

