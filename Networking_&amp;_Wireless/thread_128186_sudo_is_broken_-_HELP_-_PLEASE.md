---
title: "sudo is broken - HELP - PLEASE"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by diablozx9 on 2006-02-10
I can't upgrade and believe the problem may be affecting some apps.

When I try to use SUDO ( sudo apt-get update ) I am propted for a password
  I enter it,,, then I get the following:
 E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)

When I try to use the " System - Administration - Update Manager " I am probpted for a password,,, I enter it,, the widow flashes up for a second , then, gone...

---

### Post by Mustard on 2006-02-10
Can you enter this command in terminal and paste the output in here please?

```
sudo whoami
```

I'm looking for a clue in the error messages as to what might have happened to your sudo functions.

---

### Post by diablozx9 on 2006-02-10
Oh crap,,, before I saw your post,, I tried another posting (at another site) which may have made it worse (I will stop trying now,, except for input from this site).

I editted Sudoers through Alt-Ctl-F1 at login screen,,, I thought I returned it to normal but now,,,

When I enter the " sudo whoami " you suggested,,, I get:

>>> sudoers file: syntax error, line 0 <<<
sudo: parse error in /etc/sudoers near line 0


Please,, get me through my retardation.

---

### Post by Mustard on 2006-02-10
ok..well now that your /etc/sudoers file is misconfigured, you are going to have to get to a root prompt so you can edit it again.  The easiest way to do that is to boot up in 'recovery mode'.  This is in your grub menu when you first start up.  When you get to the root prompt in recovery mode, you can use this command below to edit your /etc/sudoers file.

```
visudo
```

The visudo commands one and only purpose is to edit the sudoers file.  Your sudoers file should look something like this..

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
mustard ALL=(ALL) ALL
```

The only line you need to change is the final line.  Note that the example above uses my username.  Just subsitute your own username for mine.  Some systems set up and 'admin group' and add users to the admin group so they can have sudo priviliges.  In this situation you usually have an entry in your sudoers file showing '%admin' if the name of the group is 'admin'.  Its fine just to use your username though.

---

### Post by diablozx9 on 2006-02-10
OK,,, Done...
Mine looks a little different than the one you provided.

Yours looks like :

# User privilege specification
root	ALL=(ALL) ALL
mustard ALL=(ALL) ALL

Mine is different:

# User privilege specification
root	ALL=(ALL) ALL

# Members of the administration group ....
%admin ALL=(ALL) ALL

---

### Post by Mustard on 2006-02-10
[QUOTE=diablozx9]OK,,, Done...
Mine looks a little different than the one you provided.

Yours looks like :

# User privilege specification
root	ALL=(ALL) ALL
mustard ALL=(ALL) ALL

Mine is different:

# User privilege specification
root	ALL=(ALL) ALL

# Members of the administration group ....
%admin ALL=(ALL) ALL[/QUOTE]


Yeah..as I mentioned in my post above, some systems are set up with the sudoers file referring to an admin group, using the syntax '%admin'.  What this means is that if a user is a member of the the group called 'admin' then they have sudo privileges.  You can keep the reference to %admin in your sudoers file, and make sure you are in the 'admins' group, or you can just add an extra line which specifically references your username like mine does.  Having and entry for '%admin' and a user specific entry as well is not a problem.

So now that you have done that is sudo working or are you still getting problems?

---

### Post by diablozx9 on 2006-02-10
Thanks for your help so far,,, please continue...

I added my user to the bottom of the file.

Rebooted and tried The - sudo apt-get update
command again only to get:

>>> sudoers file: syntax error, line 0 <<<
sudo: parse error in /etc/sudoers near line 0

---

### Post by Mustard on 2006-02-11
[QUOTE=diablozx9]Thanks for your help so far,,, please continue...

I added my user to the bottom of the file.

Rebooted and tried The - sudo apt-get update
command again only to get:

>>> sudoers file: syntax error, line 0 <<<
sudo: parse error in /etc/sudoers near line 0[/QUOTE]

Your sudoers file still has an error in it.  It's possible that when you saved the file it didnt save to the correct filename.  I would double check what filename you save it as when you edited it again using visudo. When I have used visudo to edit my sudoers file, I have noticed that when I went to save it, it said it was going to save it as 'sudoers_temp' or something like that.  If you find that this is the case for you to, then I would alter the file name its asking to save it to, to just 'sudoers'.

If you could paste your current sudoers file in here it would be helpful too, as it says the error is in line 0 which sounds like its pretty early in the file.  Probably the first line that doesnt have a '#' character in front of it.  To send a copy of your sudoers file to your desktop via command line, you could do this when you are logged in as root....

```
cp /etc/sudoers /home/yourusername/Desktop/
#substitute your username for the part in the above command that says 'yourusername'

```

Then you would need to change the ownership of the file (while still in root), so you could see it and view it on Desktop. I just realised this after testing my above command.  The file was not visible on Desktop and its own by root. :)

```
chown username.username /home/yourusername/Desktop/sudoers
#substitute your username where applicable in the above command
```

That should put a copy of the sudoers file on your Desktop, so you can paste the contents into this thread.

---

### Post by diablozx9 on 2006-02-11
I didn't include SUDOERS file because You provided enouph info that I was able to fix it.

1) I had accidently UN-commented the first line.
2) I was saving changes to TEMP file

Now that file seems to be good (THANK YOU) but, now I only have my initial problem.

I added my user to Root but still get errors as follows.

> sudo apt-get update

E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)

---

### Post by bscbrit on 2006-02-11
Well it appears that your sources.list is either missing or corrupt.  If it exists, can you please post a copy of it here.  If it doesn't exist let me know and we will start to recreate one for you.  If we do recreate one, we will need to know where you are or, more correctly, from which region you want to source your repositories.

Why do you get an 'E:' before you error message?  Is it a prefix for an error message, have you actually named a drive 'E:', or am I being stupid?

---

### Post by diablozx9 on 2006-02-11
The "E:" in the error was just there. I have no drive named "E".
Yet another mistery in my mind.

The contents of the " apt " directory are :
directory - ap.conf.d
file - secring.gpg
file - sources.list.backup
file - sources.list.save
file - sources.list_backup
file - trustdb.gpg
file - trusted.gpg

Help ( and thanks again to all who have helped ) !

---

### Post by bscbrit on 2006-02-11
Try 

sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list

to get you back with a working synaptic / apt system.

Presumably there were some changes to sources.list (hence the backup) which might be lost but you can probably remember what you changed in the file.


EDIT Regarding the E:, I was probably being stupid but I haven't seen that on error messages before. 8)

---

### Post by diablozx9 on 2006-02-11
Thanks...

That seems to have got me past another issue.
Updating via command line and Update Manager now function BUT with errors.

One problem at a time I guess.

Thanks to everyone who got me through these errors...
You guys were quick and very helpfull.

---

### Post by bscbrit on 2006-02-11
If you are updating from the command line run

sudo apt-get update

to correct the contents of your repos.

See you on the forums.  :D

---

