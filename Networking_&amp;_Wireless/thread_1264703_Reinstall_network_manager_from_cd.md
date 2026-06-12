---
title: "Reinstall network manager from cd?"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by brsmits on 2009-09-12
Long story short, network-manager and net-tools got removed.  Any way to reinstall them from the boot cd?  (ubuntu 9.04) I cannot connect to ANYTHING at the moment so apt-get is a no go.  Trying to get this done without losing anything ( and typing this on my phone is kinda annoying)

---

### Post by lswb on 2009-09-12
First make sure that you have not simply deleted the "notification area" from the panel. The nm-applet needs the notification area to be visible. If necessary right-click on panel, select Add to Panel, select Notification Area. It may be necessary to log out/log back in to the desktop to see changes.

To answer your question:
Start synaptic, select Setting/Repositories and under the Ubuntu Software tab check the box to enable cdrom. Close the dialog, you may need to click "reload" once, then install NM and nm-applet. After networking is restored, deselect the cdrom, connect to the internet, clcik "reload" in synaptic again, and download the updated versions of NM and nm-applet.

---

### Post by casonmarine on 2009-09-28
so I did the above and I still get an error message saying:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg) Could not resolve 'archive.ubuntu.com'
same as above but also another saying :
/jaunty/main/i18n/translation-en_us.bz2
then it states that some index files failed to download etc...
I am working from my Wii currently so internet connection is good ...just not with the laptop. Thanks

---

### Post by dkolars on 2009-10-04
Having the same problem... cannot reinstall without internet connection... cannot re-install Jaunty without re-doing the entire HDD setup... sheesh...  May end up having to do that...  Linux has a way to go to get the networking up to speed, imho...  it was bad enuf in WIN, but this is ridiculous... I've spent about 20 hrs. trying to get my new laptop to connect wirelessly, and ended up deleting Network Manager in hopes of installing WICD... of course, after I deleted NM, I had no connection, and could not replace it with WICD... ya just can't always believe what you find in newsgroups!!  :-)

---

### Post by nila789 on 2009-10-04
You can run the CD again to repair the install if all else fails. That's one of the options listed. What I'm thinking is, that the network manager may not be on the cd, but during the install process, Kubuntu establishes the connection and downloads it.  I'm not sure, I thought it was on the CD.
_______________________________________________________
[football betting](http://betonline.com/sports-betting/football)  [Ski Holidays France](http://www.allmountainholidays.com/)

---

### Post by Iowan on 2009-10-05
Check System>Preferences>Startup Applications to see if Network Manager is gone - or is only "unchecked".

---

### Post by mikewhatever on 2009-10-05
> > **dkolars said:**
> Having the same problem... cannot reinstall without internet connection... cannot re-install Jaunty without re-doing the entire HDD setup... sheesh...  May end up having to do that...  Linux has a way to go to get the networking up to speed, imho...  it was bad enuf in WIN, but this is ridiculous... I've spent about 20 hrs. trying to get my new laptop to connect wirelessly, and ended up deleting Network Manager in hopes of installing WICD... of course, after I deleted NM, I had no connection, and could not replace it with WICD... ya just can't always believe what you find in newsgroups!!  :-)


To reinstall a package from the installation cd, you need to add the cd to the repositories' list. There is a nice GUI for that under System->Admin->Software Sources. 
Alternatively, **sudo apt-cdrom add && sudo apt-get update**. Now try installing.

I have to say that you problem is rather odd. First, you don't have to redo the entire HDD to reinstall Jaunty, just reuse the partitions and you are done after about half an hour. Second, you don't need to remove the Network Manager manually before installing Wicd.

---

### Post by slakkie on 2009-10-05
If you have a wired connection and setup DHCP on your router is dead easy to get a working connection. 

```

sudo dhclient eth0 

```

Then edit /etc/resolv.conf (as root):

```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

Nameservers are from opendns

---

### Post by toroblanco2002 on 2010-06-14
Thank you my friend for the advice I had the same issue here, deleted my network manager by accident and did not have any connection wired or wireless, even trying to install from the cd I was not sure how to do it. so I did a search and the only solutions I found was yours! You Rock man!! I hook up my cat5 wire. run the cmd sudo dhclient eth0 and I was up and running did not have to use the nameservers.  Thanks again and keep up the good work.:guitar:

---

### Post by fixxser on 2010-09-25
What worked for me was:
sudo dhclient eth0
I could not even use the CD as source.  It kept looking for internet for source.

---

### Post by fisheater on 2010-10-15
Your cmd saved the day.

My problem was similar: [http://ubuntuforums.org/showthread.php?t=1596911](http://ubuntuforums.org/showthread.php?t=1596911)

The fix: sudo dhclient eth0

The power of open source is superb.

Thanks for the help.

FE!

---

