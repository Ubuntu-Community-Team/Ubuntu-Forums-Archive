---
title: "Cannot Connect to Ethernet"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by patrickscott on 2011-04-01
Greetings,

I have a dual boot netbook (Acer Aspire One D255) with Mint and Ubuntu 10.4.  Using Mint, I was able to connect via the ethernet and install all updates including wireless driver.

In Ubuntu 10.4, regardless of what I do, I cannot connect via ethernet cable at home and at work. 

How can I locate the right wireless driver? In the past, I have always been able to simply plug in the ethernet cable and get the necessary updates.

Feeling dumb in Dallas.

Pat

---

### Post by patryk77 on 2011-04-01
Hey,

2 things to try in the terminal:

```
sudo lshw -c network
ifconfig
```

The first will list the available network cards (seen by the system), the second will tell you IP addresses and whatnot.

Please post the output of these 2 commands to start with.

---

### Post by patrickscott on 2011-04-01
Thanks! 

Will post code as soon as I can borrow a jump drive.

Pat

> **patryk77 said:**
> Hey,

2 things to try in the terminal:

```
sudo lshw -c network
ifconfig
```

The first will list the available network cards (seen by the system), the second will tell you IP addresses and whatnot.

Please post the output of these 2 commands to start with.

---

### Post by patrickscott on 2011-04-01
THANKS! Here is the code:

patrick@patrick-laptop:~$ sudo lshw -c network 
[sudo] password for patrick: 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: c1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list 
       configuration: latency=0 
       resources: iomemory:ffffffff0-fffffffef 
  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:56000000-56003fff 
patrick@patrick-laptop:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6248 (6.2 KB)  TX bytes:6248 (6.2 KB) 

patrick@patrick-laptop:~$ 


> **patrickscott said:**
> Thanks! 

Will post code as soon as I can borrow a jump drive.

Pat

---

### Post by Razorback on 2011-04-01
Can you post the contents of your /etc/network/interfaces file?

---

### Post by patrickscott on 2011-04-01
How/where would I get the contents of my
/etc/network/interfaces file?

Thanks.

QUOTE=Razorback;10626510]Can you post the contents of your /etc/network/interfaces file?[/QUOTE]

---

### Post by Razorback on 2011-04-01
You can browse for it with Nautilus file manager.
Then double click it to open it for viewing.  Then you can highlight the contents (like Windows) and copy it.  Then paste it into a post here.

---

### Post by Razorback on 2011-04-01
Also, you need to check network connections.  You can click System > Preferences > Network Connections.  Make sure the wired connection (eth0) is enabled.

[http://www.youtube.com/watch?v=xOphZMu7Lho](http://www.youtube.com/watch?v=xOphZMu7Lho)

---

### Post by patrickscott on 2011-04-01
I noticed that there is no Auto eth0

How does one enable it?


> **Razorback said:**
> Also, you need to check network connections.  You can click System > Preferences > Network Connections.  Make sure the wired connection (eth0) is enabled.

[http://www.youtube.com/watch?v=xOphZMu7Lho](http://www.youtube.com/watch?v=xOphZMu7Lho)

---

### Post by Razorback on 2011-04-01
Did you get a chance to look at your /etc/network/interfaces file?
It should look something like this.

```

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

```

---

### Post by patrickscott on 2011-04-01
How does one search using Nautilus? I did a search using Places and Search for Files...

In the menus, I cannot locate Nautilus.

Thanks!


[/CENTER]

> **Razorback said:**
> Did you get a chance to look at your /etc/network/interfaces file?
It should look something like this.

```

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

```

---

### Post by Razorback on 2011-04-01
Under Places click Home Folder.  This launches nautilus.  On the left there will be a folder tree like Windows.  Click File System.  You should see many folders for the system.  Double click etc, then look for the network folder, double click then you should see the interfaces file in that folder.  Double click and it will launch a read-only window.

---

### Post by patrickscott on 2011-04-01
Thank you for your patience and clarity.

It has:

auto lo
iface lo inet loopback



> **Razorback said:**
> Under Places click Home Folder.  This launches nautilus.  On the left there will be a folder tree like Windows.  Click File System.  You should see many folders for the system.  Double click etc, then look for the network folder, double click then you should see the interfaces file in that folder.  Double click and it will launch a read-only window.

---

### Post by patrickscott on 2011-04-01
I carpool and will be leaving work in about 5 minutes. I will look at your post this evening when I get home.

Thanks!

---

### Post by Razorback on 2011-04-01
Interesting read on this thread.  Seems your ethernet card has an issue.

[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)

It is a large thread but has the information to get your Ethernet running.
I think post #6 provides the information.  I browsed the thread and posts go on to this year and they are still using it.

---

### Post by patrickscott on 2011-04-02
I tried repeatedly to install the driver with no success. I then thought that since Mint found the driver, somewhere in Mint there should be the information I needed for the driver. In Mint, I did a search for the installed driver, found it and found a link to the website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 

I downloaded the 802.11 Linux STA (32 bit) 

I then went to my installation file and changed the driver name so I ended up with this code:

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
hybrid-portsrc_x86_32-v5_100_82_38.tar.gz
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install

I ran the command, rebooted and, finally, I was connected to the internet via ethernet.

Right now I am doing all my initial software update. When it has finished updating,I will then check to see if my wireless is working.

THANKS for your tremendous support.

---

### Post by Razorback on 2011-04-02
Thats great.  Glad you got it going.  Hopefully, wireless will work with the updates.

---

### Post by patrickscott on 2011-04-02
Once I did the updates, it is no longer connecting via the ethernet cable. Just to be sure, I tried a different cable, different location  --from my dad's apt--  reinstalling driver in different ways... absolutely no success. I still cannot connect to the internet.

I am typing this using Mint.

Somewhat frustrated in Dallas.




> **Razorback said:**
> Thats great.  Glad you got it going.  Hopefully, wireless will work with the updates.

---

### Post by patrickscott on 2011-04-02
Now I get the following code and when I type uppercase or lowercase **y** and press enter, it aborts

patrick@patrick-laptop:~$ sudo apt-get update
[sudo] password for patrick: 
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
patrick@patrick-laptop:~$ sudo apt-get update
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
  Could not resolve 'security.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA 
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
  Could not resolve 'ca.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
patrick@patrick-laptop:~$ 
patrick@patrick-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
  xz-utils
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,572kB of archives.
After this operation, 24.6MB of additional disk space will be used.
Do you want to continue [Y/n]? 


 
> **patrickscott said:**
> Once I did the updates, it is no longer connecting via the ethernet cable. Just to be sure, I tried a different cable, different location  --from my dad's apt--  reinstalling driver in different ways... absolutely no success. I still cannot connect to the internet.

I am typing this using Mint.

Somewhat frustrated in Dallas.

---

### Post by Razorback on 2011-04-02
OK, try ifconfig and see what you get.

---

### Post by Razorback on 2011-04-02
> **patrickscott said:**
> I tried repeatedly to install the driver with no success. I then thought that since Mint found the driver, somewhere in Mint there should be the information I needed for the driver. In Mint, I did a search for the installed driver, found it and found a link to the website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 

I downloaded the 802.11 Linux STA (32 bit) 

I then went to my installation file and changed the driver name so I ended up with this code:

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
hybrid-portsrc_x86_32-v5_100_82_38.tar.gz
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install

I ran the command, rebooted and, finally, I was connected to the internet via ethernet.

Right now I am doing all my initial software update. When it has finished updating,I will then check to see if my wireless is working.

THANKS for your tremendous support.

Actually, that driver looks like it is for wireless.

---

### Post by patrickscott on 2011-04-02
As a last desperate act, at the boot window (dual boot), I selected one of the prior versions of Ubuntu options --I tried a restore first and then a prior version-- and when Ubuntu booted upthe ethernet driver installed automatically. I was then able to search for the wireless driver and it install with absolutely no problem. I rebooted several times always selecting the top most ubuntu link (the default link) and have been able to log in to the internet wirelessly. Of course, I have no idea why... but I am glad it is finally working.

This is being written via Ubuntu log in.

Thanks Razorback for being so helpful.

UOTE=Razorback;10629805]Actually, that driver looks like it is for wireless.[/QUOTE]

---

### Post by Razorback on 2011-04-02
> **patrickscott said:**
> As a last desperate act, at the boot window (dual boot), I selected one of the prior versions of Ubuntu options --I tried a restore first and then a prior version-- and when Ubuntu booted upthe ethernet driver installed automatically. I was then able to search for the wireless driver and it install with absolutely no problem. I rebooted several times always selecting the top most ubuntu link (the default link) and have been able to log in to the internet wirelessly. Of course, I have no idea why... but I am glad it is finally working.

This is being written via Ubuntu log in.

Thanks Razorback for being so helpful.

UOTE=Razorback;10629805]Actually, that driver looks like it is for wireless.

Glad you got it going.  Yeah, I have had things right themselves and not known why.  But the nice thing about Linux is sometimes it is a struggle but you learn a lot, especially from the folks around here - I know I have.

---

### Post by patrickscott on 2011-04-03
Thanks again. I have a lot to learn. I have installed Ubuntu and used it on and off for several years... but have never gotten serious about learning some commands, etc. I am a Windows software trainer... but linux is still Greek to me. I need to learn much more about it.

Have a great week.

Pat



> **Razorback said:**
> Glad you got it going.  Yeah, I have had things right themselves and not known why.  But the nice thing about Linux is sometimes it is a struggle but you learn a lot, especially from the folks around here - I know I have.

---

