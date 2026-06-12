---
title: "CIFS, autofs - doesn't work on 12.04, but worked on 10.04!"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by uusrs on 2012-06-08
Hello,
after unsuccessful attempts to solve the problem, I'm asking for your help!

I'm trying to mount CIFS shares from Samba server automatically using autofs.

It works with manual command:
**sudo mount -t cifs -o user=uusrs,password=passwd,uid=uusrs,gid=uusrs,file_mode=0600,dir_mode=0755 //darkstar/music /home/uusrs/@/music**

However, I can't have it mount automatically with autofs. 
I used it for several years already, and it worked on Ubuntu 10.04. I do the same on Ubuntu 12.04, and it doesn't work.

What I did:

I added the following to /etc/auto.master:
**/home/uusrs/@  /etc/auto.uusrs --timeout=60 --ghost**

I created /etc/auto.uusrs. It contains:
**music   -fstype=cifs,credentials=/etc/auto.uusrs.cred,uid=uusrs,gid=uusrs,file_mode=0600,dir_mode=0755       ://darkstar/music**

/etc/auto.uusrs.cred contains:
[B]username=uusrs
password=passwd[/B]

Also, I added a string:
**automount: nis files** to /etc/nsswitch.conf

However, when I run
**sudo service autofs start** I see autofs start/running, process 12381

but my /home/uusrs/@/music directory is empty. I checked /var/log/syslog and seen
**ypbind[925]: broadcast: RPC: Timed out.** I guess ypbind problem is not necessary the reason because manual mount command works. And exactly the same autofs settings worked on Ubuntu 10.04!

Could you please help solve the problem?

Thank you!

---

### Post by uusrs on 2012-06-11
Hello!

Maybe someone can point to a guide on how to implement auto mount of Samba shares in Ubuntu **12.04**?

Old guides do not apply because I implemented it in 10.04 but the same procedures do not work in 12.04. Maybe there is a step by step guide written specifically for 12.04?

Thank you!

---

### Post by quirino77 on 2012-06-16
I'm having similar problem on 12.04.
Same commands i used with success on 11.10 do not work on 12.04.
Now i have no autofs since i could not make it works.
Using fstab works fine, but it's not what i really want.

Still looking for a solution.

---

### Post by kalyp on 2012-07-16
I'm having the same problem, and it really is an issue for me. Anybody figured out what was wrong and how to solve it? 
Thanks!!

(I'll add that it did work on 12.04 as configured with successive upgrades. After a clean install, it's broken...).

---

### Post by redmk2 on 2012-07-16
> **kalyp said:**
> I'm having the same problem, and it really is an issue for me. Anybody figured out what was wrong and how to solve it? 
Thanks!!

(I'll add that it did work on 12.04 as configured with successive upgrades. After a clean install, it's broken...).

This may be 2 or more problems with 1 underlying root cause.  The root cause seems to be timing of the various services.  AutoFS needs networking to function and won't start without it.  The first problems in this thread deal with NIS (ypbind).  The others may be due to Network Manager.  Eithe way this is due to the change to Upstart for starting services.

See [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/958704") and [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/1007273") for Upstart bugs that are related to this.

---

### Post by kalyp on 2012-07-16
I'm not sure this is the same problem? Both seem to be linked to autofs not starting (I was not aware that autofs was linked to login issues BTW? since autofs needs to be installed manually, it shouldn't be required to log in?).

In my case, autofs is running (sudo start autofs replies that it's already running). But the location where the mounts should be is empty (as if the ghost option didn't work) and manually looking into the (possibly hidden) directories says they don't exist.


> **redmk2 said:**
> This may be 2 or more problems with 1 underlying root cause.  The root cause seems to be timing of the various services.  AutoFS needs networking to function and won't start without it.  The first problems in this thread deal with NIS (ypbind).  The others may be due to Network Manager.  Eithe way this is due to the change to Upstart for starting services.

See [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/958704") and [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/1007273") for Upstart bugs that are related to this.

---

### Post by papibe on 2012-07-16
Hi uusrs.

After a quick look to your first post, it looks like you are not using the proper syntax for the auto.uusrs file. The mount options should be on the end of the line.

Could you post both autofs files, but now using code tags so we can take a detail look at them?

Regards.

---

### Post by redmk2 on 2012-07-16
> **kalyp said:**
> I'm not sure this is the same problem? 
I was responding to your...> I'm having the same problem.If you are having a different problem then I would start a new thread.> 
Both seem to be linked to autofs not starting (I was not aware that autofs was linked to login issues BTW? since autofs needs to be installed manually, it shouldn't be required to log in?).
It's not related to login.  It is related to the order and timing of processes being brought up.  If autofs requires interfaces to be up before launching then they have to be up.  If Network Manager (for example) requires you to login before you have an interface up, then you have a problem that you need to resolve. > 

In my case, autofs is running (sudo start autofs replies that it's already running). But the location where the mounts should be is empty (as if the ghost option didn't work) and manually looking into the (possibly hidden) directories says they don't exist.
Sounds like a configuration problem.  I would start a new thread for that.

---

### Post by kalyp on 2012-07-16
It is the same problem as uusrs, who started this thread. And probably same as quirino77 as well. In particular his 
"However, when I run 
sudo service autofs start 
I see autofs start/running, process 12381
but my /home/uusrs/@/music directory is empty."
It is exactly my problem - autofs is running, with the same configuration files that used to work, but now the directory is empty. It could be a configuration problem, except that I use exactly the same files (auto.master and auto.nfs - when I say exactly I mean it, the files are on my ubuntu one and locally I only have links to those) in a different computer running 11.04, and they work just fine.

What I meant is that I am not sure the problem associated with the links you sent is the same as uusrs and mine.

> **redmk2 said:**
> I was responding to your...If you are having a different problem then I would start a new thread.

---

### Post by redmk2 on 2012-07-16
> **kalyp said:**
> It is the same problem as uusrs, who started this thread. And probably same as quirino77 as well. In particular his 
"However, when I run 
sudo service autofs start 
I see autofs start/running, process 12381
but my /home/uusrs/@/music directory is empty."
It is exactly my problem - autofs is running, with the same configuration files that used to work, but now the directory is empty. It could be a configuration problem, except that I use exactly the same files (auto.master and auto.nfs - when I say exactly I mean it, the files are on my ubuntu one and locally I only have links to those) in a different computer running 11.04, and they work just fine.

What I meant is that I am not sure the problem associated with the links you sent is the same as uusrs and mine.

Are you running NIS and mounting a home directory?  Did you look at the bug reports?

---

### Post by kalyp on 2012-07-16
OK now I feel pretty silly because it just got working again, and I have no idea how. The only thing that I changed in the last hour is starting Ubuntu One (where my configuration files are) but I was accessing them locally and even modified the files by trying to put the options at the end of the line as suggested by papibe. So that I don't get it.

I'll try to figure out if I changed anything else in between (possible as I'm reinstalling that computer). Sorry for the false problem... although I'm happy it got resolved :)


-------------------------------------
keeping my answers in case, and thanks redmk2 for helping me out: 

> **redmk2 said:**
> Are you running NIS and mounting a home directory?  Did you look at the bug reports?

I am not mounting a home directory, but several networks shares. I looked quickly at the bug reports you sent but they all seem to be about autofs not starting properly. I did google and search forums etc but didn't find any relevant issue - this thread is the closest to my problem.

I don't have ypbind/nis (not installed). I guess those are related to the ypbind error of uusrs but because (s)he said "I guess ypbind problem is not necessary the reason because manual mount command works. And exactly the same autofs settings worked on Ubuntu 10.04!" I thought there was a very good chance we had the same problem, that would have nothing to do with ypbind.

---

### Post by uusrs on 2012-07-26
> **papibe said:**
> Hi uusrs.

After a quick look to your first post, it looks like you are not using the proper syntax for the auto.uusrs file. The mount options should be on the end of the line.

Could you post both autofs files, but now using code tags so we can take a detail look at them?

Regards.

Hi papibe and everybody reading/responding to the thread. Thank you for your help!

Here is the content of /etc/auto.master:
```

+auto.master
/home/uusrs/@  /etc/auto.uusrs --timeout=60 --ghost

```/etc/auto.uusrs:
```
music     -fstype=cifs,credentials=/etc/auto.uusrs.cred,uid=uusrs,gid=uusrs,file_mode=0600,dir_mode=0755     ://192.168.1.11/music
```The directory I'm trying to mount is not a home dir. But I mounted successfully both home and non-home directories in the previous 10.04 configuration. I left only one non-home dir in the config files for simplicity.

Also, I checked description of ypbind and not sure I really need it to mount shares from this server, because all necessary information is available already in static configs and server is resolvable via DNS,

Messages like **ypbind[857]: broadcast: RPC: Timed out.** are really annoying and I prefer not to use unnecessary complexities if possible and turn off ypbind. May one do it in this config?

Thank you!

---

### Post by uusrs on 2012-07-26
Hello everybody,

I found my mistake.

After I commented "+auto.master" string in /etc/auto.master, autofs mounted the network share successfully.

Now, the corrected /etc/auto.master is:

```
/home/uusrs/@  /etc/auto.uusrs --timeout=60 --ghost

```/etc/auto.uusrs is mostly unchanged (I used DNS resolvable name of the server instead of IP address). Both methods work.

```
music    -fstype=cifs,credentials=/etc/auto.uusrs.cred,uid=uusrs,gid=uusrs,file_mode=0600,dir_mode=0755    ://darkstar/music
```**ypbind[857]: broadcast: RPC: Timed out.** still in /var/log/syslog but I plan to turn off ypbind since I do not see any need to use it in my network.

Thank you!

---

