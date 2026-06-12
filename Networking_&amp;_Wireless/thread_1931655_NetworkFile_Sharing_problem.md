---
title: "Network/File Sharing problem"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by Alan.Brown on 2012-02-25
I have 2 computers running Xubuntu 11.10 and using Dolphin as the file manager on both.   I managed to get them connected and was able to share files both ways across the network.  The setup was done automatically and was easy.

Then something went Wrong!  (Finger trouble probably!)

Now the network connections using the common WORKGROUP seem to be there but trying to access files on the remote computer gives me the files on the local computer.  The same on both computers.  I hope this makes sense.  

I need (I think) to delete the current network settings completely and get the system to re-establish the network from scratch.  I can't see where WORKGROUP is setup and whether I can change it.

Any help please?

Alan

---

### Post by bab1 on 2012-02-26
> **Alan.Brown said:**
> I have 2 computers running Xubuntu 11.10 and using Dolphin as the file manager on both.   I managed to get them connected and was able to share files both ways across the network.  The setup was done automatically and was easy.

Then something went Wrong!  (Finger trouble probably!)

Now the network connections using the common WORKGROUP seem to be there but trying to access files on the remote computer gives me the files on the local computer.  The same on both computers.  I hope this makes sense.  

I need (I think) to delete the current network settings completely and get the system to re-establish the network from scratch.  I can't see where WORKGROUP is setup and whether I can change it.

Any help please?

Alan

Alan,

I have to assume you are using Samba to share files between these hosts.  I use Gnome, but the basics should be the same on your installation.

If you configured the shares manually you must have edited the /etc/samba/smb.conf file.  This is where you set the WORKGROUP and at the least defined the shares on either or both hosts.

I believe the app Gigolo provides the Gnome libs to allow you do define Samba usershares.  These shares are defined by non-root users with a GUI interface.  The usershares definitions are located at /var/lib/samba/usershares.

Do you have Gigolo installed?  Did you define the shares with a GUI interface (Right Click >> etc, etc)?

Ring any bells?

---

### Post by Morbius1 on 2012-02-26
Take one machine and post the output of the following commands so we can see how it's set up:
```
testparm -s
``````
net usershare info --long
``````
smbtree
```

---

### Post by Alan.Brown on 2012-02-26
@bab1

I followed the advice in

[http://ubuntuforums.org/showthread.php?t=1930914&highlight=file+share](http://ubuntuforums.org/showthread.php?t=1930914&highlight=file+share)
[http://ubuntuforums.org/showthread.php?t=1930381](http://ubuntuforums.org/showthread.php?t=1930381)

I am using Samba and have set up both computers using Gigolo.  All directories to be shared have been set using **Right Click >> etc, etc** on both computers :)

Naming the computers as A and B I have the following.   On B I have full read/write access to all files on the shared directories on A (using both Dolphin and Thunar).   This is what I want.

On A, B does not show so there is no access to shared files.

On A - **smbtree** shows the network name (WORKGROUP) and the host name of A.

On B - **smbtree** again shows the network name but _**shows the host name of A**_. I think this should be the host name of B - and is the reason why A cannot see B.  How can I change this so that **smbtree** shows the correct hostname for B?

The **hostname** command shows the correct hostnames on both computers.

Also on B there is no entry for the directories to be shared as there is on A.

On B I can use the printer connected to A.

@Morbius1

The output from the commands you suggested seem OK except for the hostname of B as mentioned above.

Thank you both for your replies.

Alan

---

### Post by bab1 on 2012-02-26
> **Alan.Brown said:**
> @bab1

I followed the advice in

[http://ubuntuforums.org/showthread.php?t=1930914&highlight=file+share](http://ubuntuforums.org/showthread.php?t=1930914&highlight=file+share)
[http://ubuntuforums.org/showthread.php?t=1930381](http://ubuntuforums.org/showthread.php?t=1930381)

I am using Samba and have set up both computers using Gigolo

Naming the computers as A and B I have the following.   On B I have full read/write access to all files on the shared directories on A (using both Dolphin and Thunar).   This is what I want.

On A there is no connection to B so there is no access to shared files.

On A - **smbtree** shows the network name (WORKGROUP) and the host name of A.

On B - **smbtree** again shows the network name but _**shows the host name of A**_. I think this should be the host name of B - and is the reason why A cannot see B.  How can I change this so that **smbtree** shows the correct hostname for B?

The **hostname** command shows the correct hostnames on both computers.

@Morbius1

The output from the commands you suggested seem OK except for the hostname of B as mentioned above.

Thank you both for your replies.

Alan

The command *smbtree *should show the same info from **BOTH** hosts.  It is the display of all the shares available (on all hosts).  

If you don't have anything displayed for **Host B** then I would assume that the Samba daemons (smbd and nmbd) are not running on that host.

From **Host B**; what output do you get from```
pgrep -l mbd
```

I get this```
$ pgrep -l mbd
992 smbd
1065 smbd
1139 nmbd

```
The numbers may vary.  These are the process numbers.  You should have at minimum 2 smbd and 1 nmbd daemons running.

If the daemons are NOT running you can restart them like this ```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by Morbius1 on 2012-02-26
I'm working in the dark since I have no output to work with and it;s the end of the day for me so I'll just throw out some random things:

On both A and B:

** Make sure samba services are running:
```
sudo service smbd status
sudo service nmbd status
```If any are not running start them:
```
sudo service smbd start
sudo service nmbd start
```** Make sure bcast is first in how samba converts host names to ip addresses:
```
name resolve order = bcast host lmhosts wins
```Put that line in the right under the workgroup line in /etc/samba/smb.conf
Then restart samba:
```
sudo service smbd restart
```** I don't care if the hostname is correct what's important is how long is it. If it's 16 characters or more in length then it's invisible to everyone else. So fix it by adding another line in the [global] section of smb.conf:
```
netbios name = whatever
```"Whatever" has to be 15 characters or less in length. Then restart smbd again.

Oh and turn off your firewalls if you've done anything with it.

It's possible that there is something wrong with smb.conf itself but without testparm we'll never know.

[COLOR=Blue][B]
EDIT:[/B][/COLOR]  Overlap there. Sorry bab1.

---

### Post by Alan.Brown on 2012-02-26
OK - thanks again for your replies.

I had edited smb.conf on both computers with **netbios name = StarNet**.

I have changed computer B to **netbios name = MoonNet**.  A stays the same as before.

Now everything works well both ways - problem solved!

Thanks again.

Alan

---

### Post by bab1 on 2012-02-26
> **Alan.Brown said:**
> OK - thanks again for your replies.

I had edited smb.conf on both computers with **netbios name = StarNet**.

I have changed computer B to **netbios name = MoonNet**.  A stays the same as before.

Now everything works well both ways - problem solved!

Thanks again.

Alan
Right!  The netbios name identifies the individual host.  Just imagine what it would be like if everyone was named Alan.  ;-)

---

### Post by Alan.Brown on 2012-02-27
How dare they!!  I am unique!!!'


:)

Alan

---

