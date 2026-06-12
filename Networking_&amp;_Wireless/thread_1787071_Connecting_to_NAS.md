---
title: "Connecting to NAS"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Chazzer on 2011-06-20
Having become so frustrated with the many bugs in 11.04 I have stepped backward and instead installed Ubuntu 10.10 onto my Dell laptop. Until now I have been very pleased, as nearly everything has worked well, straight out of the box. So, just as I thought I was home and dry I have noticed that I cannot see my Synology NAS drive on my network. This is doubly frustrating because my other PC, also running 10.10, has suddenly lost it's ability to see the NAS drive too. Throughout last week I used the NAS in conjunction with my Ubuntu PC without a hitch but now it's gone. The NAS is visible to both Windows and Macs it's just the Ubuntu machines that cannot use it. It is also vaguely annoying knowing that the NAS itself uses a Linux OS or maybe that could be a clue to what's wrong.

As things stand my Apple Macs can see each other, they see the Windows box, see the NAS and see the shared folders on the Ubuntu machines. The Windows machines see the Macs, each other, the NAS and the Linux shared folders. The Ubuntu machines only see the Apple Mac shares, no Windows and no other Ubuntu shared folder nor the NAS. 

It is curious because the little program Avahi Zero Conf Browser can see absolutely everything on my network yet the Ubuntu GUI is proving to be the most difficult thing to network using anything other than than a web browser. Is there a concise definitive reason why Linux (Ubuntu) is so infernally difficult to network? I am not very experienced with Linux or the terminal but was hoping that this system might by now have become a little more user friendly for ordinary people.

Could there also have been something in a recent OS update that has killed off my PC running Ubuntu's ability to see the NAS where previously there has been no problem.

Thanks, Chazzer

---

### Post by Chazzer on 2011-06-20
Since writing the first piece re my NAS problem I've discovered that I can use Go>Location> in Nautilus, then enter the smb://address for the drive and it will mount. Is this the best I can hope for? Does Ubuntu expect me to first obtain the local IP address and then type it into Nautilus to mount a network disk? It doesn't add up that some shares should automatically display in the network folder while others do not.

---

### Post by capscrew on 2011-06-20
> **Chazzer said:**
> Since writing the first piece re my NAS problem I've discovered that I can use Go>Location> in Nautilus, then enter the smb://address for the drive and it will mount. Is this the best I can hope for? Does Ubuntu expect me to first obtain the local IP address and then type it into Nautilus to mount a network disk? It doesn't add up that some shares should automatically display in the network folder while others do not.

You need to provide name services on the LAN.  This can be as simple as telling your DHCP server what the hostname is of each computer or editing the /etc/hostname file if you have static IP addressing.  The bottom line is that Samba expects you have set this up BEFORE you install Samba server.  Then everything else "just works".

---

### Post by superduperlinuxperson on 2011-06-20
if what capscrew wrote does not work, simply write a program from shell script to do that (post #2)

---

### Post by Chazzer on 2011-06-21
Capscrew, I'll try and follow your suggestion with regards the router as I don't have static IP. I think I could be forgiven for not understanding this before, as I've never seen any obvious documentation when trying to set up the network within Ubuntu. I just figured that Ubuntu would just pick up any machine that offers a share and simply display it in the network array, like Windows or Macs do. Another thing I just cannot figure the purpose of is the "Windows Network" folder that resides with the Network folder. Whenever I try to open it a pop-up window displays the message that I can cancel the operation by hitting the cancel button. In any event it always fails to open.

Actually I've just looked into my router (which is my DHCP server) and it know all the names of my attached devices, it has them listed along with their MAC addresses and IP numbers. Is there a more obvious way to map a drive using Nautilus?

Thanks again for your input.

---

### Post by Chazzer on 2011-06-21
While hunting for more information on this forum I discovered this now closed thread dating back to 2005.. [http://ubuntuforums.org/showthread.php?t=289918]("http://ubuntuforums.org/showthread.php?t=289918")
In it several individuals are complaining/ranting about the same thing that's bugging me here, the inability of Gnome/Nautilus to easily mount network drives. These complaints go back years yet nothing is ever done to address the problem.

Like me all these users greatly admire the idea of GNU/Linux and the advances made by Ubuntu over the passed few years. They are all however, dismayed that the simple mapping/mounting of frequently used drives on the LAN, an aspect of computing which we take for granted on other systems, is apparently ignored by the developers of Nautilus/Gnome.

I am really trying to move more in the direction of GNU/Linux but this local network issue is a real put-off. :(

---

### Post by spynappels on 2011-06-21
What happens when you go to Places > Network? Do you not see the shares there?

---

### Post by Chazzer on 2011-06-21
The only shares I see listed in Places>Network are Apple Mac shares. These are represented by an icon of what looks like a stack of three drives. Double clicking these 'stack icons' opens a window that displays any public or shared folders on that disk, although there doesn't seem to be any way to log into any of these disks as a registered user, as I would be able to do connecting from another Mac. I'm not too bothered about that (at this stage) though, at least I can get ***some*** fairly straightforward network access. As mentioned previously there's always the 'Windows Network' folder visible but it makes no sense to me, as yet.

---

### Post by spynappels on 2011-06-21
> **Chazzer said:**
> The only shares I see listed in Places>Network are Apple Mac shares. These are represented by an icon of what looks like a stack of three drives. Double clicking these 'stack icons' opens a window that displays any public or shared folders on that disk, although there doesn't seem to be any way to log into any of these disks as a registered user, as I would be able to do connecting from another Mac. 

Ok, double clicking on one of these folders should then ask you for a username and password for access to that folder.

For the shares you cannot see, I'm not sure what is going on there as on my systems I see all my Samba shares in this location. A workaround is for you to create a shortcut pointing to the smb://ip-address location and just clicking on that to access them.

---

### Post by Chazzer on 2011-06-21
> **spynappels said:**
> Ok, double clicking on one of these folders should then ask you for a username and password for access to that folder.

For the shares you cannot see, I'm not sure what is going on there as on my systems I see all my Samba shares in this location. A workaround is for you to create a shortcut pointing to the smb://ip-address location and just clicking on that to access them.

That is what I am doing, as an when I need to transfer data. However it seems to be a rather primitive way to go about things, seeing as I'm used to more fluid connections using other computer systems. 

One of the reasons I am bothering with Ubuntu is so I can get further away from using Windows and even to recommend Ubuntu to other frustrated Windows users. The truth is I cannot put my hand on my heart and say it works fluently. I have other issues like lack of scanner support but that's not for this discussion.

---

### Post by capscrew on 2011-06-21
> **Chazzer said:**
> That is what I am doing, as an when I need to transfer data. However it seems to be a rather primitive way to go about things, seeing as I'm used to more fluid connections using other computer systems. 

One of the reasons I am bothering with Ubuntu is so I can get further away from using Windows and even to recommend Ubuntu to other frustrated Windows users. The truth is I cannot put my hand on my heart and say it works fluently. I have other issues like lack of scanner support but that's not for this discussion.

Samba (the smbd daemon) has 2 functions.  [LIST]
[*]Serves files via SMB format
[*] Creates a browse list for visually viewing the SMB resources
[/LIST]

You can do the first part via IP address.  Populating the browse list requires some sort of name services,

I have never used DHCP on my network I use static IP addresses and /etc/hosts files to map the IP address to the hostname.

The nmbd daemon is used for all the converting the DNS (hosts) name to NetBIOS calls.

---

### Post by Chazzer on 2011-06-21
Hi Capscrew, I have achieved some success in my task to map my network drive this evening. Time will tell if I've made an error. Here's what I've done.

1. Identify the IP Address or name of device as listed by the router.
2. Enter this address in Go>Location. Something like smb://192.168.1.15/ **or** the name of the device if it's known e.g. smb://DiskStation/
3.The device will mount as a share in the places column on the left of the main window panel, normally accompanied by an eject symbol at its side. Of course the contents of the disk are displayed within the main window panel.
4. The address path is shown in block buttons on top of the main window.
5. Drag the button down from the address path into the bottom of the lefthand side column array and voila, it becomes a permanent link to the disk or shared folder, even after a restart it will be there whereas all the shares previously loaded with the eject symbols next to them will have disappeared. They're temporary.
6. You can rename the address to something more convenient and also the icon will automatically change to a disk share.

It's taken me days to figure this process out. I'm so relieved I think it might be worth making into a little movie to help others.

---

### Post by capscrew on 2011-06-21
> **Chazzer said:**
> Hi Capscrew, I have achieved some success in my task to map my network drive this evening. Time will tell if I've made an error. Here's what I've done.

1. Identify the IP Address or name of device as listed by the router.
2. Enter this address in Go>Location. Something like smb://192.168.1.15/ **or** the name of the device if it's known e.g. smb://DiskStation/
3.The device will mount as a share in the places column on the left of the main window panel, normally accompanied by an eject symbol at its side. Of course the contents of the disk are displayed within the main window panel.
4. The address path is shown in block buttons on top of the main window.
5. Drag the button down from the address path into the bottom of the lefthand side column array and voila, it becomes a permanent link to the disk or shared folder, even after a restart it will be there whereas all the shares previously loaded with the eject symbols next to them will have disappeared. They're temporary.
6. You can rename the address to something more convenient and also the icon will automatically change to a disk share.

It's taken me days to figure this process out. I'm so relieved I think it might be worth making into a little movie to help others.

Sorry to be a party pooper but...

Youtube is full of inaccurate and misleading videos.  What good is another one? 

I don't see your description as friendly process.  Not when I can start my machine in the morning , open Places>>Network and see all the shares available to me on my server and start working.  

I can easily browse to the 6 shares from 3 different hosts as they come and go from the network by name. When my wifes laptop is on I can see the shares I made on that host.  When I start my laptop I can see those shares.  I don't have to check on IP addresses or drag anything around.

Why would you resist setting up name services?  What is reason you feel the kludge you have just described is better?  Have you tried to implement what I suggested regarding name services?  

I say at least try my suggestion.  The benefits are well worth it.  I have successfully helped others do this many times.  It's not just guess or that I stumbled into this and it is unique to my network only.

---

### Post by Chazzer on 2011-06-22
Well I certainly don't want to contribute to further confusion in the world, I'll hold fire on the video idea.

I'm not resisting setting up a name service list, I will try that. However editing the etc/hosts.conf file isn't exactly the simplest thing. It's a strictly Terminal process using vim or pico with root authority, and then I still expect to make errors or run into problems in making the list. I would have hoped there was a simple way in the GUI.

I'll let you know how things progress.

---

### Post by Chazzer on 2011-06-22
Hi Capscrew, I have added the local IP array to the IPv4 section of my hosts file and there is a marked improvement.

Thank you

---

### Post by vanadium on 2011-06-22
> **capscrew said:**
> You need to provide name services on the LAN.  This can be as simple as telling your DHCP server what the hostname is of each computer 
Sorry for intervening in this thread which I have been following, but how is this to be done? All ubuntu computers connecting to my router (Netgear DG834GT), which is by default configured to work as a DHCP server, show up with a device name "unknown", whereas my Mybookworld NAS does show up with devicename "mybookworld".

---

### Post by capscrew on 2011-06-22
> **vanadium said:**
> Sorry for intervening in this thread which I have been following, but how is this to be done? All ubuntu computers connecting to my router (Netgear DG834GT), which is by default configured to work as a DHCP server, show up with a device name "unknown", whereas my Mybookworld NAS does show up with devicename "mybookworld".

You can configure your dhcp client to tell the DHCP server what the hostname should be.  This *might* do what you want.

For most folks the technique is to use "reserved addresses" via DHCP and add the host to the /etc/hosts file.  Here is what I have mapped in my /etc/host file```
127.0.0.1	localhost
192.168.1.3	malibu 
192.168.1.2     rincon

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

This is on the host *malibu*.  Both *malibu* and *rincon* are Samba servers.  There are 6 hosts that are clients of these servers.

If you need further help just ask.

---

### Post by vanadium on 2011-06-23
This is the manual setup I am familiar with. I would expect, however, that in a modern small network, a linux client would be able to connect using the hostname without the need of having a static IP of that host coded in its hosts file. This is what DHCP is all about. The technique you describe also works without DHCP server.

---

### Post by capscrew on 2011-06-23
> **vanadium said:**
> This is the manual setup I am familiar with. I would expect, however, that in a modern small network, a linux client would be able to connect using the hostname without the need of having a static IP of that host coded in its hosts file. This is what DHCP is all about. The technique you describe also works without DHCP server.
Linux (the kernel) has nothing to do with *configuring* hosts, DNS or DHCP.  That is the province of the various Distros's config files.

Different distro's handle the configuration of name services in different ways.  You can see that when looking at RedHat based distros as compared to Debian based distro's.  Debian even has a hack that causes a known bug in its default /etc/hosts.  All this variation means the user is left with some choices and decisions at install time.  I accept the responsibility of configuration in exchange for the flexibility.

Microsoft and Apple each have a single corporate entity and therefore a more consistent (but arbitrary) approach to this in their OS versions.  Microsoft products use NetBIOS as the basic name service for LAN based shares communication.  Apple I believe favors WebDAV.    

As Samba is an implementation of Microsoft's SMB (CIFS) protocol it uses NetBIOS calls.  Samba solved the incompatibility issue (DNS <-->NetBIOS) with the daemon *NMBD*.  The daemon resolves DNS hostnames to NetBIOS names.

Ultimatly it is what it is.  If you install Ubuntu and want the complete Samba experience as the Samba dev's envisioned it, you need to have a functioning name service.  DNS works over a wider group of needs than NetBIOS, so I deploy that.  Using DNS correctly also cures the hack that Debian (Ubuntu) built into the default /etc/hosts file.

---

