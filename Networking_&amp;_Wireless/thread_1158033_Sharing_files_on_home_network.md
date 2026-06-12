---
title: "Sharing files on home network"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Joe_Coppens on 2009-05-13
As this is my first post, let me start by saying hello. 

Just last week I purchased an Asus eee PC 1000HE. I downloaded the desktop edition of Ubuntu and installed it yesterday. I'm liking the look and feel of it, but for the life of me I can't get file sharing to work.

My setup is as follows: I have two Macs, both running OS 10.5. I have DSL and I'm using an Apple Time Capsule router with a 1TB HD. I'd like to be able to move files between my Macs and my Ubuntu netbook, and to access the hard drive on my router from the netbook.

In a library book "How to Do Everything Ubuntu" and in several tutorials on the internet, I've found references to a network settings tool that should be located under System-Administration-Network. I don't have such a tool and can't find it anywhere on my machine. I did manage to find a command to access sharing, and got my shared folder to show up on my Mac. When I tried connecting to it, the Mac said the server was no longer available or did not exist. When I rebooted the netbook, it didn't show up on the sidebar of my Mac.

Since I just downloaded Ubuntu Monday, I'm running what I believe to be the most recent build, 9.04 if I'm not mistaken. If anyone has any suggestions for me, it will be greatly appreciated.

Thanks,
   -Joe

---

### Post by dbuttera187 on 2009-05-13
i know nothing about macs but when I set up a workgroup at my house between 2 windows xp computers and my kubuntu 9.04, i used Samba. I'm not sure if that will work with mac's or not. The way i did it is I set up a windows workgroup between the two XP computers first, then i installed samba on the kubuntu machine. Samba allowed me to join the workgroup. I couldn't access my windows shares but i just used the share on the kubuntu machine anyway as the standard for the workgroup. hope that helps some :)

---

### Post by Peter09 on 2009-05-13
For windows you will need to install samba server - its in synaptic.

---

### Post by Macchi on 2009-05-18
I am experiencing problems with Ubuntu 9.04 Jaunty while trying to access a file share on a time capsule. 

This worked seamlessly before and now I cannot get trough. File sharing with Macs works fine on another machine running Ubuntu 8.10 Intrepid.

Has anyone experienced similar problems? Apparently yes, although communications with Macs over smb has neever been a problem for me before.
Thank you for any qualified hints and answers.

PS: Sorry I am in the production phase around three projects and don't have time to pursue a solution.

---

### Post by thered on 2009-05-18
I upgraded to 9.04 last month and have just tried to transfer some files for the first time since then.

Like Macchi it just seems to have stopped working!  I happened across this thread and though I post here.

I'm sure there used to be a System-Admin-network link where I setup a 'workgroup' but it seems to have disappeared.

Any ideas? :)

edit: All my 'shares' are gone too :(

---

### Post by Peter09 on 2009-05-18
Workgroup for the server is set up in the file /etc/samba/smb.conf

---

### Post by thered on 2009-05-18
I have it setup (samba), but using two ubuntu machines I shouldn't need samba anyway (should i?) - but I can't 'see' either machine on the network, locally or remotely.

---

### Post by Iowan on 2009-05-18
@Joe_Coppens: What version does the book cover? Some things have evolved a little. Samba seems different than on Gutsy.  

@thered: Samba is one option - I use it 'cuz I have windows machines, too.  Strictly Ubuntu (or linux) machines could use Samba, NFS, or SSHFS - to name a few (besides FTP). Clients are probably already installed in default setup, but to share FROM the machine will require the server portion to be installed.

---

### Post by thered on 2009-05-18
Iowan: Shouldn't I be able to see the local machine at least on places-> network? That would be a start.

nfs-common is installed and running on both machines.

<headscratching> :)

---

### Post by thered on 2009-05-19
<bump>

I can ping my other machine successfully :)

---

### Post by dmizer on 2009-05-19
> **Joe_Coppens said:**
> I have DSL and I'm using an Apple Time Capsule router with a 1TB HD. I'd like to be able to move files between my Macs and my Ubuntu netbook, and to access the hard drive on my router from the netbook.

You can access the time capsule by following the second link in my sig.

---

### Post by Macchi on 2009-05-20
Dmizer,

If I recall correctly I never had to make any special tweaks to talk between and Ubuntu machine and a Time Capsule. Samba should simply work. This is happening with more that one machine, thus I fear there is a regression bug hiding somewhere.

---

### Post by dmizer on 2009-05-20
> **Macchi said:**
> Dmizer,

If I recall correctly I never had to make any special tweaks to talk between and Ubuntu machine and a Time Capsule. Samba should simply work. This is happening with more that one machine, thus I fear there is a regression bug hiding somewhere.

I doubt that, as the "places" > "connect to server" has been (at best) buggy since I started using Ubuntu back in Warty.

Yes, samba should just work, but it's been my long time experience that it does not without a bit of tooling. Once you've configured everything, you'll never have to think about it again.

---

### Post by Iowan on 2009-05-20
> **dmizer said:**
> I doubt that, as the "places" > "connect to server" has been (at best) buggy since I started using Ubuntu back in Warty.Hmmm... Through Gutsy, I had better luck with Places>Connect to Server than I did with Places>Network.

---

### Post by dentog on 2009-05-20
Why I should go into Windows Network-WORKGROUP-... for see files on another Ubuntu computer

---

### Post by Iowan on 2009-05-20
Just my opinion... 
SMB was (originally) a Windows network.  Samba was created to let Unix (Linux) computers share files on a Windows network.  Samba shares (even on a Linux box) would be considered a Windows network.

---

### Post by Macchi on 2009-05-21
> **dentog said:**
> Why I should go into Windows Network-WORKGROUP-... for see files on another Ubuntu computer
This is a relevant question *dentog*, but sometimes it can be a good strategy to standardize file access across different machines and operating systems. This is a good application for Samba and the smb protocol.
 
For instance I store all my important files on a Ubuntu server with RAID 1 (mirrowed disks). All files can be accessed consistently from different machines through smb from Mac, Windows and Ubuntu clients.




PS: I still cannot access a Time Capsule from Ubuntu 9.04, but that worked with previous versions.

---

### Post by krishmish on 2009-05-21
In the Ubuntu Machine, install samba...
just go thru this...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


and i think u can nearly solve evry issue of urs...;)

---

### Post by Macchi on 2009-05-23
Back to an implicit topic in the thread:

Regarding file exchange with an Apple Time Capsule I recall that it worked through samba in previous versions of Ubuntu without tweaks.
Both in "Connect to Server..." and though "Network..."


Somehow it doesn't work in Jaunty.
I am the IT-Manager for an industry and we have such equipment in our offices and in our factory. Unfortunately, with our present workload we do not have time to test, diagnose and identify the cause of problem.
Thus our Ubuntu desktops are temporarily banned in some workstations before the problem is solved. 

Our colleague DMIZER says: 
> **dmizer said:**
> I doubt that ....[stuff removed]

I don't wish to start a controversy here, but:
Have you tested this yourself dmizer with Ubuntu and a Time Capsule?









PS: I personally believe that Ubuntu should NOT rely on command line tweaks for cross operation with the two other leading families of operating systems in the market (I mean Windows and Mac OS X).
However difficult it might be to achieve interoperability, it should be our goal. Otherwise Ubuntu may not manage to become a serious alternative for business enterprises. We should not settle for less. Otherwise the market may keep that (often erroneous) perception that GNU/Linux is exclusively for experts and hobbyists.

---

### Post by IThinker on 2009-05-23
> **dbuttera187 said:**
> i know nothing about macs but when I set up a workgroup at my house between 2 windows xp computers and my kubuntu 9.04, i used Samba. I'm not sure if that will work with mac's or not. The way i did it is I set up a windows workgroup between the two XP computers first, then i installed samba on the kubuntu machine. Samba allowed me to join the workgroup. I couldn't access my windows shares but i just used the share on the kubuntu machine anyway as the standard for the workgroup. hope that helps some :)

Can you explain to me how to install and configure samba, because I have the same problem as you had. I want to use two windows 2000 PCs to access a Kubuntu machine with samba installed. I will be very grateful if you'll explain how to do this step by step. Thanks in advance.

---

### Post by dmizer on 2009-05-23
> **Macchi said:**
> I don't wish to start a controversy here, but:
Have you tested this yourself dmizer with Ubuntu and a Time Capsule?

Sorry for not making myself more clear. I was replying to this point only:
> **Macchi said:**
> [...] thus I fear there is a regression bug hiding somewhere.
Since it has been both my personal experience and my observation with many others that browsing Windows shares (Time Capsule or otherwise) has been spotty at best, I doubt that we have regression.

I recently learned that Jaunty appears to have UFW (firewall) enabled by default. Unfortunately, this would cause problems with local file browsing.

Try this
```
sudo ufw disable
```
If you can browse to Time Capsule after that, then you'll want to either permanently disable UFW, or add rules for Samba browsing.

If that still doesn't work, you may have success with this: [http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

Even if you are able to get share browsing to work, mounting the share via /etc/fstab as outlined in my howto I linked earlier has many advantages including increased speed and larger file size transfer caps.

---

### Post by Macchi on 2009-05-24
> Dmizer wrote:
I recently learned that Jaunty appears to have UFW (firewall) enabled by default...

Of course, it must be the firewall! 
I will look at how to configure ufw properly for smb and test communication at work tomorrow. Personally I prefer to keep firewalls active and with quite restrictive rules. Normally I add a couple of layers of hw-firewalls and use different network zones for increased security on mixed environments. Obvioulsly I have always active sw-firewalls on machines with Windows and Mac, but eventually bypassed those security measures while making experiments with GNU/Linux. 
The actual network where we have the time capsule has no firewalls on the Ubuntu laptops/desktops, so I was not prepared for those problems...

PS: Unfortunately I have seen several regression bugs on GNU/Linux and feared it was another software error on Ubuntu. Hope that this time it is only a problem with the firewall. Samba (the software!) is fantastic and apparently has been very stable for a long time. But I have to mention that configuration in more complex environments may require time consuming experiments since there are lots of parameters. Documentation for Samba is very detailed, but that implies in a long time to read the material. I am glad that Ubuntu has a default configuration for smb that works in many environments.

---

### Post by Macchi on 2009-05-25
Well, some people asked about sharing files with computers running Windows, Mac OS X, and even other Linux distributions. There are several methods to accomplish that but cross platform file sharing is mastered by the smb protocol. It is a good solution and is almost ready for use in Ubuntu.

Please forgive me for multiple postings on the same subject but here are a few hints:

> 
Server Configuration for Ubuntu 8.04 and later:

For Ubuntu 8.04 and later, shared folders are created directly from the folder. Browse to the location of the folder you would like to share, right-click the folder, and choose Sharing Options. Click the Share this folder check box, and click Install Services. Enter your password, and the Samba server packages will be downloaded and installed. 

If you want to go deeper some good sources are:

1) Ubuntu Samba documentation:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

2) Linux Cookbook 
It has great cookbook recipes for fast Linux "meals" you will find in Carla Schroder's book published by the outstanding O'Reilly "Linux Cookbook". The book was published in 2004 but it is excellent to get a fast start and better insight in a wide range of techniques useful for GNU/Linux. Start to look at chapter 23 page 447. 
(there is an online preview):
[http://oreilly.com/catalog/9780596006402/preview.html](http://oreilly.com/catalog/9780596006402/preview.html)

3) [www.samba.org](www.samba.org)
The real source has it all, but may imprint some fear on the uninitiated.

---

### Post by dmizer on 2009-05-25
> **Macchi said:**
> Well, some people asked about sharing files with computers running Windows, Mac OS X, and even other Linux distributions. There are several methods to accomplish that but cross platform file sharing is mastered by the smb protocol. It is a good solution and is almost ready for use in Ubuntu.

FTP is another good solution for Mac/Windows/Ubuntu/anything-else file sharing. Good howto is located in the 5th link in my sig.

Yesterday, I wrote a howto for fixing network browsing issues, including firewall configuration: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

