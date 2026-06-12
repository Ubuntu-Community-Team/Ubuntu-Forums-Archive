---
title: "Brasero on Lucid RC cannot create CD image"
date: 2010-05-03
forum: Multimedia Software
---

### Post by RavanH on 2010-05-03
Hi,

After upgrading to Lucid RC I notice that I cannot create a CD image anymore. Brasero gives me three options : two .toc and one .cue file format but neither of them work :(

the CDDAO variant of the .toc format gives me a notification that i need to install some extra packages but even after installing those, the image creation hangs. I used to be able to create .iso images but that option has completely gone...

Any solutions around?

---

### Post by RavanH on 2010-05-04
So far, this seems to be two issues at once... 

**1.** The first is some problem with Cdrdao dependencies where Brasero first reported that the packages **cdrdao** and **toc2cue** (! not cue2toc as it should read) needed to be installed and after installing them via Synaptic (not even a nice auto-installer dialog like with codecs in Rythmbox and such :( ) it STILL tells me "not all required programs and libraries are installed" and then comes up with an EMPTY list of packages to install :confused:

**2.** The other seems to be some problem with the auto-mounting of CD/DVD that is new in Lucid. Found that 10.04 no longer uses an /etc/fstab entry to configure the mount point for the device and during the reading/copying process the CD appears to suddenly unmount -- causing the reading/copying to halt and wait indefinately... 

Weird stuff going on. This Lynx is too Lucid :(

---

### Post by RavanH on 2010-05-04
Some extra info that might explain issue 1:

On the Plugins dialog in Brasero the cdrdao plugin is switched off and cannot be checked. Below it, it is stated: "cdrdao version is too old" even though it is the latest in the repository!

And a related bugreport shows me I am not the only one :( :
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696)

---

### Post by itsols on 2010-06-27
So that definitely sounds like a bug. Even I had a similar issue but not with ISO... I mean, I never really tried ISO burning after the upgrade.

I'm on Ubuntu 10.4, fully up-to-date.
After burning a .wav file as a CD audio on the disk, I only find the disk still EMPTY!

Maybe you should report this as a bug.

Cheers!

---

### Post by lisati on 2010-06-27
Notice the date of the thread and the fact that it's about the Release Candidate, not the final release. There are likely to have been updates since.

Thread closed.

---

