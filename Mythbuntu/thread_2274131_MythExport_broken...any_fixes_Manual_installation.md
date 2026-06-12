---
title: "MythExport broken...any fixes? Manual installation?"
date: 2015-04-18
forum: Mythbuntu
---

### Post by RideMan on 2015-04-18
I just built a Raspberry Pi-based OSMC system to use as an alternate frontend on an older NTSC TV. I hate the OSMC interface compared to Mythfrontend, but for hardware reasons it will have to do until I can replace the TV.

But in order to do that, I had to upgrade my MythTV from 0.25 to 0.27. So now I am running 0.27 on Ubuntu 14.04.2 LTS. 

My latest problem is that Mythexport seems to be irreparably broken. In fact, three days of Googling and forum trawling has revealed that while Mythexport is probably just fine, it seems there is something wrong with the installer package which causes it to fail on installation, whether installed via apt-get, dpkg, or the MCC. It's the same problem that has apparently been reported dozens of times, but for which I have not seen any published solution:

```
Setting up mythexport (2.2.4-0ubuntu2) ...
mkdir: missing operand
Try 'mkdir --help' for more information.
dpkg: error processing package mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems, based on the error, that this should be a pretty simple problem to solve. But I don't know enough about the way packaging works to fix it myself. 

Is it possible to install MythExport manually, so that  I can get the script plugged into Mythtv so that I can start exporting TV shows again? Or is it possible to edit the package scripts to either correct or bypass the error and thus get the automatic installation to work?

If I could get the MythExport part working, then maybe I could sit down and figure out how to get ffmpeg working again.......

--Dave Althoff, Jr.

---

### Post by blm-ubunet on 2015-05-05
This issue seems to be an old recurring problem.
If it has the **same **root cause as previous then you could try to create these (2) directories **first**, then try install mythexport.

```
mkdir -p /var/www/.mythtv
mkdir -p /home/mythtv/.mythtv
```

The second dir/folder should already exist. The first one must have been a typo.

---

