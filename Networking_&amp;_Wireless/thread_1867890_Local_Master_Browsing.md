---
title: "Local Master Browsing"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Bradburts on 2011-10-23
I have set ```
local master = no
``` as a quick fix to allow my server's hard drives to spin down.
 
I have spent some time reading but cannot find a simple explanation of what local master browsing is/does.
My understanding is that the local master maintains a cache of devices on the network.
Other computers get information about network resources from the local master.
As I have decided that my server is not the local master then some other computer will have to take this role and will negotiate this responsibility with the other computers on the network.
 
I would like to know that I have not create some insidious problem with this option!
Am I right or am I wrong?

---

### Post by capscrew on 2011-10-23
> **Bradburts said:**
> I have set ```
local master = no
``` as a quick fix to allow my server's hard drives to spin down.
 
I have spent some time reading but cannot find a simple explanation of what local master browsing is/does.
Quoting from [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/newreply.php?do=newreply&p=11384170"):```
 local master (G)

    This option allows *[COLOR="Red"]nmbd[/COLOR]*(8) to try and become a local master browser on a subnet. 
     If set to _*no*_ then nmbd will not attempt to become a local master browser on a subnet
     and will also lose in all browsing elections.
``` 

Does this mean that Samba will not participate in elections?  I really don't know the answer to that.  Only that on the host in question that it won't win any elections.> 

My understanding is that the local master maintains a cache of devices on the network.  Other computers get information about network resources from the local master.
Only other hosts that have SMB/CIFS shares.  Not all network devices> 
As I have decided that my server is not the local master then some other computer will have to take this role and will negotiate this responsibility with the other computers on the network.
The election process is what determines what machine is the LMB.  You  are not stopping the election process.

I would like to know that I have not create some insidious problem with this option!
Am I right or am I wrong?
You could have temporary SMB share browsing problems.

---

### Post by Bradburts on 2011-10-24
> **capscrew said:**
> You could have temporary SMB share browsing problems.
What makes you say that?
I can see that unless you have a Local Master that a simple device may have problems finding resources. As all the devices I have will be PCs then I think that will be OK?
I found the manual sections you quote but the sections do not really explain what a Local Master does for you.
 
My other option was to mount a ram drive @ /run/cache/samba.
The ramdisk was mounted OK but browse.dat was not created. The folder /printing was created with its files, any ideas?

---

### Post by capscrew on 2011-10-24
> **Bradburts said:**
> What makes you say that?
I can see that unless you have a Local Master that a simple device may have problems finding resources. As all the devices I have will be PCs then I think that will be OK?
The browse master is typically a host that is always up.  If the browse master goes down, an election is held and a new browse master is created.  This can take up to 15 minutes.  During that time you will have trouble browsing the network for shares.> 
I found the manual sections you quote but the sections do not really explain what a Local Master does for you.
The master browser holds the browse list of shares for the network.> 
 
My other option was to mount a ram drive @ /run/cache/samba.
The ramdisk was mounted OK but browse.dat was not created. The folder /printing was created with its files, any ideas?
What is the RAM drive for?  Are you also running a WINS server?  Does this network have multiple subnets?

---

### Post by Bradburts on 2011-10-24
Thanks. I understand now.
I did not realise that the election would take time to arrange, just figured that when a computer wondered along the election process would be initiated.
 
The ram disk was just a means to stop samba logs/etc from keeping the hard disks from parking. I wanted to make a low power NAS and samba was keeping the disks awake.
 
I got the ram disk (tmpfs) sorted now. Samba is very fussy about the mount mode for some reason. Gotta be 0755 or browse.dat is not created.
So now my samba server is local master & I have all the samba logs & browse information on ram disks & so my hard drives can now sleep for the 90% of the day that they are have nothing to do but write samba logs & cache info. 
This saves me around 8 Watts which is about £10 a year with the server running 24/7.

---

