---
title: "[SOLVED] Compiling FFMPEG for Ipod Video conversion -- Build-dependencies not found"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by mwsherman on 2008-04-20
Hi. New to Linux. Ubuntu is my first attempt. So far things have been tough, but this is the first time I've been unable to fix my problem on my own. I'm still a newbie, so please be patient with me.

I've been spending a lot of time trying to make my 6th generation Ipod work in Linux. I updated some ipod handling packages to the Hardy Heron versions and was able to get support for writing the iPod database(using Rhythmbox as an iPod manager, but I dumped it as an iPod manager for lack of video support). I switched back to the Gutsy repositories after doing this (I think the only packages I wonked with were iPod ones, but I don't remember what they were :( )

 I decided to just use [Floola.]("http://www.floola.com/modules/wiwimod/") Floola has been working just fine, but now I want to convert videos to make them playable on my ipod. Floola supports conversion, but requires a self-compiled version of ffmpeg with aac and H264 support. So I found [these]("https://wiki.ubuntu.com/ffmpeg") instructions. But when I put the first line into the terminal:

```
sudo apt-get build-dep ffmpeg
```

I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for ffmpeg could not be satisfied.
```

The first things I did to fix this were install ffmpeg from Synaptic and fixing broken packages in synaptic. That didn't work. Then I typed this in the console

```
apt-cache showsrc ffmpeg | grep '^Build-Depends'

```

Which outputted a list, presumably of packges? 

```
Build-Depends: debhelper (>= 4.0), quilt, libogg-dev, libvorbis-dev, zlib1g-dev, libsdl1.2-dev, libfreetype6-dev, libimlib2-dev, texi2html, libraw1394-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libdc1394-13-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libtheora-dev (>> 0.0.0.alpha4), libgsm1-dev

```

I began to manually install these packages in Synaptic. When I attempted to install libogg-dev, it gave an error message. Here's the command line output with the error message: 

```
michael@COMPUTERNAME:~$ sudo apt-get install libogg-dev

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
michael@OMFGTEHLINUX:~$ sudo apt-get install libogg-dev
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
  libogg-dev: Depends: libc6-dev but it is not going to be installed
E: Broken packages
```

Attempting to then install libc6-dev gives a similar error message, with the last line readng:

```

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-9ubuntu2 is to be installed
E: Broken packages
```

I looked into removing and then reinstalling libc6, but qucikly realized that was a bad idea :). 

At this point, I've given up. Further searches of this error haven't led very far. I've read things that just suggest I should wait for Hardy to come out (or just go with the release candidate?) since the issue here is versions of packages not matching up?? Although I'd rather not do that--I've had to solve a lot of time consuming problems since I've installed Ubuntu, and I don't want to have to re-install (and thus solve them all again?) if I can help it. But if that is indeed the case, isn't this a bug that these dependencies of libc6-dev don't match up with what is available in the gutsy repository?

Admittedly, I really don't have any idea what I'm talking about. I am still new to Linux and Ubuntu, after all.

What should I try next? Is it possible I made some mistake at some point and screwed up some packages?
Or can anyone recommend an easier way to convert various video types to iPod playable formats that gets around this whole ffmpeg issue.

Thanks for reading. Apologies for the lengthy post (I didn't know what information would be important), and for what is probably bad formatting. I'm still learning here.

---

### Post by mc4man on 2008-04-20
There are some excellent choices for doing ipod conversions but....
> I looked into removing and then reinstalling libc6  upgrading your libc6 to a version that gutsy doesn't use is going to continually hamper you and cause issues. I thought I remembered a thread where someone in same position was able to go back to gutsy's version without too much damage, unfortunately I can't find it, I'll try searching a bit more. You may want to consider either a fresh install of gutsy or upgrading to hardy. One way or the other you need to get this fixed.

edit; actually it was after trying to to downgrade libc6 (unspecified method - possibly tried force version), a bit of a hassle to say the least
[http://ubuntuforums.org/showthread.php?t=728879&highlight=chroot](http://ubuntuforums.org/showthread.php?t=728879&highlight=chroot)

---

### Post by mwsherman on 2008-04-21
Thanks for your reply.

Perhaps it wasn't clear in my torrent of babble, but (as far as I know), libc6 has never been touched. I don't think I've ever done anything with the libc6 package--its been installed since I first installed ubuntu, and I've certainly never done anything with it, to my knowledge at least. Of course, it is possible I am wrong.

Anyway, am I interpreting this error message wrong? :
```

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-9ubuntu2 is to be installed
E: Broken packages
```

To me it sounds like libc6-dev is looking for libc 2.7-9ubuntu2 (Hardy?), when what I have installed is 2.6.1ubuntu10 (Gutsy?). Why would libc6-dev be looking for a Hardy version of libc6? Is it possible I broke something? Is there a way I can check to see if my repositories are the proper Gutsy ones? I did some fooling with my repositories when I installed the Hardy versions of the ipod libraries, but I'm positive I switched them back...

How would I go about checking if my computer is looking at the correct repositories? And if this is indeed what's broken, how can I fix it?

I think I'm using bad jargon : (. Sorry.

It's also possible I'm going way up the wrong tree here. Can someone help me understand that error message better?

Thanks!

---

### Post by sdennie on 2008-04-21
If you set your repositories to Hardy and installed any software it's entirely possibly that it pulled in the new libc.  If you are just looking for a short term fix, you may be able to get away with just setting your repositories temporarily back to Hardy and installing libc6-dev and then switching back to Gutsy (it will probably pull in a new libc6 as well).

---

### Post by mwsherman on 2008-04-21
Thanks both for your help. I'm guessing that during the package upgrades I did to get Ubuntu to write the database for my 6th generation ipod classic, the lib6c package was upgraded. I set my repositories to Hardy (which took me awhile to figure out again), installed the necessary packages, and was able to get ffmpeg working from the command line (although Floola doesn't recognize it). But command line is good enough for me--I can get video on my iPod now, even if it is not as easily as i would like.

Going back to Gutsy isn't going to happen -- I'll just have the same issues again when I update libraries to get Ubuntu to work with the 6th gen ipod. Since my system now appears stable, I'm just going to re-install when Hardy comes along. That shouldn't be too long now!

What irks me a little is I had no idea that I replaced a package as critical as libc6--I thought I was just replacing ipod packages. Oh well. A warning would have been nice--although I suppose that's the result of the instructions I followed not being clear about the replacement of core packages.

In truth, the useful lesson I'm getting out of this is to keep better track of everything I do after I reinstall. I have no recollection of the stuff I did to get some of my hardware working when I first installed. Figuring that out again is going to suck. But next time I'll keep notes, so that way reinstalls wont be a big deal.

For future reference though, any recommendations for better ipod manages/video converts would still be welcome.

---

### Post by sdennie on 2008-04-21
I'm not sure if versions of Ubuntu prior to 8.04 include a gui version of avidemux but, it seems like a pretty powerful tool to convert to/from a large number of formats.  It might be worth having a look at.

---

### Post by mc4man on 2008-04-21
what i use is h264enc  [http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)
on goiing thread and new release info - [https://forum.doom9.org/forumdisplay.php?f=63](https://forum.doom9.org/forumdisplay.php?f=63)
It is an interactive cli app - the faq is informative
It works best with newer rev. of mplayer/mencoder - custom built on machine your going to do encoding is the  best  way (hence fixing libc6), otherwise hardy does have decent one.

---

