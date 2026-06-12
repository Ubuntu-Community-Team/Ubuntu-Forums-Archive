---
title: "How I removed nvidia-gfx"
date: 2008-05-28
forum: Multimedia Software
---

### Post by AndrewStout on 2008-05-28
I just upgraded to 8.04, and noticed after install that I didn't have accelerated video.  As many other people here, there was some problem and my video drivers got a little mangled in the upgrade.  I wanted to clean up, but apt-get wouldn't uninstall nvidia-gfx:

```
andrew@lucky:~$ sudo apt-get -f remove nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdevelop kdevelop-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 241226 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/X11R6/lib/modules/extensions/libglx.a': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I poked around the gazillion seemingly relevant posts on the forum for inspiration, and eventually just made the missing directory:

```
andrew@lucky:~$ sudo mkdir /usr/X11R6/lib/modules
andrew@lucky:~$ sudo mkdir /usr/X11R6/lib/modules/extensions
```

That seems to have been enough to get apt-get to play along:

```
andrew@lucky:~$ sudo apt-get -f remove nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdevelop kdevelop-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 241226 files and directories currently installed.)
Removing nvidia-glx ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

Might not be entirely clean, but it allowed me to go back to synaptic (where I'm a little more comfortable) and install nvidia-gfx-new, which appears to be working.  The restricted drivers applet reports that the new driver is in use; I haven't tried rebooting yet or doing anything that would tax the driver.  Now I'll try to reboot...

Posting in the hopes that this helps someone.

---

