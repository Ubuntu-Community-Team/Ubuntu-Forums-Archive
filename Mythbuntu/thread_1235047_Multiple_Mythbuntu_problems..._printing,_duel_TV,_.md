---
title: "Multiple Mythbuntu problems... printing, duel TV, and TV exit"
date: 2009-08-08
forum: Mythbuntu
---

### Post by tony.morse on 2009-08-08
Hi All,
After weeks of messing with ubuntu and MythTV I finally tried the mythbuntu live cd and havn't looked back, its great!!!

Anyway I'm left with a few problems and would appreciate some advice as I've searched the forums and and am still stuck, so in no particular order here they are....

1)  Printing: I want a desktop too so I've installed the standard Gnome which is great but I can't seem to set up and find my HP usb printer???  I've followed a few guides and installed hplips and hplips-gui but that hasn't helped.  The printer is not found and the configuration utility lists printer ports, serial ports, and network printer options but no usb option.

2)  Duel TV:  I have a nova t-500 duel tuner card, but it seems I can only use one tuner.  Myth backend sees both tuners, and both have scanned so I have DVB:0 and DVB:1.  I've set up a single source and then 2 links to that source, one from each tuner, but the system behaves as if it only has one tuner.  Any ideas???

3)  When I watch TV, if I press escape it exits back to the desktop rather than back to the MythTV menu.  (doesn't always do this but usually)

4)  Channel loss:  Sometimes I only get a few channels.  A reboot usually fixes this but why does this happen???

Please please help me sort this lot out.

Thanks in advance

---

### Post by tony.morse on 2009-08-18
bump

---

### Post by tony.morse on 2009-08-19
Ok the printer is fixed (install CUPS and HPlips)

BUT I can't record (except live TV??)

any ideas?

---

### Post by tgm4883 on 2009-08-19
Lets try your backend logs located at /var/log/mythtv/mythbackend.log

---

### Post by kadafi69 on 2009-08-20
> **tony.morse said:**
> 
2)  Duel TV:  I have a nova t-500 duel tuner card, but it seems I can only use one tuner.  Myth backend sees both tuners, and both have scanned so I have DVB:0 and DVB:1.  I've set up a single source and then 2 links to that source, one from each tuner, but the system behaves as if it only has one tuner.  Any ideas???

3)  When I watch TV, if I press escape it exits back to the desktop rather than back to the MythTV menu.  (doesn't always do this but usually)


2) this is something to do with either the firmware or the drivers, i cant remember which, but the latest version is not the best, and reverting to a previous version is the cure. this problem has been dealt with on here before so have a good search for it.

3) I've recently had this problem, and it stems from Pulse, removing Pulse solves the problem. Again this has been an issue on these forums, so have a search and you'll find more details.

---

### Post by roundhay on 2009-08-20
I have had problems recording when I upgraded to mythbuntu 9.04.

I solved this on 2 machines by reconfiguring the myth database

```
sudo dpkg-reconfigure mythtv database
```

I can't remeber exectly how i came to try this but it was mentioned on a forum (not this one).

Before I didi this I could only record what i was watching, I can now schedule and have had no problems.

---

### Post by tony.morse on 2009-09-02
hmm still stuck...
I've tried both the new and old drivers.  Do I have to remove the new driver before Install the previous on?

I've tried sudo dpkg-reconfigure mythtv database
and I get this in response...

Package `database' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: database is not installed

What am I doing wrong?

---

### Post by tony.morse on 2009-09-11
bump

---

### Post by SiHa on 2009-09-11
I think it should be ```
sudo dpkg-reconfigure mythtv-database
```(note the second hyphen).

Otherwise you're trying to reconfigure two separate packages, 'mythtv' and 'database' and, no surprises there is no package installed called 'database'.

Hope this helps.

---

