---
title: "Connecting to AFP shares"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by walletmender on 2008-12-14
Hi all,

I've been trying to connect to AFP shares on a macbook running Leopard from my macbook running Ubuntu 8.10.
So, after some searching on the internet, I chose to install 'afpfs-ng' (0.8.1). I read somewhere that it needs libfuse-dev and libgcrypt to run, so I installed those first, but when I tried 'sudo make install' on afpfs-ng, it returned errors (see attached files). the command afp_client doesn't work either.

I ran the following commands
./configure
sudo make install 2> make-install-errors.txt

I attached a file containing the errors during make install.

Does anyone know how to get it working?

Thanx

---

### Post by nixscripter on 2008-12-14
I haven't had good luck with AFP or that particular utility.

I would suggest instead using NFS to share the files. Instructions for setting up an NFS server on your Mac can be found here: [http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html](http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html)

Hope this helps.

---

### Post by walletmender on 2008-12-17
Thanx for your quick reply, but it's not going to work in my case, since the Leopard machine is my sister's, and she doesn't like me messing around with her computer. I did try SMB sharing (since that's a leopard builtin function, though, but that didn't work either. It keeps saying I can't connect, and I can't find a way to enter a username and password to login to the machine SMB-wise.
Any thoughts on that?

---

### Post by nixscripter on 2008-12-18
If she wouldn't allow you to set up an NFS server, I would suggest that you might want to give SMB another shot. If you think the problem is with your Ubuntu machine on the client side, you might want to look into a very long post that looks promising:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by alexthepuffin on 2008-12-22
I wrote afpfs-ng, so I can probably help.

Building afpfs-ng requires first installing the readline development libraries, you should do that first.

Did you try the prebuilt afpfs-ng debian package?

- A

---

### Post by alexthepuffin on 2008-12-22
What were your problems with afpfs-ng?  I'd like to make sure it works, so your feedback is appreciated.

---

### Post by walletmender on 2008-12-26
> **alexthepuffin said:**
> I wrote afpfs-ng, so I can probably help.

Building afpfs-ng requires first installing the readline development libraries, you should do that first.

Did you try the prebuilt afpfs-ng debian package?

- A

I do not recall manually installing any 'readline development libraries' and I was not aware of the existence of a debian package, I would have tried that first (way easier).
So: I've been looking on the internet for the readline libraries and I found a package called ['libreadline5-dev']("http://packages.ubuntu.com/search?lang=nl&keywords=libreadline5"), and installed it.
Also, I searched for a prebuilt Debian package of afpfs-ng and I found [this]("http://sourceforge.net/project/showfiles.php?group_id=179882&package_id=208206&release_id=582751") on sourceforge that looked promising. I downloaded the .deb one, but it didn't install, (wrong architecture 'i386', I have Core2Duo).

So after installing libread5-dev, I tried building the platform independent package again, but no success.

I attached a file with errors during 'make install'.

Thanks for the help.

--
walletmender

PS @nixscripter:
I haven't had much time at all last week, so I haven't had time to check out the link you posted. But thanks anyway and I'll be doing that later on, if there's really no hope for the AFP way.

---

### Post by alexthepuffin on 2008-12-27
You need to install autoheader and autoconf to your system, and then rebuild.

---

### Post by nixscripter on 2008-12-28
Do you have the **build-essential** package installed? I think that should include both of those, but I'm not sure.

---

### Post by blackhornet on 2009-01-16
> **walletmender said:**
> I downloaded the .deb one, but it didn't install, (wrong architecture 'i386', I have Core2Duo).

So after installing libread5-dev, I tried building the platform independent package again, but no success.

I attached a file with errors during 'make install'.

I had the same problems (running Intrepid on an amd64). Ubuntu rookie here. I made sure the following were installed:

libfuse-dev libreadline5 libreadline5-dev build-essential libgcrypt11-dev libgmp3-doc libmpfr-dev libgcrypt11 libgcrypt11-dbg libgmp3-dev libgmp3c2 fuse-source

then recompiled and voila! Overkill, probably, but I was trying everything until I saw this about the readline libs.

I even installed curlftpfs to make sure that I didn't miss a fuse dependency, but I should have known that shouldn't have been a problem because sshfs should have already been installed. But I didn't know what I needed to install for building rather than just installing. 

As far as connection options, an earlier poster was right - you could also connect to the Mac using nfs or smbfs or even sshfs.

I haven't tried ftpfs yet. I also haven't tried to put this into the fstab according to the instructions on [this page]("http://alexthepuffin.googlepages.com/")

---

### Post by tehk on 2009-01-19
running intrepid (8.10) on AMD64 and built afpfs-ng from source, all that was needed was to use synaptic first to install the fuse dev packages and readline... then it configured/made with no errors...

However, when I try to mount a share from my Apple Time Capsule (and I've tried every imaginable URL and mount option) I'm greeted with the following message:

```
Mounting 192.168.0.17 from User on /mnt/TimeMachine
Could not pick a matching UAM
```

Any ideas here?

---

### Post by logopolis on 2009-01-21
It has been difficult to find folks in the same situation because usually it's a question of having Time Machine backup to Ubuntu, or use samba to keep files in Ubuntu. I will share my progress and hope it is helpful.

I have had luck with Alex's afpfs-ng. I run Intrepid Server on a Dell desktop, and also a test environment using Parallels in OS X Leopard. My Time Capsule is on the LAN, and is also my router. The Dell connects via ethernet cable, and the Mac connects wirelessly. The purpose for mounting my Time Capsule in Ubuntu is not to park files so much as it is for running scheduled backup scripts via a command-line utility (rsync or dirvish). I can mount it in Ubuntu using either CIFS or afpfs-ng. I have recently decided to give AFP another shot after getting stuck on some permission and write issues with CIFS.

With AFP, I can mount the drive using the following command:

```
mount_afp afp://username:password@host/timecapsulevolume /mountpoint
```

Or in fstab:

```
afpfs#afp://username:password@host/timecapsule volume /mountpoint fuse user=adrick,group=fuse 0 0
```

Where your username and password are for the Time Capsule disk, depending on whether or not you allow disk access with accounts, the Time Capsule password or a disk password. You host is either what you choose when setting up time capsule (i.e. Bill Bixby's Time Capsule.local), your local IP address for the TIme Capsule, or if you allow WAN access you can use your domain name or IP address. Your Time Capsule Volume would be the name of the Time Capsule disk. The user and group in the fstab entry are for the Ubuntu user mounting the share.

More information about this can be found on Alex's page:

[http://alexthepuffin.googlepages.com/]("http://alexthepuffin.googlepages.com/")

I have tried both CIFS and AFP, and AFP thus far has required less intimate time with configuration files and mount procedures than CIFS. Once setup mounting and unmounting is a breeze.

In your case I would recommend having a look at /etc/netatalk/afpd.conf to make sure you have a line at the end of the file looking something like:

```
- -transall -uamlist uams_randnum.so,uams_clrtxt.so,uams_dhx.so -nosavepassword -advertise_ssh
```

The important part is it pertains to mounting your Time Capsule to to make sure you have uams_dhx.so in that line.

By the way, once I started having success I decided to make the configuration more permanent by removing the Time Capsule drive, plugging it into my Mac, and then partitioning it to create a separate, non-journaled HFS file system for Ubuntu. That way I don't have Time Machine on my Mac fighting with Ubuntu for space. Here is an article to show you how if you end up going that route:

[Teardown: a look inside Apple's Time Capsule backup appliance]("http://www.appleinsider.com/articles/08/03/06/teardown_a_look_inside_apples_time_capsule_backup_appliance.html")

---

### Post by tehk on 2009-01-24
Thanks for the reply logopolis, but I'm not using netatalk. I previously posted that I built afpfs-ng from source, hence there is no afpd.conf file to speak of. If there should be one, I couldn't find anything about the need to create it in the afpfs-ng documentation...

---

### Post by logopolis on 2009-01-25
When I downloaded afpfs-ng, I also picked up the patched Netatalk from the Sourceforge page. Though you built yours, there may be a dependance on some of the Netatalk components.

[Patched Netatalk]("http://sourceforge.net/project/showfiles.php?group_id=179882")

---

### Post by tehk on 2009-01-26
I don't think the afpfs-ng package is dependant on the netalk package because it configures and builds without asking anything about netatalk being there. I did however attempt to test afpfs-ng mounting my Time Capsule both with and without netatalk installed on my machine with the same results, it gave me the UAM errors. 

I'm actually not enjoying the tremendous amount of trouble here to get this accomplished and have decided to wait for a 64bit package of afpfs-ng before I will attempt to use it again. 

In the meantime I'm going to go down the samba route towards accessing my Time Capsules share as it easily mounts in windows today.

However, if a 64bit debian package becomes available, please post on this thread as I will continue to follow it and you will have one more tester :)

---

### Post by addicha on 2009-01-30
Hi, quick question:
What if the password has the @ character. It confuses the command. Is there an escape sequence for this?


Thanks,
Addiel

---

### Post by martin.k on 2009-07-10
> **tehk said:**
> running intrepid (8.10) on AMD64 and built afpfs-ng from source, all that was needed was to use synaptic first to install the fuse dev packages and readline... then it configured/made with no errors...

However, when I try to mount a share from my Apple Time Capsule (and I've tried every imaginable URL and mount option) I'm greeted with the following message:

```
Mounting 192.168.0.17 from User on /mnt/TimeMachine
Could not pick a matching UAM
```Any ideas here?

I did run into the exact same issue (8.10/amd64), the important thing seems to be that libgcrypt (and libgmd?) are installed before ./configure - otherwise some encrypted authentication methods do not seem to work, but compilation succeeds without prominent warnings.

This is a rough version of the commands I did run to get it to work:
```

sudo aptitude install libgcrypt-dev libgmp3-dev libfuse-dev libreadline-dev
# extract sourcecode, cd into source directory
./configure --prefix=/usr
make
sudo make install

```note that the default prefix /usr/local installed libraries into /usr/local/lib, which were not  found when running afp_mount or afpfsd using my default? ubuntu config, hence the --prefix=/usr

---

### Post by alexthepuffin on 2009-07-11
Hi.  I'm the author of afpfs-ng, maybe I can help.

When compiling from source, you first need to install said crypto devel packages before running configure.  If not,  it won't include all the authentication modes which are required for the TC.

In a future release, I will include a clearer error message, something like "Could not find a matching UAM, you probably built afpfs-ng without the gcrypt-devel package.".

In terms of the @ character in a password, I can't remember the escape sequence I added to handle this (and don't have the code in front of me).  It may be "@@" or "\@".  Another way is to use a password of "-", which will then prompt you interactively for the password.

My email address is a better way to get hold of me, and I really do want afpfs-ng to work for you.

- Alex

---

### Post by antonellom on 2009-07-26
Hello!

I have following problem

mount_afp afp://ufficio:ufficio@192.168.178.8 /media/afp_mount_Geremia/
Incorrect permissions on /dev/fuse, mode of device is 20660, uid/gid is 0/106.  But your effective uid/gid is 1000/1000

---

### Post by tehk on 2009-07-31
sweetness!

a few months go by, the author stops in, and mounting prevails :popcorn:

i used the 0.8.1 code instead of CVS source (cvs wouldn't compile-errors)
and first installed the dev packages as recommended, worked like a charm!

this is all good because the last 24 hours have seen my macbook air "undeleting" my user folder (38 gigs gone) to my time capsule. now that i can mount this on my linux box, i can swap the files over, sort em out... and rebuild my airbook!

cheers for the help fellas

-tehk

---

### Post by zim2dive on 2009-08-07
Ok, ignorant question...

Does netatalk also work as an AFP client? or just as a server? (in which case I would need both netatalk and afpfs

(so that my Mac can mount the drives on my Jaunty HTPC and my HTPC can mount the "AirDisk" I have hanging off my Airport Extreme)

I guess I could just set up the jaunty box to share SMB (for access from the Mac).. any idea of the performance difference?

thanks,
Mike

---

### Post by zim2dive on 2009-08-14
1 note and a question

I installed under Jaunty with ```
sudo apt-get install netatalk
``` and I think it started right up.. it did not restart after a reboot so I had to edit /etc/netatalk/atakd.conf and uncomment eth0.

I've added a 2nd drive to my Jaunty box... mounted under /media/backups.

Question: How do I get this volume offered up via netatalk?  I only get the 1 main drive.

---

### Post by tiepolo on 2010-01-21
Hello,

I'm using afpfs with success
I can automatically mount afp remote files in ubuntu with this instruction : mount_afp afp://user:password@ipaddress/'Documenti Server' /media/localfilename user=myuser

but I can't obtain fstab to do it automatically

afpfs#afp://user:password@ipaddress/'Documenti Server' /media/localfilename fuse user=myuser,group=fuse 0 0

I obtain : mount point Server does not exists, or, if I do 
sudo mount -a

invalid line number......

I believe a problem with the space in 'Documenti Server' but don't know how to solve

If I use 

afpfs#afp://user:password@ipaddress/Documenti\040Server /media/localfilename fuse user=myuser,group=fuse 0 0

I get Incorrect permissions on mountpoint Server: No such file or directory

Paolo

---

### Post by hydraconsole on 2010-02-01
my wife shares her files folders from her macbook. I can mount the folder in my karmic koala with her credentials but when i use the ```
ls -l mountpoint
``` it comes up with my uid and gid instead of her credentials. i'm having permissions error with a shared file. i want to know how to use the --map <uam> flag. the man page said that it should make the files appear to be owned by the uid and gid of the userid i used to authenticate.

any help would be great.

---

### Post by lethalfang on 2010-09-27
I installed afpfs-ng on two computers. 
On one, I downloaded and compiled it from source code on a Ubuntu 10.04 x64 machine. On another, I downloaded the .deb and installed it on a 32-bit machine.

When I do the following command:
```
mount_afp afp://UserName:Password@www.webaddress.com/Folder ~/localfolder
```

I get the following:

Mounting [www.webaddress.com](www.webaddress.com) from Folder on /home/username/localfolder/
Could not connect, Connection refused


What did I do wrong?

Thanks in advance.


**EDIT: I figured out what was wrong. I typed the wrong web address. HA! How silly. I typed ".org" when it should've been ".net!"**

---

### Post by speedwolf on 2010-11-20
I really like the simple access that afpfs gives me in getting to my files.

It works fine when I mount_afp from the CLI and allows me to mount the target with no issues. Sadly the same cannot be said of the fstab approach which is what I need.

The CLI entry looks like this:
```
mount_afp afp://remoteuser:password@remotehost/targetfolder /mount/point
```
And results in:
```
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
Mounting remotehost from targetfolder on /mount/point
Mounting of volume Sites of server users MacBook succeeded.
```

The fstab entry looks like this:
```
afpfs#afp://remoteuser:pass@remotehost/targetfolder   /mount/point   fuse    user=localuser,group=fuse       0 0
```

But the result is this:
```
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
Could not find server (afpfsd)
Error in starting up afpfsd
Trying to startup afpfsd: No such file or directory
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
Could not find server (afpfsd)
Error in starting up afpfsd
Trying to startup afpfsd: No such file or directory
Trying to startup afpfsd: No such file or directory
```

Then it dies. Can someone give me a little heads up on how to fix this if at all possible?

Forgot to mention that it's afpfs-ng 0.8.1, Ubuntu 10.10 and Mac OS X 10.6

---

### Post by Wolf-Jakob Gratz on 2010-11-28
I can't get this to work. I always get this error:

```
mount_afp afp://wolfo:password@192.168.0.1/UNTITLED /home/wolfo/temporaer

Mounting 192.168.0.1 from UNTITLED on /home/wolfo/temporaer
Could not connect, Connection refused
```

The target server is an Airport Extreme sharing a USB disk (UNTITLED). I am able to connect to that share from other Macs, but not from my linux server.
Any ideas?

---

### Post by rkevsmith on 2011-04-04
> **alexthepuffin said:**
> I wrote afpfs-ng, so I can probably help.

Building afpfs-ng requires first installing the readline development libraries, you should do that first.

Did you try the prebuilt afpfs-ng debian package?

- A
Hi Alex, 

Thanks for putting afpfs-ng together. 

I keep getting closer to mounting my time capsule's disk, I think.

I've run into a similar situation as [tiepolo]("http://ubuntuforums.org/member.php?u=85550") above.

Here's what I'm trying:

keverage@cuauhtemoc:~$ mount_afp afp://;AUTH=No%20User%20Authent@192.168.1.101/coffre ~/capsule -o volpass=v0lp@SS
Incorrect permissions on mountpoint (null): No such file or directory
bash: /home/keverage/capsule: is a directory
keverage@cuauhtemoc:~$

---

### Post by rkevsmith on 2011-04-11
I'm in. I changed configurations on my Time Capsule to allow for accounts, instead of Time Capsule password.

Thanks for this. All best, 
K

---

### Post by SpoBo on 2011-09-28
I'm a bit of a linux noob but I'm planning to learn a lot more of it. Running 11.04

I need to share my Drobo which is connected to an Airport Extreme. I had no succes using SMB so nbow I'm trying afp. I tried the afpfs-ng package and I am able to mount my drive using the following command:
sudo mount_afp afp://root:pass@w00p.local/Drobo /media/drobo/

first I did sudo mkdir /media/drobo
sudo chown vincent /media/drobo

The problem though is that the files are only readable when I use sudo. Like sudo ls /media/drobo.

Trying to access my files in XBMC so this is not working for me :x

I"'m also unable to get it mounted through fstab. This is my line but it gives me the error at the end.
afpfs#afp://root:pass@w00p.local/Drobo /media/drobo fuse user=vincent,group=vincent 0 0

vincent@HTPC:~$ sudo mount -a
Unknown option dev, skipping
Unknown option suid, skipping
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
Could not find server (afpfsd)
Error in starting up afpfsd
Trying to startup afpfsd: No such file or directory
The afpfs daemon does not appear to be running for uid 1000, let me start it for you
Could not find server (afpfsd)
Error in starting up afpfsd
Trying to startup afpfsd: No such file or directory
Trying to startup afpfsd: No such file or directory

For the record, I did the mount -a command after I manually mounted the drobo in media/. So I think the afpfs daemon should be running, no?

---

### Post by raidoh on 2011-09-29
I haven't tried using AFP to connect to a share, but I've had good luck mounting a shared Airport Extreme disk using CIFS on Ubuntu 10.04. I'm able to automatically mount (fstab) my WD MyBook (HFS+) attached to a Airport Extreme and shared with a password over my workgroup. The drive is always mounted at /media/MB_Media as well as on my desktop and on the side of the Places explorer. If it helps anyone, here's what I did (based on a compilation of tutorials around the 'net).

Create the mountpoint directory and edit the fstab to automount.
[FONT="Courier New"]sudo mkdir /media/mount
sudo vi /etc/fstab[/FONT] 

Add a line at the bottom of the fstab for the new share. //Disk/MB Media is the share, raidoh is the local user, credentials holds the u/p for the remote user, file_mode and dir_mode set share permissions same as chmod and can be whatever you need.
#Mount Airport Extreme media server for music and storage (\040 is for the space in the name)
[FONT="Courier New"]//Disk/MB\040Media /media/MB_Media cifs auto,iocharset=utf8,uid=raidoh,gid=users,rw,credentials=/root/.credentials.MB_Media,file_mode=0700,dir_mode=0700 0 0[/FONT]
 
Create the credentials file to securely store the username and password
[FONT="Courier New"]sudo vi /root/.credentials.MB_Media[/FONT]
 
Add a line for u/p. I don't have a username since the AE shares with just a password.
[FONT="Courier New"]username=username
password=password[/FONT]
 
Save the file and exit
Change the persmissions of the file so it's only readable by the root
[FONT="Courier New"]sudo chmod 600 /root/.credentials.MB_Media[/FONT]
 
Test the setup
[FONT="Courier New"]sudo mount -a[/FONT]
 
If you ever need to unmount it
[FONT="Courier New"]sudo umount /media/MB_Media[/FONT]

I know my Mac is connecting to the AE disk and running Time Machine (hence the HFS+ for the partition on the WD MyBook), but is there another advantage to AFP over CIFS I should be considering?

---

### Post by molindern on 2012-05-14
I'm trying to connect to a friends AFP server and I'm stuck at installing afpfs-ng... I downloaded the debian package and tried to install it, but I received this error message


(Reading database ... 197601 files and directories currently installed.)
Unpacking afpfs-ng (from .../afpfs-ng_0.8.1-1_i386.deb) ...
dpkg: error processing /home/myuser/Downloads/afpfs-ng_0.8.1-1_i386.deb (--install):
 trying to overwrite '/usr/lib/libafpclient.so.0.0.0', which is also in package libafpclient0 0.8.1.0-0ubuntu1~ppa3~oneiric1
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe

I'm pretty new to linux so I have no idea what this means. I tried deleting libafpclient.so.0.0.0 but no luck

any help would be appreciated!

---

### Post by javirosa on 2012-07-25
That error is telling you that you already have the package installed via apt-get or aptitude. You need to remove it first using a command like: "sudo apt-get remove afpfs-ng-utils"

---

