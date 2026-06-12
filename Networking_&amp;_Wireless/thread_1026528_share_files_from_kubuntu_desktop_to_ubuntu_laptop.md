---
title: "share files from kubuntu desktop to ubuntu laptop"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by nixie21 on 2008-12-31
I have tried a lot of things.  I am a bignetworking novice and linux novice for that matter.  Trying to start zeroconf caused a command not found error.  I tried turning on other things, but do not think it is working.  if you look here: [http://www.dslreports.com/forum/r21658309-Re-Network](http://www.dslreports.com/forum/r21658309-Re-Network)

you will see a couple of pics.  I am unsure how to share on kubuntu and also then how to access the shares from ubuntu.

please help!!  and thanks so much!!!!

---

### Post by bobbob1016 on 2008-12-31
Try using nfs.  Basically you just edit the file /etc/exports to say what folders you want to share.  Then restart the computer, and you can then mount the share from the other computer.
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) - A howto use nfs

---

### Post by nixie21 on 2008-12-31
Ok, here is where I get stuck.  On the Kubuntu desktop I did eveything.  I have the folders I want shared.  How to I access them on the other machine?  How do I know the name to mount? (I know dumb question, but I just dont entirely get this)

Thanks so much

---

### Post by nausicaavow on 2008-12-31
Here is a samba wlak-through. For the sake of this description I will refer to the kubuntu desktop as the server. The ubuntu laptop is the remote machine.

-- server --

1) Check to see you have samba installed (or install if you don't)
[FONT="Lucida Console"]-> sudo aptitude install samba[/FONT]

2) Open the samba configuration file and add a new section at the bottom. The file is located /etc/samba/smb.conf
[COLOR="Navy"][SHARE]
   comment = Linux Share
   path = /home/<username>/share
   browseable = yes
   writeable = yes[/COLOR]

[SIZE="1"]( Where you see <username>, substitute the userid for the ***machine you are on***. If you are not sure of your userid, just type [FONT="Lucida Console"]echo $LOGNAME[/FONT] in the Terminal)[/SIZE]

3) Create a samba userid for access to the share
[FONT="Lucida Console"]-> sudo smbpasswd -a <username>[/FONT]

[SIZE="1"]( This userid is for the ***remote machine***. It will be used by the remote machine to access the share )[/SIZE]

4) Restart samba
[FONT="Lucida Console"]-> sudo /etc/init.d/samba restart[/FONT]

5) Ensure your IP address is static. [SIZE="1"](It is beyond the scope of this post, but most routers can assign a static IP for a particular machine. Or you can do it the old fashioned way.)[/SIZE]

Done!

-- remote machine --

1) Make a directory to mount the filesystem to
[FONT="Lucida Console"]-> sudo mkdir /mnt/share[/FONT]

2) Add the IP address of the server to your hosts file. The file location is /etc/hosts
[SIZE="1"](This is why the static IP on the server is necessary)[/SIZE]
[COLOR="Navy"]192.168.1.100 <server>[/COLOR]

3) Open fstab on the remote machine and add a new line so that the share is mounted automatically upon startup. The file is located /etc/fstab.
[COLOR="Navy"]//<server>/share /mnt/share smbfs defaults,credentials=/etc/<server>.smbcred 0 0
[/COLOR]
4) Create the credentials file
[FONT="Lucida Console"]-> sudo touch /etc/<server>.smbcred
-> echo "username=<username>" >> /etc/<server>.smbcred
-> echo "password=<password>" >> /etc/<server>.smbcred
-> sudo chmod 600 /etc/<server>.smbcred[/FONT]
[SIZE="1"](This is the userid and password you created earlier for samba by using smbpasswd)[/SIZE]

5) Mount the share
[FONT="Lucida Console"]-> mount /mnt/share[/FONT]

Done!

---

### Post by nixie21 on 2008-12-31
thanks

when i get to this line
-> sudo echo "username=<username>" >> /etc/<server>.smbcred

I get a bash: /etc/192.168.1.4.smbcred: Permission denied

thanks

---

### Post by Iowan on 2008-12-31
> **nixie21 said:**
> ...I have the folders I want shared... How did you share the files, Samba, NFS, SSH, FTP? You will need a "server" installed for most (if not all).  How you retrieve the files will depend on how they were shared.

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> thanks

when i get to this line
-> sudo echo "username=<username>" >> /etc/<server>.smbcred

I get a bash: /etc/192.168.1.4.smbcred: Permission denied

thanks

It is probably redirecting the output as your user rather than root. You can become root by entering [FONT="Lucida Console"]sudo su -[/FONT]
Then do the [FONT="Lucida Console"]echo "username=<username>" >> /etc/<server>.smbcred[/FONT]

---

### Post by nixie21 on 2008-12-31
> **nausicaavow said:**
> It is probably redirecting the output as your user rather than root. You can become root by entering [FONT="Lucida Console"]sudo su -[/FONT]
Then do the [FONT="Lucida Console"]echo "username=<username>" >> /etc/<server>.smbcred[/FONT]

thanks so much for your help...every step is killing me LOL

5) Mount the share
-> mount /mnt/share

I get 
mount : can't find /mnt/share in /etc/fstab or /etc/mtab

I did all your directions up to this last one.

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> thanks so much for your help...every step is killing me LOL

5) Mount the share
-> mount /mnt/share

I get 
mount : can't find /mnt/share in /etc/fstab or /etc/mtab

I did all your directions up to this last one.

Ha! No problem, glad to help. Can you post your /etc/fstab line for the samba share? Also can you verify the directory /mnt/share exists?

---

### Post by nixie21 on 2008-12-31
//192.168.1.4/share /mnt/share/smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0


and yes the /mnt/share is created

thanks!!

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> //192.168.1.4/share /mnt/share/smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0


and yes the /mnt/share is created

thanks!!

Ok looks good, just change the slash "/" before smbfs to a space " "

---

### Post by nixie21 on 2008-12-31
> **nausicaavow said:**
> Ok looks good, just change the slash "/" before smbfs to a space " "

Getting closer?

nixie21@ubuntu-laptop:/$ sudo mount /mnt/share
mount: wrong fs type, bad option, bad superblock on //192.168.1.4/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by nixie21 on 2008-12-31
nixie21@ubuntu-laptop:/$ dmesg |tail
[  758.350207] RPC: Registered udp transport module.
[  758.350250] RPC: Registered tcp transport module.
[  818.480381] rpcbind: server Kubuntu not responding, timed out
[ 3894.480105] rpcbind: server Kubuntu not responding, timed out
[ 4265.512082] NET: Registered protocol family 10
[ 4265.515615] lo: Disabled Privacy Extensions
[ 4265.517636] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4275.984039] ath0: no IPv6 routers present
[ 5429.165799] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[ 5429.165815] smbfs: mount_data version 1684370019 is not supported

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> Getting closer?

nixie21@ubuntu-laptop:/$ sudo mount /mnt/share
mount: wrong fs type, bad option, bad superblock on //192.168.1.4/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Ok looks like you do not have smbfs installed. Try this:
[FONT="Lucida Console"]-> sudo aptitude install smbfs[/FONT]

---

### Post by nixie21 on 2008-12-31
ok, did that and tries the mount again.  The prompt is just blinking and nothing is happening?

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> ok, did that and tries the mount again.  The prompt is just blinking and nothing is happening?

Ok, lets try a few things:
1) can you ping your server?
2) unmount the filesystem
[FONT="Lucida Console"]-> sudo umount /mnt/share[/FONT]
3) on the server make sure the /home/<username>/share directory exists

---

### Post by nixie21 on 2008-12-31
> **nixie21 said:**
> ok, did that and tries the mount again.  The prompt is just blinking and nothing is happening?



here is the error

nixie21@ubuntu-laptop:/$ sudo mount /mnt/share
mount error 110 = Connection timed out
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


thanks again

---

### Post by nixie21 on 2008-12-31
let me make sure i am doing this right.

i am using 192.168.1.4 because that is what the router says the kubuntu machine is.

i can ping 192.168.1.1 but not 192.168.1.4?

the sares are there as they are
/home/nixie21/Pictures
/home/nixie21/Music

thanks so much

---

### Post by nixie21 on 2008-12-31
in the smb.conf

[NIXIE21MUSIC]
   path = /home/nixie21/Music
   comment = /home/nixie21/Music
   public = yes
   guest ok = yes
   writable = no

[NIXIEPICTURS]
   path = /home/nixie21/Pictures
   comment = /home/nixie21/Pictures
   public = yes
   guest ok = yes
   writable = no
   wide links = no

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> in the smb.conf

[NIXIE21MUSIC]
   path = /home/nixie21/Music
   comment = /home/nixie21/Music
   public = yes
   guest ok = yes
   writable = no

[NIXIEPICTURS]
   path = /home/nixie21/Pictures
   comment = /home/nixie21/Pictures
   public = yes
   guest ok = yes
   writable = no
   wide links = no

Ok, there is a couple things going on.

A) You have created two shares nixiepictures and nixie21music
If you *want *to have two separate shares you will need two mount points on the remote machine
[FONT="Lucida Console"]-> mkdir /mnt/pictures
-> mkdir /mnt/music[/FONT]
The fstab would look like this:
//192.168.1.4/nixie21music /mnt/music smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0
//192.168.1.4/nixiepictures /mnt/pictures smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

or
B) Alternately, you can create just one mount, containing both pictures and music on the server.
The smb.conf would look like this:
[SHARE]
comment = Linux Share
path = /home/<username>/share
browseable = yes
writeable = yes

You will have to make the directory called "share"
-> mkdir /home/<username>/share
Then link in any directories you want to include to be shared
[FONT="Lucida Console"]-> cd /home/<username>/share
-> ln -fs /home/nixie21/Pictures pictures
-> ln -fs /home/nixie21/Music music[/FONT]

The fstab would look like this:
//192.168.1.4/share /mnt/share smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

---

### Post by nixie21 on 2008-12-31
> **nausicaavow said:**
> Ok, there is a couple things going on.

A) You have created two shares nixiepictures and nixie21music
If you *want *to have two separate shares you will need two mount points on the remote machine
[FONT="Lucida Console"]-> mkdir /mnt/pictures
-> mkdir /mnt/music[/FONT]
The fstab would look like this:
//192.168.1.4/nixie21music /mnt/music smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0
//192.168.1.4/nixiepictures /mnt/pictures smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

or
B) Alternately, you can create just one mount, containing both pictures and music on the server.
The smb.conf would look like this:
[SHARE]
comment = Linux Share
path = /home/<username>/share
browseable = yes
writeable = yes

You will have to make the directory called "share"
-> mkdir /home/<username>/share
Then link in any directories you want to include to be shared
[FONT="Lucida Console"]-> cd /home/<username>/share
-> ln -fs /home/nixie21/Pictures pictures
-> ln -fs /home/nixie21/Music music[/FONT]

The fstab would look like this:
//192.168.1.4/share /mnt/share smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

I am sorry to be a pain....

I changed the share from the 2 directries to just share /home/nixie21
I made the change in the smb.conf file as well...

Now I changed everything to use 192.168.1.1  - does this seem right? (since it could not ping 192.168.1.4)

when trying to mount, I still get the mount error 111 = connection refused
refer to the mount.cifs(8) manual page

Thanks fo spending the time to help

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> I am sorry to be a pain....

I changed the share from the 2 directries to just share /home/nixie21
I made the change in the smb.conf file as well...

Now I changed everything to use 192.168.1.1  - does this seem right? (since it could not ping 192.168.1.4)

when trying to mount, I still get the mount error 111 = connection refused
refer to the mount.cifs(8) manual page

Thanks fo spending the time to help

Ok no problem, one share is fine.

So, your server smb.conf is like this now?
[SHARE]
comment = Linux Share
path = /home/nixie21
browseable = yes
writeable = yes
[SIZE="1"]( the text between the brackets "[ ]" is the samba share name, so in this case the name is called "share" )[/SIZE]

And on the remote machine the fstab is like this now?
//192.168.1.4/share /mnt/share smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0
[SIZE="1"]( the first section "//192.168.1.4/share" is the samba share on the server so it is the same name you used in smb.conf, in this case the name is called "share" )
( the second section is the mount point on the local machine (laptop), so you need to make sure the directory is there, in this case "/mnt/share" )[/SIZE]

Ideally you should just name your server, instead of using the IP address. This way if it changes you only need to change the entry in /etc/hosts with the new address.

192.168.1.1 is most likely your router, not your server. On your server type [FONT="Lucida Console"]sudo ifconfig[/FONT] to find your IP.

---

### Post by ugm6hr on 2008-12-31
I know you are close to getting SMB to work, but my experience has been that it is a real nuisance.  The only reason I see for its use is including Windows in the shares.

For a KDE / Gnome - Linux situation, I have found SSH the easiest protocol:
[http://ubuntuforums.org/showpost.php?p=4631437&postcount=4](http://ubuntuforums.org/showpost.php?p=4631437&postcount=4)

Kubuntu would be the "server" and Ubuntu the "client"

You can then add any directory (including /) as a bookmark in Nautilus for future easy access.  Nautilus will offer to save the password if you want it to.

---

### Post by nausicaavow on 2008-12-31
> **ugm6hr said:**
> I know you are close to getting SMB to work, but my experience has been that it is a real nuisance.  The only reason I see for its use is including Windows in the shares.

For a KDE / Gnome - Linux situation, I have found SSH the easiest protocol:
[http://ubuntuforums.org/showpost.php?p=4631437&postcount=4](http://ubuntuforums.org/showpost.php?p=4631437&postcount=4)

Kubuntu would be the "server" and Ubuntu the "client"

You can then add any directory (including /) as a bookmark in Nautilus for future easy access.  Nautilus will offer to save the password if you want it to.

Yes, I didn't even think of that. It may be simpler to do this method. Sometimes I forget all the things that you must know in order to configure samba!

---

### Post by ugm6hr on 2008-12-31
> **nausicaavow said:**
> Yes, I didn't even think of that. It may be simpler to do this method. Sometimes I forget all the things that you must know in order to configure samba!

There is one other option that is supposed to be even easier.  Unfortunately, it's currently only available in the Intrepid repo.

[Giver]("apt:giver") by Novell: 
[http://video.google.com/googleplayer.swf?docId=3768442676796881783&hl=en](http://video.google.com/googleplayer.swf?docId=3768442676796881783&hl=en)
[http://idea.opensuse.org/content/ideas/easy-file-sharing](http://idea.opensuse.org/content/ideas/easy-file-sharing)

---

### Post by nixie21 on 2008-12-31
> **ugm6hr said:**
> I know you are close to getting SMB to work, but my experience has been that it is a real nuisance.  The only reason I see for its use is including Windows in the shares.

For a KDE / Gnome - Linux situation, I have found SSH the easiest protocol:
[http://ubuntuforums.org/showpost.php?p=4631437&postcount=4](http://ubuntuforums.org/showpost.php?p=4631437&postcount=4)

Kubuntu would be the "server" and Ubuntu the "client"

You can then add any directory (including /) as a bookmark in Nautilus for future easy access.  Nautilus will offer to save the password if you want it to.

can you explain this to me?

---

### Post by nixie21 on 2008-12-31
smb.conf


[NIXIE21]
   path = /home/nixie21/
   comment = /home/nixie21/
   public = yes
   guest ok = yes
   writable = no

---

### Post by SuperSonic4 on 2008-12-31
> **ugm6hr said:**
> I know you are close to getting SMB to work, but my experience has been that it is a real nuisance.  The only reason I see for its use is including Windows in the shares.

For a KDE / Gnome - Linux situation, I have found SSH the easiest protocol:
[http://ubuntuforums.org/showpost.php?p=4631437&postcount=4](http://ubuntuforums.org/showpost.php?p=4631437&postcount=4)

Kubuntu would be the "server" and Ubuntu the "client"

You can then add any directory (including /) as a bookmark in Nautilus for future easy access.  Nautilus will offer to save the password if you want it to.

How do I access the server in a kubuntu client?

---

### Post by nixie21 on 2008-12-31
fstab = 
//192.168.1.4/NIXIE21 /mnt/share smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

now how do i get it mounted?

---

### Post by nixie21 on 2008-12-31
> **ugm6hr said:**
> I know you are close to getting SMB to work, but my experience has been that it is a real nuisance.  The only reason I see for its use is including Windows in the shares.

For a KDE / Gnome - Linux situation, I have found SSH the easiest protocol:
[http://ubuntuforums.org/showpost.php?p=4631437&postcount=4](http://ubuntuforums.org/showpost.php?p=4631437&postcount=4)

Kubuntu would be the "server" and Ubuntu the "client"

You can then add any directory (including /) as a bookmark in Nautilus for future easy access.  Nautilus will offer to save the password if you want it to.

ok, i did this and i got an connection timed out error

what i want to do is point my music player to the folder on the kuuntu machine..plus some other stuff

---

### Post by nausicaavow on 2008-12-31
> **nixie21 said:**
> fstab = 
//192.168.1.4/NIXIE21 /mnt/share smbfs defaults,credentials=/etc/192.168.1.4.smbcred 0 0

now how do i get it mounted?

Ok, just change NIXIE21 to lowercase nixie21
Then, you just mount /mnt/share

---

### Post by nixie21 on 2008-12-31
> **nausicaavow said:**
> Ok, just change NIXIE21 to lowercase nixie21
Then, you just mount /mnt/share

Thanks, it seems I have no luck.  I changed it to lowercase and tried the mount command again.  After a like 5 minutes or so, it just says...

mount error 110 = conection timed out
refer to mount.cifs(8) manual page

Do you think there is something I need to do in my router to allow this? (another thing I am unsure of!!!)

I really appreciate your time!!!

---

### Post by ugm6hr on 2008-12-31
> **nixie21 said:**
> ok, i did this and i got an connection timed out error

what i want to do is point my music player to the folder on the kuuntu machine..plus some other stuff

On the kubuntu machine:
```
sudo ufw allow 22
```

Then try again.

---

### Post by nixie21 on 2008-12-31
> **ugm6hr said:**
> On the kubuntu machine:
```
sudo ufw allow 22
```

Then try again.

ok, now I get

cannot display location "sftp://nixie21@198.168.1.4/"
timmed out when logging in


thanks

---

### Post by nixie21 on 2008-12-31
could both problems be that I can not ping 192.168.1.4?  I do not know why this would be?

---

### Post by SuperSonic4 on 2008-12-31
> **ugm6hr said:**
> On the kubuntu machine:
```
sudo ufw allow 22
```

Then try again.

Works for me but is there any way I can copy something from the desktop to the laptop and vice versa?

---

### Post by nixie21 on 2008-12-31
looking in router, i am unsure if this is the norm:

Host:	Kubuntu
IP Address:	192.168.1.4
Subnet Mask:	255.255.255.0
MAC Address:	00:0c:f1:9a:51:5c
Network Connection:	Bridge
Lease Type:	Dynamic
Port Forwarding Services:	None
Windows Shared Folders:	\\192.168.1.4\

    * Diagnostics can assist in testing network connectivity. This feature pings (ICMP echo) an IP address and displays the results, such as the number of packets transmitted and received, round trip time, and success status


Ping (ICMP Echo)
Destination:	192.168.1.4
	
Number of pings:	4
Status:	Test Failed
Packets:	4/4 transmitted, 0/4 received, 100% loss
Round Trip Time:	Minimum = 0 ms
Maximum = 0 ms
Average = 0 ms

How is this possible if I am using this now to connect?

---

### Post by ugm6hr on 2008-12-31
> **SuperSonic4 said:**
> Works for me but is there any way I can copy something from the desktop to the laptop and vice versa?

Things get confusing if you hijack someone else's thread.

If you need more help - please start your own.

But - yes.  You can move files in either direction from the "client" if you mount "/" from the server in the client.  You will have permissions matching the users details that you have used to access the ssh server.

If you want to be able to the same from the "server" - then just install the client and server software on both machines.

---

### Post by ugm6hr on 2008-12-31
> **nixie21 said:**
> How is this possible if I am using this now to connect?

That's odd.

It has an IP; it connects to internet via the same router, but can't be pinged from the router.

:confused:

---

### Post by nausicaavow on 2008-12-31
It was mentioned earlier you may have a firewall up (ufw)? Can you disable it to see if that is the problem? I think [FONT="Lucida Console"]sudu ufw disable [/FONT]will do it...

---

### Post by Iowan on 2008-12-31
Getting back late, again... Is there a reason you're mounting the shares via smbfs instead of cifs?

---

### Post by nixie21 on 2009-01-01
> **Iowan said:**
> Getting back late, again... Is there a reason you're mounting the shares via smbfs instead of cifs?

how do you mount cifs?

---

### Post by Iowan on 2009-01-01
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
(But it won't solve inability to ping.)

---

### Post by nixie21 on 2009-01-01
thanks, I started a new thread about the pinging, it is avery weird.  I can ping nothing from the desktop

nixie21@Kubuntu:~$ sudo ping 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.6 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11009ms

nixie21@Kubuntu:~$ ping google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by Iowan on 2009-01-01
The "sendmsg" looks unusual.  I'll check your other thread so this one can remain the "sharing" problem.

---

### Post by nixie21 on 2009-01-02
OK!!!

I ran sudu ufw disable and it now works.  The problem is, do I need UFW?  I am not good with firewalls, but would use one if it was VERY easy to configure...

THANKS SO MUCH!!!!

---

### Post by ugm6hr on 2009-01-03
ufw should not stop you from pinging from your desktop.  I'm not sure if it would stop the router from pinging either.

That is very bizarre.

Also, I believe even if ufw is disabled, iptables (the underlying Firewall that ufw simplifies use of) still exists in its default all ports closed state.

There is no simpler Firewall than ufw.  If you need a GUI - try gufw.

---

