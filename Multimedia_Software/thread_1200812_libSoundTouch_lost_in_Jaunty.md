---
title: "libSoundTouch lost in Jaunty"
date: 2009-06-30
forum: Multimedia Software
---

### Post by CVarin on 2009-06-30
I posted this in the Multimedia Production forum and got no response, soI thought I'd try it here.
After upgrading my Dell Latitude D530 from Intrepid to jaunty, Audacity will not load, exiting with the error:
audacity: error while loading shared libraries: libSoundTouch.so.1: cannot open shared object file: No such file or directory

I tried reinstalling Audacity with no luck. I tried ReZound and got an identical message. Gnusound restarts the entire X-windows system, leaving me at the login prompt.

I tried using apt to install libSoundTouch and got the following:
****~$ sudo apt-get install libsoundtouch1-dev libsoundtouch1c2 soundstretch
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsoundtouch1c2 is already the newest version.
libsoundtouch1c2 set to manually installed.
soundstretch is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsoundtouch1-dev: Depends: libsoundtouch1c2 (= 1.3.1-2) but 1.3.1-mb1 is to be installed
E: Broken packages


Any suggestions?  An alternative working sound editor?  Any help appreciated.

---

### Post by ajgreeny on 2009-06-30
That is very strange because I have audacity and use it a lot on jaunty without any problems, and I have the version of libsoundtouch 1.3.1-2, that you can't find, showing in synaptic.  Check you have the universe repos enabled, as it is in that as far as I can see, and there should be absolutely no problem getting it up and running

I'm sure there are other sound editors available, but life without audacity would be unthinkable to me.

---

### Post by CVarin on 2009-07-01
I have universe enabled.  What it seems to be balking about is libsoundtouch1c2, and Synaptic shows that as 1.3.1-mb1, just as the error message indicates.  I upgraded from Hardy to Intrepid and now from Intrepid to Jaunty.  Did something get broken along the way, perhaps?

---

### Post by ajgreeny on 2009-07-01
In synaptic preferences you can choose to add a column which allows you to see which repo the packages come from (component & section both do this) so I would be interested to see where your libsoundtouch comes from, because it is a different version to mine.  I assume it must be from a third party repo, or you may have the backports or proposed repos enabled, otherwise I can see no reason why you would have a different version available to me.

A last thought! in **synaptic > package > force version**, you may find both versions, ie your 1.3.1-mb1 and my 1.3.1-2 are shown and you can then install the 1.3.1-2 needed.

---

