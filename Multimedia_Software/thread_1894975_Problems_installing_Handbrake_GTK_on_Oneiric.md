---
title: "Problems installing Handbrake GTK on Oneiric"
date: 2011-12-13
forum: Multimedia Software
---

### Post by MCSECLP on 2011-12-13
I am wanting to rip DVDs to MP4 files so that my kids can watch them on the Nook tablets.  I like Handbrake GTK, but I am getting the following errors when installing:
The following packages have unmet dependencies:

handbrake-gtk: Depends: libatk1.0-0 (>= 1.12.4) but 2.2.0-0ubuntu1 is to be installed
               Depends: libc6 (>= 2.7) but 2.13-20ubuntu5 is to be installed
               Depends: libcairo2 (>= 1.2.4) but 1.10.2-6ubuntu3 is to be installed
               Depends: libdbus-1-3 (>= 1.0.2) but 1.4.14-1ubuntu1 is to be installed
               Depends: libdbus-glib-1-2 (>= 0.78 ) but 0.94-4 is to be installed
               Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
               Depends: libglib2.0-0 (>= 2.16.0) but 2.30.0-0ubuntu4 is to be installed
               Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.12) but 0.10.35-1 is to be installed
               Depends: libgstreamer0.10-0 (>= 0.10.0) but 0.10.35-1 is to be installed
               Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is to be installed
               Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4 is to be installed
               Depends: libnotify1 (>= 0.5.0) but it is not going to be installed
               Depends: libnotify1-gtk2.10 but it is not going to be installed
               Depends: libpango1.0-0 (>= 1.18.0) but 1.29.3+git20110916-0ubuntu1 is to be installed
               Depends: libstdc++6 (>= 4.5) but 4.6.1-9ubuntu3 is to be installed
               Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

Anyone else having problems with Handbrake GTK on 11.10 and how does one fix it?

---

### Post by papibe on 2011-12-13
How are you installing it?
Are you using a ppa?

I would recommend this steps:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```
Hope it helps.
Regards.

---

### Post by MCSECLP on 2011-12-15
I had tried that before and it had failed, but it worked great this time!  Thanks!

---

### Post by bentrider1957 on 2012-01-31
> **MCSECLP said:**
> I had tried that before and it had failed, but it worked great this time!  Thanks!

If anyone still has problems, please make sure that you go into Software Sources and delete all instances of Handbrake.  Also delete all keys associated.  If you have sources that didn't work installed, it could cause your system to conflict and fail to install.

After removal, do the CLI update as listed again.  This will install all fresh and clean and pretty sources for you and it should work.

sudo add-apt-repository ppa:stebbins/handbrake-snapshots

sudo apt-get update 

sudo apt-get install handbrake-gtk

NB: Oneric is supported and if you are running Oneric, you will have no issues.

---

