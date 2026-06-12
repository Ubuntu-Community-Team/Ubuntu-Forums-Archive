---
title: "Samba Windows 7 cannot login. Keeps asking credentials login."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by barleone on 2010-05-06
I set up Samba on my Ubuntu 10.04 Desktop version using this guide: **[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)**.
Plus partially this guide: **[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html)**.
```
My **/etc/samba/smb.conf**
[share]
    comment = Ubuntu File Server Share
    path = /
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```
```
This option lists all the user accounts present in the users database.
sudo pdbedit -L
    nobody:65534:nobody
    barleone:1000:barleone

```

**Problem:**
From Windows 7 I can only browse with: [anonymous][] (empty password)
But I want to log in with my own Ubuntu username/password.
Now how do I do that? Or what might be the reason it doesn't work now?

Please help, Barleone

PS. From Windows XP (Prof) I can browse anonymous, but I also cannot log in to the share with my Ubuntu credentials.

---

### Post by barleone on 2010-05-06
**UDATE: Problem solved partially.** :)
I managed to browse the share by logging in with my own Ubuntu credentials.
Now I'm figuring out how to give myself all rights to edit normal files.
Tips and howto's are still welcome.

---

### Post by Ylon on 2010-05-06
Consider switching to ftp.. if it's **File**TransportProtocol is for a reason:
Server*ize* windows: [http://filezilla-project.org/download.php?type=server](http://filezilla-project.org/download.php?type=server)
Then you can mount the ftp folder as a normal one.

---

### Post by myk.dinis on 2010-05-06
Windows 7 doesn't play nice with SMB but it does play nice with CIFS...
Nautilus doesn't play nice with CIFS

So, you need to edit your fstab to include the share...

This site: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") will help immensely!!

You can use samba to manage your passwords for the share but not as the actual protocol.

Cheers!!

BTW, I used google and searched for "adding windows 7 shares to fstab ubuntu"

Good luck!

-myk

---

### Post by barleone on 2010-05-06
@Ylon: Many thanks for your alternative idea. I allready fixed it with a little dirty hack though.

@myk.dinis: That's actually the other way around. I was trying to access Ubuntu/[SIZE="1"]shares[/SIZE] on my Win7 computer.

_My solution:_ (see the hyperlink)
[QUOTE=https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html]
For example, if you wanted to give the user melissa administrative permissions to the share example, you would edit the **/etc/samba/smb.conf** file, and add the following line under the [share] entry: 
```
    admin users = melissa
```[/QUOTE]

---

### Post by dude378 on 2010-05-07
Hi Guys,

I'm also having trouble with the Samba sharing and Windows 7.


I just installed Ubuntu 10.04, all settings are default. I only have one user on the computer, which was setup during install.

I create a test folder on the Desktop and right click and choose share. I select "share this folder", "allow others to create..." and "guest access...".

When I hit "create share" is says, "nautilus needs to add some permissions to your folder, I select "add permissions automatically".

I see the share emblem on the folder. Now on Win7, I can see the computer in the Networks folder. When I double click I can see the folder I just shared. But the problem is that when I try to open the folder it says, "Windows cannot access \\server\folder".

I just want to set up a share for my home so that all computers can access it without any passwords or anything.



Thanks.


EDIT: I should point out that I have shared folders on Windows 7 that have no password and I can access them just fine from Ubuntu.

---

### Post by dude378 on 2010-05-07
Ok Found the solution. These are the steps required to get windows 7 to see a Samba share from Ubuntu 10.04 without using command line or modifying config files. Anyone who wants to use command line can adapt this procedure.

1. Create a new Ubuntu User
A) System -> Administration -> Users and Groups
B) Add, give username and password

2. Create smb user
run the command: sudo smbpasswd -a username (I lied about the no command line, this is the only command you have to do)
(make the username the same as above, it must say Added user xxx after you have entered a password)
Note: I tried this using the username I created during install, it gives the prompt for the smb password, but afterwards it does not say the user was added, I don't know what this means, but it didn't work for me, thats why you have to make another user. Easiest to keep this password the same as the Ubuntu user password, but not required.

3. Make a folder and check that the new user can read and write to it (easiest way it to log on as that user and make the folder in your /home/username directory, or use command line and switch to the user (su username) then make the folder)

4. Once the folder is made right click and select "Sharing Options". Allow others to read/write and give guest access. If it asks about permissions, say add automatically. Note: I don't think you need to be login to Ubuntu as the user you just created, meaning you can be logged in as any user when you select the sharing options. You should see the share emblem appear on the folder.

5. To access in windows, you will be able to see the folder in the Network folder, but if you double click it it won't work. You must right click it and select "Map Network Drive".

6. THE KEY: this is what got me, when mapping, select "Connect Using Different Credentials", then for username type in: username@servername, where username is the user you just created and servername is the name of the server you are connected to (the name it says in the Networks Folder, also the name you gave the computer during install). For password, put the password you chose.

The folder should open, try creating a folder to see if you have write permission.


Hope this helps,
Ubernoob

---

### Post by barleone on 2010-05-07
I think that step 5. and 6. would have helped you allready without creating the new user. I guess that you could have logged in to the share with these steps. Because I got it working from Win7 like your steps 5. and 6.

---

### Post by rats54 on 2010-05-11
I have a similar problem and cannot find an answer for it.  I have a LAN setup with Windows 7 machines and Ubuntu 10.04 machines.  I have setup one of the Ubuntu 10.04 machines as a file server.  I am the only user of the LAN and I use the same user name and password on all of the machines.

The Ubuntu servers sees and can access the Windows 7 machines.  Which is something I will change if I ever get everything working.  I do not want the server to be able to access the other machines.

One of the Win 7 machines can see the shared folder on the Ubuntu machine, but when I try to open the folder I am asked for my password. After I enter the password and press Enter the password screen reappears with two messages; a. Access denied, and b. Try again.  Re-trying produces the same result.

The other Win 7 machine only sees the Ubuntu server once-in-a-while.  But, when it does, it has the same problem as the first machine.

I have tried adding a new user and password, but still have the same problem.

I have also tried to map the shared folder on the Ubuntu server as a drive on the Win 7 machines.  During the mapping process I get the Win 7 machines cannot find the server.

I have made what should be the proper changes in the /etc/samba/smb.conf file.

I have turned off the firewalls and still have the same problem.  So, it is not a firewall problem.

Any suggestions?

Thanks.

---

### Post by kanaida on 2010-05-11
Here's whats going on:
Install Windows 7 Fresh
\\sambaserver\sharename    -Works no problem

Add Windows 7 To a domain
\\sambaserver\sharename    -Asks for password - wtf?

How to get around it (for the current logged on user):
Open a command prompt
type: net use \\sambaserver\sharename /user:nobody   (no password)

now magically  \\sambaserver\sharename works... until you log off.

This does NOT happen from windows XP. It's almost as if xp used to pass guest as username or something. I know enabling the guest user account also has something to do with this and it helps.

If anyone knows the answer please let me know.

---

### Post by pricetech on 2010-05-11
I'm not sure if this will help in any of your situations but the only thing I had to do with mine was run the smbpasswd command.  I did everything else via the gui.

I have shares that anyone can read, containing windows software for new installations and updates.  I have a share that is writable by anyone in case I need to upload something for some odd reason.  All of these shares are within another share that is accessible only by server administrators.

All of this worked under Hardy but quit working under Lucid, exhibiting symptoms like some posters have mentioned.  Running smbpasswd fixed everything.  It appears to be a bug in the latest Samba, but obviously the workaround is easy enough.

Good luck to everyone.

---

### Post by rar222 on 2010-10-17
**FIXED (sort of): Here's how I can access Samba on Windows 7**

I have the same problems as everyone else - windows continually asks for my username/password - this seems to work for much older Samba installs also, which is why I posted it. No need to play around with Samba passwords.

I've found that if I use ssh (for example putty) to log into the linux server BEFORE trying to connect samba, samba will connect quite happily. It only works if ssh uses a password (i.e. not a DSA/RSA key).

So basically my actions are this

[LIST=1]
[*]Reboot windows machine
[*]Run putty and ssh into the linux server using a username/password (no keys).
[*]Once logged in successfully via ssh, can close terminal session in putty - you don't need it any more
[*]From windows, connect to //servername/user on windows
[*]Type in standard password as per 2 above
[*]Everything works happily
[/LIST]

Other options (am at work so cannot control the network)

[LIST=1]
[*]Samba options are set to "encrypt passwords = false", "[homes]" are enabled, "valid users = %S"
[*]Windows 7 Setting : "Send NTLMv2 response only" set to "Send LM & NTLM - use NTLMv2 session security if negotiated"
[*]Windows 7 Setting : "Microsoft network client: Send unencrypted password to third-party SMB servers" set to "Enabled"
[/LIST]

---

### Post by ariel on 2010-11-23
> **rar222 said:**
> **FIXED (sort of): Here's how I can access Samba on Windows 7**

I have the same problems as everyone else - windows continually asks for my username/password - this seems to work for much older Samba installs also, which is why I posted it. No need to play around with Samba passwords.

I've found that if I use ssh (for example putty) to log into the linux server BEFORE trying to connect samba, samba will connect quite happily. It only works if ssh uses a password (i.e. not a DSA/RSA key).

So basically my actions are this

[LIST=1]
[*]Reboot windows machine
[*]Run putty and ssh into the linux server using a username/password (no keys).
[*]Once logged in successfully via ssh, can close terminal session in putty - you don't need it any more
[*]From windows, connect to //servername/user on windows
[*]Type in standard password as per 2 above
[*]Everything works happily
[/LIST]

Other options (am at work so cannot control the network)

[LIST=1]
[*]Samba options are set to "encrypt passwords = false", "[homes]" are enabled, "valid users = %S"
[*]Windows 7 Setting : "Send NTLMv2 response only" set to "Send LM & NTLM - use NTLMv2 session security if negotiated"
[*]Windows 7 Setting : "Microsoft network client: Send unencrypted password to third-party SMB servers" set to "Enabled"
[/LIST]



I found quite a simpler solution to this problem for a quick share (ubuntu 10.10 shares, and win7 accesses). 

This assumes an Ubuntu 10.10 box with no tweakings whatsoever to the SAMBA configuration or anything.

In ubuntu > nautilus, simply right-click on the file to share, select Share, then enable the share and select "Allow Guest access (for people without a user account)"; click OK and allow nautilus to adjust the permissions.

Say you Ubuntu box has the IP address: 10.10.10.10

In you win7 laptop, open a file manager window, and in the address bar, type:
```
\\10.10.10.10
```
Then windows will ask you for a username and password, and will show you the "default" **Domain** name which normally will be the name of your windows box in uppercase.

So here is the trick: in the username field, type:
```
WORKGROUP\guest
```
In the password field, type whatever you want, e.g. "guest"

Click OKay.
Enjoy.

ps. yes the trick is forcing windows to show a "WORKGROUP" domain, which is the one used by SAMBA by default. Or so I think. In any case it worked fine :)

---

### Post by jonandrews on 2010-11-26
My experience with this issue from Windows 7, as compared with XP was as follows:

After installing Samba, you rt-click on a folder & select sharing options, and the 'Folder Sharing' dialog appears, with 3 tick boxes.

I used to tick the first 2 boxes (Share this folder, Allow other....etc) and leave the 'Guest access' unticked.

This resulted in one-time request from a connecting XP machine for a user name & password. These were the ones for the Ubuntu pc's login. Acess was granted, & the dialog was never seen again.

However, when I did the same & tried to gain access with a Windows 7 pc, I could not get past the user name & password request.

The solution was to tick the 'Guest Access' box. Ubuntu now grants access to the Win7 pc without any request for a password.

I have written all the steps up in the form of series of guides at [www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by CimmerianX on 2011-05-06
I ran across this thread after running into the same issue.   

I wanted to offer a different solution to allow a domain member win 7 to access these shares without using Guest.

In Win 7, change the NTLM so that it's compatible with a version used in XP.   

Open the registry editor and add in the following key
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa]
"LmCompatibilityLevel"=dword:00000002

Then you can connect with username and password without win7 prefixing the entry with 'domain/'.

---

### Post by Redsandro on 2011-12-02
I have the same problem. Guest shares work fine, but valid users cannot authenticate.

I tried 
> Windows 7 Setting : "Send NTLMv2 response only" set to "Send LM & NTLM - use NTLMv2 session security if negotiated"
and
> [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa]
"LmCompatibilityLevel"=dword:00000002
but still, the authenticate dialog keeps appearing, or it sais:
*\\blah is not accessible. You might not have permission to use this network resource.*

---

