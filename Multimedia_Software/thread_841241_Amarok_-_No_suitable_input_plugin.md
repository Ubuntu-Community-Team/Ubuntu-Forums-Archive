---
title: "Amarok - No suitable input plugin"
date: 2008-06-26
forum: Multimedia Software
---

### Post by diablo75 on 2008-06-26
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75383&stc=1&d=1214477798[/IMG]

This doesn't seem to happen with all streams.  The one tried above is the radio station called Philosomatika.  I can play their station by going to their website and streaming their mp3 from the direct link, but it seems to cause Amarok to turn grey for about a minute, and then the above error appears.

---

### Post by Pu1se on 2008-07-05
I am having the same problem. I'm trying to connect two different streams from different sites. I get the same error when I try to [www.etn.fm](www.etn.fm) streams and the same with [www.di.fm](www.di.fm) streams. I don't have any problems with sound or playing mp3,aac files. So if anyone out there could help us that would be great. 

Thank you

---

### Post by diablo75 on 2009-01-06
Bump  :)

---

### Post by Levias on 2009-03-13
I have got the same problem, amarok says "No suitable input plugin. ..."

I was trying to play last.fm.

Switching between OSS, ALSA, Pulseaudio, ... didnt help.

commandline outpout of amarok:
```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
user@pc-user:~$ QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3e0009e
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3e00088
```

```

uname -a
Linux pc-user 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

```

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

```

```

dpkg-query --show -f='${Package}\t${Version}\n' | grep -i amarok
amarok	2:1.4.10-0ubuntu3
amarok-common	2:1.4.10-0ubuntu3
amarok-engine-xine	2:1.4.10-0ubuntu3
amarok-engine-yauap	2:1.4.10-0ubuntu3
amarok-engines	2:1.4.10-0ubuntu3

```

---

### Post by PrinceArithon on 2009-03-14
OK what you definitely need to do is go to Synaptic (or whatever the KDE version of Synaptic is) and go download the FFMPEG, gstreamer0.10-ffmpeg, libxine1-ffmpeg.

Now for KDE you may have something else you can used instead of gstreamer but I don't know what it is you'll have to look it up.

Anyway after you download those 3 packages it won't give you the error anymore...at least it shouldn't.

---

### Post by Levias on 2009-03-16
im working with gnome

all the packages you mentioned were installed all the time

```

 dpkg-query --show -f='${Package}\t${Version}\n' | grep -i gstreamer
bluez-gstreamer	4.12-0ubuntu5
gstreamer0.10-alsa	0.10.21-3
gstreamer0.10-ffmpeg	0.10.5-1
gstreamer0.10-gnomevfs	0.10.21-3
gstreamer0.10-plugins-bad	0.10.8-1
gstreamer0.10-plugins-bad-multiverse	0.10.6-1ubuntu1
gstreamer0.10-plugins-base	0.10.21-3
gstreamer0.10-plugins-base-apps	0.10.21-3
gstreamer0.10-plugins-good	0.10.10.4-1ubuntu1
gstreamer0.10-plugins-ugly	0.10.9-1ubuntu0.1
gstreamer0.10-plugins-ugly-multiverse	0.10.7-2
gstreamer0.10-pulseaudio	0.10.10.4-1ubuntu1
gstreamer0.10-schroedinger	1.0.5-1
gstreamer0.10-tools	0.10.21-4
gstreamer0.10-x	0.10.21-3
libgstreamer-plugins-base0.10-0	0.10.21-3
libgstreamer0.10-0	0.10.21-4
totem-gstreamer	2.24.3-0ubuntu1

```

```

 dpkg-query --show -f='${Package}\t${Version}\n' | grep -i ffmpeg
ffmpeg	3:0.svn20080206-12ubuntu3
gstreamer0.10-ffmpeg	0.10.5-1
libxine1-ffmpeg	1.1.15-0ubuntu3.1intrepid1

```

---

### Post by markbuntu on 2009-03-16
Amarok uses the xine engine so you need xine and all the xine plugins. If you are using Amarok2 in Intrepid, amarok uses the new phonon api which also uses xine. Phonon and the basic xine engine and kde base should have been installed automatically as dependencies with amarok if you are using gnome but the plugins may not have been.

libxine1-ffmpeg
libxine1-all-plugins
libxine1-misc-plugins

KDE and Amarok do not use gstreamer and xine does not have ALL the codecs yet so some things will not work.

---

### Post by Levias on 2009-03-17
installing these libxine*-packages didnt help

however a fiend told me to uninstall all pulseaudio-packages (it messes up alsamixer) and after uninstalling them all radios except lastfm are woring

---

### Post by UltraAnders on 2009-04-06
Anyone found a way to get LastFM working? I just installed Amarok to try as an alternative to Rythmbox and I'm very impressed ... but the lack of LastFM support means I probably won't stick with. I found this on  [LastFM](http://www.lastfm.de/group/Amarok+Users/forum/18538/_/500689/) discussion which suggests it's caused by something being switched off at LastFm's side.

---

### Post by neu2buntu on 2009-04-06
if i remember right dont you have to register with lastfm? maybe you have already done this?

---

### Post by Levias on 2009-04-08
yes i did

my laftfm account is working, i tested it with rhytmbox

---

### Post by UltraAnders on 2009-04-16
Been registered with LastFM for ages. Works fine in Rythmbox, just prefer the look and feel of Amarok. No solution beyond trying to upgrade to Amarok 2 then?

---

### Post by neu2buntu on 2009-04-16
i will install amarok and see if i can get this sorted!! i use rhythmbox myself...

---

### Post by neu2buntu on 2009-04-16
ok on my 1st run with amarok 1.4 im getting the same error when trying to play lastfm....back to the drawingboard...lol (this was just the basic install from ticking "amarok" and in total 6 packages were installed, from synaptic) and also when setting up there were 2 other options i chose "sqlite" there was also "mysql" and another (although this may be irrellevent,wont just rule out yet)

---

### Post by neu2buntu on 2009-04-17
tried all the fixes from the forums old and new,it seems to be something to do with compatability with amarok 1.4 and last.fm stream. i have just upgraded to amarok 2 (amarok kde4 from synaptic) and last.fm is working great.... and im running in the gnome desktop environment!!!

---

### Post by UltraAnders on 2009-04-17
Thanks for taking the time to look at this.

I added the repo:
```

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

```
and for the key:
```

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 9423A34CCA967634 && gpg --armor --export 9423A34CCA967634 | sudo apt-key add -

```
but when I try to install amarok-kde4 I get this error:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  amarok-kde4: Depends: kdebase-runtime (>= 4:4.1.2) but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.1.2) but it is not going to be installed
E: Broken packages

```
It's a this point I realise the magic letters KDE ... but you're using Gnome? I'm quite a novice at this if you can't tell :D

---

### Post by neu2buntu on 2009-04-17
hmmm this is getting more complex by the minute..... probably the reason my system was "ready" for amarok2 is that i have been installing and uprading kde programs inside gnome and building cutting edge programs from source from e.g svn.  my system is hacked to pieces and if i had a crash it would take months to get back...  heres a screenshot of my 3rd party sources (this may help,not sure!!)



i can usually get things working,but i lose track of how i got there,. if my memory serves me right(dont quote me on this) qt3 qt4 plays a part in kde and gnome!!!


i do not have kde ie the desktop environment installed,yet i can run all kubuntu packages(although i get an error on logout,where system looks for kde sometimes...) God my post is getting long:-\" maybe search "kubuntu inside gnome" or something......

hopefully someone with knowledge on this will be along soon UltraAnders/*



cd ~/


and i was just thinking maybe this can help ```
sudo dpkg --configure -a
``` the command for fixing broken packages or goto >system>administration>synaptic p.m.>edit>fix broken packages (think the latter is the gui for 1st command)

---

### Post by UltraAnders on 2009-04-18
Ah, getting well beyond my level of knowledge now! I tried the fix broken packages thing, but still the same error.

Tried to install kubuntu-desktop but that also throws lots of errors, despite other posts suggesting this should be possible. :(

---

