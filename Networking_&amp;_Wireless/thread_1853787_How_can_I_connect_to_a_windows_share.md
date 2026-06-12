---
title: "How can I connect to a windows share?"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2011-10-03
Hi.

I have an ubuntu host with a windows seven virtual machine under virtualbox.
I'd like to share files using windows sharing.

I've created a shared folder called 'shared' under My Documents. I've opened access to everybody.

I've followed this guide:
[http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share](http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share)

But, whenever I try to connect, the 'connect to server' dialogue dissapears for about a minute. Eventually, I then get a frame that pops up and tells me that the attempt to mount failed.

This is very frustrating.

The network path to the folder I'm targetting is "\\myhost\shared". The format is different from the format given by the article, making debugging the process even harder.

I've always found samba a royal, fragile pain in the ***. How can I just connect to the shared folder?

---

### Post by apollothethird on 2011-10-03
> **bobdobbs said:**
> Hi.

I have an ubuntu host with a windows seven virtual machine under virtualbox.
I'd like to share files using windows sharing.

I've created a shared folder called 'shared' under My Documents. I've opened access to everybody.

I've followed this guide:
[http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share](http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share)

But, whenever I try to connect, the 'connect to server' dialogue dissapears for about a minute. Eventually, I then get a frame that pops up and tells me that the attempt to mount failed.

This is very frustrating.

The network path to the folder I'm targetting is "\\myhost\shared". The format is different from the format given by the article, making debugging the process even harder.

I've always found samba a royal, fragile pain in the ***. How can I just connect to the shared folder?

I find samba to be very easy to use and very robust.  My hats off to the developers and maintainers.  I hope I can share some of this enlightenment to you.  While there are gui tools, I find it to be very easy to just type in a commandline and get immediate feedback with problems.  When I have a problem with Windows, since most of it's configuration is hiding and those that aren't so hiding are just not accessible via the commanline, I find the Linux/samba approach very refreshing.

First you might have to check and verify that you can actually access the virtual machine.  Since samba is so easy to use, you might not be having a problem with samba, you just might be having a problem with network access and find it convenient to blame samba for things it might not have control over.

Are you able to ping "myhost"?

If you are able to ping, "myhost" you might try testing nautilus gui network browse:

Start Nautilus -> Go -> Netowrk -> (Click) "myhost" -> (Click) "shared"

You might have to setup a user name and password in your Windows shared.  I just tested it by using test:test for the username and password.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by bobdobbs on 2011-10-03
TCp/IP networking isn't a problem. I can share files just fine by using sftp using filezilla.


> Start Nautilus -> Go -> Netowrk -> (Click) "myhost" -> (Click) "shared"

I can see a folder named 'windows network'.
This is an old folder from an older attempt to connect to a windows share. I've never been able to connect, but I can't figure out how to delete the folder.

---

### Post by apollothethird on 2011-10-03
> **bobdobbs said:**
> TCp/IP networking isn't a problem. I can share files just fine by using sftp using filezilla.




I can see a folder named 'windows network'.
This is an old folder from an older attempt to connect to a windows share. I've never been able to connect, but I can't figure out how to delete the folder.

Did you setup a username and password for the windows share?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by bobdobbs on 2011-10-03
Not explicitly.

Is there a possibility that windows created a username and password for me?


> **apollothethird said:**
> Did you setup a username and password for the windows share?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2011-10-03
> **bobdobbs said:**
> Not explicitly.

Is there a possibility that windows created a username and password for me?

Windows won't create a username and password.  You'd have to do it.  If you don't know how to do it, let me know the version of Windows you're using and I'll give you the steps.

I don't think Windows have a commandline version of doing this.  It's not as simple as Linux.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by bobdobbs on 2011-10-03
I'm ok with my windows host not having a password at the moment.
Right now, I'll take convenience over security.

---

### Post by apollothethird on 2011-10-03
> **bobdobbs said:**
> I'm ok with my windows host not having a password at the moment.
Right now, I'll take convenience over security.

You can create a Windows user and give it a password to test the suggestion I gave you.  Create a username, test.  Give that username test.  Then access that share from Ubuntu by the username and password, test.

You don't have to change anything else on your Windows machine for the way it's accessing the share.  But for the test in my environment, I found it easy to access the windows share by connecting to it by a username and password.  Someone else might have a different way.

When I browsed the share using Nautilus it prompted for a username and password.  I answered the prompt and had no problems connecting to the share.

I also have no problem when connecting to the share from the commandline:

```

sudo mount -o username=test //hostname/share /mnt/share

```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by bobdobbs on 2011-10-03
I don't quiet follow:

Do you mean that I should create a new user in windows? Or that I should create a user in linux, who would then be able to access the share?

I don't want to create a new user in windows, because I'm trying to access the data of an already existing user. Also, if there's a way to access that users share without setting up a password for that user, I'd like to do that. I'm having enough trouble accessing my existing users share without having anything password protected.

Also, I gave mounting via the cli a go, taking a stab by adapting the command that you gave.


```
mount  ///HOST/shared /mnt/tmp
```
returns:
 ```
wrong fs type, bad option, bad superblock on ///SEVEN/shared,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Dmesg says:

```

CIFS VFS: cifs_mount failed w/return code = -22

```




> **apollothethird said:**
> You can create a Windows user and give it a password to test the suggestion I gave you.  Create a username, test.  Give that username test.  Then access that share from Ubuntu by the username and password, test.

You don't have to change anything else on your Windows machine for the way it's accessing the share.  But for the test in my environment, I found it easy to access the windows share by connecting to it by a username and password.  Someone else might have a different way.

When I browsed the share using Nautilus it prompted for a username and password.  I answered the prompt and had no problems connecting to the share.

I also have no problem when connecting to the share from the commandline:

```

sudo mount -o username=test //hostname/share /mnt/share

```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-10-03
> **bobdobbs said:**
> I don't quiet follow:

Do you mean that I should create a new user in windows? Or that I should create a user in linux, who would then be able to access the share?

I don't want to create a new user in windows, because I'm trying to access the data of an already existing user. Also, if there's a way to access that users share without setting up a password for that user, I'd like to do that. I'm having enough trouble accessing my existing users share without having anything password protected.

Also, I gave mounting via the cli a go, taking a stab by adapting the command that you gave.


```
mount  ///HOST/shared /mnt/tmp
```returns:
 ```
wrong fs type, bad option, bad superblock on ///SEVEN/shared,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```Dmesg says:

```

CIFS VFS: cifs_mount failed w/return code = -22

```

Please keep in mind, there is some logic in how the shares are accessed.  Since you're trying to access a Windows share, the username and password will have to be on the Windows machine.  If all I had to do was make a username and password on my machine to access your system, that wouldn't be sound-- security-wise.

So, yes, you'd have to create a username and password on your Windows machine and give that username and password access to the share to have the same results that I have from the test I immediately performed before giving the steps to you.

Creating a new account and giving that new account access to a share will not take away from what you're already sharing on your network.  You'll still have the same access from the other computers the way you're using them.  However in this case, you'd also have simultaneous access via a different user.  Just like Linux, you can have more than one account on Windows.  You can also give each of those account various degrees of access of full access to the resources on your Windows computers.

Creating a user call test, will not take away access from your other computers.  Giving test access will only give test access.  It won't take away from the other access you already have to your resources.

As far the error messages you showed, please ensure you have the these packages installed by running:

```

sudo apt-get install samba samba-common samba-common-bin smbfs

```

You probably already have most of that installed.  Running this command will fill in the blanks of whatever you have missing.

Oh yea, you didn't tell me the version of Windows you're running.  I tested the steps I gave you with Windows 7 for your information.

To me the cli is the easiest way to go.  But of course, I find it all easy.  If you have a problem and give me the output, I'm sure it'd be very easy for me to identify your problem.  Immediately you might not have all the needed samba components installed (as per the error message you get from the cli, which I find very intuitive) or the fact that you don't have a username and password to call from Linux.  There might be an alternate way than what I've suggested, but the method I've suggested should only take a few seconds to setup.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

