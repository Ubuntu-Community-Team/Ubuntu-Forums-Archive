---
title: "Brother MFC-7860DW Drivers - Sudo issue?"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by Sunrise611 on 2012-12-03
I am trying to install the printer drivers for the Brother MFC-7860DW wireless printer as per the instructions on Brother's site that was confirmed by Jaimie on this forum at: [http://ubuntuforums.org/showthread.php?t=1854483&page=2](http://ubuntuforums.org/showthread.php?t=1854483&page=2) who has the same specs as me (Ubuntu 11.10 64 bit and the same printer) and successfully installed them.

I am starting a new thread so that this will hopefully not get lost in the shuffle or get buried deep in the other thread.

Anyway, when I entered the following command in the Terminal to install the first driver, I received an error about the sudo password.  (The command was altered slightly to remove personal information.)

> me@d-Vostro-2520:~$  sudo dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
[sudo] password for (regular user):
(regular user) is not in the sudoers file.  This incident will be reported.
me@d-Vostro-2520:~$  sudo dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
[sudo] password for (super user):
Sorry, try again.

I tried entering both my super (admin) and regular password but neither was accepted.  Both User accounts still appear in my User directory so they exist.

How do I get past this?  I am a newbie and not used to entering commands in the Terminal.

---

### Post by Isamu715 on 2012-12-03
Is this (regular user) the only user except root? If it was not the first user created on the system it's possible that (regular user) is not in *sudoers* file. Swtch to an administrator type user and in *"User accounts"* settings change the (regular user) account type from *"Regular"* to *"Administrator"*.

To use the *sudo *command a user needs to be in the *sudo *group, you can check a user's group membership by running:
```
groups (regular user)
```If (regular user) is the only no-root user on the system boot into recovery mode(an option in GRUB) so you can get into a root terminal. From the root terminal execute the following command:
```
gpasswd -a (regular user) sudo
```This should add (regular user) to the *sudo* group.

---

### Post by Sunrise611 on 2012-12-03
> **Isamu715 said:**
> Is this (regular user) the only user except root? If it was not the first user created on the system it's possible that (regular user) is not in *sudoers* file. Swtch to an administrator type user and in *"User accounts"* settings change the (regular user) account type from *"Regular"* to *"Administrator"*.

To use the *sudo *command a user needs to be in the *sudo *group, you can check a user's group membership by running:
```
groups (regular user)
```If (regular user) is the only no-root user on the system boot into recovery mode(an option in GRUB) so you can get into a root terminal. From the root terminal execute the following command:
```
gpasswd -a (regular user) sudo
```This should add (regular user) to the *sudo* group.

Thanks for your reply.  I created two accounts.

One is an admin account that I do not use.  The second is a regular account that I do use.  When I installed the pinter drivers from Brother, i entered my admin password.

So, I do not know why the terminal is not recognizing the admin account.  :(

---

### Post by pdc on 2012-12-03
you are running a very similar thread.........on installing a Brother ? I have just replied to it ..........................

---

### Post by Sunrise611 on 2012-12-03
> **Isamu715 said:**
> Is this (regular user) the only user except root? If it was not the first user created on the system it's possible that (regular user) is not in *sudoers* file. Swtch to an administrator type user and in *"User accounts"* settings change the (regular user) account type from *"Regular"* to *"Administrator"*.

To use the *sudo *command a user needs to be in the *sudo *group, you can check a user's group membership by running:
```
groups (regular user)
```If (regular user) is the only no-root user on the system boot into recovery mode(an option in GRUB) so you can get into a root terminal. From the root terminal execute the following command:
```
gpasswd -a (regular user) sudo
```This should add (regular user) to the *sudo* group.

Thanks for your reply.  I created two accounts.

One is an admin account that I do not use.  The second is a regular account that I do use.  When I installed the pinter drivers from Brother, i entered my admin password.

So, I do not know why the terminal is not recognizing the admin account.  :(

---

### Post by Isamu715 on 2012-12-04
So you only have two accounts - root and (regular user). Post the output of:
```
groups (regular user)
```
Also try loging into the root account directly with:
```
su
```
and entering your admin password.

---

### Post by Sunrise611 on 2012-12-11
I am still stuck on this issue.  

As soon as I got the computer, I created two accounts.  One is an admin account that I do not use and the other is a regular account with lesser privileges that I do use.  I am the only one using the computer so there is just one regular user.

I am trying to install the printer drivers from within my regular user account.  

When I type **sudo** and the command to install the printer driver, the computer responds by asking for rmy *regular* account's password instead of the admin password.  

When I enter the regular user password, it fails and says "try again" and when I enter the admin password, it says it's not recognized (or something) and "will be reported".  

I was able to log into the admin account with my admin password from the start menu (graphical menu).  (I did not try entering ****su in the Terminal from within my regular account.)

So, that is my **sudo** account, right?  I should be able to use that password in my regular account to grant privileges.  

Should I be attempting to install the printer driver directly from the admin account instead of the user account?  That would not be desirable since the printer is wireless and would have to be online and leave my admin account vulnerable.

Isamu ... when you say to type:  groups (regular user) does that mean to type that exactly as is or do I type groups (regular user name)?   

This is harder than it should be.  :(

---

### Post by Isamu715 on 2012-12-12
> When I enter the regular user password, it fails and says "try again"  and when I enter the admin password, it says it's not recognized (or  something) and "will be reported".  This means your (regular user) is probably not in the *sudo *group. Check with the *groups* command to make sure.
> Isamu ... when you say to type:  groups (regular user) does that mean to  type that exactly as is or do I type groups (regular user name)?   I mean the user name, so that if your username is *john*, you would type:
```
groups john
```Post the ouput of this command.

---

### Post by Sunrise611 on 2012-12-12
Thanks for your quick response and assistance.   Here is the output.  

> 
me2@me-Vostro-2520:~$ groups Me2
groups: Me2: No such user
me2@me-Vostro-2520:~$ groups me2
me2 : me2
me2@me-Vostro-2520:~$


me2 = regular account
me = admin account

I tried entering my regular account in uppercase and it didn't work so then I tried it with the lowercase and it just repeated what I wrote (me2).  Nothing else.

Is that okay?

---

### Post by Isamu715 on 2012-12-12
It appears your user accounts are misconfigured. This is how it looks on my system:
```
[ isamu: ~ ]$ groups isamu
isamu : isamu adm cdrom sudo dip plugdev lpadmin sambashare
```Notice how the user is in the *sudo* group, this is necessary to use sudo. To add your user to a group use *gpasswd.* In your case it should be:
```
gpasswd -a me2 sudo
```The above command needs to be run as root. Root is the actual admin account, the user that can do anything, it's present on every system. To log in as root use:
```
su
```and enter your admin password.

It seems strange that your user is only in it's own group. When creating new user Ubuntu automatically assigns user to groups to allow some basic tasks. See my *groups* output at the top, I'm in several groups and I didn't add any of them manually, this is the default.

---

### Post by Sunrise611 on 2012-12-12
That is odd.  I just did what I did in Windows and created a new user account from the User section and that was the admin account.  Then I added the regular user account.  I don't know why that can't be done properly using the graphical interface in the User area the way that I did.  I prefer not to rely on commands too much.

I will try your recommendation tomorrow.  

First I will  to type **su** and then enter the admin password and then the gpassword  the way that you posted it.  

Hopefully it will accept my admin password for this function from within my regular user account.

I will post the results - hopefully success!

---

### Post by Sunrise611 on 2012-12-17
Okay, I finally got the sudo issue resolved, thanks to your help.  I wasn't able to do su or sudo from within the regular User account so I had to log in to the admin account.  

Then at the command prompt, I entered: **sudo gpasswd -a me2 sudo** (the last sudo is the name of the group that I wanted to join).   Then I hit enter and it added the sudo group to my regular User account (me2). 

So, when I typed: me2 groups, sudo appeared. 

Then I had to do that separately for each group that I wanted to join.  It would not let me join multiple groups together.  I joined: adm cdrom plugdev lpadmin sambashare

So, to add the adm group to the me2 account, I entered: **sudo gpasswd -a me2 adm**

There is also dialout and admin in the admin groups but I didn't add those to the regular account at this time.  Not sure what those are or if I'll need them.

---

