---
title: "Very poor Samba/CIFS performance :("
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by kaffemonster on 2010-03-14
When I copy files to my NAS over wired GigE, I get up to 18 MB/s in Ubuntu 9.10 32 Bit, while the same laptop gets 40-55 MB/s when running Win7 32 Bit. Switching to wireless, copy rates drop to 2-4Mb/s in Ubuntu - over wireless N with 100% signal strenght.

Is there something I can do to tweak this as I really don't wan't to reboot to Windows just to copy files :(

Copying files over FTP just flies away with the same speeds as I get in Windows. I access my NAS via a CIFS share mounted in fstab, using this guide: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by dmizer on 2010-03-14
Are you using WINS for name resolution? NetBIOS name resolution can slow things down significantly. Do you get the same results if you mount the NAS IP address instead of name?

---

### Post by kaffemonster on 2010-03-14
I skipped the Wins part of your otherwise awesome guide - just added the NAS IP to the hosts file instead :)

Will try changing fstab from NAS name (resolved via hosts) to IP and post results.

Still doesnt explain the abysmal wireless performance tho...

---

### Post by dmizer on 2010-03-14
Do you get reasonable speeds on wireless using other protocols? I recognize that you indicated that you get good speeds over FTP, but it's not clear if you mean that you've tested FTP both wired and wirelessly.

---

### Post by kaffemonster on 2010-03-14
Just tested with a large, 4.7gb DVD ISO (Win7, 64 Bit - LEGAL (MVLS))

Ubuntu 9.10 wired samba/cifs: 13MB/S
Ubuntu 9.10 wireless samba/cifs: 4.1MB/S
Ubuntu 9.10 wired FTP: 35 Mb/s
Ubuntu 9.10 wireless FTP: 16Mb/s

Win7 wired samba/cifs: 45Mb/s
Win7 wireless samba/cifs: 16Mb/s

Looks to me like the Ubuntu cifs/samba needs a tuneup... I remember seing something about tweaking the buffer, but can't seem to find it again :(

---

### Post by dmizer on 2010-03-14
> **kaffemonster said:**
> Just tested with a large, 4.7gb DVD ISO (Win7, 64 Bit - LEGAL (MVLS))

Ubuntu 9.10 Wired samba/CIFS: 13MB/S

Win7 wired samba/cifs: 45Mb/s
Win7 wireless samba/cifs: 16Mb/s

Reboot to test Ubu 9.10 wireless speeds, samba and FTP. Brb :)

Please post your current /etc/fstab line, I have an idea.

---

### Post by kaffemonster on 2010-03-14
> **dmizer said:**
> Please post your current /etc/fstab line, I have an idea.

Sure thing:

```
//192.168.1.10/lager   /media/Lager cifs credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

```

---

### Post by kaffemonster on 2010-03-14
Hmm... I'd like to test this with 10.04. Should I try it using the Live CD or a virtual box installation?

---

### Post by kaffemonster on 2010-03-15
Just did a clean install of 10.04 - same speeds :(

---

### Post by dmizer on 2010-03-15
Try adding this option to your mount line in /etc/fstab: directio

Your fstab line will then look like this:
```
//192.168.1.10/lager   /media/Lager cifs [COLOR="Red"]directio[/COLOR],credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by kaffemonster on 2010-03-16
> **dmizer said:**
> Try adding this option to your mount line in /etc/fstab: directio

Your fstab line will then look like this:
```
//192.168.1.10/lager   /media/Lager cifs [COLOR="Red"]directio[/COLOR],credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
```

Now I'm getting 10Mb/s via CIFS in 10.04 :(

---

### Post by dmizer on 2010-03-16
> **kaffemonster said:**
> Now I'm getting 10Mb/s via CIFS in 10.04 :(

Well, that's no good. Try this then:
```
//192.168.1.10/lager   /media/Lager cifs credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777,rsize=130048 0 0
```

More enligtening information about rsize from man mount.cifs:
```
       rsize=arg
           default network read size (usually 16K). The client currently can
           not use rsize larger than CIFSMaxBufSize. CIFSMaxBufSize defaults
           to 16K and may be changed (from 8K to the maximum kmalloc size
           allowed by your kernel) at module install time for cifs.ko. Setting
           CIFSMaxBufSize to a very large value will cause cifs to use more
           memory and may reduce performance in some cases. To use rsize
           greater than 127K (the original cifs protocol maximum) also
           requires that the server support a new Unix Capability flag (for
           very large read) which some newer servers (e.g. Samba 3.0.26 or
           later) do. rsize can be set from a minimum of 2048 to a maximum of
           130048 (127K or CIFSMaxBufSize, whichever is smaller)
```

---

### Post by kaffemonster on 2010-03-16
> **dmizer said:**
> Well, that's no good. Try this then:
```
//192.168.1.10/lager   /media/Lager cifs credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777,rsize=130048 0 0
```

Awesome - just entered the above in fstab, will post results as soon as I get home from work...

Sadly - No difference, stil around the 10mb mark :(

Is there another way to mount the shares?

---

### Post by kaffemonster on 2010-03-16
Just a bump, really - just updated the post above.

The shares are on a Synology DS-209 NAS, would NFS be faster - and how would I mount it?

---

### Post by dmizer on 2010-03-16
> **kaffemonster said:**
> Just a bump, really - just updated the post above.

The shares are on a Synology DS-209 NAS, would NFS be faster - and how would I mount it?

Yes, NFS would be faster. Take a look at the client section of the howto located in the 4th link in my sig.

---

### Post by kaffemonster on 2010-03-17
> **dmizer said:**
> Yes, NFS would be faster. Take a look at the client section of the howto located in the 4th link in my sig.

I'll look into that - thanks a ton for your help so far!

NFS results will be posted as soon as I have them :)

---

### Post by dmizer on 2010-03-17
> **kaffemonster said:**
> I'll look into that - thanks a ton for your help so far!

NFS results will be posted as soon as I have them :)

Sounds good. Don't forget to adjust the rsize=8192,wsize=8192 options to gigabit frame sizes. Take a look here for more information: [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)

---

### Post by kaffemonster on 2010-03-17
Pure awesome - 33 mb/s steady as a rock:

[IMG]http://i70.photobucket.com/albums/i94/kaffemonster/33.png[/IMG]

Edit: And 8,5 mb/s on wlan! :D

The FSTAB line that did the trick:
```
siimnas:/volume1/lager /media/Lager nfs rsize=262144,wsize=262144,timeo=14,intr
```

Thanks a TON for your help! Browsing the shares are so much smoother now, not to mention file transfers :)

---

### Post by dmizer on 2010-03-17
Fantastic!

Glad to have helped :)

---

### Post by kaffemonster on 2010-03-18
At first, NFS performed similar to CIFS when rsize and wsize were set to 8192, but after changing them, performance soared. Is there a way to define those sizes with CIFS as well? I like the username/password verification more than the hostname/IP that NFS uses.

---

### Post by jrssystemsnet on 2010-03-18
> **kaffemonster said:**
> At first, NFS performed similar to CIFS when rsize and wsize were set to 8192, but after changing them, performance soared. Is there a way to define those sizes with CIFS as well? I like the username/password verification more than the hostname/IP that NFS uses. For reference, you really shouldn't be seeing slow cifs performance.  This is what I got when I tested mount.cifs on Ubuntu Karmic amd64, connecting to Samba 3.3.6 on a FreeBSD 7.3-R machine on a gigabit LAN:

```
me@banshee:~$ sudo mount.cifs //192.168.0.2/test /mnt -ouser=me
Password:
me@banshee:~$ dd if=/mnt/1G.bin bs=8M of=/dev/null
128+0 records out
1073741824 bytes (1.1 GB) copied, 13.7859 s, 77.9 MB/s
```

Note that this is absolutely bone stock all the way around - no funny options on the cifs mount, and no funny options on the Samba 3.3.6 server that mount.cifs was accessing.

I will note, though, that when you're testing gigabit speeds you **have to remember that your hard drive can be the bottleneck** - in my example, I was accessing a file that was already in the server's filesystem cache (so no hard drive slowdowns there), and I was dumping it to /dev/null on the client system (so no hard drive slowdowns there either).

---

### Post by dmizer on 2010-03-18
> **kaffemonster said:**
> At first, NFS performed similar to CIFS when rsize and wsize were set to 8192, but after changing them, performance soared. Is there a way to define those sizes with CIFS as well? I like the username/password verification more than the hostname/IP that NFS uses.
That's what this post was about: [http://ubuntuforums.org/showpost.php?p=8975973&postcount=12](http://ubuntuforums.org/showpost.php?p=8975973&postcount=12). Since you indicated that it didn't work, then I have no other ideas for increasing the speed of CIFS.

Though many people do not believe so, NFS is just as secure (if not more secure) than CIFS. However, permissions are handled at the file system level rather than the network level. You have to learn Linux file permissions, but it's more secure because you can't break it unless you have direct access to the machine.

> **jrssystemsnet said:**
> This is what I got when I tested mount.cifs on Ubuntu Karmic amd64, connecting to Samba 3.3.6 on a FreeBSD 7.3-R machine on a gigabit LAN [snip]
As a general rule, people who are complaining about speeds in CIFS indicate that speeds are satisfactory with the CLI, but slow via Nautilus in the GUI. Not sure why this is the case, but it seems to be fairly common. So, this is why dd may be showing decent speeds whereas something like streaming video to VLC is not.

> **jrssystemsnet said:**
> I will note, though, that when you're testing gigabit speeds you have to remember that your hard drive can be the bottleneck [snip]
This could have been a concern except kaffemonster indicated in the OP that speeds were satisfactory over FTP. Both FTP and CIFS would be subject to the same hardware bottleneck.

---

### Post by kaffemonster on 2010-03-18
> **dmizer said:**
> That's what this post was about: [http://ubuntuforums.org/showpost.php?p=8975973&postcount=12](http://ubuntuforums.org/showpost.php?p=8975973&postcount=12). Since you indicated that it didn't work, then I have no other ideas for increasing the speed of CIFS.
Okay - thanks :)

> **dmizer said:**
> Though many people do not believe so, NFS is just as secure (if not more secure) than CIFS. However, permissions are handled at the file system level rather than the network level. You have to learn Linux file permissions, but it's more secure because you can't break it unless you have direct access to the machine.
I set up a DHCP reservation for my laptop (both wired and wireless) so that it always gets the same IP address on my lan. That IP address is the only one with RW access to the shares - but what if another laptop sets up a static IP and tries to access the server?


> **dmizer said:**
> As a general rule, people who are complaining about speeds in CIFS indicate that speeds are satisfactory with the CLI, but slow via Nautilus in the GUI. Not sure why this is the case, but it seems to be fairly common. So, this is why dd may be showing decent speeds whereas something like streaming video to VLC is not.


This could have been a concern except kaffemonster indicated in the OP that speeds were satisfactory over FTP. Both FTP and CIFS would be subject to the same hardware bottleneck.

Plus the same machine on the same LAN, connected to the same shares gets great CIFS/Samba performance when booted to Windows 7... As stated in my first post.

---

### Post by dmizer on 2010-03-18
> **kaffemonster said:**
> I set up a DHCP reservation for my laptop (both wired and wireless) so that it always gets the same IP address on my lan. That IP address is the only one with RW access to the shares - but what if another laptop sets up a static IP and tries to access the server?

Create a group on the server for NFS access. Set the shared directory to 770 permissions, and chown the directory to nfs-group. Give all allowed remote NFS users an account on the server and add them to the NFS group.

I'm not an expert on Linux file permissions, but this should give more than adequate protection from unwanted access.

Additional information here: [http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)

---

### Post by jrssystemsnet on 2010-03-18
> **dmizer said:**
> (hard drive performance) could have been a concern except kaffemonster indicated in the OP that speeds were satisfactory over FTP. Both FTP and CIFS would be subject to the same hardware bottleneck.Well, yes and no - because nobody's said anything to indicate that the hardware's actually been accounted for either way.  It's not exactly uncommon for people to think "y is faster than x" when in reality, it's just that when they did x the fileserver had a cache miss, but then when they did y shortly after, the fileserver had a cache hit.

> As a general rule, people who are complaining about speeds in CIFS indicate that speeds are satisfactory with the CLI, but slow via Nautilus in the GUI.  OK, so here's a screenshot of a file copy via Nautilus:

[img]http://virtual.tehinterweb.net/livejournal/2010-03-18_Samba-performance.png[/img]

Note that in this case, we're bottlenecked by write I/O to the target drive since there's no way to copy something to /dev/null with Nautilus.

Again, there is *absolutely no performance tweaking* done on this connection; smb.conf is bone stock default on the Samba server, the mount.cifs has no arguments other than target share and username, and absolutely no tweaking is done to the TCP stack on either machine.

The thing I'm getting at here is that all too frequently I see users who have crippled performance by trying to blindly apply "tweaks" they found on the internet which may or may not have helped five years ago, but may actively HURT performance on a modern system.  All I'm really trying to demonstrate here is that if you're not getting at least 30MB/sec out of a bone stock Samba config, something besides Samba (or the default TCP stack) is seriously wrong - either you're hitting drive bottlenecks (which is EXTREMELY frequent, particularly if you've got a lot of fragmentation on the source or target) or some "tweak" that you've applied has actually hurt performance rather than helped it.

---

### Post by Lampi on 2010-03-20
thanks **jrssystemsnet** for your CIFS performance feedback - I observe similar lack of performance on lucid lynx beta server edition!

The server DISK is capable of: hdparm -tT = 107mb/s

CIFS with a "vanilla" smb.conf gives me with large files no more than 30mbit/s (this used to be like 50-60mbit on my debian etch system)

Vanilla nfs gives me the 65-75mbit/s I expected

So there is something wrong with CIFS - mount options kept as default:

For **CIFS** that is according to cat /proc/mounts/
```
rw,mand,nosuid,nodev,relatime,unc=\\UBULL\share1,username=<myusername>,domain=<mydomain>,uid=1000,forceuid,gid=1000,forcegid,addr=<MYSERVERIP>,posixpaths,acl,rsize=16384,wsize=57344 0 0
```
And for **nfs**:
```
rw,relatime,vers=3,rsize=262144,wsize=262144,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=MYSERVERIP>,mountvers=3,mountproto=tcp,addr=<MYSERVERIP> 0 0
```

If some1 knows what's wrong I'm happy :)

---

### Post by Lampi on 2010-03-21
*bump*

There seems to be a bug report on launchpad about it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512)

*not* solved so far, so I doubt this will be fixed by the Lucid release date

---

### Post by dmizer on 2010-03-21
> **Lampi said:**
> *bump*

There seems to be a bug report on launchpad about it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512)

*not* solved so far, so I doubt this will be fixed by the Lucid release date

Good find. I was looking for a bug report earlier but couldn't find one. For anyone effected by this problem (only in 9.10), I encourage you to go to this bug report and click on the "Does this bug affect you?" link at the top of the bug report.

---

### Post by mensfort on 2011-07-05
> **dmizer said:**
> Please post your current /etc/fstab line, I have an idea.

 got the same problem in linux 11.4: with Gvfs =18 MB/sec. With fstab = 3 MB/sec. But i found gvfs instable too bad. windows7= 20MB/sec... so why!  //192.168.1.40/Volume_1 /home/nas cifs username=mensfort,password=zhongguo,uid=1000,gid-100,rsize=57344,wsize=57344 0 0

---

### Post by LordNodens on 2011-07-08
Using CIFSMaxBufSize=130048 and directio/rsize=130048 options did  help in some cases. For example if I try to extract a MKV with MakeMKV  the speed rises to 60MB/sec. But if I try to copy a file from Nautilus  speed remains at 8-10 MB/sec. That's strange.

---

### Post by solnyshok on 2011-07-09
> **LordNodens said:**
> Using CIFSMaxBufSize=130048 and directio/rsize=130048 options did  help in some cases. For example if I try to extract a MKV with MakeMKV  the speed rises to 60MB/sec. But if I try to copy a file from Nautilus  speed remains at 8-10 MB/sec. That's strange.
Hi, how do you set CIFSMaxBufSize=130048?
I created cifs.conf with this in /etc/modprobe.d/
rebooted
when I do mount -t cifs .... -o ... ,rsize=130048
and then cat /proc/mounts
I still see rsize of 16384

//update ok, i found syntaxis mistake, should be 
options cifs CIFSMaxBufSize=130048

---

### Post by LordNodens on 2011-07-11
This is what I use for mounting in fstab:

//.../...  /.../...  cifs  directio,rsize=130048,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0


Then I created a file named cifs.conf in /etc/modprobe.d/ which has the following: options cifs CIFSMaxBufSize=130048

---

### Post by dcstar on 2012-04-09
> **LordNodens said:**
> 
...........
Then I created a file named cifs.conf in /etc/modprobe.d/ which has the following: options cifs CIFSMaxBufSize=130048

This also improved the performance on shares on my 10.04 system from < 500 Kb/s to > 15 Mb/s.

---

### Post by Lampi on 2012-05-01
I did some testing with cifs in precise, and I noticed cifs performance is considerably better than it was in lucid.

some TR benchmarks from a dm-raid share into /dev/null - tested without MAXBUFSIZE:

60 MB/s using mc and a cifs mountpoint
70 MB/s using cp and a cifs mountpoint
45 MB/s using Nautilus and a cifs mountpoint
30 MB/s using Nautilus with its own samba client implementation

Nautilus still needs some improvement, I have yet to check how dolphin is handling things with the smb// protocol.

But let's assume they finally fixed cifs issues from one LTS to the other.

---

### Post by kid1000002000 on 2012-06-21
[https://bugzilla.samba.org/show_bug.cgi?id=7699](https://bugzilla.samba.org/show_bug.cgi?id=7699)
[http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)

These may be pertinent?

---

