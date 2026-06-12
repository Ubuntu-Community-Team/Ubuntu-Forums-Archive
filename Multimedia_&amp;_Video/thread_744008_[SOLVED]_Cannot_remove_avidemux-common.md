---
title: "[SOLVED] Cannot remove avidemux-common"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by peterthebike on 2008-04-03
I cannot remove avidemux-common from Synaptic. It gives the error:
```
E: avidemux-common: subprocess post-removal script returned error exit status 1
```
To try and get more detail I used apt-get and this is the output:
```
$ sudo apt-get remove avidemux-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  avidemux-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1798kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217558 files and directories currently installed.)
Removing avidemux-common ...
The generated cache was invalid.
dpkg: error processing avidemux-common (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 avidemux-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Looking at other threads I have also tried these two commands without success:
```
sudo apt-get install --reinstall avidemux-common
sudo apt-get purge avidemux-common && sudo apt-get update && sudo apt-get install avidemux-common
```
Can anyone suggest what I should try please?

---

### Post by gsmanners on 2008-04-03
Another thing to try is to download the deb file itself (avidemux-common) and reinstall it with dpkg.

sudo dpkg -i filename

Then you may be able to remove it.

---

### Post by peterthebike on 2008-04-03
I am afraid that did not work:
```
sudo dpkg -i avidemux-common_2.4.1-0.0ubuntu1_all.deb 
Selecting previously deselected package avidemux-common.
(Reading database ... 217559 files and directories currently installed.)
Preparing to replace avidemux-common 1:2.4.1-0.0 (using avidemux-common_2.4.1-0.0ubuntu1_all.deb) ...
Unpacking replacement avidemux-common ...
The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
The generated cache was invalid.
dpkg: error processing avidemux-common_2.4.1-0.0ubuntu1_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 avidemux-common_2.4.1-0.0ubuntu1_all.deb
```

---

### Post by gsmanners on 2008-04-03
Are you trying to use a Hardy package on Gutsy there? I imagine that would mess up more than just your apt cache.

---

### Post by peterthebike on 2008-04-03
I was just trying to find the same version (1:2.4.1) as Synaptic reported.

Unfortunately I cannot even open Synaptic now.
```
E: The package avidemux-common needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

I think I am making a bigger mess!:oops:

---

### Post by gsmanners on 2008-04-03
Yeah, you may be forced to edit /var/lib/dpkg/status and remove the entries for avidemux-common before it will work.

---

### Post by peterthebike on 2008-04-04
> **gsmanners said:**
> Yeah, you may be forced to edit /var/lib/dpkg/status and remove the entries for avidemux-common before it will work.
Did that and Synaptic is now working OK again. Thanks for your help gsmanners.

After doing a reload in Synaptic I see that there is no avidemux-common. I wonder where I managed to load it from because 99.9% of all my software is loaded through Synaptic. Avidemux-common must have been the 0.1%.:-k As all is working now I don't think I will worry about that.<grn>

---

