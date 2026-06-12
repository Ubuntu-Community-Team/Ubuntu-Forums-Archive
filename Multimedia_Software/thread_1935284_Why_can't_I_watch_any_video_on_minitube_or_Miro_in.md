---
title: "Why can't I watch any video on minitube or Miro internet tv?"
date: 2012-03-04
forum: Multimedia Software
---

### Post by agentfortyseven on 2012-03-04
hello friends,
I need an application like minitube on my computer. I tried mythtv but its too complicated. I've tried minitube and Miro internet tv but I can't watch any video. Can anyone tell me what could possibly be wrong?

---

### Post by sunewbie on 2012-04-29
same here, me too, I tried on both Ubuntu and Xubuntu 12.04

Video is not streamed. Audio plays

---

### Post by evilsoup on 2012-04-29
Have you tried the version from the [website]("http://flavio.tordini.org/minitube")?
The version in the repositories is outdated (this may or may not be the case for 12.04, I haven't upgraded yet).
Oh there's also a PPA (**[ppa:ferramroberto/minitube]("https://launchpad.net/%7Eferramroberto/+archive/minitube"))**, but I can't speak to its quality, having not used it myself.

---

### Post by sunewbie on 2012-04-29
Software center contains latest version

I also tried to install tarball, though I am not comfortable with tarballs, but could not do it.

The installation instructions say to install dependencies

```
sudo apt-get install libqtgui4 libqt4-xml libqt4-network libqt4-dbus phonon-backend-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
```

and to remove

```
sudo apt-get remove phonon-backend-xine
```

[http://flavio.tordini.org/minitube/minitube-linux-setup](http://flavio.tordini.org/minitube/minitube-linux-setup)

Xine cannot be removed.

```
Virtual packages like 'phonon-backend-xine' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Dont know what to do? any idea?

---

### Post by mc4man on 2012-04-29
Minitube suffers from 2 bugs
One causes it to crash ocassionally, don't have link handy atm

The other is gstreamer will fail to decode many youtube vid's, you'll only get sound

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

If you where to have minitube use the phonon-backend-vlc that would resolve the decoding issue.
Unfortunately minitube packages in ubuntu depend on the gstreamer backend & will use it over the vlc one.

There are ways around this depending on what you want to do

You can install the vlc backend, remove the gstreamer one & minitube, Then just use the pre-compiled binary downloaded from minitube site manually 

Or you can install the vlc backend, - then
 Take the current repo minitube deb package & unpack it. Edit the control file to allow the vlc backend, repack & re-install. 
Then remove the gstreamer backend
(actually easier to do then it sounds

I did request a change in the minitube packaging 2 months ago to allow either backend but it was never done, too bad really
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

---

### Post by sunewbie on 2012-04-29
ok thanks. So basically it's a bug. 

I reinstalled it a couple of times, purged and installed, installed from weupd8 ppa, still the same result. 

When I read it for first 2 times, I thought it to be complicated. So I left it for some time and came back again. Now I can understand what are you trying to say :)

It plays few videos,but not the most of videos

I will try gmediafinder

[http://www.linuxandlife.com/2012/04/gmediafinder-better-alternative-for.html](http://www.linuxandlife.com/2012/04/gmediafinder-better-alternative-for.html)

---

### Post by sunewbie on 2012-04-29
cannot install gmediafinder :(

```
Reading state information... Done
E: Unable to locate package gmediafinder
```

any other alternatives

---

### Post by agentfortyseven on 2012-05-01
I guess I'm better off without minitube or miro internet tv. I hate bugs (bedbugs included).

---

### Post by sunewbie on 2012-05-06
@mc4man

Sorry for delayed response, my house is under renovation.

there are many gstreamer plugins. Which one should I have to uninstall.

It is confusing. 

UnPacking and repacking is a bit difficult. I will try it in free time. It will be a learning experience, but not today.

I think I will directly use youtube.

---

