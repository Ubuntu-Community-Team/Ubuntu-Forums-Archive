---
title: "Embedded Quicktime  in Firefox Problems"
date: 2008-06-26
forum: Multimedia Software
---

### Post by marrowhk on 2008-06-26
*I have no problems with standard embedded media files but some new quicktime sites seem troublesome!*

**Could anyone tell me how to play the following site (no.1) in Firefox?**

This one [COLOR="DarkRed"]**won't**[/COLOR] play
1. [http://www.apple.com/trailers/disney/walle/teaser2_large.html](http://www.apple.com/trailers/disney/walle/teaser2_large.html)

This one [COLOR="Green"]**will**[/COLOR] play (gnome-mplayer + FF mediaplayerconnectivity plugin)
2. [http://www.apple.com/trailers/weinstein/thelongshots/trailer/](http://www.apple.com/trailers/weinstein/thelongshots/trailer/) 

Neither gecko-mediaplayer or totem or mplayer firefox plugins on their own seem to be able to cope with No.1 above.

Any ideas :confused:

---

### Post by ubuntu-freak on 2008-07-02
Complete part 1 and 2 of my [howto](ubuntuforums.org/showthread.php?t=766683), then follow the instructions found in the troubleshooting section.

---

### Post by Riffer on 2008-07-05
That worked for me :)

Why is it that quicktime is so ummmm... quirky, I've always had trouble with it working consistently even in windows.

---

### Post by ubuntu-freak on 2008-07-05
> **Riffer said:**
> That worked for me :)

Why is it that quicktime is so ummmm... quirky, I've always had trouble with it working consistently even in windows.

 
I'm not sure, you wouldn't think Apple would want to be so inconsistant and overcomplicate things.

---

### Post by jaygo on 2008-08-10
This looked like fun until I found out all of the packages it was going to upgrade or install: > The following extra packages will be installed (kubuntu 8.04):
  cups-common cupsys-common findutils gtk2-engines-pixbuf hplip-data libc6 libc6-dev libc6-i686 libcairo2 libcups2 libcupsys2 libgcrypt11 libgcrypt11-dev libglib2.0-0
  libgnomecanvas2-0 libgnutls26 libgtk2.0-0 libgtkhtml2-0 libpango1.0-0 libpango1.0-common libpopt0 libselinux1 libtalloc1 libwbclient0 libxcb-render-util0 libxcb-render0
  lsb-base python-cupshelpers python-usb samba-common smbclient winbind
Suggested packages:
  glibc-doc manpages-dev rng-tools libgcrypt11-doc gnutls-bin ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp smbfs
Recommended packages:
  libglib2.0-data libgtk2.0-bin
The following packages will be REMOVED:
  cupsys-driver-gutenprint foomatic-db-hpijs hpijs hpijs-ppds hplip hplip-gui kubuntu-desktop libcupsys2-dev libgail-common libgail18 samba splix
The following NEW packages will be installed:
  cups-common gecko-mediaplayer gnome-mplayer libcups2 libgnutls26 libtalloc1 libwbclient0 libxcb-render-util0 libxcb-render0 python-cupshelpers python-usb
The following packages will be upgraded:
  cupsys-common findutils gtk2-engines-pixbuf hplip-data libc6 libc6-dev libc6-i686 libcairo2 libcupsys2 libgcrypt11 libgcrypt11-dev libglib2.0-0 libgnomecanvas2-0 libgtk2.0-0
  libgtkhtml2-0 libpango1.0-0 libpango1.0-common libpopt0 libselinux1 lsb-base samba-common smbclient winbind
23 upgraded, 11 newly installed, 12 to remove and 1038 not upgraded.
Need to get 39.6MB of archives.
After this operation, 7426kB disk space will be freed.


---

### Post by eye208 on 2008-08-10
Both clips work fine in Ubuntu's default media player plug-in. Make sure all the necessary GStreamer plug-ins are installed. Here's how to do it:

Open the page in Firefox as usual. If the media player plug-in lacks video and/or sound, right click it and select "Open in Movie Player". This will open the stream in a separate window. At this point you will automatically be asked to install additional plug-ins, if required. After installing the plug-ins, close the media player window and reload the page in Firefox. The stream should now play fine.

Edit: Most of the required plug-ins are in the "multiverse" repository. Make sure it is enabled, otherwise the plug-ins may not be found.

---

### Post by marrowhk on 2008-08-15
ubuntu-freak : Great help, thanks -- works 4 me!! :)

---

### Post by stwert on 2008-08-22
Ok, so I tried ubuntu-freak's quicktime fix... and it seems to have sort of worked, with flickering video, so I don't know what's up with that. The real problem though, is that it seems to have removed gnucash, which was kind of important, as well as all the games that came with the system and I don't know what else.
I don't know what's up with this. I followed the directions carefully. The only thing I can think of is the "Don't let update manager upgrade", which I didn't think was happening.
So some thoughts on this would be nice. I'll reinstall gnucash, hopefully it'll be fine.

---

### Post by ubuntu-freak on 2008-08-23
> **stwert said:**
> Ok, so I tried ubuntu-freak's quicktime fix... and it seems to have sort of worked, with flickering video, so I don't know what's up with that. The real problem though, is that it seems to have removed gnucash, which was kind of important, as well as all the games that came with the system and I don't know what else.
I don't know what's up with this. I followed the directions carefully. The only thing I can think of is the "Don't let update manager upgrade", which I didn't think was happening.
So some thoughts on this would be nice. I'll reinstall gnucash, hopefully it'll be fine.

 
Sorry, thought I deleted that method from all the relevent posts. As time went on, and Intrepid evolved, that method started to cause problems.
 
I recommend a different method now, which can be found in the troubleshooting section of my [howto](ubuntuforums.org/showthread.php?t=766683).

---

### Post by stwert on 2008-08-23
Alright, I'll give that a shot in the future. First though, it says that I'm unable to install gnucash. When I try to install it, I get:
```

>sudo apt-get install gnucash

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: gnucash-common (>= 2.2.4-1ubuntu1) but it is not going to be installed
           Depends: libgtkhtml3.8-15 (>= 1:3.13.5) but it is not going to be installed
E: Broken packages

```

---

### Post by ubuntu-freak on 2008-08-23
You could try adding the Intrepid repos again, then try to reinstall that package once more. Trouble is, you can't use dist-upgrade to fix the broken package, as it will transform your OS from 8.04 Hardy, to a very buggy 8.10 Intrepid.

---

### Post by stwert on 2008-08-23
By the way, I tried installing the dependencies required for the gnucash... but if I follow the errors down, I get to libgail18, which, if I do install it, will remove practically everything left on my computer.

ubuntu-freak, I noticed that you removed the quicktime method that was problematic, which is good, but perhaps you could post a summary of that so that others will be able to see what I did to cause my problem so they can come up with solutions.

Sorry for sidetracking the thread, but maybe I'll start a new one if I don't get this fixed.
Thanks

---

### Post by stwert on 2008-08-23
Sorry, I must have missed your last post before I posted...
How would I go about re-adding the Intrepid repos?

---

### Post by ubuntu-freak on 2008-08-23
> **stwert said:**
> Sorry, I must have missed your last post before I posted...
How would I go about re-adding the Intrepid repos?

 
To be honest, it would be better to reinstall Hardy, then follow my howto. Otherwise, you're gonna have a weird Hardy/Intrepid mix.
 
I'm just sorry that I didn't remove those out-of-date instructions.

---

### Post by stwert on 2008-08-23
Ok, thanks for the advice. I guess I should research a bit first before I try things. :)

---

### Post by ubuntu-freak on 2008-08-23
> **stwert said:**
> Ok, thanks for the advice. I guess I should research a bit first before I try things. :)

 
Nah, you saw it worked for me and at least one other guy. I should've removed it. Intrepid changes fast, that's why it snowballed and wanted to update more packages than when I and others first used that method. It's the kinda thing I did in Debian, but I doubt I will advise others to do that again in Ubuntu.

---

