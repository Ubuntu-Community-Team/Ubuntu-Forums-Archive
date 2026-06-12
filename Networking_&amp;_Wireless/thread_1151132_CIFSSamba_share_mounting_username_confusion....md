---
title: "CIFS/Samba share mounting username confusion..."
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by gradysghost on 2009-05-06
Sorry for the long post, but I just wanted to make sure I gave as much detail as possible.

I recently did a clean install of Jaunty on my laptop.  I had this working before in Intrepid, but as I recall, I had a ton of trouble doing it then, too.  Eventually, though, in Intrepid, I was able to condense this action into a script and set it to a panel launcher icon to mount all three of my media shares on my server (but that's neither here nor there).

Problem:  I have a server running Ubuntu Intrepid at the moment.  Samba is set up to share out three folders, all of which reside in my home folder on the server.  The smb.conf is as follows (with useless comments removed):

```

#======================= Global Settings =======================
[global]
   workgroup = BAMF
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

    usershare allow guests = yes

#======================= Share Definitions =======================

[video]
    comment = Video files
    read only = no
    locking = no
    path = /home/ryan/Videos
    guest ok = yes

[music]
    comment = Music files
    read only = no
    locking = no
    path = /home/ryan/Music
    guest ok = yes

[pictures]
    comment = Pictures
    read only = no
    locking = no
    path = /home/ryan/Pictures
    guest ok = yes

```

So I will do something like this to mount the video share:

```
sudo mount -t cifs //192.168.0.123/video /media/video -o user=<myusername>,pass=<mypassword>
```

It fails out with Error 13: Permission denied.  192.168.0.123 is the static, internal IP address of my server, which is running and pingable.  <myusername> is the username on the remote server where the Samba shares are hosted.  <mypassword> is the password of that remote host.

Here's where it gets interesting.  I'm sitting in my living room on my laptop, which is wirelessly connected to the same router that the server is on.  When I set this thing up, I used the same username/password combination as on my server -- it's my standard user/pass MO, if you will.  So this complicates things a bit.  Here are some test cases I've run:

Logged in on laptop as "ryan" (which is the same username as on my server) && mounting with -o user/pass parameters:
Permission denied.

Logged in on laptop as "ryan" && mounting with no -o parameter at all:
Asks for my password.  Provide the password that is identical on both the laptop and the server.
Successfully mounted.

Logged in on laptop as "jenny" (my wife's account) with her password (which is identical to mine) && using -o user/pass parameters:
Permission denied.

Logged in on laptop as "jenny" && using no -o parameter at all:
Successfully mounted

Logged in on laptop as "ryan" or "jenny" and using the -o credentials=/root/.creds option, where /root/.creds reads:
username=ryan
password=<mypassword>
Result: permission denied

It basically seems that any time I try to pass a username of any kind along I get a permission denied error.  But if my smb.conf is allowing guest users, why is it even prompting me for a password when I do **not** pass a username?  Shouldn't it just connect me?  And why is it that the script that I used under Intrepid that I was able to make work no longer works (I directly copied the file, along with my entire home directory)?

Should I enable security = user?  I wanted it to also work for guest accounts if friends came over who do not have accounts on my server (there is only my account there, and root).

Just to rule things out, my server is obviously properly equipped to serve up these shares because I am able to get a successful connection when mounting as long as I don't pass along a username.  My laptop from which I am connecting has all the necessary SMB packages installed, including:

smbclient
smbfs
samba
samba-tools
libsmbclient
libsmbios2
python-smbc

Is there something I'm missing?

---

### Post by gradysghost on 2009-05-10
Bump.

Also, the Samba logs don't show anything important or indicative.  I suppose I could bump up the logging level for a short period of time to see if that changes...

---

### Post by capscrew on 2009-05-10
Have you added ryan or jenny to the smbpasswd file?

---

### Post by gradysghost on 2009-05-10
No, that's a good point.  Thanks for that.  I'll do that now (at work, have remote access), but will have to verify when I get home.

---

### Post by capscrew on 2009-05-10
The reason I asked is that samba will compare the logged in user with it's own data base.  This does not prevent you from connecting as you have seen.  It does however help it determine if you are "guest" or not.

I'm sure that if you look at files created when connected before that they are owned by... Hmmmmm, you haven't defined that in your smb.conf file.  The reference to```
 map to guest = bad user

```should be followed by a definition.  Such as:```
 guest account = nobody
```
A "bad user is just a user that is not in the smbpasswd data base ie: anonymous.  So if Samba can't determine who the user is then it must be a "bad user" and a bad user mapped to a guest account.

---

### Post by gradysghost on 2009-05-11
You, sir, are a genius.  The funny thing is that I am well aware of smbpasswd and how all of that operates, but I just assumed that I had already done it.  Consider this case closed.

For anybody who comes across this thread, here's the deal (and much of this is regurgitated from what capscrew already mentioned).

My Samba shares are pretty much defined correctly.  They allow for guests, but I want to actually authenticate when I connect using my username.  Samba keeps a separate database to store separate user accounts.  In this way, you don't need to have an actual logon account to Linux, only one for Samba shares.  Handy.  The problem is that I never defined myself as a Samba user.  Here's how to fix it:

```
smbpasswd -U <YourUserName>
```

You'll be asked for your password, and then you're done.  Thanks again, capscrew!

---

### Post by capscrew on 2009-05-11
Glad I could be of assistance.  I'm not sure what you have setup on your system and what ever works, is fine by me, but > smbpasswd -U is incorrect for what I suggested.

First your must be a user on Samba server.  You don't need to have a home directory or a defined shell, but you must be a user (basically like the user "nobody").

At this point you should add this user to the smbpasswd data base with the incantation```
sudo smbpasswd -a <username>
```

After adding the user it should be enabled using ```
sudo smbpasswd -e <username>
```

See [**[COLOR="Blue"]here[/COLOR]**]("http://www.comptechdoc.org/os/linux/manual4/sambausers.html") for the same idea.

In the end if what you did worked, then great.

---

