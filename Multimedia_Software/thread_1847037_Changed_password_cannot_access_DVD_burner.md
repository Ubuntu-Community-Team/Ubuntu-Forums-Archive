---
title: "Changed password cannot access DVD burner"
date: 2011-09-20
forum: Multimedia Software
---

### Post by Loki*PI on 2011-09-20
Ubuntu 10.04 - my DVD/CD burner has been working for a long time, no problems.  I changed my password and now I cannot burn DVD/CD, I can make coasters. Says application - K3B for example - does not have access rights.

Tired to reset in K3b system setup - didn't work

Uninstalled and reinstalled K3b - didn't work

Same problem with other 'burning' applications.

I need to tweak access rights some place but I have no idea what or where.

I've read a number of threads but haven't found anything that helps.  Seems like this should be straight forward, in fact, why is there a problem at all?  Changing a password should flow through and reset as required. :(

Thanks for any suggestions on this.

---

### Post by Loki*PI on 2011-09-20
I've tried launching k3b and Brasero with sudo and that also fails.

---

### Post by Loki*PI on 2011-09-20
The files below appear to be what k3b is calling up, so I changed the permissions to:
        - /usr/bin/wodim - ugo+rwx
	- /usr/bin/growisofs - ugo+rwx
	- /usr/bin/cdrdao - ugo+rwx

don't know if this is a good idea, but it did NOT solve the problem.  I still get error message on no access rights.

---

### Post by BicyclerBoy on 2011-09-20
Just guessing..
Check your user is a member of the required cdrom group.

---

### Post by Loki*PI on 2011-09-20
Yes thanks I did that.  I'm in the group.

---

### Post by ron999 on 2011-09-20
Hi
Start K3b with this command:-
```
sudo k3b
```

Then "Modify Permissions".
Then "Defaults".

---

### Post by Loki*PI on 2011-09-20
Thanks Ron999:
I did that sudo k3b - then reset to default.

Then I did sudo k3b again because I saw a lot errors first time.  Now I get the following errors:

Error: "/var/tmp/kdecache-ric" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ric" is owned by uid 1000 instead of uid 0.
k3b(2122)/kdeui (kdelibs): Attempt to use QAction "view_projects" with KXMLGUIFactory! 
k3b(2122)/kdeui (kdelibs): Attempt to use QAction "view_dir_tree" with KXMLGUIFactory! 
k3b(2122)/kdeui (kdelibs): Attempt to use QAction "view_contents" with KXMLGUIFactory! 
k3b(2122)/kdeui (kdelibs): Attempt to use QAction "location_bar" with KXMLGUIFactory! 
ric@Raven:~$ Error: "/tmp/ksocket-ric" is owned by uid 1000 instead of uid 0.

---

### Post by ron999 on 2011-09-20
Hi
I see the 'Error' messages too, but K3b works OK.:D
Maybe your problem is not K3b related.

```
Error: "/var/tmp/kdecache-ron" is owned by uid 1000 instead of uid 0.
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/var/tmp/kdecache-ron" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-ron" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-ron" is owned by uid 1000 instead of uid 
```

---

### Post by aeiah on 2011-09-20
perhaps k3b didnt clear the tmp files after permission changes? try clearing (or safer, moving) k3b related files out of /tmp/

---

### Post by Loki*PI on 2011-09-20
Ron999 - hi Thanks, I see you have basically same errors. Maybe because we launch k3b with sudo?   

aeiah - Hi thank you also.  I don't know.  I've rebooted several times. I thought that cleared tmp file but I don't really know.

Late here I need to shut down for the night.  I'll follow up tomorrow.

Thanks again

---

### Post by Loki*PI on 2011-09-23
Anyone have any suggestions with this problem?  I still cannot get the DVD to burn.  What is the deal with Ubuntu and DVDs seems there is a long long standing problem in this area and it never gets really fixed.

---

### Post by BicyclerBoy on 2011-09-23
My 10.04.3 box burns DVD just fine..
There has been the odd brassero hiccup over the last year.

I think launching k3b as sudo was only suggested to help correct/remove config files.
You should not normally run programs as sudo. This is a good sign that something is wrong..

---

### Post by Loki*PI on 2011-11-25
Hello All - (I lost my internet connection for 2 months but back on now. Joys of living in the 3rd world.)

I still have the DVD burning problems. Now I also cannot read CD or DVDs. I've pulled the burner out and reinstalled it. Check connections all of that. Nothing.

I really don't think it is the burner, hardware. I still think I have some kind of configuration problem or rights problem. 

Also, if I put in a DVD movie I can open it and see the files, but cannot run the movie. I get the same error, no access rights.

Anyone any suggests?  

Thanks.

---

### Post by Loki*PI on 2011-11-26
Not getting much response on this. So my plan is to do a new install of 11.10.  Maybe that will fix things.

---

