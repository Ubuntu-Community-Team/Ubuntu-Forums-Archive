---
title: "CIFS Mount with Guest Account not Work"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by shyl on 2009-03-25
My issue is that I cannot connect the Samba share drive with guest account.  The command I used is 

[COLOR="Red"][FONT="Arial"]    sudo mount -t cifs -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test[/FONT][/COLOR]

But the error I got is

[COLOR="Red"][FONT="Arial"]    mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/FONT][/COLOR]

I've also tested the connection with smbclient.  Strange is that smbclient works fine.  The command I used was:

[COLOR="Red"][FONT="Arial"]    smbclient //mybookworld/data whateverpass -U whateveruser[/FONT][/COLOR]

So my question here is that, what could possibly be the reason that the smbclient works but the mount.cifs does not?

---

### Post by shyl on 2009-03-25
Here is the info of the machine running the Samba.  It is a Mybookworld box also running Linux, but not Ubuntu.  The log info I got from it is that:

[COLOR="Red"][FONT="Arial"][2009/03/25 06:33:09, 0] smbd/service.c:make_connection_snum(773)
  make_connection: connection to data denied due to security descriptor.[/FONT] [/COLOR]

I believe the Samba service running on it, like all the other services, were trimmed to fit its memory.  And here is the excerpt of its smb.conf file:

[COLOR="Red"][FONT="Arial"][global]
server string=MyBookWorld
workgroup=workgroup
interfaces=192.168.1.117/24 127.0.0.1/8
security=user
smb passwd file=/var/private/smbpasswd
private dir=/var/private
guest account=www-data
log file=/var/log/log.%m
log level=1 auth:3
max log size=50
dns proxy=No
lock directory=/var/locks
pid directory=/var/locks
use sendfile=Yes
map to guest = Bad User
create mask = 755
map hidden = Yes
veto files = /shares/internal/.senvidData/ /shares/internal/lost+found/

[data]
   path = /dr01/data
   writeable = yes
   guest ok = yes
   browseable = yes
   create mask = 775
   directory mask = 775
   force create mode = 775
   force directory mode = 775
   force group = sambashare
   map hidden = No
[/FONT] [/COLOR]

---

### Post by dmizer on 2009-03-25
The smb.conf file is strange. I've marked the problem points:
```
[global]
server string=MyBookWorld
workgroup=workgroup
interfaces=192.168.1.117/24 127.0.0.1/8
[COLOR="Red"]security=user[/COLOR]
smb passwd file=/var/private/smbpasswd
private dir=/var/private
[COLOR="Red"]guest account=www-data[/COLOR]
log file=/var/log/log.%m
log level=1 auth:3
max log size=50
dns proxy=No
lock directory=/var/locks
pid directory=/var/locks
use sendfile=Yes
[COLOR="Red"]map to guest = Bad User[/COLOR]
```
So the share definition (not included in my excerpt above) indicates that guest is okay, but the global options indicate that guest is a bad user.

You might have success by simply removing the "map to guest = Bad User" option from the worldbook smb.conf. I'm not sure why this was included and it doesn't make much sense given the rest of the smb.conf file.

Or, try this:
```
sudo mount -t cifs -o user=whateveruser,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test
```

---

### Post by shyl on 2009-03-25
> **dmizer said:**
> The smb.conf file is strange. I've marked the problem points:
```
[global]
server string=MyBookWorld
workgroup=workgroup
interfaces=192.168.1.117/24 127.0.0.1/8
[COLOR="Red"]security=user[/COLOR]
smb passwd file=/var/private/smbpasswd
private dir=/var/private
[COLOR="Red"]guest account=www-data[/COLOR]
log file=/var/log/log.%m
log level=1 auth:3
max log size=50
dns proxy=No
lock directory=/var/locks
pid directory=/var/locks
use sendfile=Yes
[COLOR="Red"]map to guest = Bad User[/COLOR]
```
So the share definition (not included in my excerpt above) indicates that guest is okay, but the global options indicate that guest is a bad user.

You might have success by simply removing the "map to guest = Bad User" option from the worldbook smb.conf. I'm not sure why this was included and it doesn't make much sense given the rest of the smb.conf file.

Or, try this:
```
sudo mount -t cifs -o user=whateveruser,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test
```


Reply appreciated.  But it unfortunately it does not work by marking the [COLOR="red"]map to guest"[/COLOR] line.

---

### Post by dmizer on 2009-03-25
Okay, try this then:
```
sudo mount -t cifs -o user=whateveruser,pass=whateverpass,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test
```
This should be a duplicate of what you say works in smbclient.

---

### Post by shyl on 2009-03-25
> **dmizer said:**
> Okay, try this then:
```
sudo mount -t cifs -o user=whateveruser,pass=whateverpass,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test
```
This should be a duplicate of what you say works in smbclient.
No, same error.  

Client side:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

But this time it has not message on server side.  The /var/log/log.{clientname} was not changed, nor does

smbclient //mybookworld/data whateverpass -U whateveruser

work.

---

### Post by dmizer on 2009-03-25
Humm ... if you still have the "map to guest = Bad User" commented out, you might want to reinable that.

Double check to make sure you have all the necessary packages installed with this command:
```
sudo aptitude install smbfs
```

---

### Post by shyl on 2009-03-25
> **dmizer said:**
> Humm ... if you still have the "map to guest = Bad User" commented out, you might want to reinable that.

Double check to make sure you have all the necessary packages installed with this command:
```
sudo aptitude install smbfs
```
Thanks, dmizer.  I've checked and found that everything are updated.  And also I've restored the "map to guest" parameter back.

Just have done a bit more, when I used type the command:

[FONT="Courier New"]    sudo mount -t cifs [COLOR="red"]--verbose[/COLOR] -o guest,rw //mybookworld/data ~/test[/FONT]

and got the output 
[FONT="Courier New"]
mount.cifs kernel mount options unc=//mybookworld\data,ip=192.168.1.117,ver=1,rw,guest,[COLOR="Red"]user=root[/COLOR],ver=1,rw,guest
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/FONT]

So that means the *guest *parameter using mount.cifs are connecting to the Samba server via user root.  So I doubt, probably I need to change the password of the user root, in smbpasswd file to an empty value, that might make the *guest *option work.

---

### Post by dmizer on 2009-03-25
You may try disabling the unix extensions like so:
```
sudo mount -t cifs -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,[COLOR="Red"]nounix[/COLOR],noperm //mybookworld/data ~/test
```

If there any way to determine the UID and GID in your Worldbook NAS? If so, you may have luck by including them (as well as nounix) in your mount command:
```
sudo mount -t cifs -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,[COLOR="Red"]gid=###,uid=###,nounix[/COLOR],noperm //mybookworld/data ~/test
```

Also, check for (and install) any firmware updates for your NAS.

---

### Post by capscrew on 2009-03-25
> **shyl said:**
> My issue is that I cannot connect the Samba share drive with guest account.  The command I used is 

[COLOR="Red"][FONT="Arial"]    sudo mount -t cifs -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm //mybookworld/data ~/test[/FONT][/COLOR]

But the error I got is

[COLOR="Red"][FONT="Arial"]    mount error 13 = Permission denied
Refer to the mount.cifs(8 ) manual page (e.g.man mount.cifs)[/FONT][/COLOR]


The use of guest is incorrectly used in the above ***mount*** command.  In addition, I have never seen the command constucted in this manner either, but I can't say whether it will work or not.  The common construction is:
```
sudo mount -t //mybookworld/data ~/test -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm
```
I have left the guest directive in the statement, but I assure you it is incorrect usage.  BTW, you are using the variable $HOME in the mount command.  The tilde (~) is the logged in users home dir.  In this case you should use the explicit directory name(/home/<yourname>/test). 

Be aware that not all options are for command line usage.  Some are for fstab automount.  Consider what you would need to do on a password protected share that you were automounting (ie: before anyone was even logged in). This is what the term guest is used for.  
> 

I've also tested the connection with smbclient.  Strange is that smbclient works fine.  The command I used was:

[COLOR="Red"][FONT="Arial"]    smbclient //mybookworld/data whateverpass -U whateveruser[/FONT][/COLOR]

So my question here is that, what could possibly be the reason that the smbclient works but the mount.cifs does not?

Your use of smbclient isn't using the guest option and therefore succeeds.

If what you are after is mounting the share to the Linux file system without using your password then I would use a credential file.

In other posts in this thread there seems to be some confussion on what is a ***guest*** when using a Samba; in paticular the Global directives of: bad user and guest account.  I have described them here:

#  Bad user means "user not found in passwd/smbpasswd" if this occurs,
#  we will default to the guest account that we have defined
        map to guest = bad user
        guest account = smbguest

Typically the guest accout is mapped to the account **[COLOR="Teal"]nobody,[/COLOR]** but I prefer to use an account I created ie;smbguest.  Either way Samba checks the login name of the requestor (client) and comapres it to its database.  If the login is not available it declares the user a "bad user" (maybe we should think of it as a bad name user) and maps the login to the guest account.

---

### Post by dmizer on 2009-03-25
> **capscrew said:**
> The use of guest is incorrectly used in the above ***mount*** command.

I'm unsure what you mean here. I would sincerely appreciate a more detailed explanation. It's been used like that for as long as I can recall, unless I'm missing something. I'll admit that I don't use the guest option often though.

> **capscrew said:**
> In addition, I have never seen the command constucted in this manner either, but I can't say whether it will work or not. The common construction is:<snip>

There must be a howto somewhere with an odd mount configuration, but it seems to work just fine even though the options are before the directories. In your revision, you left off the cifs mount type though:
```
sudo mount -t [COLOR="Red"]cifs[/COLOR] //mybookworld/data ~/test -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm
```

---

### Post by capscrew on 2009-03-26
Dmizer,

I sure did leave the "cifs" out.  Thanks for the correction.

Let me explain my "incorrect use of guest" in the mount command statement.  First let me say that I mount a smb share using the *mount -t cifs* command via a script in my own network.  I added guest to the -o section and had instant failure, just as the OP described.

I assume also that we both agree  the mount option *guest* has nothing to do with the Samba Server guest directive.  

The -o section of the man page for mount  is worth noting:
```

 -o     Options are specified with a -o flag followed by a  comma  sepa&#8208;
              rated  string of options.  [I][COLOR="Purple"]Some of these options are only useful
              when they appear in the /etc/fstab file.[/COLOR][/I] ...
```

And continuing in the mount.cifs man pages:
```
 Options to mount.cifs  are  specified  as  a  comma-separated  list  of
       key=value pairs. It is possible to send options other than those listed
       here, assuming that the cifs filesystem kernel  module  (cifs.ko)  sup&#8208;
       ports them. [COLOR="Purple"][I]Unrecognized cifs mount options passed to the cifs vfs ker&#8208;
       nel code will be logged to the kernel log.[/I][/COLOR]

```

Finally the guest option:
```
       guest
          don&#8217;t prompt for a password

```
To my way of thinking, this means just what it says.  It does not refer to a guest account in any way.  I could have just as easily been called *[COLOR="Navy"]noprompt[/COLOR]*.

Using the references in the man pages, my conclusion is as I stated before "*_[COLOR="DarkGreen"]...not all options are for command line usage. Some are for fstab automount... [/COLOR]_*"

The guest option is to suppress the password prompt when mounting cifs shares via fstab (automount).  We can use a cred file for the same effect.  But in a large environment I think I would rather not leave cred files exposed.  Some day I will create a share and mount it via fstab with the option *guest* to see what happens.  But that is for another day.

Edit: I see another reference to my thought in the mount.cifs man pages.  See:
> password=arg 
    specifies the CIFS password. If this option is not given then the environment variable PASSWD is used. *[COLOR="Magenta"]If the password is not specified directly or indirectly via an argument to mount mount.cifs will prompt for a password, unless the **guest** option is specified.[/COLOR]*

The OP's problem was in understanding what a guest (or maybe a guest account) is.  In this case the *-o guest* (even if there were no errors) was misguided.

---

### Post by dmizer on 2009-03-26
Thank you for the clarity!

Actually, to view all valid CLI CIFS arguments, you should view the manual for mount.cifs, which does include the guest option. Logically speaking, there needs to be a way to disable password prompting when mounting open shares if you're mounting from the CLI or from /etc/fstab.

I will have to do reasarch, but it was my understanding that when using the "guest" option, the cifs mount actually does present itself as user "guest" to the server. It has been a very long time since I've researched this option so I am willing to admit that I could be wrong here.

---

### Post by capscrew on 2009-03-26
> **dmizer said:**
> Thank you for the clarity!

Actually, to view all valid CLI CIFS arguments, you should view the manual for mount.cifs, which does include the guest option.


[SIZE="2"]**Did you miss the following in my previous response?**[/SIZE]
[SIZE="2"]And continuing in the mount.cifs man pages:[/SIZE]
```


 Options to mount.cifs  are  specified  as  a  comma-separated  list  of
       key=value pairs. It is possible to send options other than those listed
       here, assuming that the cifs filesystem kernel  module  (cifs.ko)  sup&#8208;
       ports them. Unrecognized cifs mount options passed to the cifs vfs ker&#8208;
       nel code will be logged to the kernel log.

```


[SIZE="2"]Finally the guest option:[/SIZE]
```
[SIZE="2"]
       guest
          don&#8217;t prompt for a password
[/SIZE]
```




> 
 Logically speaking, there needs to be a way to disable password prompting when mounting open shares if you're mounting from the CLI or from /etc/fstab.

[SIZE="2"]**I believe I addressed that too...**[/SIZE]
[SIZE="2"]Read the previous post again.[/SIZE]

> 

I will have to do reasarch, but it was my understanding that when using the "guest" option, the cifs mount actually does present itself as user "guest" to the server. 


Users on any system are always explicitly created.  There is no user "guest" created by Samba.  There is, however, a mapping between the extant user *nobody* and the detection of a login that is not in the smbpasswd database. 
> 

It has been a very long time since I've researched this option so I am willing to admit that I could be wrong here.

But not before you poke your finger in my eye by telling me to read the man pages. ;-).  <CHIDE> I thought we were not supposed to tell others to RTFM. </CHIDE>

In the future it might help for you to document your thoughts.  As in, *I think this and here is why*, instead of just saying it must be this way.

Edit:

As a P.S. I found this statement interesting:
> "[I]Note that '-o guest' is not intended to be an instance of '-o <username>',
it's meant to specify an anonymous connection to the server with *no*
username."

[B]Steve Langasek
Debian Developer
vorlon_at_debian.org 
Tue, 15 May 2007 12:43:10 -0700
[/B][/I]

---

### Post by foresto on 2009-04-10
I was having a similar problem.  mount.cifs was failing with error 13 (permission denied) when I used -o guest, but it worked with a username and password.  This was on a share which allows guest access, as verified by the fact that smbnetfs was able to mount it as a guest just fine.  I eventually found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/98658](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/98658)

In short, try this:   -o guest,sec=none

---

### Post by capscrew on 2009-04-10
> **foresto said:**
> I was having a similar problem.  mount.cifs was failing with error 13 (permission denied) when I used -o guest, but it worked with a username and password.  This was on a share which allows guest access, as verified by the fact that smbnetfs was able to mount it as a guest just fine.  I eventually found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/98658](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/98658)

In short, try this:   -o guest,sec=none

@Foresto,

Would you try something for me?

Try this: -o sec=none  (no guest at all)

Let us know what response you get.

---

