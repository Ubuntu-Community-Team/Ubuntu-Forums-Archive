---
title: "Ubuntu 10.04 can't reach some hosts"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by bryanshook on 2010-08-31
Hello Ubuntu community,
I have a problem reaching some hosts on the Internet, namely newegg.com and djangoproject.com.  On the same machine and network connection using Windows 7 the host names resolve properly and I can connect to them.  The host names are resolving in Ubuntu, but I cannot connect to them.  I'm not sure where to go from here because the connection is dying on some hop along the way.

---

### Post by MaindotC on 2010-08-31
In order to better help you, please explain the following:

Is this a new installation or was your Ubuntu machine working properly prior to some event?

Are you connecting via home network or are you on a campus or work network that is managed by a network administrator?

Please try following the troubleshooting guides for [wireless](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Connection%20Established,%20Problems%20Persist) and [general network troubleshooting](http://ubuntuforums.org/showthread.php?t=25557).  It really doesn't seem to be an issue with your network device operating properly, so you'll probably skip to general network troubleshooting.

---

### Post by bryanshook on 2010-08-31
The machine was originally installed via VirtualBox in Windows 7 directly onto the drive (no disk image).  I decided I didn't want to virtualize since I don't have those extensions for my processor.  lsmod does not show any of the virtualbox addons running so I don't feel that the problem lies there.

This is a home DSL connection and what perplexes me further is that the windows machines can connect to these sites and browse them (not in offline mode or any such nonsense) but they cannot ping them.  I might try a different set of DNS servers, but I would guess the problem lies with my ISP's routing and I'll go to dslreports.com for that.

Update:
Used the live cd to test the issue further.  Apparently the virtualbox additions altered a setting.  I'll just install a clean version from this live cd rather than track down the virtualbox additions for removal. I appreciate the response, strAlan.

---

### Post by MaindotC on 2010-08-31
I'm glad you found a solution to your problem.  May I ask you to clarify this:

> **bryanshook said:**
> The machine was originally installed via VirtualBox in Windows 7 directly onto the drive (no disk image).

I know you can use Vbox to install a machine to a usb stick, but how do you install it to your hard drive?  Did you create a partition for it or does it just fit inside a folder?

---

### Post by bryanshook on 2010-08-31
I used a separate partition.  It's in the manual [ch 9 the part on raw disks]("http://www.virtualbox.org/manual/ch09.html#rawdisk").

It looks like my problem is back.  The default install and live cd works.  Changes that were made to the installation after install were installing eclipse, nvidia drivers, and other software (nothing in the network stack).  I also installed the suggested updates from the update manager.  I think this last part is critical and I could be wrong.  I attached the output of a simulated apt-get for the live cd for inspection.

The last thing that might be worth mentioning is the firefox sync addon.  I'm gonna try removing that and see if it is the problem.

Update:  The problem seems resolved now and is unrelated to Ubuntu.  It was mostly likely an issue with my router that AT&T provided.
Final Update: The problem was the Firefox Sync addon.  I can't get Firefox to connect to those sites even after uninstalling the addon.  No big deal.  There's always Chromium or countless other browsers.

---

### Post by MaindotC on 2010-09-01
I'm sorry that you narrowed down Firefox to appear to be the problem.  However, using a different browser doesn't really solve the problem.  If Firefox really is the problem, can you try and figure out what problem it's causing?  The developers will need to know as obviously it is used by millions of users worldwide.  Thanks!

---

### Post by bryanshook on 2010-09-01
The problem lies with an addon by the Mozilla development team.  If I ```
rm -fr ~/.mozilla
``` then all is well.  The Firefox Sync addon is the source of the issue.  Uninstalling the addon does not fix the issue.  I had to remove all of my Firefox settings to get it resolved.  I'll see if I can find the respective bugtracker upstream to file a report.

---

### Post by MaindotC on 2010-09-02
Ah good - yes the the .mozilla folder contains configurations and I believe it also contains the plugins.  You know, in the future, if you wanted to keep that folder so you could help determine where in that plugin a configuration problem was occurring, you could just move it to something like .mozilla.bak instead of deleting it permanently.  Thank you for addressing this!

---

### Post by Sean Hayes on 2010-11-09
> **bryanshook said:**
> Hello Ubuntu community,
I have a problem reaching some hosts on the Internet, namely newegg.com and djangoproject.com.  On the same machine and network connection using Windows 7 the host names resolve properly and I can connect to them.  The host names are resolving in Ubuntu, but I cannot connect to them.  I'm not sure where to go from here because the connection is dying on some hop along the way.

I've been having the saem problem with djangoproject.com for a while now, and I just tried newegg.com and that doesn't work either.

Any ideas on how to fix this with out deleting all my profiles?

---

### Post by Spectre5 on 2010-11-30
I also have this issue...

Ubuntu 10.04, home network.  newegg.com works with google chrome, but not from firefox.  Both are from the ubuntu repositories - nothing fancy.  I tried starting firefox in safe mode (firefox -safe-mode), but this didn't work.  I really don't want to purge anything...I do have firefox sync, so maybe that is the problem...

---

### Post by Sean Hayes on 2010-11-30
Sorry I forgot to post this sooner, I found a solution 2 weeks ago: [http://forums.mozillazine.org/viewtopic.php?p=10119503#p10119503](http://forums.mozillazine.org/viewtopic.php?p=10119503#p10119503)

---

### Post by Spectre5 on 2010-12-01
> **Sean Hayes said:**
> Sorry I forgot to post this sooner, I found a solution 2 weeks ago: [http://forums.mozillazine.org/viewtopic.php?p=10119503#p10119503](http://forums.mozillazine.org/viewtopic.php?p=10119503#p10119503)

Awesome, thanks!  The last comment solved it for me:
> ...but if I go in Firefox > Edit > Preferences > Content > Languages > Choose, in addition to "English/United States [en-US]" in the list there's also "[chrome://global/locale/intl.properties]", and removing it instantly solves the problem.

---

