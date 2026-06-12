---
title: "Share internet through win XP"
date: 2006-03-03
forum: Networking &amp; Wireless
---

### Post by TheChad on 2006-03-03
Right now I have a laptop running Win XP that is connected to my college's network by wire.  I have internet connection sharing enabled on that connection.  I've been able to do a wireless adhoc connection to my ubuntu box by doing:

sudo iwconfig eth1 mode Ad-Hoc
sudo iwconfig eth1 ESSID MYNETWORKNAME

So far all I can see is that both are connected, but not actually do anything.  Mostly I would like to have the ubuntu box access the internet by going to the laptop through wireless and then out through the wired connection.  A little file sharing wouldn't hurt either.

---

### Post by eriefisher on 2006-03-03
You might have to set a AD-hoc network on your XP machine for a through connection in wireless. This would make XP act like a router (I think). As for file sharing, you'll need to set up Samba so Linux can talk to Windows. Can you ping back and forth?

eriefisher

---

### Post by soonindallas on 2006-03-03
you need to bridge the 2 network connections in XP.  I think you just need to select the 2 connections in "network connections" (or whatever), right click and select bridge.

---

### Post by eriefisher on 2006-03-03
soonindallas might be right there.

I did a similar set up wired with dial up. I did not have to bridge or anything but I had to disable the XP firewall for my ethernet connection and also had to use a crossover cable to get it to work. I don't know with wireless but without a router or switch you need to crossover to communicate back and forth. I think by setting up a AD-HOC network in XP it will be switched.

eriefisher

---

### Post by TheChad on 2006-03-03
Sorry guys, it was a simple fix.  The above mentioned steps allowed me to enable an ad-hoc connection which windows successfully connected to.  It turns out PCCillin's firewall was being naughty.  Internet connection sharing is working fine.  I just have to figure out how to make my firewall behave and figure out filesharing.

---

### Post by soonindallas on 2006-03-03
glad you got it working!

file sharing is easy.  you need samba on your ubuntu box,I think it's part of the standard install.

Samba is a linux app that will allow you to share folders, files and printers both ways with Windows computers over a network.

I have my Ubuntu box networked with a WinXP box. The XP box has a printer that is shared and I print from Ubuntu to this printer.

Check in the file /etc/samba/smb.conf that samba is using the same windows workgroup name as your windows box (MSHOME by default).

whenever you change smb.conf you need to restart samba so the new config gets loaded:

```
sudo /etc/init.d/samba restart
```

On your windows box you need to enable sharing of your files and printers as necessary (in folder properties and printer properties) and check in the XP firewall exceptions that these services are allowed.

you can configure your shares on ubuntu using system>administration>shared folders.

search the forums a bit and you'll find tons of information about samba configuration.

---

