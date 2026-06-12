---
title: "Lost In SSH"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by ubunwhat on 2012-07-12
I'm new to ssh and am having fits.  I need to pick up some files from a server and download them to my local machine.  There are some other factors but I'll just skip all of that and get to the problem.  I've had the same issue using both openssh through the terminal and using putty.

I have no problems logging into the remote server at all.  The issue comes when I try to copy the files to my local machine using scp.  I am basically trying to copy a directory - I need to migrate from one server to another and have to move old email in email boxes so I'm picking up the entire vmail directory.  Anyway, I have a folder in my home directory for this user on the local machine that is named atransfer.  I have a folder inside atransfer named mail.  So I type the command as follows...

scp -r [email]root@domain.com[/email]:/var/spool/vmail /atransfer/mail

I get a message saying that /atransfer/mail does not exist.  Okey dokey.  I tried every conceivable variation of paths and it rejected all of them.  I got frustrated and went with just "." to copy to the current directory and that worked.  Sort of.  Putty said it was successful but the vmail directory, it's subdirectories, and it's file are nowhere to be found.  I've searched the entire file system.  Nada.  I even went with ...

scp -r [email]root@domain.com[/email]:/var/spool/vmail Downloads

Again it went through each file, this time in openssh via the terminal, and said it was successful.  So, I go into Downloads and.... nothing.  They aren't there!  Again I search the entire files system.  Nope.  Nada.  Nothing.  I'm about six hours into this madness now and I really need it done very quickly.  Can anyone offer any insight into this for me?

---

### Post by drmrgd on 2012-07-12
> **ubunwhat said:**
> I'm new to ssh and am having fits.  I need to pick up some files from a server and download them to my local machine.  There are some other factors but I'll just skip all of that and get to the problem.  I've had the same issue using both openssh through the terminal and using putty.

I have no problems logging into the remote server at all.  The issue comes when I try to copy the files to my local machine using scp.  I am basically trying to copy a directory - I need to migrate from one server to another and have to move old email in email boxes so I'm picking up the entire vmail directory.  Anyway, I have a folder in my home directory for this user on the local machine that is named atransfer.  I have a folder inside atransfer named mail.  So I type the command as follows...

scp -r [email]root@domain.com[/email]:/var/spool/vmail /atransfer/mail

I get a message saying that /atransfer/mail does not exist.  Okey dokey.  I tried every conceivable variation of paths and it rejected all of them.  I got frustrated and went with just "." to copy to the current directory and that worked.  Sort of.  Putty said it was successful but the vmail directory, it's subdirectories, and it's file are nowhere to be found.  I've searched the entire file system.  Nada.  I even went with ...

scp -r [email]root@domain.com[/email]:/var/spool/vmail Downloads

Again it went through each file, this time in openssh via the terminal, and said it was successful.  So, I go into Downloads and.... nothing.  They aren't there!  Again I search the entire files system.  Nope.  Nada.  Nothing.  I'm about six hours into this madness now and I really need it done very quickly.  Can anyone offer any insight into this for me?

Try running the first SCP command, but use the whole path for both locations:

```
scp -r root@domain.com:/var/spool/vmail /home/<username>/atransfer/mail
```

I think you got the /atransfer/mail does not exist error because you created the folder in your home directory, but you told SCP to look for it under root.

---

### Post by asmoore82 on 2012-07-12
Copying whole folders (recursively) is always a little tricky. When I'm not careful, the new copy always ends up in a folder 1 level deeper than I expected.

To handle this better and to take it up to that "whole server migration" level, I would recommend rsync.

rsync will use the SSH transport by default and to pull whole folders recursively the magic switch it needs is archive mode (-a). This will also preserve all the timestamps

A rule of thumb when doing whole folders with rsync is to always include the trailing slash on both the source and destination. This makes 2 folders mirror images of each other as opposed to backing up one inside the other.

```
rsync -av root@domain.com:/var/spool/vmail/ $HOME/atransfer/vmail/
```

---

### Post by rukiaEnix on 2012-07-12
You could also try SSHFS to sync folders.

---

### Post by Lars Noodén on 2012-07-12
File managers like Nautilus and Thunar have built-in SFTP support.  So you could connect with one of those and then drag-and-drop your folders.

---

### Post by rukiaEnix on 2012-07-12
But I think he/she is working with console.

---

### Post by Lars Noodén on 2012-07-12
> **rukiaEnix said:**
> But I think he/she is working with console.

If working with the console, then it is possible to use the regular [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) client.  The command [font=Courier New]get -r[/font], when used on a directory, will get the directory and its contents.

---

### Post by ubunwhat on 2012-07-12
It really seems to be completely unable to access my local machine once I am logged into the remote machine.  I tried using rsync and got no love at all.  Specifically, I logged into the remote machine using ssh, and then tried to rsync with the folder on my local machine.  I got the same error message that I always get; folder or file does not exist.  Only this time I received a notice that mkdir failed to create the folder on root.  It's as if it's trying to run scp and rsync on the remote machine rather than to my local machine.  I'm totally baffled here.

---

### Post by rukiaEnix on 2012-07-12
OK, if you are already log in, in the remote machine you will never get to your directories of the local machine by just typing the path. You have to do like this the scp:

```

scp file user@localmachine.com:/path

```

The way I typed the command will just work if you are inside the remote machine.

---

### Post by ubunwhat on 2012-07-12
> **rukiaEnix said:**
> OK, if you are already log in, in the remote machine you will never get to your directories of the local machine by just typing the path. You have to do like this the scp:

```

scp file user@localmachine.com:/path

```

The way I typed the command will just work if you are inside the remote machine.

Except that I would have to replace "user" with my account name on the local machine, right?

---

### Post by rukiaEnix on 2012-07-12
Yes, and also the path, for the path of your directory, and localmachine.com for your hostname of the local machine or IP.

---

### Post by ubunwhat on 2012-07-12
Actually, no.  Both "user@localmachine.com" and my actual user name @localmachine.com returned the same error.  No such file or directory.

---

### Post by rukiaEnix on 2012-07-12
Are you using the user of your local machine?

Could you please post your path of the local machine and user?

Also could you post the path of the file you want to copy from the remote machine?

---

### Post by ubunwhat on 2012-07-12
Providing as much as I can....

Local Machine...

user: joe
hostname: Bubbles
path to target: /atransfer/mail

I am logging into the remote machine as root, so the first command look like this 

```
ssh root@remotedomain.com 
```

I am then prompted to give the root password, which I do.  From there my prompt reflects that I am on the remote machine as "root".  I then type the following

```
 scp -r root@remotedomain.com:/var/spool/vmail joe@Bubbles/atransfer/mail 
```

No such file or directory exists.  I have tried replacing "Bubbles" with my actual IP address and get a connection error. I've tried "joe@Bubbles.com" and get the no such file or directory error.

---

### Post by rukiaEnix on 2012-07-12
OK, try like this please inside the REMOTE machine:

```

scp -r /var/spool/vmail joe@Bubbles:/atransfer/mail

```

If it fails, change Bubbles for the local machine IP

---

### Post by ubunwhat on 2012-07-12
I just realized what a complete knucklehead I have been.  The problem wasn't with the path.  I didn't even realize the problem until I re-read what I just posted to you.  If you read it again you will see the problem right away.  I was logging into the remote machine and running scp from there.  I just need to run scp from the local machine.  Man, this is embarrassing.

---

### Post by rukiaEnix on 2012-07-12
haha no problem, things like that happen some times, but yes I realized it was a mistake of copying from the wrong place or something like that.

What I thought was that you wanted to copy stuff from the remote to the local. So I gave you the command to do it like that. :p

---

### Post by ubunwhat on 2012-07-12
I did want to copy from the remote to the local.  I still needed to run scp from the local.  Essentially what I was doing was sitting on the remote machine and telling it to copy files from itself to itself, on the destination didn't exist there.  It was as simple as this when running straight from terminal on the local machine...

```
 scp -r root@remotedomain.com:/var/spool/vmail /atransfer/mail 
```

Gravy.

---

### Post by rukiaEnix on 2012-07-12
From the local to the remote would be like this:

```

scp -r /atransfer/mail user@remotedomain.com:/var/spool/vmail

```

---

### Post by ubunwhat on 2012-07-12
Yup.  Well, thanks for trying to help.  As they say, you can't fix stupid.  Fortunately this time stupid managed to fix itself.

---

