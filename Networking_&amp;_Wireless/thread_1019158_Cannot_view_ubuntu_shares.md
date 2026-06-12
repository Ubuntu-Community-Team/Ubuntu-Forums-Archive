---
title: "Cannot view ubuntu shares"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by reev3r on 2008-12-22
I know that this has been posted a million times, and I have read through many of the previous posts. None of them seemed to fix the issue. 

I have been successful for some time in sharing folders on my Ubuntu box. Recently I have more people accessing folders on my machine and I was attempting to add some form of authentication to my folders.

Someone suggested I try gsambad to edit samba via gui. This proved both unsuccessful and devastating.

I can no longer view my samba shares as well as not being able to even see the machine on my local network, clearly at this point, gsambad is not the optimal choice for me.

Any help solving this issue would be helpful. I ended up purging samba from my machine in an effort to completely start over. However, this proved unsuccessful as well.


Thank You,

~reev3r

---

### Post by albinootje on 2008-12-22
> **reev3r said:**
> 
I have been successful for some time in sharing folders on my Ubuntu box. Recently I have more people accessing folders on my machine and I was attempting to add some form of authentication to my folders.

Someone suggested I try gsambad to edit samba via gui. This proved both unsuccessful and devastating.


The Samba project offers swat, a web-interface to handle shares and users :
[http://www.linux.com/feature/125452](http://www.linux.com/feature/125452)

I recommend first purging your old samba (with : sudo apt-get remove --purge samba) and gsambad completely.
Then :
```

sudo apt-get install swat

```

However if you prefer to manually edit your samba config, try the following :

1) Create a section in /etc/samba/smb.conf which does use authentication, here for example for user "adrian" :

[test]
   comment = test
   path = /home/samba/test
   valid users = adrian
   public = yes
   writable = yes
   create mode = 0775
   directory mask = 0775

2) Create the samba-user that you need (This needs to be a user which already exists in Ubuntu.)
```

sudo smbpasswd -a adrian

```
3) Set the proper permissions
```

sudo chown -R adrian /home/samba/test

```
4) Restart samba, and try it.

Did I forget something ?
You can troubleshoot by using the smbclient command, and checking the /var/log/samba/ logfiles.

---

### Post by reev3r on 2008-12-22
I guess I was not entirely clear about some of my issues. At this point I cannot even view the shares from the ubuntu machine, and any time I attempt to view them from a windows based machine the machine will lock up for about 3-5 mins and not display anything. I did try to install swat and it is proving unsuccessful also.

Thanks again,

~reev3r

---

### Post by albinootje on 2008-12-22
> **reev3r said:**
> I guess I was not entirely clear about some of my issues. At this point I cannot even view the shares from the ubuntu machine, and any time I attempt to view them from a windows based machine the machine will lock up for about 3-5 mins and not display anything. I did try to install swat and it is proving unsuccessful also.


Can you run :
```

testparm
ps auxw|grep smb
ps auxw|grep nmb

```
to check the syntax of your samba config, and to see whether samba is actually running properly ?
I think in your situation it's best to start completely from scratch, add a share without authentication needed, and then work towards a share which needs authentication.

For testing you can use smbclient in a terminal :
For example :
```

smbclient -L localhost

```
(no password needed) to see all shares.
The following for anonymous access :
```

smbclient //localhost/share-name

```
And this for testing a share with authentication :
```

smbclient //localhost/share-name -U your-username

```
After successfully logging in with the last command, try the "put" command to upload something to test the write permissions, for example :
```

smbclient //localhost/mysharename -U adrian
Enter adrian's password: 
Domain=[TESTING1] OS=[Unix] Server=[Samba 3.0.24]
smb: \> put cats.png
putting file cats.png as \cats.png (9044.1 kb/s) (average 9044.1 kb/s)
smb: \> 

```

---

### Post by reev3r on 2008-12-22
> **albinootje said:**
> Can you run :
```

(no password needed) to see all shares.
The following for anonymous access :
[code]
smbclient //localhost/share-name

```

The output I get is an error message:

Connection to localhost failed (Error NT_STATUS_BAD_NETWORK_NAME)

Not sure where to go from here. I have started from scratch with Samba and swat, as well as gsambad. (Having Purged all of the above)

Thank you,

~reev3r

---

### Post by reev3r on 2008-12-22
Okay, upon doing the steps prescribed above, I can view the shares on ubuntu, however the XP system is still locking up and not displaying that the Ubuntu machine is on the network. Samba is running fine and I am able to vnc into the machine, ftp works, and so does my mp3 server. Really not sure what is happening.


~reev3r

---

### Post by albinootje on 2008-12-23
> **reev3r said:**
> Okay, upon doing the steps prescribed above, I can view the shares on ubuntu, however the XP system is still locking up and not displaying that the Ubuntu machine is on the network. Samba is running fine and I am able to vnc into the machine, ftp works, and so does my mp3 server. Really not sure what is happening.


You can try adding the hostname of your Ubuntu machine to the lmhosts of the Windows-machine.
See here, esp. the section about errors.
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/integrate-ms-networks.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/integrate-ms-networks.html)
[http://linux.die.net/man/5/lmhosts](http://linux.die.net/man/5/lmhosts)
[http://www.swerdna.net.au/linhowtosambabrowse_recipe.html](http://www.swerdna.net.au/linhowtosambabrowse_recipe.html)

---

