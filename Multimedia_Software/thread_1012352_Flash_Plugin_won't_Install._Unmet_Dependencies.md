---
title: "Flash Plugin won't Install. Unmet Dependencies"
date: 2008-12-15
forum: Multimedia Software
---

### Post by keuller on 2008-12-15
Hello,

There are many threads about Flash-Plugin not installing, but this seems to be a rather unique problem.

```
esteban@deathstar:~$ sudo apt-get install adobe-flashplugin
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages

```

So how can I rollback my libpango version? According to my updated (five minutes ago) Synaptic Package Manager 1.20.1-1 is the latest version.

Thank you very much.

---

### Post by Therion on 2008-12-15
Try... ```


sudo apt-get install flashplugin-nonfree flashplayer-nonfree
``` instead.

---

### Post by keuller on 2008-12-15
Ok.

Installed flashplugin-nonfree just fine, but cannot find package for flashplayer-nonfree. . . 

Flash not working in Firefox still. Websites tell me to get the latest version of Flash Player and link to adobe website.

I've downloaded and installed the latest Flash Player from them with no luck, so currently I don't have it installed.

---

### Post by Therion on 2008-12-15
Ah, Okay...  You may need to install the necessary repo.

Are you using Hardy or Intrepid, or what?

---

### Post by keuller on 2008-12-15
8.04 Hardy
main, universe, restricted, and multiverse are open.

Third party
[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner (and source)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free (and source)

Are there any other's that are common and I should be referencing?

p.s. know of a quick terminal command to pop out that info?

---

### Post by Therion on 2008-12-15
You need the Medibuntu for this.  See the link below:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then I'd suggest using synaptic and searching for, and installing, a package called **ubuntu-restricted-extras**

This will install codecs, flash, java... Lots of good stuff.

---

### Post by keuller on 2008-12-15
Ok, I installed medibuntu, and download that package.

Flash still doesn't work.

I cannot install adobe-flashplugin because of the error I started this thread over.

I can ALMOST install flashplugin-nonfree but I get the 404 error that's been posted around the forums and the other solutions I'm seeing aren't helping.

```
Downloading...
--17:09:35--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.190.70
Connecting to fpdownload.macromedia.com|72.246.190.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:09:35 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

```

---

### Post by keuller on 2008-12-16
Bump.

I just need to get the correct version of libpango. Anyone out there know where I can download something specific like that OTHER than Synaptic?

---

