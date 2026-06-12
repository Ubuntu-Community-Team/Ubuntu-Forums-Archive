---
title: "No smb connection after upgrade"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by frankO on 2009-04-15
Hi,
I updated from Ubuntu 8.04 to 8.10. Since then I have had problems connecting to my share server.

I know it is not my mount statement that is the problem. I use the same set up on a couple other machines but they were fresh installs. I also have a couple still running 8.04 until I can solve this problem.

Once logged into my desktop I can open a terminal and mount the share drive with no problems.

I don't know why fstab does not mount it on start up. I cannot find any errors in the logs. I think maybe the start up scripts might be faulty. But the rc3.d directory looks the same as the fresh install. And I don't have the skills to compare init.d with the fresh install init.d directory.

fstab has this entry
//192.168.1.6/share /media/share cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

If I open a terminal and write
sudo mount /media/share
It mounts ok

After mounting mtab shows
//192.168.1.6/share /media/share cifs rw,mand 0 0

Any ideas?

---

### Post by dmizer on 2009-04-15
try adding

mount /media/mount

to /etc/rc.local before exit 0

---

### Post by frankO on 2009-04-15
Thanks Dmizer, but it still did not mount.
I am getting a kernel error though

CIFS VFS: Error connecting to socket. Aborting operation
CIFS VFS: cifs_mount failed w/return code = -101

which I was not getting earlier.

---

### Post by dmizer on 2009-04-15
Try using the server's netbios name instead of IP address.

Edit /etc/nsswitch.conf and find the line that looks something like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line in front of dns (order is important), so the line looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

Then install winbind:
```
sudo aptitude install winbind
```

Reboot and see if that helps.

---

### Post by wkulecz on 2009-04-15
> **dmizer said:**
> Try using the server's netbios name instead of IP address.

Edit /etc/nsswitch.conf and find the line that looks something like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line in front of dns (order is important), so the line looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

Then install winbind:
```
sudo aptitude install winbind
```

Reboot and see if that helps.



Hmmm, my 8.04 is working to mount Samba shares, but when I added this it broke.  I got the desktop icon when I mounted the share using "Places" menu, but got a "no viewer" error when I tried to see the files.

Removing Winbind package and deleting the wins entry from nsswitch.conf file restored my Samba ability.

What I can't figure out is I can only access the share via gnome tools or menus.  Other things like Thunderbird attachments or command lines cannot access the share, if its mounted I've no idea where!

--wally.

---

### Post by dmizer on 2009-04-15
> **wkulecz said:**
> Hmmm, my 8.04 is working to mount Samba shares, but when I added this it broke.  I got the desktop icon when I mounted the share using "Places" menu, but got a "no viewer" error when I tried to see the files.

Removing Winbind package and deleting the wins entry from nsswitch.conf file restored my Samba ability.

What I can't figure out is I can only access the share via gnome tools or menus.  Other things like Thunderbird attachments or command lines cannot access the share, if its mounted I've no idea where!

--wally.

Hi wally.

Your problem is different than the OP. You can solve your problem by following the directions in the second link in my sig.

---

### Post by wkulecz on 2009-04-15
I'm not willing ot try anything if it breaks the Gnome access!  That is 99% of what my wife uses and if its broke, I'm done!

What I'm warning about, is your modification to nsswitch.conf and installation of winbind package does indeed let things like "ping windowshost" work now, but on my 8.04 system it breaks Gnome file sharing!

Reversing the mod, cures the issue, no reboot required!

--wally.

---

### Post by dmizer on 2009-04-15
> **wkulecz said:**
> Reversing the mod, cures the issue, no reboot required!

It doesn't cure this issue:
> What I can't figure out is I can only access the share via gnome tools or menus. Other things like Thunderbird attachments or command lines cannot access the share ...


As I said before, your problem is not the same as the OP. :)

---

### Post by frankO on 2009-04-16
> **dmizer said:**
> 

Then install winbind:

Reboot and see if that helps.

Hi Dmizer,
I already had winbind in the system.

I changed the fstab to 
//darkstar6/share /media/share cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

I changed rc.local to
mount /media/share

and it still did not work

I still got the error
CIFS VFS: Error connecting to socket. Aborting operation
CIFS VFS: cifs_mount failed w/return code = -101

It still works if I open a terminal and 
sudo mount /media/share

So using the netbios name made no difference.:(

It seems like it is trying to mount before the network is up. 

I presume all the networking and mounting starts in /etc/rcS.d
In /etc/rcS.d it shows

S35mountall.sh
S40networking

The computers with a clean install also show the same. I presume the mounting of network drive waits until the network is up. How does it do that?

---

### Post by dmizer on 2009-04-16
Edit /etc/network/interfaces and remove all the settings except loopback. When you are done, it should look like this:
```
auto lo
iface lo inet loopback
```
Reboot and see if your share is mounted then.

If that doesn't work, all I have left to suggest then is to install network-manager-gnome, remove network-manager, and configure your network via system > administration > network (just as you did in Hardy)

if you're using wireless, you may be successful with wicd.

---

### Post by frankO on 2009-04-23
Hi,
 I ended up doing a complete new install. The computer is nearly back to the way I want it. The other computers I will keep with 8.04. To much of a hassle upgrading.
Thanks

---

### Post by Boynas on 2009-05-19
> **dmizer said:**
> Try using the server's netbios name instead of IP address.

Edit /etc/nsswitch.conf and find the line that looks something like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line in front of dns (order is important), so the line looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

Then install winbind:
```
sudo aptitude install winbind
```

Reboot and see if that helps.


While this fixed my problem with samba.. Now I am able to browse windows server 2008 shares (I was able to browse any smb share except for MS 2008 server). But it broke my dns look up.. It is veeery slow.

My installation of ubuntu is 64 bit, I don't know if it makes a difference, I've seen a lot of threads regarding slow dns resolution and they talk about ip6 issues. Really my problem started when I added wins to the host field in nsswitch.conf

any ideas???

---

### Post by dmizer on 2009-05-19
> **Boynas said:**
> any ideas???

Yup, I highly suggest that (since it works for everything but the MS 2008 server, that you do one of two things:
1) add the MS 2008 server's IP address to /etc/hosts like so:
```
127.0.0.1	localhost
127.0.1.1	ubuntu-hostname
[COLOR="Red"]192.168.x.x	server-2008-hostname
[/COLOR]
```

2) mount your server 2008 shares according to the second link in my sig, and use the IP address instead of the host name.

---

### Post by Anubis on 2009-10-08
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Broke Liferea's ability to add feeds via Firefox.

Liferea segfaults 11 anytime a feed is added. After removing WINS from /etc/nsswitch.conf, all is well.

[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/446649](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/446649)

I kept WINS package installed on my machine, and so far the samba shares are all browsable.:popcorn:

---

