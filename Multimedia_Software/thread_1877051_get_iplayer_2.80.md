---
title: "get_iplayer 2.80"
date: 2011-11-07
forum: Multimedia Software
---

### Post by jonesyp on 2011-11-07
Hello,

Could anyone let me know if you can get get_iplayer 2.80 running on Ubuntu.  I see it is in the package list for the next version, but the version in 11.10 seems to be 2.79.

Failing this can you suggest an Ubuntu derivative which would include it?

Many thanks

Peter

---

### Post by ajgreeny on 2011-11-07
I am running 2.80 on Lucid 10.04 with no problem, but not installed from the repos.

Go to [http://git.infradead.org/get_iplayer.git](http://git.infradead.org/get_iplayer.git) and get the latest snapshot as a tar.gz file.  You can then extract the get_iplayer perl script and replace the one you have in /usr/bin with the new one.  I always rename the old one with the version number, ie **get_iplayer** to **get_iplayer2.79**, but leave it in place, just in case the new script does not work.

Nothing else needs to be done, you will simply see the new version number the next time you run it in terminal.

PS:  I have aliases set up for it with **gip** for TV feeds, **gipr** for radio, and **gipg** for the download command.  All I have to add is the search term or download number.  It saves a few key presses each time.

---

### Post by ron999 on 2011-11-07
There's also a PPA here:- [https://launchpad.net/~jon-hedgerows/+archive/get-iplayer]("https://launchpad.net/~jon-hedgerows/+archive/get-iplayer")

---

### Post by ajgreeny on 2011-11-07
> **ron999 said:**
> There's also a PPA here:- [https://launchpad.net/~jon-hedgerows/+archive/get-iplayer]("https://launchpad.net/%7Ejon-hedgerows/+archive/get-iplayer")
Thanks for that ron999.  I wasn't aware of the ppa, which will mean I don't need to check manually for updates in future.

---

### Post by jonesyp on 2011-11-07
Thanks for this. could you tell me how to add a ppa? Command line is best if possible. thanks

---

### Post by nothingspecial on 2011-11-07
Adding that ppa may break flash for you.

---

### Post by ajgreeny on 2011-11-07
> **nothingspecial said:**
> Adding that ppa may break flash for you.
What makes you think that?  I have just enabled the ppa and updated using it.  My flash plugin, which is what I assume you are talking about still seems to be working fine.  I have flash 11 by using the flash-aid plugin from livinglinux, if that makes any difference.

EDIT:
OK, I take that back.

Flash has been well and truly broken on my system, but it was only after a firefox restart that it happened.

I have removed (purged) the packages which were installed from that ppa and the ppa itself, and re-installed get-iplayer from the normal repos.  I have re-run the flash-aid add-on in firefox, and I have tried restarting my system, but it looks as if that ppa has broken flash totally and completely.

Have you any idea how to get flash running properly again?

---

### Post by nothingspecial on 2011-11-08
Try purging the PPA and re-install the flash-plugin-installer.

Then add the ppa and try a dist-upgrade. Before you accept have a look to see if the dist-upgrade will remove anything.

---

### Post by ajgreeny on 2011-11-08
I have done all that except the dist-upgrade, and still it is not working.  I want to keep using Lucid, so a dist-upgrade is not something I want to do.  Have I misunderstood your suggestions?

Thanks for the help;  if really necessary I will reinstall Lucid, which I think is the best version of Ubuntu for me on my desktop, and which I have been running for 18 months, so there is probably some cruft that I can remove.   But it is annoying if it comes to that just to get flash running.  However, flash is now so important on a huge number of web pages that it is almost impossible to do without it.

---

### Post by nothingspecial on 2011-11-08
dist-upgrade will not upgade you to a later version of Ubuntu.

```
sudo apt-get dist-upgrade
```

The repo upgrades a librtmp0 that flash depends on so in the process it removes flash. Then you cannot reinstall flash because apt doesn't recognise the updated package as a dependency of flash.

Trouble is, I can't remember exactly what happened.

I solved it by purging the ppa and re-installing flash. Then only doing upgrades, not dist-upgrades. The problem seems to have resolved itself now in 11.10.

Although if you haven't done a dist-upgrade, but have done everything else then something else is wrong.

---

### Post by ajgreeny on 2011-11-09
Well, I am now completely mystified and a bit overwhelmed by whatever has happened.

I have re-installed my whole system, which with a separate /home folder, took about 15 minutes plus time to update and add extra packages, but for some strange reason I still can not get flash running on this setup.

Thinking it must be something in my /home, I made a new user, checked in **about:plugins** that flash was installed and active, and tried the adobe flash test page.  Still no go!

This is not a hardware problem because until two days ago when I enabled the ppa for get-iplayer, flash was working well, and on Xubuntu 11.10 on the same machine, flash is working fine, but since using that ppa in my 10.04 it simply refuses to do so.  I can not really believe that a system reinstall did not work.  I have tried flash-aid add-on for firefox, and the various flash installation packages from the repos, but nothing will do the job.

Any idea of any sort what is going on?

---

### Post by nothingspecial on 2011-11-09
:(

What happens if you try a different browser?

---

### Post by satanselbow on 2011-11-09
I'm now using the ppa version and have not experienced any flash problems in any browser... sorry...

Just to confirm it may well be your local settings rather than an inherent problem generated by the ppa... you may well be on the right track with there being a dodgy config (hidden folder?) under /home

Might be worth creating a clean test firefox profile?

What do you get if you start firefox from a terminal?

---

### Post by ajgreeny on 2011-11-09
A clean profile start of firefox makes no difference, so that rules that out.  I renamed the hidden .mozilla folder in /home to do this and restarted firefox, but did not use the profile manager;  I assume that amounts to the same thing, and gives me a totally clean firefox profile.

Starting firefox in terminal gives duplicated errors that don't seem to be related
```
user@Lucid:~$ firefox
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```Using chromium is just the same; it tells me I have a missing plugin, but no way to install it, even though I know flash is installed.

EDIT:
Well, believe it or not, I seem to have got at least a partial solution to the problem, which seems to be simply that this version of either firefox (7.01), or flash-aid with this combination of firefox and 10.04 Lucid, does not like the beta version of flash from adobe that flash-aid gives as the default. I don't know why, as the flash beta has worked fine until the get-iplayer ppa messed it up.

I have just tried flash-aid a few minutes ago, but asked it to install the stable flash from ubuntu repos, surely the same as I get if I use synaptic, and that seemed to work;  why does it not work if I use synaptic?  Very weird!!

I am now tempted to try flash-aid again to try the beta version just in case that add-on has magically managed to remove something that nothing else would do properly.

EDIT 2:
Yes it is the flash beta that is the problem.  I have just tried flash-aid again and asked for the beta flash version from adobe, and once again it will not work in my combination of software/hardware.  I straightaway used flash-aid again to get the stable version and it again works without problem.

Life gets stranger and stranger sometimes, but at least it's working again properly.

Many thanks to all who tried to help.  It gave me good ideas to try everything you and I could think of, and now all seems well again

Phew!

---

### Post by jon47 on 2011-11-09
(I own ppa:jon-hedgerows/get-iplayer in launchpad)

> **nothingspecial said:**
> 

[ppa:jon-hedgerows/get-iplayer] upgrades a librtmp0 that flash depends on so in the process it removes flash. Then you cannot reinstall flash because apt doesn't recognise the updated package as a dependency of flash.

The ppa upgrades librtmp0 (for versions prior to oneiric), but since adobe flash doesn't use librtmp0 I have difficulty believing the rest.  I use my own ppa, and test it quite a bit, and have never had a problem with flash (well, not that's related to that ppa anyway ;-).

> 
Trouble is, I can't remember exactly what happened.

Well, yes...

> 
I solved it by purging the ppa and re-installing flash. Then only doing upgrades, not dist-upgrades. The problem seems to have resolved itself now in 11.10.


If you're using Oneiric/11.10 then you will have had a problem that's now fixed:  There are some packages that use librtmp0, but this problem got fixed a week or two ago (by providing a statically-linked updated rtmpdump, and not providing librtmp0).  But oneiric doesn't update librtmp0 from the ppa without you telling it to, at which point it tells you what will break.

If you use Lucid, Maverick or Natty you shouldn't have any problem with flash, or anything else for that matter, as a result of installing get-iplayer from my ppa.

If you have problems with flash I'd be really surprised if they are actually anything to do with the ppa.  I've certainly never seen a case of installation of stuff from my ppa causing flash to be uninstalled and/or broken.  I've tested (in the past, not in the last few weeks) with lucid, maverick and natty, both i386 and amd64 versions.  Oneiric amd64 has been tested recently, I concede I've not actually tested my ppa with oneiric i386.

However, since I've already done the work to repackage rtmpdump so that it's statically linked for oneiric so that I can leave librtmp0 untouched, I'll backport that to lucid, maverick and natty, and then I can happily sit back and say "certainly not my fault" if flash breaks.  Give launchpad 24 hours and update.  You'll have to rollback librtmp0 to the distribution's version (or remove it completely) yourself.

The real problem is that librtmp0 doesn't follow the normal versioning conventions for shared libraries, and the original developers keep introducing API-breaking changes without changing (the non-existent) library version numbers.  I expect this'll get fixed one day, but I can work around it for the purpose of making get_iplayer work nicely.

Regards
Jon

---

### Post by satanselbow on 2011-11-09
> **jon47 said:**
> (I own ppa:jon-hedgerows/get-iplayer in launchpad)

The real problem is that librtmp0 doesn't follow the normal versioning conventions for shared libraries, and the original developers keep introducing API-breaking changes without changing (the non-existent) library version numbers.  I expect this'll get fixed one day, but I can work around it for the purpose of making get_iplayer work nicely.



Thanks for the detailed explanation and good work Jon :popcorn:

---

### Post by nothingspecial on 2011-11-09
> **jon47 said:**
> ..



If you're using Oneiric/11.10 then you will have had a problem that's now fixed:  There are some packages that use librtmp0, but this problem got fixed a week or two ago (by providing a statically-linked updated rtmpdump, and not providing librtmp0).  But oneiric doesn't update librtmp0 from the ppa without you telling it to, at which point it tells you what will break.



That was the problem```


Start-Date: 2011-10-26  12:03:56
Commandline: apt-get install get-iplayer
Install: libnet-ssleay-perl:amd64 (1.36-3, automatic), libx264-115:amd64 (0.115.1947+3-ppa2~oneiric, automatic), liburi-perl:amd64 (1.58-1, automatic), libhtml-parser-perl:amd64 (3.68-1build1, automatic), atomicparsley:amd64 (0.9.4-hg83.814077d09d34-0ppa2~oneiric, automatic), libhttp-daemon-perl:amd64 (6.00-1, automatic), libfont-afm-perl:amd64 (1.20-1, automatic), libunicode-string-perl:amd64 (2.09-4build1, automatic), libhttp-negotiate-perl:amd64 (6.00-2, automatic), libfile-listing-perl:amd64 (6.01-1, automatic), libhtml-form-perl:amd64 (6.00-1, automatic), get-iplayer:amd64 (2.80+n3-gitc313712-ppa2), libmp3-info-perl:amd64 (1.24-1, automatic), libhtml-tree-perl:amd64 (4.2-1, automatic), libencode-locale-perl:amd64 (1.02-1, automatic), libhttp-date-perl:amd64 (6.00-1, automatic), ffmpeg-static:amd64 (0git-N-30582-gef28c7b-ppa1~oneiric, automatic), libmailtools-perl:amd64 (2.08-1, automatic), liblwp-protocol-https-perl:amd64 (6.02-1, automatic), libmp3-tag-perl:amd64 (1.12-1, automatic), rtmpdump:amd64 (2.4-n23-gitc58cfb3-ppa3~oneiric, automatic), libhttp-cookies-perl:amd64 (6.00-2, automatic), libhttp-message-perl:amd64 (6.01-1, automatic), libnet-http-perl:amd64 (6.01-1, automatic), libhtml-format-perl:amd64 (2.10-1, automatic), libhtml-tagset-perl:amd64 (3.20-2, automatic), libwww-perl:amd64 (6.02-1ubuntu1, automatic), libio-socket-ssl-perl:amd64 (1.43-1, automatic), libwww-robotrules-perl:amd64 (6.01-1, automatic), liblwp-mediatypes-perl:amd64 (6.01-1, automatic), libimage-exiftool-perl:amd64 (8.60-2, automatic)
End-Date: 2011-10-26  12:04:30

Start-Date: 2011-10-26  12:22:50
Commandline: apt-get install mplayer librtmp0
Upgrade: librtmp0:amd64 (2.3-2ubuntu1, 2.4-n23-gitc58cfb3-ppa3~oneiric)[COLOR="Red"]
Remove: flashplugin-downloader:i386 (11.0.1.152ubuntu1), libcurl3:i386 (7.21.6-3ubuntu3), flashplugin-installer:amd64 [/COLOR](11.0.1.152ubuntu1), librtmp0:i386 (2.3-2ubuntu1)
End-Date: 2011-10-26  12:22:57
```

:)

And as I've said, everything is working swimmingly now. Thanks for the explanation and the ppa itself.

---

### Post by ajgreeny on 2011-11-09
Thanks all.  As I said in my second edit of post 15 in this thread, it seems likely to me that the problem is more related to my hardware and the beta flash that flash-aid adds by default, which is where my system trips up.

I think I will use flash-aid with some caution at the moment, although it looks as if I can use it as long as I just ask for the stable version of flash instead of the beta.

EDIT:
I have just ascertained that the problem is definitely related to the beta version of flash not working on my hardware when using flash-aid to install it.

I have five OSs on the same machine, Ubuntu 10.04 as my main OS on the large drive, 11.10 of each of Ubuntu, Xubuntu, Kubuntu, and Lubuntu on a separate drive for testing purposes, and it looks as if this beta flash will not work in any of those five OSs.

Has that beta version just been updated?

---

### Post by jonesyp on 2012-07-31
Many thanks for all the help.

Peter Jones

---

