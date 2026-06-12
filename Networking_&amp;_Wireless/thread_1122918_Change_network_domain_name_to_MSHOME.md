---
title: "Change network domain name to MSHOME"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Straumoy on 2009-04-11
Hello,

I'm running Ubuntu 8.10 on my laptop and been fooling a bit around with sharing folders over the home network.

We've got 3 other computers, 1 running XP Pro, 1 running XP Home and 1 running Vista Home Premium. All these computers are part of MSHOME domain and can see each other on the network, share printers, folders and files.

So I turned to my laptop and turned on Sharing on the Public folder under my Home dir. From there I could access windows network, found myself and MSHOME. After some tinkering around with username\password I was able to access my vista from unbuntu and vice versa. This was alarmingly easy by the way.

Now on to the actual "problem". I wanted my laptop to be under MSHOME domain, but by default it is set to WORKGROUP. Digging around, [I found something that made sense]("https://answers.launchpad.net/ubuntu/+question/29389"), but...

I did what they suggested and nothing happened. Fair enough, take a reboot then I figured. Sure enough, when I check on my vista computer, everyone is under MSHOME and all is good. However, when I go to Places | Network | Windows Network nothing happens. Well, it loads for a bit (the toe animation on the upper right corner runs), but then zero zip and nada.

Get one error message first though, which reads:
Unable to mount location
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

So I went back in and changed the workgroup name to MSHOME1, took another reboot and now under windows network I get:
MSHOME - all computers listed, included my laptop, everything works like a charm I might add.;)
MSHOME1 - just laptop):P
WORKGROUP - get an error saying: 
Unable to mount location
Failed to retrieve share list from server

While things are working, I find it irritating that there are 3 domains when there's only need for 1. 

So any ideas? Surely it should be possible to get an ubuntu machine to work in the same domain as windows computers.

---

### Post by bab1 on 2009-04-11
The term "domain" has more than one meaning.  An Internet Domain such as ubuntuforums.org is different from a MSHOME domain.  The MSHOME domain is really a workgroup and it is only needed for browsing Windows type networks (Samba).

If you want all the hosts to be in the same browsing domain (workgroup), then do like you started to do and edit the /etc/samba/smb.conf as so:```
# Workgroup/NT-domain name your Samba server will part of
        workgroup = MSHOME
```

You may have been a little to quick on the trigger for Samba to recognize the addition to the workgroup.  There is a routine for updating who and what is in the workgroup (Browse Master).  This usually takes about 15 minutes at first.  I have seen it on my network when I make changes or a user with shares first comes online.

If you made your shares via Gnome/Nautilus you may have to remove the sharing and after a bit add them again.  This sounds like your problem here:```
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
```

---

### Post by Straumoy on 2009-04-12
Hello again,

followed your advice and after a couple of reboots along with some share\unshare of folders things are now working fine.

Thanks a lot:)

---

