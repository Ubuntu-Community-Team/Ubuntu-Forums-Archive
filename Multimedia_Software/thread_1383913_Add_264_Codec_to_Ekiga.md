---
title: "Add 264 Codec to Ekiga"
date: 2010-01-17
forum: Multimedia Software
---

### Post by HuckleSmothered on 2010-01-17
I'm trying, reeeeally trying to use Ekiga. But the video quality is horrible. So I started messing with the settings, lo-and-behold I find info about h.264 and how fantastic it is. Well, I say to myself, let's try that on for size. 

What? No h.264 option in Ekiga. That's weird, especially considering they have supported it since 3.0 and I'm using the version in the Karmic repos, 3.2.5. Not free, ok, I'll just install it then, right?

x264 package didn't do it. A little ffmpeg install as well. libavcodec52, which uninstalled a buttload of other stuff also. Even dl'd and installed libopal3.6.4-plugins-non-free. All to no option for the h.264 codec option in Ekiga. 

Oddly enough, the libopal non free plugins DID add the iLBC audio codec into Ekiga as on option. Why not h.264? What am I missing? Also, why is this SO difficult? There is not any decent documentation that I can find out there that goes over this. Google has failed me.

All I have in the video codecs is theora and h261.

---

### Post by mc4man on 2010-01-17
You could try to install the 'extra' versions of the ffmpeg libs (libavcodec-extra-52, ect. or maybe even add the karmic medibuntu repo to your sources, install the 'extra' versions and then see.

is so, don't remove your current ffmpeg libs, just search ffmpeg in synaptic and mark the extra packages for install

(myself don't know ekiga at all, so other than that....?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by HuckleSmothered on 2010-01-17
Thank you for the reply.

I installed the libavcodec-extra... and it conflicts with libavcodec52. After removal, and installation of the -extra package, I still lacked the h.264 option and actually lost the audio iLBC option.

I also already have the Medibuntu repo's enabled.

Still no h.264 video codec ability in Ekiga. I suppose I should see if the x264 package even works, besides showing as installed. I'm not familiar with it and will play with that. In the meantime, more suggestions welcome.

---

### Post by mc4man on 2010-01-18
A quick look in the ubuntu ekiga source shows this ( sorta interesting that you get iLBC, but fairly clear about h264

> The following non-free codecs have been stripped from ekiga ([COLOR="Blue"]in fact,
from opal library[/COLOR]):
- audio: iLBC
- video: H.263-1998 (aka H.263+), MP4V-ES, H.264.
More information is at [http://wiki.ekiga.org](http://wiki.ekiga.org).

You can find help at:
- [http://wiki.ekiga.org](http://wiki.ekiga.org)
- ekiga user mailing list
- irc.gimp.net, channel #ekiga

 -- Eugen Dedu <Eugen.Dddu@pu-pm.univ-fcomte.fr>, Thu,  4 Jun 2009 15:25:08 +0200

Which if you check the description of the libopal package you'll see it  says.. 
> This package contains the shared version of the OPAL library, together
with several free audio codecs and theora and H261 video codecs.

So you'd probably need to build an un-stripped opal source and then possibly ekiga itself.

Best first bet is to search for a ppa that has done this for you if one exists

Edit:
here's a ppa that will enable all the codecs (karmic and jaunty packages
[https://launchpad.net/~bojo42/+archive/ekiga](https://launchpad.net/~bojo42/+archive/ekiga)

the bug report page, I'd look thru first ( I haven't
[https://bugs.launchpad.net/ubuntu/+source/opal/+bug/316971](https://bugs.launchpad.net/ubuntu/+source/opal/+bug/316971)

---

### Post by HuckleSmothered on 2010-01-18
Is it me?

Before the last post's edits with the PPA, I was looking for just that. I figured ekiga themselves would have something. I found and used their ppa which unfortunately did not include the non-free plugins either, to my surprise. 

However, they have a link for the libopal3.6.6-plugins-non-free. Which then quickly failed due to a lacking dependency of libx264-76. I was unable to find this package anywhere on God's green Earth. I found that odd.

So, I moved onto the ppa that is in the previous post, ppa:bojo42/ekiga. I've added ppa's before and used them successfully. However, I feel stupid with this one and could not get the package manager to recognize the new packages that should have been available, which are all named opal-*, I'm probably needing the opal-h264 package. The correct software sources show in the Third Party Software tab in Software Sources. No errors on an apt-get update, but no packages by the opal- names found.

How the heck do I get this?

---

### Post by mc4man on 2010-01-18
well i'm going to dump this karmic install as soon as lucid is a bit more mature so I'll add the ppa and see what I can see.

Otherwise i'll see if I can find a link to a libx264-76 - shouldn't be to hard, have it here (one can have multiple libx264-XX's installed, one per core version (XX)

---

### Post by mc4man on 2010-01-18
Well that ppa is a bit of a dead end, while packages were built for karmic, they were never updated to reflect the opal/ekiga versions used in karmic.
In other words they depend on the jaunty version of libopal.... and another package not even on karmic.

Then you'd need to use the jaunty ekiga and related deb's,  a road best not taken. ( and anyway it appears in jaunty  the libs may not have beeen stripped anyway...

As far as libx264-76 as a .deb. While it would of been available from debian-multimedia last fall, they don't archive all the versions so it's no longer there. ( at least in a readily accessible area
The [oldest there]("http://debian-multimedia.org/pool/main/x/x264/x264.php") is libx264-78

Maybe a ppa , though could prove hard to find ( never used in ubnutu in that XX

If you need a -76 vs.  -76 or greater there are some build options by getting the appropriate source version

Myself I keep a private repo and tend to collect such things in case I need them
So if find no other way I guess I could upload it to my mediafire acc.
-76 from debian-multimedia - sept. 28 2009 32 bit

( it seems one can no longer attach .debs here, 


Otherwise the whole build deal mentioned in last post would work or keep searching or let it go

---

### Post by HuckleSmothered on 2010-01-23
First off, I really appreciate the help you are giving.

Recently I have tried to install the libx264-65 and libx264-78, the two closest to libx264-76. This still gave dependency issues.

Tried the ol' symbolic link in the /usr/lib folder (ln -s libx264-78 libx264-76), this did not work either.

Forced an installation anyway with --force-depends and it installed it. However, Ekiga is apparently smarter than that and was not fooled. The codec remains non-existent according to Ekiga.

I think I am at the point of giving it up. It really shouldn't be this difficult. Hopefully it's not me, but I'm not above admitting incompetence.

---

### Post by Yellow Pasque on 2010-01-23
I just installed the libopal3.6.4-plugins-non-free and I see h264 in list of video codecs.

---

### Post by mc4man on 2010-01-23
@ HuckleSmothered
as Temüjin as noted go to the [orig. place you tried]("http://snapshots.ekiga.net/snapshots/debian/") (I think) and use the 3.6.4 ver instead of the 3.6.6
Should install cleanly in karmic

---

### Post by HuckleSmothered on 2010-01-24
Well, then it appears to be me. But ... me on two separate computers? Both with Ubuntu Netbook Remix 9.10. 

Started from scratch. A computer I had not touched yet and that already had ekiga on it. I installed libopal3.6.4-plugins-non-free from the link above (only missing dependency that I did not have at the time but installed then was libavcodec52).

Still no h262. Results from a dpkg -s:
```
Package: libopal3.6.4-plugins-non-free
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 348
Maintainer: Debian VoIP Team <pkg-voip-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: opal-non-free
Version: 3.6.4~1
Depends: libopal3.6.4, libavcodec52, libc6 (>= 2.3.6-6~), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1), libx264-67 (>= 1:0.svn20090516)
Description: OPAL non-free codecs (iLBC, h264, h263-1998, mp4v-es)
 This package contains some of the Debian non-free plugins of the OPAL
 library: iLBC audio codec, and h264, h263-1998 and mp4v-es video codecs.
 .
 The OPAL project aims to create a full featured, interoperable, Open Source
 implementation of the H.323 and SIP protocols that can be used freely by
 everybody.  These protocols are most used for Voice over IP (VoIP)
 conferencing.
Homepage: [http://www.opalvoip.org/](http://www.opalvoip.org/)
```


Two computers, both ones that I personally installed with Ubuntu NBR 9.10. The package says h264. Others get it. So it HAS to be me. But I can't for the life of me think of where I am going wrong.

dpkg -s ekiga:
```
Package: ekiga
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 15448
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 3.2.5-1ubuntu1
Depends: libatk1.0-0 (>= 1.20.0), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.4), libdbus-glib-1-2 (>= 0.78), libebook1.2-9 (>= 2.27.4), libedataserver1.2-11 (>= 2.27.4), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.23.2), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.17.5), liblaunchpad-integration1 (>= 0.1.17), libldap-2.4-2 (>= 2.4.7), libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libopal3.6.4, libpango1.0-0 (>= 1.14.0), libpt2.6.4 (>= 2.6.4-1ubuntu1~), libsasl2-2, libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.4.0), libx11-6, libxext6, libxml2 (>= 2.6.27), libxv1, gconf2 (>= 2.10.1-2), evolution-data-server, libpt2.6.4-plugins
Recommends: gvfs, yelp
Suggests: siproxd, gnugk, mediaproxy, ser, openser, rtpproxy, asterisk, yate, callweaver
Description: H.323 and SIP compatible VoIP client
 H.323 and SIP compatible videoconferencing and VoIP/IP-Telephony application
 that allows you to make audio and video calls to remote users with H.323
 hardware or software (such as Microsoft Netmeeting) as well as SIP endpoints.
 .
 It supports all modern videoconferencing features, such as contact roster,
 presence status, high-quality audio and video codecs, various video
 resolutions, registering to an LDAP directory, gatekeeper support,
 making multi-user conference calls using an external MCU, using modern
 Quicknet telephony cards, and making PC-To-Phone calls.
Homepage: [http://www.ekiga.org](http://www.ekiga.org)
Original-Maintainer: Kilian Krause <kilian@debian.org>
```

Temujin, can you provide the versions of your libopal, libopal plugins-non-free, and ekiga?

---

### Post by mc4man on 2010-01-24
karmic  Ekiga ( which depends - installs, the karmic libopal
the nonfree plugin

You should install the 'extra' version of libavcodec (libavcodec-extra-52

or maybe even better [add the medibuntu repo]("https://help.ubuntu.com/community/Medibuntu") and then use theirs

```
sudo apt-get install libavcodec-extra-52
```

---

### Post by Yellow Pasque on 2010-01-25
Yeah, like mc4man said, all I did was install ekiga/libopal/libpt from standard Karmic repo, and then install the libopal3.6.4-plugins-nonfree .deb from [http://snapshots.ekiga.net/snapshots/debian/](http://snapshots.ekiga.net/snapshots/debian/)

I'm using amd64 architecture if it makes any difference..

---

### Post by HuckleSmothered on 2010-01-25
Well, I was very curious to see if it was indeed just me. Fresh Xubuntu install.
Installed ekiga, libopal3.6.4, libpt2.6.4. No 264 codec.
Installed libopal3.6.4-plugins-non-free. No 264 codec.
Installed libavcodec52-extra-52. No 264 codec.
   This requires libavcodec52, and removes libopal3.6.4-plugins-non-free.
Installed libopal3.6.4-plugins-non-free. no 264 codec.
   This time it wanted to remove libavecodec-extra-52 and install libavcodec52
   I did a --force-all and it set it up regardless.

So, I installed a fresh Arch Linux. Same basic steps. I get the iLBC audio one, but not the 264 video. This was a very minimal install. What I'm thinking is that I'm missing something else. Maybe a recorder or player or something. But wouldn't be a dependency? 

Anyway, one last note for today. On Arch, I only had the same two video codecs as I'm getting on Ubuntu and Xubuntu (theora, h261) UNTIL I installed ffmpeg. Then I got an h263, an mp4v-ev and some other one. But no h264. 

Ekiga hates me.

---

### Post by Yellow Pasque on 2010-01-25
Oh, and you need this: [http://packages.ubuntu.com/karmic/libx264-67](http://packages.ubuntu.com/karmic/libx264-67)

67, not 76 ;)

---

### Post by HuckleSmothered on 2010-02-06
That did it!! Thank you SO much for all the help here.

I'm quite amazed that I didn't find that libx264-67 out there earlier. Thank for pointing it out to me, I can be dense sometimes.

For anyone having the same issues, here's a quick recap of what I did in case it helps you:

1. install ekiga
    (from the ubuntu repos)
2. install x264
    (from the ubuntu repos)
3. install libx264-67
    (from the ubuntu repos)
3. install libavcodec52
    (from the ubuntu repos)
4. install libopal3.6.4-plugins-non-free
    (from the ekiga.net site)
5. link library files *
* On one computer I had to create a link /usr/lib/libavcodec.so to /usr/lib/libavcodec.so.52
* On a second computer I had to do something a little different. Which is, recreate the /usr/lib/libx264.so to point to /usr/lib/libx264.so.67 instead of /usr/lib/libx264.so.78

So ... it works now. I feel accomplished. Time to move on to the next project.

---

### Post by stunted on 2010-05-09
Anyone know how to do this on 10.04?

I think my n900 only has h264.

Thanks people

<edit> for added impetus x-lite video calling almost works with the n900, can anyone with h264 on ekiga confirm it works with x-lite? </edit>

---

### Post by stunted on 2010-05-18
Does anyone know if ekiga x-lite video calls work if you install h264 for ekiga?

Also bump.

---

### Post by siabost on 2010-06-22
Hi,

Being now on 10.04LTS I have the same problem with really really poor video with Ekiga.

I'm going to try the same steps as HuckleSmothered tried with Karmic, but Jaysus, it shouldn't be this hard!

In any case, why are the open-source codecs so bad?

---

### Post by sles on 2011-12-29
Hello!

Is there h264 howto for 11.10?

thank you!

---

### Post by nothingspecial on 2011-12-29
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

