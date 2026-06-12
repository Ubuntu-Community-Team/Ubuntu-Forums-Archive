---
title: "office file sharing"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by tyhee88 on 2009-09-13
I'm looking to set up to share files from my secretary's conputer, which was simple enough (I set it up using a wizard) in Win XP, and am hoping it will be simple enough for me to do in Ubuntu 9.04.

I'm not entirely a noob, but could probably reasonably be described as a perpetual novice.  My understanding of a terminal pretty much ends at ls/cd/mv and such file management basics.  My experience with networking is next to nil-I set up sharing of files in Windows using a network wizard in XP Home, and set up my small home network using a wizard that came with my router at home, again using XP Home.  That's not enough for me to understand where to get started in Ubuntu.

The small office has 2 computers, one for me, one for my secretary.  I also use a notebook computer at times.

Back when I was on Windows, I had a local tech set up a simple Windows network, then I set up some file sharing later using the network wizard.  We have ADSL through a Linksys, I believe a WRT54G, wireless router.   The router is next to my computer and I am attached by ethernet cable.  My assistant's computer is on wireless, an Artheros card that gets automatically detected and configued when installing Jaunty.  (The notebook wireless card is a dreaded Broadcom, but also is configured easily in Jaunty without needing to download a driver specially.)

Her computer runs Ub 9.04.  Mine dual boots Ubuntu 9.04 and Win XP Home (the latter usually only for a few minutes twice a month for one specific task.)  My notebook dual boots Ubuntu 9.04 and Win Vista Home Basic (the latter last booted the weekend I received the notebook.)   The dual boots are on ext3 partitions.  I may or may not upgrade to Karmic but do expect to upgrade (or reinstall) to the next LTS.

Previously, when her computer had Windows XP Home, I'd gone on her computer and set up file sharing so I'd have access to files on her hard drive.  Her computer now has a different hard drive and only has Ub 9.04.  I'd still like to share files from her computer, and be able to also see them if I use my notebook.  If I read correctly Samba is for connecting to Windows, which is not what I'm seeking to do, and there might be some advantage, in case my wireless code is cracked, if Windows machines can't share the files.

When I'd set up the sharing, my secretary ran Win XP Home.  Now that it has a new hard drive, with only Ub 9.04, I went on her machine, right clicked on the folders I wanted access to, downloaded the necesary files and set up file sharing.  From my machine, I tried to access the folders in Ub 9.04 through Places-Network.  The only network that appears is Windows Network (same as it was before my assistant's computer was only Ubuntu) and when I try to access it, it looks for the old folders I was set up access before, her folders on Windows, which are no longer on her computer.  

I have no idea where I'm starting or the best way to go.  Could someone let me know what I should be looking at to figure it out?  If this makes sense, my preference is for someone to point me in the right direction to get started, with just enough info for me to look things up so the extra time I spend looking things up will be relevant to what I'm doing.    

Thanks, all.


                                                                  bob

---

### Post by swerdna on 2009-09-14
The key file is smb.conf located at /etc/samba/smb.conf.

Have a look at this to follow what I'm saying: 
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

Check they both have the same workgroup name.

Add the secretary's username to the samba user database on her machine so you can access her files using her username/password when (on your machine) you are asked for her creds to access her machine.

Set both machines to be [Local Master Browsers]("http://ubuntu.swerdna.org/lanprimer/smb.conf.lmb_not_pmb.txt") but not Preferred Masters (see the tute).

Set the name resolve order to this:```
name resolve order = bcast host lmhosts wins
```

Disable firewalls temporarily while you get the network going. Use this command to do that:```
sudo ufw disable
```

See the [homes] share in the tutorial. You can access all her files using that.

---

### Post by tyhee88 on 2009-09-17
Thanks for the reply.

I was hoping to avoid Samba as I didn't want Windows machines able to connect to the network.  

Would I be able to use a new VPN configured from my gateway using Ubuntu?  Am I on the wrong track?

                                                  bob

> **swerdna said:**
> The key file is smb.conf located at /etc/samba/smb.conf.

Have a look at this to follow what I'm saying: 
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

Check they both have the same workgroup name.

Add the secretary's username to the samba user database on her machine so you can access her files using her username/password when (on your machine) you are asked for her creds to access her machine.

Set both machines to be [Local Master Browsers]("http://ubuntu.swerdna.org/lanprimer/smb.conf.lmb_not_pmb.txt") but not Preferred Masters (see the tute).

Set the name resolve order to this:```
name resolve order = bcast host lmhosts wins
```Disable firewalls temporarily while you get the network going. Use this command to do that:```
sudo ufw disable
```See the [homes] share in the tutorial. You can access all her files using that.

---

### Post by swerdna on 2009-09-17
I misunderstood, thought you wanted interoperability with windows. If you're not including windows boxes, you can use NFS, the Linux file sharing system.

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
and
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

