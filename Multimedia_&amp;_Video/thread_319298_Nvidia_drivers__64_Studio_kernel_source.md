---
title: "Nvidia drivers / 64 Studio kernel source"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by Bloke on 2006-12-15
I installed the preemptive kernel from the most recent version (v1) of 64 Studio which seems to be working perfectly for audio production on Ubuntu. I need to install Nvidia drivers using the installer, but it requires kernel source. I checked on the 64 Studio CD, and Googled for it, but have not found it. This is the output of uname -r:

2.6.18-2-multimedia-486

How can I find, or create the necessary kernel headers so I can install drivers for my graphics card?

NOTE: The kernel source available at 64 Studio is for 2.6.17.

NOTE: I am also trying to get in contact with someone at 64 Studio regarding, but it seems they only have a mailing list.

NOTE: I realize this isnt exactly an Ubuntu type question, but I figured maybe someone here has been through this, or something similar.

---

### Post by tseliot on 2006-12-15
Did you install the kernel headers for that kernel?

---

### Post by Bloke on 2006-12-15
These are the files installed after a fresh / updated Ubuntu 6.10 install:

01) installed linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb (64 Studio CD)

02) installed linux-headers-2.6.18-2-multimedia_2.6.18-5_i386.deb (64 Studio CD)

03) installed linux-kbuild-2.6.18_2.6.18-1_i386.deb (dependancy for the 486 headers not available on CD = downloaded from [HERE]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-kbuild-2.6%2Flinux-kbuild-2.6.18_2.6.18-1_i386.deb&md5sum=77c86452edf1c8ddcfa0334419be00f0&arch=i386&type=main") 

04) linux-headers-2.6.18-2-multimedia-486_2.6.18-5_i386.deb (64 Studio CD)

---

### Post by Bloke on 2006-12-15
The title of this post should read: "Nvidia drivers / 64 Studio kernel **source**"

Not: Nvidia drivers / 64 Studio kernel **headers**

I didnt know how to change it.

---

### Post by MetalMusicAddict on 2006-12-15
Keep an eye on the [Ubuntu Studio Project]("http://ubuntustudio.org/") and look at the [Multimedia Production Kernel]("https://wiki.ubuntu.com/MultimediaProductionKernel") spec. Also in Feisty currently theres a -lowlatency kernel that im told works on Edgy if you cant wait till Feisty.

---

### Post by Bloke on 2006-12-15
I got the drivers installed.

01) install / updated 6.10

02) used the 4 files from my post above

03) edited xorg.conf from "nv" to "nvX", and rebooted. I find this easiest to make sure X is not running.

04) cd'ed to NVIDIA-Linux-x86-1.0-8776-pkg1.run (I realize its not the latest) and ran it:
"sudo ./NVIDIA-Linux-x86-1.0-8776-pkg1.run"

The installer complained about the system being "modular", and to make certain adjustments if the drivers failed to work. I let the installer adjust my xorg.conf file for me.

05) rebooted / tested Foobillard = success

---

### Post by tseliot on 2006-12-15
> **Bloke said:**
> The title of this post should read: "Nvidia drivers / 64 Studio kernel **source**"

Not: Nvidia drivers / 64 Studio kernel **headers**

I didnt know how to change it.

Changed ;)

---

### Post by oblio9 on 2007-01-06
Bloke - 
  I have tried your method (though using 2.6.17 from the 64 Studio cd) and am running into an error. When I try and install the nvidia driver it says I am missing the libc dev package. I've tried to install build-essential but that is giving me dependency issues. If you ran into this how did you sort it out? Or anyone else that may read this??? Thanks for any help.
-O

---

