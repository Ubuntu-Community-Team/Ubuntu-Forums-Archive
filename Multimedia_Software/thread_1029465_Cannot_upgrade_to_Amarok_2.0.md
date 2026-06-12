---
title: "Cannot upgrade to Amarok 2.0"
date: 2009-01-03
forum: Multimedia Software
---

### Post by ChronicLogic on 2009-01-03
I know this posting was already discussed here:

[http://ubuntuforums.org/showthread.php?t=1008837&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1008837&highlight=amarok)

But No one seemed to be able to help, either never responded, so I felt the need to re-post this on a new thread. 

Thanks for understanding, I really want Amarok to be installed and fully functional,, :P

Any help from the Masters Of Ubuntu is well appreciated!



> **ChronicLogic said:**
> Well when I attempted the above terminal entry here were the results of the entry attempt:


diane@dianes-desktop:~$ sudo apt-get install amarok-kde4
[sudo] password for diane: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
diane@dianes-desktop:~$ sudo apt-get install amarok-kde4
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
  amarok-kde4: Depends: kdebase-runtime (>= 4:4.1.2) but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.1.3) but it is not going to be installed
               Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu4 is to be installed
               Depends: libgcrypt11 (>= 1.4.0) but 1.2.4-2ubuntu7 is to be installed
               Depends: libmtp8 but it is not installable
               Depends: libphonon4 (> 4:4.2.0) but it is not going to be installed
               Depends: libqt4-dbus (>= 4.4.3) but it is not installable
               Depends: libqt4-network (>= 4.4.3) but it is not installable
               Depends: libqt4-opengl (>= 4.4.3) but it is not installable
               Depends: libqt4-script (>= 4.4.3) but it is not installable
               Depends: libqt4-sql (>= 4.4.3) but it is not going to be installed
               Depends: libqt4-svg (>= 4.4.3) but it is not installable
               Depends: libqt4-webkit (>= 4.4.3) but it is not installable
               Depends: libqt4-xml (>= 4.4.3) but it is not installable
               Depends: libqtcore4 (>= 4.4.3) but it is not installable
               Depends: libqtgui4 (>= 4.4.3) but it is not installable
               Depends: libstreamanalyzer0 (>= 0.5.11) but it is not going to be installed
               Depends: libstreams0 (>= 0.5.11) but it is not going to be installed
               Depends: libtag1c2a (>= 1.5) but 1.4-8ubuntu1 is to be installed
               Depends: phonon (> 4:4.2.0) but it is not installable
E: Broken packages
diane@dianes-desktop:~$ 




Hmm, Now what? :P

Thanks in advance.

---

