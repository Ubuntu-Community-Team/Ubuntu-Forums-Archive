---
title: "flashplugin-installer (24.0.0.186ubuntu0.14.04.1) randomly fails on install"
date: 2017-01-05
forum: Multimedia Software
---

### Post by montyp2 on 2017-01-05
I was curious if others were seeing this issue recently.  Back on Dec 13th, a new flash plugin version was released.  I was doing a new install of Lubuntu 14.04.1 LTS i386 version today and installed the Lubuntu-restricted-extras metapackage.  One of the items it installs is flashplugin-installer.  I noticed after installing completed without error, that the flash plugin was still not installed (went to [https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html)).

So, I purged the flashplugin-installer and reinstalled:

```
 admin@pc1:~$ sudo apt-get purge flashplugin-installer
admin@pc1:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cifs-utils linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  localechooser-data python3-pyqt4 python3-sip
Use 'apt-get autoremove' to remove them.
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 410 not upgraded.
Need to get 0 B/6,792 B of archives.
After this operation, 140 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 207293 files and directories currently installed.)
Preparing to unpack .../flashplugin-installer_24.0.0.186ubuntu0.14.04.1_i386.deb ...
Unpacking flashplugin-installer (24.0.0.186ubuntu0.14.04.1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz)
Setting up flashplugin-installer (24.0.0.186ubuntu0.14.04.1) ...
admin@pc1:~$ 
```    

After this, it still was not installed despite no error message, so I repeated the purge and install process.  On the third time around doing this, it finally installed.  Notice at the end how it is slightly different where at says it is installing and then was installed?

```
admin@pc1:~$ sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cifs-utils linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  localechooser-data python3-pyqt4 python3-sip
Use 'apt-get autoremove' to remove them.
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 410 not upgraded.
Need to get 0 B/6,792 B of archives.
After this operation, 140 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 207293 files and directories currently installed.)
Preparing to unpack .../flashplugin-installer_24.0.0.186ubuntu0.14.04.1_i386.deb ...
Unpacking flashplugin-installer (24.0.0.186ubuntu0.14.04.1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz)
Installing from local file /tmp/tmpYgR1jv.gz
Flash Plugin installed.
Setting up flashplugin-installer (24.0.0.186ubuntu0.14.04.1) ...
[COLOR=#000000]admin@pc1:~$[/COLOR]
```
[COLOR=#000000] 
[/COLOR]
This is very repeatable for me on multiple computers too.  If I purge the flashplugin-installer after a successful install and reinstall, I will have the same issues where I need to purge and reinstall a couple times.

I thought this is odd so was curious if others have had this experience in the last couple of weeks?

Thanks!

---

### Post by ajgreeny on 2017-01-05
I have not used the **flashplugin-installer** package for quite a while.

In future try enabling the canonical-partner repos and then install **adobe-flashplugin** package which seems more successful.
If you do that and then install restricted-extras package I think the need for flashplugin-installer is already satisfied.

---

### Post by montyp2 on 2017-01-05
Thanks ajgreeny for the suggestion.  That does seem to install more reliably than the [B]flashplugin-installer package.  

[/B]

---

### Post by nadrach on 2017-01-05
> **montyp2 said:**
> Thanks ajgreeny for the suggestion.  That does seem to install more reliably than the [B]flashplugin-installer package.  

[/B]

Adobe_flashplugin no longer loads, nor Adobe_flash_properties_gtk.
It seems this may be the reason flashplugin_installer is not working.
Files are missing.
Happens with 16.04 as well.
Messages from Synaptic with Lubuntu 16.04:
> W: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1-0ubuntu0.16.04.1_amd64.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1-0ubuntu0.16.04.1_amd64.deb)
  404  Not Found [IP: <removed>]
W: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20161213.1-0ubuntu0.16.04.1_amd64.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20161213.1-0ubuntu0.16.04.1_amd64.deb)
  404  Not Found [IP: <removed>]

There has also been a problem with ttf-mscorefonts_installer for some weeks, with Lubuntu 16.04, all the MS font file download calls return Error 404.
The lubuntu_restricted_extras package in 16.04 calls flashplugin_installer even if you have adobe_flashplugin installed (but broken because of the missing download).
You just keep getting messages to perform additional downloads that are incomplete, for both flashplugin and mscorefonts.  When you try to run the additional commands, they fail with 404 errors for the download files.

---

### Post by montyp2 on 2017-01-05
Thanks nadrach for the reply.
I had the same issue with adobe_flashplugin. After enabling the partners repository and running sudo apt-get update, it failed to connect to one of the download servers.  I then tried through synaptic and it worked to install it.  I would think Synaptic and apt-get should work the same, so maybe it was shear dumb luck it worked for me from synaptic.

I noticed that about the msfonts in 16.04 as well.  You probably already had this, but for the msfonts issues, this fixed it for me:  [http://askubuntu.com/questions/543673/mscorefonts-problems](http://askubuntu.com/questions/543673/mscorefonts-problems)

---

### Post by nadrach on 2017-01-07
Just tried on Lubuntu 14.04 machine, using apt-get:
> Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner adobe-flash-properties-gtk i386 1:20161213.1-0ubuntu0.14.04.1
  404  Not Found [IP: <removed>]
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner adobe-flashplugin i386 1:20161213.1-0ubuntu0.14.04.1
  404  Not Found [IP: <removed>
E: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20161213.1-0ubuntu0.14.04.1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20161213.1-0ubuntu0.14.04.1_i386.deb)  404  Not Found [IP: <removed>]

E: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1-0ubuntu0.14.04.1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1-0ubuntu0.14.04.1_i386.deb)  404  Not Found [IP: <removed>]

Is this missing files on the server, missing files, or malformed request?
Ie: should there be a space in:
> [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner

---

### Post by nadrach on 2017-01-08
Just on the offchance, I tried the two direct download links in the "E:Failed to fetch" messages in my previous post, and Lo!, manual download of both packages.  I am going to try with 16.04
Installed simply by right-clicking for GDebi on the two downloaded package files.
Ignore the complaint about the same package being available via a software channel.
Someone else can provide the answer as to why the software channel route is not working, but I am fixed for the moment.

---

