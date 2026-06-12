---
title: "vlc 2.1 on 13.10 when?"
date: 2013-10-22
forum: Multimedia Software
---

### Post by forcecore on 2013-10-22
Even official Videolan ppa has been eliminated now, it is year 2013 and Ubuntu should at least use half rolling for 3-rd party software that has new stable release.

Anyone knows why ppa:videolan/stable-daily eliminated 2.1 builds? even Win and Mac os gets 2.1.

---

### Post by mc4man on 2013-10-22
Seems a bit odd, the ppa just did 2.1 builds for 13.10 yesterday as shown here, & 14.04 builds are scheduled
[https://code.launchpad.net/~videolan/+recipe/stable-daily](https://code.launchpad.net/~videolan/+recipe/stable-daily)
You could try a email thru the ppa or ask in the videolan forums

(the last build has packages available but you'd need to manually download & install
Edit: the built 13.10 packages are a bit 'wierd' in that they can't be uipgraded with in a typical way, though certainly do-able
(they need some new dependencies installed
libbasicusageenvironment0 (2013.04.30-1)
libgnutls28 (3.2.3-1ubuntu1)
libgroupsock0 (2013.04.30-1)
libhogweed2 (2.7.1-1)
liblivemedia7 (2013.04.30-1)
libtasn1-6 (3.3-2)
libusageenvironment0 (2013.04.30-1)
And a slightly different dpkg command if vlc repo version is installed
sudo dpkg --auto-deconfigure -i  *.deb

---

### Post by forcecore on 2013-11-01
Any news about vlc 2.1 for 13.10 from official integration, dont know but at least they should add into backports. People really need half rolling release. I just told someone who got Ubuntu 13.10 from me that: sorry but Ubuntu do not update software in that way. This resulted that he returned to Windows again until Ubuntu becomes easier from software installation side(half rolling or seperated setup packages with own dependencies)

VLC ppa is still not functioning too [https://launchpad.net/~videolan/+archive/stable-daily?field.series_filter=saucy](https://launchpad.net/~videolan/+archive/stable-daily?field.series_filter=saucy)

---

### Post by Yellow Pasque on 2013-11-01
If you want a rolling release, use a rolling release. (I use Debian sid and we have vlc 2.1...) With the exception of some special programs (e.g. Firefox), Ubuntu doesn't do updates the way you think/want. VLC isn't even the default media player, so don't hold your breath for it to be updated in official repositories.

---

### Post by ian-weisser on 2013-11-01
> **forcecore said:**
> Any news about vlc 2.1 for 13.10 from official integration, dont know but at least they should add into backports.

If you want it backported, then help *test* it, then *request* the backport. See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
It's not difficult. Backporting relies upon community members to do the testing. **You** are "they".

---

### Post by andrew.46 on 2013-11-01
It can definitely be a lot easier to get newly released versions of vlc on other distros. I attach a screenshot of vlc 2.1 running on slackware 14.0, and this will be an old version of slackware in a few weeks when 14.1 is released :)

---

### Post by ian-weisser on 2013-11-01
> **forcecore said:**
> Any news about vlc 2.1 for 13.10 from official integration

I'll show you how to look it up yourself. All the tools you need are public.

According to the upstream project ( [http://www.videolan.org/news.html](http://www.videolan.org/news.html) ), 2.1 was released on 9/26/13

According to Debian ( [http://packages.qa.debian.org/v/vlc.html](http://packages.qa.debian.org/v/vlc.html) ), VLC 2.1 was packaged on 10/27/13
The package is currently in Debian SID and Unstable.

According to Launchpad ( [https://launchpad.net/vlc](https://launchpad.net/vlc) ), VLC 2.1 was synched from Debian on 10/30/13.
Since that date was well past getting into Saucy, it was added to Trusty.

Well, let's verify that 2.1 is in Trusty...
```
$ rmadison -u ubuntu vlc
       [...]
       vlc |    2.1.0-2 | trusty-proposed/universe | source, amd64, armhf, i386, powerpc

```
Yes, there it is. The rmadison command is included in the *build-essential* package.

There are also several PPAs of 2.1. One is at [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc)

I don't see any backport requests for 2.1 on the backporters to-do list ( [https://launchpad.net/~ubuntu-backporters/+subscribedbugs](https://launchpad.net/~ubuntu-backporters/+subscribedbugs) ) yet. Anyone -including you or me- can ask for a backport...after they have tested the backport themself, first. That's a really low barrier to entry - you merely must care enough to try it yourself first.

So your original question has three possible answers:
When will VLC 2.1 be available in Ubuntu?
1) 14.04 without a PPA or backport
2) Soon if somebody backports it
3) Right now if you use a PPA

---

### Post by andrew.46 on 2013-11-02
I used to run a guide on these forums that showed how to build your own vlc, but it is not a trivial matter to do so...

---

