---
title: "VlC 2.1.3 checkinstall failed"
date: 2014-02-09
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2014-02-09
Hi,

I am trying to compile VLC 2.1.3 from source on Ubuntu 13.10, It was compiled and builded without error (I tested the binary created after 'make' and it works well) But the last step
"sudo checkinstall" failed with these errors.

 ```
/bin/mkdir -p '/usr/local/bin'
 /usr/bin/install -c cvlc rvlc qvlc svlc nvlc '/usr/local/bin'
make  install-exec-hook
make[4]: Entering directory `/home/mb/Downloads/vlc-2.1.3'
if test "x86_64-unknown-linux-gnu" = "x86_64-unknown-linux-gnu"; then \
        PATH="/usr/local/bin:$PATH" \
        LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH" \
        "/usr/local/lib/vlc/vlc-cache-gen" \
             "/usr/local/lib/vlc/plugins" ; \
    else \
        echo "Cross-compilation: cache generation skipped!" ; \
    fi
/bin/bash: line 7: 21608 Segmentation fault      PATH="/usr/local/bin:$PATH" LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH" "/usr/local/lib/vlc/vlc-cache-gen" "/usr/local/lib/vlc/plugins"
make[4]: *** [install-exec-hook] Error 139
make[4]: Leaving directory `/home/mb/Downloads/vlc-2.1.3'
make[3]: *** [install-exec-am] Error 2
make[3]: Leaving directory `/home/mb/Downloads/vlc-2.1.3'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/mb/Downloads/vlc-2.1.3'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mb/Downloads/vlc-2.1.3'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

```

I have done this many times before (with VLC up to 2.1.2) and never had a problem. Not sure what went wrong this time.

Please help.

---

### Post by andrew.46 on 2014-02-09
Interesting to see the full ./configure & checkinstall syntax?

---

### Post by monkeybrain20122 on 2014-02-09
The commands are just 
./configure 
and I let vlc to figure out what options to enable (usually I just check the configure log if I need something which is not enabled, then just install the appropriate -dev files.  it is built as shared library and install to /usr/local)

then just make and sudo checkinstall (I only changed to documentation, --line 1,-- from "package created by checkinstall1.6.2" to "multimedia player and streamer", everything else just as is)

So make install (or checkinstall?) failed. But the binary is built in my home and it works.

---

### Post by andrew.46 on 2014-02-09
Perhaps try the checkinstall line I have used successfully [for vlc-git]("http://ubuntuforums.org/showthread.php?t=2141949"):

```

sudo checkinstall --pakdir "$HOME/Desktop --backup=no --deldoc=yes \
                  --pkgname vlc --pkgversion "2.1.3" \
                  --fstrans=no --deldesc=yes --delspec=yes --default

```

and modified slightly for your compile.

---

### Post by monkeybrain20122 on 2014-02-09
Hi,

Thanks. I will try it after dinner. But IIRC I already fixed some of the options (fstrans=no, e.g) in /etc/checkinstallcr, so may be make install for some reason doesn't work (so a VLC issue instead of a checkinstall issue?)

---

### Post by andrew.46 on 2014-02-09
Could be, I am only compiling the current development version so I am not aware of any issues with the release version. But if you continue to have some issues I am more than happy to download the release version and compile it, I run a VM devoted entirely to building vlc so this would not be a huge drama and I could have a closer look at the install process... I will try after lunch :)

---

### Post by andrew.46 on 2014-02-09
OK so I had a quick lunch :). Installation ran perfectly here with no installation problems. If you are interested in following my guide:

Howto: Compile the development version of vlc under the latest Ubuntu release
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

simply use the info below to compile the release version:

```

cd $HOME/vlc_build/ && \
wget http://download.videolan.org/pub/videolan/vlc/2.1.3/vlc-2.1.3.tar.xz && \
tar xvf vlc-2.1.3.tar.xz && cd vlc-2.1.3 && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local  && \
make -j 4 && \
mkdir -vp doc-pak && cp -v AUTHORS ChangeLog COPYING INSTALL NEWS README THANKS doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "2.1.3" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

which I may add into the guide when I return from 2 weeks away.

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.1.3 Rincewind (revision 2.1.3-0-ge6a71cc)
VLC version 2.1.3 Rincewind (2.1.3-0-ge6a71cc)
Compiled by andrew on corinth (Feb 10 2014 12:44:40)
andrew@corinth:~$ 

```

But I am not sure at all as to what is going on with your installation I'm afraid......

---

### Post by monkeybrain20122 on 2014-02-09
It is strange. I have another Ubuntu13.10 installed in an external hd and it works. 

 ```
/bin/mkdir -p '/usr/local/bin'
 /usr/bin/install -c cvlc rvlc qvlc svlc nvlc '/usr/local/bin'
make  install-exec-hook
make[4]: Entering directory `/home/monkeybrain/vlc-2.1.3'
if test "x86_64-unknown-linux-gnu" = "x86_64-unknown-linux-gnu"; then \
        PATH="/usr/local/bin:$PATH" \
        LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH" \
        "/usr/local/lib/vlc/vlc-cache-gen" \
             "/usr/local/lib/vlc/plugins" ; \
    else \
        echo "Cross-compilation: cache generation skipped!" ; \
    fi
make[4]: Leaving directory `/home/monkeybrain/vlc-2.1.3'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/monkeybrain/vlc-2.1.3'
make[2]: Leaving directory `/home/monkeybrain/vlc-2.1.3'
make[1]: Leaving directory `/home/monkeybrain/vlc-2.1.3'

======================== Installation successful ==========================

```

Grab the .deb created in this installation and it installs perfectly in the original one..Not sure what the problem is... Hate it when this happens for it would be horrible to try to figure out where the problem is. Thanks for the time and effort.

I did compile vlc from git before but always had some broken things (some formats don't play, volume control not working etc) so I have decided to stick with the release version as long as it is up to date and have all the features I want enabled (sadly not from any Ubuntu repo or ppa) The compiling is normally pretty easy.

---

### Post by andrew.46 on 2014-02-09
And thanks for getting me to have a look at the release version, it will be a nice addition to my guide, particularly if Trust does not ship with the latest vlc.

---

### Post by monkeybrain20122 on 2014-02-09
Hi, since you are bringing this up, just want to call your attention to the fact that phononbackend-vlc needs to be rebuilt  against the new vlc (whether it is from git or the released version higher than available in Ubuntu) When you switch to a newer version of Vlc phononbackend-vlc becomes uninstallable or it will be removed if already installed. In 13.10 it requires a higher version of libphonon as well. It happens to be available from ppa or you need to compile it too.

---

### Post by andrew.46 on 2014-02-09
Yet another excellent reason that my own guide should be undertaken in a Virtual Machine! Have you got to the bottom of the checkinstall problem with your installation? Or perhaps you are simply happy to have vlc running successfully :)

---

### Post by monkeybrain20122 on 2014-02-09
I am still investigating it. I am going to compare the configure log in both installations..

If you are doing this in VMs which version of VLC do you actually use? :)

---

### Post by monkeybrain20122 on 2014-02-10
This is unrelated but sort of strange. In order to rule out it is a checkinstall problem I am doing an experiment. I am rebuilding vlc with ./configure --prefix=$HOME/Downloads/vlc-2.1.3/vlc-install, where vlc-install is a directory I created. So I can test just "make install" to this directory without messing up my file system
Now run make with no issue, I run make install and get

```
/bin/mkdir -p '/usr/share/kde4/apps//solid/actions'
 /usr/bin/install -c -m 644 solid/vlc-openbd.desktop solid/vlc-opencda.desktop solid/vlc-opendvd.desktop solid/vlc-openvcd.desktop '/usr/share/kde4/apps//solid/actions'
/usr/bin/install: cannot remove &#8216;/usr/share/kde4/apps//solid/actions/vlc-openbd.desktop&#8217;: Permission denied
/usr/bin/install: cannot remove &#8216;/usr/share/kde4/apps//solid/actions/vlc-opencda.desktop&#8217;: Permission denied
/usr/bin/install: cannot remove &#8216;/usr/share/kde4/apps//solid/actions/vlc-opendvd.desktop&#8217;: Permission denied
/usr/bin/install: cannot remove &#8216;/usr/share/kde4/apps//solid/actions/vlc-openvcd.desktop&#8217;: Permission denied
make[3]: *** [install-soliddataDATA] Error 1
make[3]: Leaving directory `/home/monkeybrain/Downloads/vlc-2.1.3/share'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/monkeybrain/Downloads/vlc-2.1.3/share'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/monkeybrain/Downloads/vlc-2.1.3'
make: *** [install] Error 2
```

Why would it even try to write to the File system with Prefix $HOME?

This is unrelated to the original question as it happens in both my Ubuntu installs, but nevertheless curious. Am I missing something obvious?

---

### Post by andrew.46 on 2014-02-10
> **monkeybrain20122 said:**
> Why would it even try to write to the File system with Prefix $HOME?

At a guess the desktop files belong to one of the categories below which are not governed by $PREFIX:

```


Fine tuning of the installation directories:
  --bindir=DIR            user executables [EPREFIX/bin]
  --sbindir=DIR           system admin executables [EPREFIX/sbin]
  --libexecdir=DIR        program executables [EPREFIX/libexec]
  --sysconfdir=DIR        read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data [PREFIX/var]
  --libdir=DIR            object code libraries [EPREFIX/lib]
  --includedir=DIR        C header files [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc [/usr/include]
  --datarootdir=DIR       read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR           read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR           info documentation [DATAROOTDIR/info]
  --localedir=DIR         locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR            man documentation [DATAROOTDIR/man]
  --docdir=DIR            documentation root [DATAROOTDIR/doc/vlc]
  --htmldir=DIR           html documentation [DOCDIR]
  --dvidir=DIR            dvi documentation [DOCDIR]
  --pdfdir=DIR            pdf documentation [DOCDIR]
  --psdir=DIR             ps documentation [DOCDIR]

```

although I would have thought that you would be looking at DATAROOTDIR which is defined by $PREFIX..... so I am not sure...

---

### Post by andrew.46 on 2014-02-10
> **monkeybrain20122 said:**
> If you are doing this in VMs which version of VLC do you actually use? :)

To tell the truth my day to day work is done in Slackware and at the moment I am actually using a vlc *package* of 2.1.3 built by alienBOB, the man who provided all of the good ideas for my own vlc guide :)

---

### Post by monkeybrain20122 on 2014-02-10
I am quite at a lost. Did a diff on both configure logs and found nothing unusual. I simply cp checkinstallrc from the install where it works to another, didn't do anything..
Searched google some arch guys said libfluidsynth was the culprit but the install where it worked has libfluidsynth installed so that couldn't be the cause. The closest thing I found was the post of jplatt39 on [http://alien.slackbook.org/blog/vlc-media-player-at-version-2-0-0/](http://alien.slackbook.org/blog/vlc-media-player-at-version-2-0-0/) But alienbob didn't have an answer.


Edited: when running ./bootstrap there is a message saying gttext is not installed or outdated .. (I have all the relevant packages installed are in the latest versions as far as Ubuntu can provide,--same major version of gttext as in Trusty) What is it about? Is that in the git version of vlc? This has nothing to do with the original question of this thread as the message appears in both my installs, vlc is successfully built in both and checkinstall was successful in one despite the warning.

---

### Post by monkeybrain20122 on 2014-02-11
Well I have compiled a few other things with checkinstall and there was no problem whatsoever. I have a theory but I am not going to risk breaking vlc to test it. 

I now remember Vlc 2.1.2 on this Ubuntu system was also a deb I created from the other Ubuntu system, as was the package phononbackend-vlc. Instead of removing Vlc1.08 or whatever from the repo I updated by installing the .deb on top, which had a different prefix (/usr/local instead of /usr) and then sudo ldconfig. I compiled the deb with prefix=/usr/local in the original system because had I set prefix=/usr then phononbackend-vlc would be replaced by phononbackend-null or gstreamer and for some strange dependency reasons I couldn't easily switch back, so I had to keep this package somehow coexisted with an incompatible vlc, and then compile a newer version against the new vlc libs then upgraded by installing the .deb thus created. The approach was convoluted and ugly. There may be a better way of doing it when I think about it now, but I am not going to spend hours to find out.

So it is possible that something got messed up then. In order to test this I would have to unsinstall vlc (so far I am only upgrading) and I am not in the mood of doing it  because the phonon thing is a bit tricky and I remember having spent hours on finding a way to do that. I now have the latest vlc with all the features I want. I suppose I can do the same thing for the next vlc update  by making a deb in the other Ubuntu and install it until 13.10 reach eol. So I am marking this thread as solved.

**Edited:** Hmm.. maybe I will test it after I created a partial clone of this system elsewhere.. but that will need to wait..

---

