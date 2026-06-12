---
title: "Warning - PPA update removed Mythtv"
date: 2009-11-04
forum: Mythbuntu
---

### Post by Al_Vampyre on 2009-11-04
Just a warning guys, I applied an update this morning from PPA and it has completed uninistalled mythtv!

*EDIT - Just reinstalled and tried again - it wasn't the PPA repos that did it, it was 0.22 from the mythbuntu-repos that caused the problem.*

It said something about a partial upgrade, contents of /var/log/dist-upgrade below
```

Log time: 2009-11-04 08:13:41.804654
Starting
Starting 2
Investigating mythtv-frontend
Package mythtv-frontend has broken Depends on mythtv-common
Investigating mythtv-transcode-utils
Package mythtv-transcode-utils has broken Depends on mythtv-common
Investigating mythtv-backend
Package mythtv-backend has broken Depends on mythtv-common
Investigating mythtv
Package mythtv has broken Depends on mythtv-frontend
Investigating mythtv-backend-master
Package mythtv-backend-master has broken Depends on mythtv-backend
 Try to Re-Instate mythtv-frontend
Investigating mythtv-frontend
Package mythtv-frontend has broken Depends on mythtv-common
  Considering mythtv-common 56 as a solution to mythtv-frontend 12
  Removing mythtv-frontend rather than change mythtv-common
 Try to Re-Instate mythtv-transcode-utils
Investigating mythtv-transcode-utils
Package mythtv-transcode-utils has broken Depends on mythtv-common
  Considering mythtv-common 56 as a solution to mythtv-transcode-utils 5
  Removing mythtv-transcode-utils rather than change mythtv-common
 Try to Re-Instate mythtv-backend
Investigating mythtv-backend
Package mythtv-backend has broken Depends on mythtv-common
  Considering mythtv-common 56 as a solution to mythtv-backend 4
  Removing mythtv-backend rather than change mythtv-common
Investigating mythmusic
Package mythmusic has broken Depends on mythtv-frontend
  Considering mythtv-frontend 12 as a solution to mythmusic 1
  Removing mythmusic rather than change mythtv-frontend
 Try to Re-Instate mythtv
Investigating mythtv
Package mythtv has broken Depends on mythtv-database
  Considering mythtv-database 4 as a solution to mythtv 1
  Removing mythtv rather than change mythtv-database
Investigating mytharchive
Package mytharchive has broken Depends on mythtv-transcode-utils
  Considering mythtv-transcode-utils 5 as a solution to mytharchive 1
  Removing mytharchive rather than change mythtv-transcode-utils
Investigating mythgallery
Package mythgallery has broken Depends on mythtv-frontend
  Considering mythtv-frontend 12 as a solution to mythgallery 1
  Removing mythgallery rather than change mythtv-frontend
Investigating mythmovies
Package mythmovies has broken Depends on mythtv-frontend
  Considering mythtv-frontend 12 as a solution to mythmovies 1
  Removing mythmovies rather than change mythtv-frontend
 Try to Re-Instate mythtv-backend-master
Investigating mythtv-backend-master
Package mythtv-backend-master has broken Depends on mythtv-database
  Considering mythtv-database 4 as a solution to mythtv-backend-master 1
  Removing mythtv-backend-master rather than change mythtv-database
Investigating mythweather
Package mythweather has broken Depends on mythtv-frontend
  Considering mythtv-frontend 12 as a solution to mythweather 1
  Removing mythweather rather than change mythtv-frontend
Investigating mythvideo
Package mythvideo has broken Depends on mythtv-frontend
  Considering mythtv-frontend 12 as a solution to mythvideo 1
  Removing mythvideo rather than change mythtv-frontend
Done
ERROR:root:NvidiaDetection returned a error: datadir './modaliases/' not found
MarkUpgrade() called on a non-upgrable pkg: 'mythbuntu-desktop'
Log time: 2009-11-04 08:14:59.726434
Starting
Starting 2
Investigating libtorrent-rasterbar5
Package libtorrent-rasterbar5 has broken Depends on libboost-thread1.38.0
  Considering libboost-thread1.38.0 10002 as a solution to libtorrent-rasterbar5 1
  Removing libtorrent-rasterbar5 rather than change libboost-thread1.38.0
Investigating python-libtorrent
Package python-libtorrent has broken Depends on libboost-thread1.38.0
  Considering libboost-thread1.38.0 10002 as a solution to python-libtorrent 0
  Removing python-libtorrent rather than change libboost-thread1.38.0
Done
Starting
Starting 2
Investigating libswt-gtk-3.4-java
Package libswt-gtk-3.4-java has broken Depends on libswt-gtk-3.4-jni
  Considering libswt-gtk-3.4-jni 10001 as a solution to libswt-gtk-3.4-java 0
Package libswt-gtk-3.4-java has broken Depends on libswt3.4-gtk-jni
  Or group remove for libswt-gtk-3.4-java
Done
Starting
Starting 2
Investigating libesd-alsa0
Package libesd-alsa0 has broken Depends on esound-common
  Considering esound-common 10002 as a solution to libesd-alsa0 6
  Removing libesd-alsa0 rather than change esound-common
Investigating esound-clients
Package esound-clients has broken Depends on libesd-alsa0
  Considering libesd-alsa0 6 as a solution to esound-clients 0
Package esound-clients has broken Depends on libesd0
  Considering libesd0 2 as a solution to esound-clients 0
  Or group remove for esound-clients
Package esound-clients has broken Depends on esound-common
  Considering esound-common 10002 as a solution to esound-clients 0
  Removing esound-clients rather than change esound-common
Investigating libgnome2-0
Package libgnome2-0 has broken Depends on libesd-alsa0
  Considering libesd-alsa0 6 as a solution to libgnome2-0 16
  Added libesd-alsa0 to the remove list
Package libgnome2-0 has broken Depends on libesd0
  Considering libesd0 2 as a solution to libgnome2-0 16
  Fixing libgnome2-0 via keep of libesd-alsa0
Investigating libesd-alsa0
Package libesd-alsa0 has broken Depends on esound-common
  Considering esound-common 10002 as a solution to libesd-alsa0 6
  Removing libesd-alsa0 rather than change esound-common
Investigating libgnome2-0
Package libgnome2-0 has broken Depends on libesd-alsa0
  Considering libesd-alsa0 6 as a solution to libgnome2-0 16
  Added libesd-alsa0 to the remove list
Package libgnome2-0 has broken Depends on libesd0
  Considering libesd0 2 as a solution to libgnome2-0 16
  Fixing libgnome2-0 via keep of libesd-alsa0
Investigating libesd-alsa0
Package libesd-alsa0 has broken Depends on esound-common
  Considering esound-common 10002 as a solution to libesd-alsa0 16
  Removing libesd-alsa0 rather than change esound-common
Investigating libgnome2-0
Package libgnome2-0 has broken Depends on libesd-alsa0
  Considering libesd-alsa0 10002 as a solution to libgnome2-0 16
Package libgnome2-0 has broken Depends on libesd0
  Considering libesd0 2 as a solution to libgnome2-0 16
  Or group remove for libgnome2-0
Investigating libbonoboui2-0
Package libbonoboui2-0 has broken Depends on libgnome2-0
  Considering libgnome2-0 16 as a solution to libbonoboui2-0 12
  Removing libbonoboui2-0 rather than change libgnome2-0
Investigating libgnome2-perl
Package libgnome2-perl has broken Depends on libbonoboui2-0
  Considering libbonoboui2-0 16 as a solution to libgnome2-perl 9
  Removing libgnome2-perl rather than change libbonoboui2-0
Investigating libpanel-applet2-0
Package libpanel-applet2-0 has broken Depends on libbonoboui2-0
  Considering libbonoboui2-0 16 as a solution to libpanel-applet2-0 5
  Removing libpanel-applet2-0 rather than change libbonoboui2-0
Investigating gnome-power-manager
Package gnome-power-manager has broken Depends on libpanel-applet2-0
  Considering libpanel-applet2-0 16 as a solution to gnome-power-manager 4
  Removing gnome-power-manager rather than change libpanel-applet2-0
Investigating libgnomeui-0
Package libgnomeui-0 has broken Depends on libbonoboui2-0
  Considering libbonoboui2-0 16 as a solution to libgnomeui-0 4
  Removing libgnomeui-0 rather than change libbonoboui2-0
Investigating gdm
Package gdm has broken Depends on libbonoboui2-0
  Considering libbonoboui2-0 16 as a solution to gdm 3
  Removing gdm rather than change libbonoboui2-0
Investigating xulrunner-1.9.1-gnome-support
Package xulrunner-1.9.1-gnome-support has broken Depends on libgnome2-0
  Considering libgnome2-0 16 as a solution to xulrunner-1.9.1-gnome-support 2
  Removing xulrunner-1.9.1-gnome-support rather than change libgnome2-0
Investigating firefox-3.5-gnome-support
Package firefox-3.5-gnome-support has broken Depends on xulrunner-1.9.1-gnome-support
  Considering xulrunner-1.9.1-gnome-support 16 as a solution to firefox-3.5-gnome-support 1
  Removing firefox-3.5-gnome-support rather than change xulrunner-1.9.1-gnome-support
Investigating mythbuntu-desktop
Package mythbuntu-desktop has broken Depends on gdm
  Considering gdm 16 as a solution to mythbuntu-desktop 0
  Removing mythbuntu-desktop rather than change gdm
Done
Starting
Starting 2
Investigating libtorrent-rasterbar5
Package libtorrent-rasterbar5 has broken Depends on libboost-filesystem1.38.0
  Considering libboost-filesystem1.38.0 10002 as a solution to libtorrent-rasterbar5 1
  Removing libtorrent-rasterbar5 rather than change libboost-filesystem1.38.0
Investigating python-libtorrent
Package python-libtorrent has broken Depends on libboost-filesystem1.38.0
  Considering libboost-filesystem1.38.0 10002 as a solution to python-libtorrent 0
  Removing python-libtorrent rather than change libboost-filesystem1.38.0
Done
Starting
Starting 2
Investigating libswt-gtk-3.4-java
Package libswt-gtk-3.4-java has broken Depends on libswt-gtk-3.4-jni
  Considering libswt-gtk-3.4-jni 10001 as a solution to libswt-gtk-3.4-java 0
Package libswt-gtk-3.4-java has broken Depends on libswt3.4-gtk-jni
  Or group remove for libswt-gtk-3.4-java
Done
```

Whats the easiest way of getting things back up and running??

---

### Post by kilowhisky on 2009-11-04
I seem to be on the same boat. I had a working mythbutu 9.10, mythtv .22 rc1 installation and then i installed the mythbuntu repos and everything went fubard.  It said that i needed to do a partial update in order to install the new packages, so after i said ok to that it went ahead and deleted mythbackend and mythfrontend!!!  

Now when i try to apt-get it back in i get this error. 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.22.0+fixes22594-0ubuntu1) but 0.22.0+fixes22679-0ubuntu0+mythbuntu3 is to be installed
                  Depends: mythtv-transcode-utils (= 0.22.0+fixes22594-0ubuntu1) but it is not going to be installed
  mythtv-frontend: Depends: mythtv-common (= 0.22.0+fixes22594-0ubuntu1) but 0.22.0+fixes22679-0ubuntu0+mythbuntu3 is to be installed
E: Broken packages

```

I tried removing the repository in the sources.list and dpkg-reconfigured the mythbuntu repos.  It won't let me install mythtv!!!!  Can anyone help???

---

### Post by prmedloc on 2009-11-04
Mine was offering to do that, fortunately i checked details and have not run it.

---

### Post by Al_Vampyre on 2009-11-04
> **prmedloc said:**
> Mine was offering to do that, fortunately i checked details and have not run it.

Lol, thanks for your help! ;)

I'm thinking this may be a good time to add the second hard drive I've been planning but if I decide not to if I add mythtv in from synaptic will it overwrite my existing database?

---

### Post by joshoekstra on 2009-11-04
With daily rebuilds (it seems) it might happen that some packages take a little longer to build. In my situatation myth-common is the last to roll in and after that an upgrade is possible.
I've been bit too many times to do partial installs, I always check out the revision-number before I continue.

---

### Post by tgm4883 on 2009-11-04
Don't do partial upgrades. It's not the PPA/mythbuntu-repos that removed your packages. The computer did exactly what you told it to do.

---

### Post by Al_Vampyre on 2009-11-04
> **tgm4883 said:**
> Don't do partial upgrades. It's not the PPA/mythbuntu-repos that removed your packages. The computer did exactly what you told it to do.

I know, sorry, I didn't mean it to sound accusatory, I just didn't want anyone else falling into the same trap I did!

---

### Post by kilowhisky on 2009-11-04
Well the question is why did it give me the option to do partial upgrades?  Is it safe now to using the mythbuntu weekly builds repos?

BTW i got mythtv reinstalled by removing the repos and then completely removing any package that has to do with mythtv. After a restart it allowed me to reinstall mythtv.

---

### Post by tgm4883 on 2009-11-04
> **kilowhisky said:**
> Well the question is why did it give me the option to do partial upgrades?  Is it safe now to using the mythbuntu weekly builds repos?

BTW i got mythtv reinstalled by removing the repos and then completely removing any package that has to do with mythtv. After a restart it allowed me to reinstall mythtv.

Cause that is how upgrades work in debian based systems?

---

### Post by eamonn_sullivan on 2009-11-05
> **tgm4883 said:**
> Cause that is how upgrades work in debian based systems?

Please avoid belittling people. I've been using Linux since 1994, Debian since the beginning and Ubuntu since Warty and even I got caught running in circles for a couple of hours trying to figure out why all of my mythtv packages were being held back. The mythbuntu repo is broken and has been for at least a couple of days now, which would be very hard for the average user to figure out. They need to fix the PPA process to avoid adding packages until all of their dependencies are built.

---

### Post by cat2005 on 2009-11-05
Forgive me, but what is "PPA"?

---

### Post by Dewey_Oxberger on 2009-11-05
PPA = "Personal Package Archive"

Basically it's a cool box of rocks.  It lets developers submit some source code.  It builds it into packages that are easy to install (with out all that "compile it yourself" complexity that trips up noobs like me).

You just go to Software Sources, add somebodies PPA and you can get their code.

Mythbuntu has a ppa for the current builds of mythtv and the utilities.

Have a read of: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

---

### Post by Dewey_Oxberger on 2009-11-05
I'm confused here.

I've seen posted that using the nvidia ppa to update Karmic to nv 190 will remove mythtv.  I've checked and it looks like nvidia-190-libvdpau wants to uninstall 185 libvdpau and then take all of mythtv with it.

This is not using weekly builds for mythbuntu.

Is this an nvidia ppa problem or a mythtv problem?

Is this related to the original issue posted here?

---

### Post by suffice on 2009-11-06
the myth removal has to do with the fact that when myth was compiled it was done specifically for the 185.X or the 180.X.  To get a functioning myth qith 190.X you have to reinstall it.  

I have been looking in my myth problems for a few days now (getting vdpau working, a wierd squished picture (1.85:1 with 19:9 video), not coverering the the gnome panel) and some others.  That is what i read about the driver update.

I have a GT220 and want to take advantage of it so I have just installed the 190.X, though have yet to test that out.

Apparantly they are making really soon a driver / myth that is independant. I think we wont see tah tuntil 10.04

---

### Post by Dewey_Oxberger on 2009-11-06
Ahh, this is something I've never done.  Are you saying use apt-get to uninstall 185 (it will take mythtv with it), then install 190, then install mythtv?

Or is mythtv totally cooked for 185?

I assume all my myth settings will stay since they are in the database.

If I uninstall 185 what packages do I need to install to get mythbuntu back to it's full glory?

---

### Post by suffice on 2009-11-07
basically what i did was just install the 190 repos and then some packages and it took myth off....but then i just installed the mythbuntu-desktop pacakge again and things were back to normal.

no need to uninstall the 185...it just overrides it i guess.

---

### Post by suffice on 2009-11-07
basically what i did was just install the 190 repos and then some packages and it took myth off....but then i just installed the mythbuntu-desktop pacakge again and things were back to normal.

no need to uninstall the 185...it just overrides it i guess.

---

### Post by williammanda on 2009-12-04
Going back to the original question...why was user getting a partial update? How do you get around that?

---

### Post by tgm4883 on 2009-12-05
> **williammanda said:**
> Going back to the original question...why was user getting a partial update? How do you get around that?

There are two possible reasons for it doing that. We would have to see the output of apt-get -s dist-upgrade to figure it out.

---

