---
title: "Cannot upgrade to Amarok 2.0"
date: 2008-12-11
forum: Multimedia Software
---

### Post by reswob on 2008-12-11
(sorry if this is long, I've been searching around trying to see if someone else has had and fixed this problem already)

Argh. I've been trying to install Amarok 2.0 on Ubuntu 8.04, but almost all my attempts have yielded version 1.4.9

I've added the following repositories and performed an apt-get update.

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

I ran the following command "sudo apt-get install amarok -V"

and got this response:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
   amarok-xine (1.4.9.1-0ubuntu3.1+medibuntu1)
   libifp4 (1.0.0.2-3)
   libmp4v2-0 (1.6dfsg-0.2ubuntu1)
   libofa0 (0.9.3-2ubuntu2)
   libpq5 (8.3.5-0ubuntu0.8.04)
   libruby1.8 (1.8.6.111-2ubuntu1.2)
   libtunepimp5 (0.5.3-6ubuntu4)
   libxcb-shape0 (1.1-1ubuntu1)
   libxcb-shm0 (1.1-1ubuntu1)
   libxcb-xv0 (1.1-1ubuntu1)
   libxine1 (1.1.11.1-1ubuntu3.1)
   libxine1-bin (1.1.11.1-1ubuntu3.1)
   libxine1-console (1.1.11.1-1ubuntu3.1)
   libxine1-ffmpeg (1.1.11.1-1ubuntu3.1)
   libxine1-misc-plugins (1.1.11.1-1ubuntu3.1)
   libxine1-plugins (1.1.11.1-1ubuntu3.1)
   ....
   ....[/I]

Notice the version of Amarok it wants to install.

I tried the steps in the following thread, but that didn't help.

[http://ubuntuforums.org/showthread.php?t=1000406&highlight=amarok+2](http://ubuntuforums.org/showthread.php?t=1000406&highlight=amarok+2)


I tried the suggestions in the following thread, but that installed Amarok 1.92:

[http://ubuntuforums.org/showthread.php?t=1000112&highlight=amarok+2](http://ubuntuforums.org/showthread.php?t=1000112&highlight=amarok+2)

I had to remove this version as it was not stable and kept crashing.

Going to the actual Amarok web page, they have Kubuntu instructions (repeated above) and a link for a Debian install.

The Debian download ( link at [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download)) says that Amarok 2.0 only works on Debian unstable and you must load the experimental repository.  The directions ([http://wiki.debian.org/DebianExperimental](http://wiki.debian.org/DebianExperimental)) give the repository required.  However, when I try to load that repository, I get an error.  Then attempting to load Amarok, again loads 1.4.9.

When I use Synaptic Package Manager and search for Amarok (using several variations of the repositories referred to above), the packages it finds all say version 2:1.4.9, but SPM **still** loads 1.4.9.  

Even more interesting, when I look at the installed software in SPM, it SAYS it installed 2:1.4.9 ... which obviously is not 2.0 . 

OK, I give.  I'm stumped.

Suggestions?

---

### Post by cariboo on 2008-12-12
You can download Amarok 2.0 [here.]("http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/") Let gdedi take care of the dependencies.

Jim

---

### Post by wfp on 2008-12-13
Thanks for the link to that amd64.deb

---

### Post by Killeroid on 2008-12-19
You are actually trying to install the wrong version of amaerok. Your install command should be   ```
sudo apt-get install amarok-kde4
```

---

### Post by ChronicLogic on 2009-01-03
> **Killeroid said:**
> You are actually trying to install the wrong version of amaerok. Your install command should be   ```
sudo apt-get install amarok-kde4
```

Well when I attempted the above terminal entry here were the results of the entry attempt:


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

### Post by qazokm on 2009-01-14
I successfully installed Amarok 2.0 with using the two files below.

Remove older versions of Amarok the install [amarok-mysql-data]("http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-mysql-dfsg-5.1/amarok-mysql-data_5.1.26rc-0ubuntu1~ppa1_all.deb") first. 

Then install this. [Amarak 2.0]("http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/amarok-kde4_2.0.1.1-0ubuntu1~ppa1_amd64.deb")

---

### Post by mandeepsmagh on 2009-02-08
Thanks every one for sharing info on how to install amarok 2.0. It was a big help for me.Thanks

---

### Post by versai on 2009-02-17
thanks cariboo! great link, hope it works for me.

versai

---

### Post by matyasfalvi on 2009-07-16
Hi Everyone!

I tried Carbioo's advice and i get this from Gdebi:

```
Error: Dependency is not satisfiable: kdebase-runtime
```

although I have all the kdebase-runtime packeges installed.

I attached two screenshots one from the package installer and one from the synaptic package manager.

I'd appreciate any kind of help.

Thanx

---

### Post by matyasfalvi on 2009-07-17
What do you guys think about trying this:

```
sudo apt-get install kubuntu-desktop

```

?

I'm just asking 'cause I don't really wanna install it just so I can use amarok.

Or could maybe anyone with an intel cpu tell how they got their amarok working?

thanx

---

