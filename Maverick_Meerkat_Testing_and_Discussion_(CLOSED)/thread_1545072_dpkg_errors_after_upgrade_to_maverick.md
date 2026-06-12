---
title: "dpkg errors after upgrade to maverick"
date: 2010-08-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crisnoh on 2010-08-03
After upgrading to maverick I got an error stating that the upgrade completed with errors.  Now I get this when attempting to run updates:


```
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 42747 package 'virtualbox-3.1':
 error in Version string `3.1.6-59338_Ubuntu_karmic': invalid character in revision number
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any idea what could be causing this?

---

### Post by kyleabaker on 2010-08-03
Are your software sources set to use Maverick repo's? It looks like you still have some Karmic sources in there.

check them with:
```
gksudo gedit /etc/apt/sources.list
```

Also check in:
System -> Administration -> Software Sources

---

### Post by dino99 on 2010-08-03
updating synaptic, got this error:

E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/test -S /var/run/dbus/system_bus_socket && /usr/bin/dbus-send --print-reply --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update' > /dev/null'
E: Sub-process returned an error code

---

### Post by ratcheer on 2010-08-03
Update Manager offered to do a partial update for my Maverick installation. I declined, but I saw that one of the parts of the partial was something about "dpkg front end".

Tim

---

### Post by forumache on 2010-08-03
I had the same problem and a quick search on Google revealed:

sudo dpkg --clear-avail

followed by

sudo aptitude update

100% success in my case.
Enjoy!

---

### Post by paul_in_london on 2010-08-03
I'm getting this at the moment:

```
paul@maverick:~$ sudo aptitude safe-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[COLOR="Red"]Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1[/COLOR]
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
paul@maverick:~$
```

Have done a bit of googling, but haven't found anything so far to fix it.

The funny thing is, **apt-get dist-upgrade** doesn't give this error.

One thing I initially tried (suggested in another thread) was:

```
rm -rvf ~/.local/share/ubuntuone/syncdaemon/
```

but it's apparently nothing to do with that.

---

### Post by paul_in_london on 2010-08-03
Well the **org.freedesktop.DBus.Error.Spawn.ChildExited** issue isn't quite as bad as I originally thought in the sense that I've had a small number of package updates since my previous post and I've discovered that upgrading via **aptitude** still works.

---

### Post by crisnoh on 2010-08-03
> **kyleabaker said:**
> Are your software sources set to use Maverick repo's? It looks like you still have some Karmic sources in there.

check them with:
```
gksudo gedit /etc/apt/sources.list
```

Also check in:
System -> Administration -> Software Sources

All my Karmic sources are commented out.

> **forumache said:**
> I had the same problem and a quick search on Google revealed:

sudo dpkg --clear-avail

followed by

sudo aptitude update

100% success in my case.
Enjoy!

Attempted this, but the same problem popped up as when using apt-get:

```
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main libdbusmenu-glib1 0.3.9-0ubuntu1 [29.0kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main libdbusmenu-gtk1 0.3.9-0ubuntu1 [16.3kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/universe phonon-backend-vlc 0.2.0-1ubuntu1 [50.6kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick/main apparmor 2.5-0ubuntu4 [351kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick/main libapparmor1 2.5-0ubuntu4 [37.4kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick/main libapparmor-perl 2.5-0ubuntu4 [39.9kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick/main apparmor-utils 2.5-0ubuntu4 [105kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick/main libruby1.8 1.8.7.299-2 [1,714kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick/main python-ubuntuone-storageprotocol 1.3.5-0ubuntu1 [48.7kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick/main virtuoso-opensource-6.1-common 6.1.2+dfsg1-1ubuntu4 [45.1kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick/main libvirtodbc0 6.1.2+dfsg1-1ubuntu4 [736kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick/main virtuoso-opensource-6.1-bin 6.1.2+dfsg1-1ubuntu4 [3,716kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick/main virtuoso-minimal 6.1.2+dfsg1-1ubuntu4 [29.8kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ maverick/universe weechat-plugins 0.3.2-1 [281kB]
Fetched 7,199kB in 11s (634kB/s)                                                
Extracting templates from packages: 100%
[B]Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 42747 package 'virtualbox-3.1':
 error in Version string `3.1.6-59338_Ubuntu_karmic': invalid character in revision number
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 42747 package 'virtualbox-3.1':
 error in Version string `3.1.6-59338_Ubuntu_karmic': invalid character in revision number[/B]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

---

### Post by crisnoh on 2010-08-03
Turns out the same error occurs regardless of what action I take using apt-get, aptitude, or synaptic.  I've tried installing, upgrading, and removing packages and the same thing happens.

---

### Post by ranch hand on 2010-08-03
Using both apt-get and aptitude on the same system will cause some little problems in both of them.

What happen with the command;
```

sudo dpkg --configure -a

```
anything?

---

### Post by Longinus00 on 2010-08-03
> **crisnoh said:**
> After upgrading to maverick I got an error stating that the upgrade completed with errors.  Now I get this when attempting to run updates:


```
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 42747 package 'virtualbox-3.1':
 error in Version string `3.1.6-59338_Ubuntu_karmic': invalid character in revision number
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any idea what could be causing this?

The problem is plainly stated in the error message. You have a package with underscores in the revision number (I'm not certain when this became illegal but evidently it was sometime between karmic and now) and dpkg is barfing while trying to parse it. To solve this you can modify the file by hand to remove the invalid entry or you can compile a version of dpkg without the check and then remove the offending package/entry.

---

### Post by paul_in_london on 2010-08-03
> **crisnoh said:**
> After upgrading to maverick I got an error stating that the upgrade completed with errors.  Now I get this when attempting to run updates:


```
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 42747 package 'virtualbox-3.1':
 error in Version string `3.1.6-59338_Ubuntu_karmic': invalid character in revision number
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any idea what could be causing this?

```
paul@maverick:~$ grep -i virtualbox /etc/apt/sources.list
deb http://download.virtualbox.org/virtualbox/debian **lucid** non-free
```

Try changing your **/etc/apt/sources.list** entry as shown above. There is no **maverick** directory on the virtualbox website yet.

I had a similar problem yesterday caused by an extra section in**/var/lib/dpkg/available** relating to virtualbox-**2**.1. Removing that section of **/var/lib/dpkg/available** and updating/upgrading via aptitude solved the problem.

Reverting to **available-old** and **status-old** before updating/upgrading may also be necessary.

Check the virtualbox section(s) in **/var/backups/dpkg.status.0**, which is an older backup of the **status** file.

---

### Post by hikaricore on 2010-08-04
> **ranch hand said:**
> Using both apt-get and aptitude on the same system will cause some little problems in both of them.

I don't think this is actually true in any way..

---

### Post by crisnoh on 2010-08-04
> **ranch hand said:**
> Using both apt-get and aptitude on the same system will cause some little problems in both of them.

What happen with the command;
```

sudo dpkg --configure -a

```
anything?

Same error.

---

### Post by crisnoh on 2010-08-04
> **Longinus00 said:**
> The problem is plainly stated in the error message. You have a package with underscores in the revision number (I'm not certain when this became illegal but evidently it was sometime between karmic and now) and dpkg is barfing while trying to parse it. To solve this you can modify the file by hand to remove the invalid entry or you can compile a version of dpkg without the check and then remove the offending package/entry.

I attempted commenting out the offending package in that file and apt-get choked.  How do I do this correctly?

---

### Post by Longinus00 on 2010-08-05
> **crisnoh said:**
> I attempted commenting out the offending package in that file and apt-get choked.  How do I do this correctly?

Try replacing the underscores with tildes.

---

### Post by collinp on 2010-08-05
> **hikaricore said:**
> I don't think this is actually true in any way..

It's not. There's nothing at all wrong with using aptitude and apt on the same system.

Try this:

```
sudo apt-get install -f
```

---

### Post by moted on 2010-08-05
> **Longinus00 said:**
> Try replacing the underscores with tildes.

I had this exact same issue, modifying the underscores to tildas seems to have fixed that issue.  I'm currently updating the rest of the packages through aptitude.

---

### Post by moted on 2010-08-05
It is now failing on two broken packages.

```

root@athos:> dpkg --configure -a
dpkg: dependency problems prevent configuration of libavcodec52:
 libavcodec52 depends on libavutil50 (>= 4:0.6-2ubuntu2) | libavutil-extra-50 (>= 4:0.6); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
 libavcodec52 depends on libavutil50 (<< 4:0.6-99) | libavutil-extra-50 (<< 4:0.6-99); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
dpkg: error processing libavcodec52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavformat52:
 libavformat52 depends on libavcodec52 (>= 4:0.6-2ubuntu2) | libavcodec-extra-52 (>= 4:0.6); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.6-99) | libavcodec-extra-52 (<< 4:0.6-99); however:
  Package libavcodec52 is not configured yet.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavutil50 (>= 4:0.6-2ubuntu2) | libavutil-extra-50 (>= 4:0.6); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
 libavformat52 depends on libavutil50 (<< 4:0.6-99) | libavutil-extra-50 (<< 4:0.6-99); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
dpkg: error processing libavformat52 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libavcodec52
 libavformat52
```

I've tried removing and upgrading these packages, but I seem stuck in a dependency loop.  Any ideas on how I might continue?

---

### Post by ranch hand on 2010-08-05
If you have run dpkg --configure -a and got no relief and you can boot to recovery, you may want to try the "dpkg fix broken pacages" option on the menu there.  It is pretty good and takes a fairly aggressive approach to its job.

The Alt install disk and the Live DVD both have a "rescue a broken system" which supplies a command line attack that seems more aggressive with the commands than when they are run elsewhere.

---

### Post by crisnoh on 2010-08-06
> **Longinus00 said:**
> Try replacing the underscores with tildes.

This did the trick.  Still had to reinstall some broken packages, but now I'm good to go.  Thanks!

---

