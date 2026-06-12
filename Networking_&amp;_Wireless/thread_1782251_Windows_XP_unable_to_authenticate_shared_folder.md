---
title: "Windows XP unable to authenticate shared folder"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by BakerBug on 2011-06-14
Hello everyone!

I have a file server running Ubuntu 10.4.2.  From the desktop, I have enabled sharing on a folder inside my user's home directory.  I'm now trying to mount this folder as a network drive on a Windows 7 and a Windows XP box.  

The Win7 box works just fine.  It can both read and write files on the server.

When I try to map a network drive on my WinXP box, it continuously prompts me for a username and password.  I enter the credentials that match my account on the Ubuntu box, but XP continues to prompt me over and over.

Since the Win7 box is working just fine, I'm assuming that XP must have some compatibility issue with the current sharing implementation.  Does anyone know what options need to be set to fix this?

Thanks!

---

### Post by dandnsmith on 2011-06-14
I don't think the problem is with XP/Ubuntu 10.04, as mine works quite happily now it has been set up - no repeated prompts.
It's possible that it is a problem with verifying a password, and the encryption used in linux.

You might be able to verify this from the smbd or nmbd logs (never can remember what goes where)

---

### Post by doas777 on 2011-06-14
to clarify, you are using the same username/password on the win7 machine that you are using to connect from XP, right?

one thing to try, is to bump up the minimum NTLM authentication protocol,  which may help:
run 'secpol.msc' and follow these instructions to use NTLMv2:
[https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/576.mspx?mfr=true](https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/576.mspx?mfr=true)

---

### Post by BakerBug on 2011-06-14
Here is a log entry from one of the WinXP machines that fails.
```
[2011/06/14 13:04:59,  0] param/loadparm.c:8569(process_usershare_file)

  process_usershare_file: stat of /var/lib/samba/usershares/tftp_storage failed. Permission denied
```

I am using the same username/password that I use on the working Win7 machine.  I've also found out that about half the WinXP users in our group were successful in mounting the share, but everyone that fails has the same error in their log.

---

### Post by capscrew on 2011-06-14
> **BakerBug said:**
> Here is a log entry from one of the WinXP machines that fails.
```
[2011/06/14 13:04:59,  0] param/loadparm.c:8569(process_usershare_file)

  process_usershare_file: stat of /var/lib/samba/usershares/tftp_storage failed. Permission denied
```
]
I am using the same username/password that I use on the working Win7 machine.  I've also found out that about half the WinXP users in our group were successful in mounting the share, but everyone that fails has the same error in their log.

What do you get with this ```
net usershare info --long
```
[COLOR="RoyalBlue"][B]
Edit:[/B][/COLOR] Also the output of```
ls -l /var/lib/samba/usershares/tftp_storage
```

---

### Post by BakerBug on 2011-06-14
```
root@aos-filesrv:~# net usershare info --long
[2011/06/14 16:38:41,  0] param/loadparm.c:7472(lp_do_parameter)
  Ignoring unknown parameter "SO_RCVBUF"
info_fn: file /var/lib/samba/usershares/storage is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[tftp_storage]
path=/home/public/tftp_storage
comment=
usershare_acl=Everyone:F,
guest_ok=y


```

and...

```
root@aos-filesrv:~# ls -l /var/lib/samba/usershares/tftp_storage
-rw-r--r-- 1 public public 86 2011-06-07 13:49 /var/lib/samba/usershares/tftp_storage

```

---

### Post by capscrew on 2011-06-14
> **BakerBug said:**
> ```
root@aos-filesrv:~# net usershare info --long
[2011/06/14 16:38:41,  0] param/loadparm.c:7472(lp_do_parameter)
  Ignoring unknown parameter "SO_RCVBUF"
info_fn: file /var/lib/samba/usershares/storage is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[tftp_storage]
path=/home/public/tftp_storage
comment=
usershare_acl=Everyone:F,
guest_ok=y


```

This looks like you have some of the {GLOBAL} parts of the smb.conf file in this share.  Did you add this? [COLOR="Blue"]"SO_RCVBUF"[/COLOR]

This is not good```
info_fn: file /var/lib/samba/usershares/storage is not a well formed usershare file.
```

I think I would delete this share and create another one.> 

and...

```
root@aos-filesrv:~# ls -l /var/lib/samba/usershares/tftp_storage
-rw-r--r-- 1 public public 86 2011-06-07 13:49 /var/lib/samba/usershares/tftp_storage

```

I assume you are just retrieving something from here.  Am I correct?
[B]
Edit:[/B] Actually this is where you store the files ```
/home/public/tftp_storage
```  What are the permissions?  ```
ls -l /home/public/tftp_storage
```

---

### Post by BakerBug on 2011-06-15
Alright, I've cleaned up a few things, but the problem still persists.  I don't believe that this is a permission issue, because Win7 and >some< WinXP boxes work just fine.

Here is the updated output:
```
root@aos-filesrv:~# net usershare info --long
[tftp_storage]
path=/home/public/tftp_storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

and...

```
root@aos-filesrv:~# ls -l /var/lib/samba/usershares/tftp_storage
-rw-r--r-- 1 public public 86 2011-06-15 09:35 /var/lib/samba/usershares/tftp_storage

```

---

### Post by capscrew on 2011-06-15
> **BakerBug said:**
> ...I don't believe that this is a permission issue, because Win7 and >some< WinXP boxes work just fine.

And you know best: right????> 

Here is the updated output:
```
root@aos-filesrv:~# net usershare info --long
[tftp_storage]
path=/home/public/tftp_storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

and...

```
root@aos-filesrv:~# ls -l /var/lib/samba/usershares/tftp_storage
-rw-r--r-- 1 public public 86 2011-06-15 09:35 /var/lib/samba/usershares/tftp_storage

```

The share looks correct now.

On an XP host that *fails*: Is the user that you are trying to authenticate a Samba user (added with smbpasswd -a)?  Is this same user (login) also the logged in user on XP when it fails.

From that same host can you mount the share this way```
net use x: \\SMBSERVER\share
``` You need to attempt to browse the share via Explorer to see if it really worked.

Also provide the Samba output of ```
net view \\SMBServer
```

---

### Post by BakerBug on 2011-06-16
Regarding the permissions, I have three PCs that I use to access this server. Two are WinXP, one is Win7.  I am only having this problem with one of my WinXP machines.  I use the same credentials to log into each of these three machines.

Using the "net use" command, the PCs that fail are being prompted for credentials.  The PCs that work are never prompted.

Working PC:
```
C:\>net use t: \\10.100.23.1\tftp_storage
The command completed successfully.


C:\>
```

Non-Working PC:
```
C:\>net use t: \\10.100.23.1\tftp_storage
The password or user name is invalid for \\10.100.23.1\tftp_storage.

Enter the user name for '10.100.23.1': public
Enter the password for 10.100.23.1:
System error 1326 has occurred.

Logon failure: unknown user name or bad password.


C:\>
```

Interestingly enough, I tried entering bogus credentials using the "net use" method and it successfully mounted!  I then tried bogus credentials when mounting though windows explorer and it worked as well.  This really makes no sense. :confused:

If completely bogus credentials are accepted, then why are legit credentials refused, and then again, why only from select WinXP machines?


Here is the net view output.

Working PC:
```
C:\>net view \\10.100.23.1
Shared resources at \\10.100.23.1

aos-filesrv server (Samba, Ubuntu)

Share name    Type  Used as  Comment

-------------------------------------------------------------------------------
tftp_storage  Disk  T:
The command completed successfully.


C:\>
```

Non-Working PC:
```
C:\>net view \\10.100.23.1
Shared resources at \\10.100.23.1

aos-filesrv server (Samba, Ubuntu)

Share name    Type  Used as  Comment

-------------------------------------------------------------------------------
tftp_storage  Disk
The command completed successfully.


C:\>
```

---

### Post by capscrew on 2011-06-16
> Using the "net use" command, the PCs that fail are being prompted for credentials. The PCs that work are never prompted.

Just a guess here: The PC's that just work are have a user accepted as a guest and the one that doesn't work does not have (for whatever reason) a guest user)

This is a permission problem.

Look at the logs on the Samba.  They are at: /var/log/samba

You can see the logins by using the tail command```
tail /var/log/samba/log.<samba_server>
```

See the man pages for tail ```
man tail
```

---

### Post by BakerBug on 2011-06-16
> **capscrew said:**
> Just a guess here: The PC's that just work are have a user accepted as a guest and the one that doesn't work does not have (for whatever reason) a guest user)

I'm not sure what you mean by this.  Are you saying that the Client PCs need to have a guest account on them?

The file server has one account on it that all users share.  Even so, guest access is enabled so an account on the server shouldn't be necessary.  See attached screen shot.


If this is a permission problem, what permissions are wrong?  And how does that explain the bogus credentials working?  I appreciate your help, and I'm sorry this seems to be taking so long.

---

### Post by Morbius1 on 2011-06-16
Here's my best guess.

There's a parameter in the default smb.conf ( map to guest = Bad User ) which does the following: When a remote user enters a username  that doesn't match the samba username on the server it is classified as a "bad user" and converted to "guest" and everything works.

In this particular case with a guest share no one should be asking for a username and password but that's not how Windows works. Windows automatically passes the actual Windows login username and password when it connects to a remote share. If the Linux server has a samba user that matches that login username and the passwords match then it lets the user in. If the usernames are the same but the passwords are different then you are in an infinite loop of trying to authenticate - even to a guest share.

What complicates this process even further is the introduction of a package libpam-smbpass which automatically creates a samba pssword that matches every Linux login users' login password. So you no longer have to create a samba password yourself it's done automatically for you.

So the question is does the non-working PC have a login username and password that matches exactly ( and I do mean exactly ) the login username and password of the Linux user?

---

### Post by doas777 on 2011-06-16
> **BakerBug said:**
> 
If this is a permission problem, what permissions are wrong?  And how does that explain the bogus credentials working?  I appreciate your help, and I'm sorry this seems to be taking so long.

not sure. post 'ls -al <local path to shared folder>'.

the bogus credentials indicate that initially the client was trying to connect as a specific user, and prompted for the password. that user however does not have access. after that is established the client falls back to attempting guest access.
just cause something is accessible to guest does not mean that it is accessible to everyone. all it means is that everyone can access it if they try to get in AS guest.

---

### Post by BakerBug on 2011-06-16
> **Morbius1 said:**
> 
So the question is does the non-working PC have a login username and password that matches exactly ( and I do mean exactly ) the login username and password of the Linux user?

THAT WAS IT!

The PCs that were having the problem had a local account that was an exact match for the shared account on the file server.  We were able to disable the accounts on the client machine, and now everything works perfectly!

Thanks for all the help!

---

### Post by capscrew on 2011-06-16
> **BakerBug said:**
> THAT WAS IT!

The PCs that were having the problem had a local account that was an exact match for the shared account on the file server.  We were able to disable the accounts on the client machine, and now everything works perfectly!

Thanks for all the help!

See: Good things happen when I have to go away for awhile.  :D

If this is a domain situation then your local accounts should only be local_admin.  If this is an ad hoc (P2P) free for all then I would heed Morbius1's notion.  No duplicate names on the network or ALL shares are guest only.

---

