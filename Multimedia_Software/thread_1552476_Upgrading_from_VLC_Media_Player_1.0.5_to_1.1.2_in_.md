---
title: "Upgrading from VLC Media Player 1.0.5 to 1.1.2 in Ubuntu Karmic (9.10)"
date: 2010-08-13
forum: Multimedia Software
---

### Post by Objekt on 2010-08-13
I use Ubuntu 9.10 64-bit.  The 9.10 repository only has version 1.0.5 of the VideoLAN VLC Media Player, but I would like to upgrade.  What is the best way to upgrade to the latest version of VLC Media Player, 1.1.2?

I Googled the problem and found a couple of pages suggesting this sequence at the command line:

```
    sudo add-apt-repository ppa:c-korn/vlc

    sudo apt-get update

    sudo apt-get install vlc mozilla-plugin-vlc
```

(Taken from this article at Ubuntu Geek: [http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html#more-7483]("http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html#more-7483"))

This did not quite work for me.  Here's what happened when I tried the first command:

```
objekt910@objekt910-desktop:~$ sudo add-apt-repository ppa:c-korn/vlc
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py", line 60, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py", line 79, in add_ppa_signing_key
    '\"signing_key_fingerprint\": \"(\w*)\"', lp_page)[0]
IndexError: list index out of range

```

Strangely, when I checked my software sources list, the c-korn/vlc entry had been added.

When I tried to run the next command, I got:
```
objekt910@objekt910-desktop:~$ sudo apt-get update
...
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Does that simply mean there is no 64-bit specific version of VLC 1.1.2?

I also got a bad result from trying the last command:
```
objekt910@objekt910-desktop:~$ sudo apt-get install vlc mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.2-1ubuntu2.1) but 1.0.5-1~getdeb1 is to be installed
E: Broken packages

```

So...

1) Is my Ubuntu 9.10 install hopelessly broken?  Or can it be fixed?

2) Does there exist a way to download & install VLC 1.1.2 manually?  I can only find Windows and Mac downloadable archives of VLC 1.1.2.  The only way I can find to get 1.1.2 on Ubuntu is the commands given above, which don't work.

---

### Post by andrew.46 on 2010-08-14
Hi Objekt,

I believe that Christopher Korn no longer offers vlc packages from his PPA. Not quite sure what happened there?

Andrew

---

### Post by mc4man on 2010-08-14
> Not quite sure what happened there?
Happened to be looking thru the vlc ppa for  someone last week (lucid), where he was providing new ffmpeg libs in add. to vlc. (0.6 ffmpeg shared

The ppa is now not available to browse - it appears all packages are only available thru 'getdebs2' where likewise no packages, sources, .diffs, ect. are available to inspect or review.

I gather one has to add the getdeb ppa and then see what's available. (and take their chances so to speak.

Can't say I'm a fan of that whatsoever..


Edit : I don't believe I saw a 1.1.X for karmic, though didn't pay close attention there.
If you wished to build a 1.1.2 vlc for karmic, with a slight mod of Andrew.46's vlc git how-to and a couple of updated libs should be very easy to do - once done it becomes even easier.

---

### Post by cnbiz850 on 2010-08-14
The ppa repository didn't work for me either on the Karmic 64, but worked on my Lucid 32 machine.  I tried it for a few days and found one function is missing - the Service Directory is no longer on the menu.  So I am back to 1.0.6 on Lucid now.  My most recent version on Karmic 64 is 1.0.5.

---

### Post by ron999 on 2010-08-14
> **mc4man said:**
> 
If you wished to build a 1.1.2 vlc for karmic, with a slight mod of Andrew.46's vlc git how-to and a couple of updated libs should be very easy to do - once done it becomes even easier.

I would like to do this because I'm still using Karmic.
But I need baby steps.:D
I tried to compile it using info from two websites but both times it went pearshaped.:confused:
These were the websites that I tried to follow:-
Here
[http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html]("http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html")
And here
[http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux]("http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux")

---

### Post by andrew.46 on 2010-08-14
Hi ron999,

Oddly enough I chose to write a guide for the *development* version of vlc in part because most Ubuntu users seemed happy enough to use PPAs for the newest release version, and certainly the Korn PPA was the one everybody seemed to be using. My guide would indeed have become very popular right now if it dealt with the *release* version rather than vlc-git as the hordes of Korn PPA users will be looking for alternatives :).

I attach a screenshot of the fun!

Andrew

---

### Post by ron999 on 2010-08-14
I can view those vp8 files in my newly-built mplayer/smplayer (thank you Andrew:D).

I can also view them using the Windows version of VLC v1.1.1 in Wine.:o

[IMG]http://img713.imageshack.us/img713/2372/elephant2.png[/IMG]

---

### Post by Objekt on 2010-08-14
Well, nuts.  The how-to's I found are only a week or two old in most cases, so the unavailability of the PPA is quite recent.

I did find a package for installing VLC 1.1.1.  I guess I'll make do with that until VideoLAN makes 1.1.2 available for Ubuntu users.

---

### Post by ron999 on 2010-08-14
> **Objekt said:**
> 
I did find a package for installing VLC 1.1.1.  I guess I'll make do with that 
Where did you find a v1.1.1 package for Karmic. Please will you post a link.

---

### Post by Objekt on 2010-08-14
Naturally, now that I mentioned it, I can no longer find the link I was speaking of in the previous post.

However, I did find this page, which seems to offer Linux installation packages for both VLC 1.1.1 **and VLC 1.1.2**:
[http://www.icewalkers.com/Linux/Software/527080/VLC-media-player.html]("http://www.icewalkers.com/Linux/Software/527080/VLC-media-player.html")

Perhaps I'll attempt to install that later today.

---

### Post by mc4man on 2010-08-14
ron999 - you could try a [ppa search]("https://launchpad.net/ubuntu/+ppas"), though one should be careful if the ppa provides many different packages

Slightly ot.  - maverick will be using a fairly decent build of 1.1.2 and will be providing a more current ffmpeg (0.6), which will be a good thing in many ways.

> I would like to do this because I'm still using Karmic.
But I need baby steps.

Maybe tomorrow can post how to adapt Andrew's guide - very simple - though would need to ck. a few things on a karmic install lib wise.
I'd think you'd need to upgrade your taglib libs (3), to the 1.6.3 ver.,maybe one or 2 others

(due to an inexplicable issue on my laptop - random X crashes, over the last week or so have used maverick, lucid, karmic, lucid 64, and now back to maverck - I think I've finally solved it.

So I made myself a 'crib' sheet - don't consider it a how-to, just shows how simple.
On maverick I've done both a single package vlc statically linked to ffmpeg and a package set using a shared ffmpeg to compare.

(this was steps for 32 bit, no x264, static linked ffmpeg, vaapi enabled

> Install ffmpeg, vlc and build build-dep packages
also - 
sudo apt-get install dh-autoreconf cdbs
Make and Install the splitted-desktop libva and vdpau-video packages or use the provided libva, libva-dev
Make and install libvpx or use available libvpx0, libvpx-dev

build and install live555 as in mplayer - to /usr/lib

mkdir -p ~/vlc_build/vlcdeps && cd vlc_build  

svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg && cd ffmpeg

./configure --prefix=$HOME/vlc_build/vlcdeps/usr --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-ffmpeg --disable-ffplay --disable-ffserver --disable-doc --disable-decoder=amr --enable-libvpx

make && make install-libs install-headers && make distclean
cd ..

wget [http://sourceforge.net/projects/vlc/files/1.1.2/vlc-1.1.2.tar.bz2/download](http://sourceforge.net/projects/vlc/files/1.1.2/vlc-1.1.2.tar.bz2/download)
(ck. if version # has increased

tar -xvjf vlc-1.1.2.tar.bz2

cd vlc-1.1.2

patch for bookmarks

export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"

./configure --enable-real --enable-realrtsp  --enable-snapshot --enable-merge-ffmpeg --disable-x264 --enable-loader --with-live555-tree=/usr/lib/live
make 
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc --pkgversion "1.1.2-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default

sudo ldconfig  (or have tried --addso in checkinstall, seems ok, Though I think best not to use



---

### Post by ron999 on 2010-08-14
OK mc4man
I already have good installs of x264 and ffmpeg from fakeoutdoorsman's tutorial.
And new mplayer from Andrew's tutorial.

I don't use live555.
I probably don't use vaapi.

I suppose that I would like a similar set of commands to compile and install VLC v1.1.2.
Previously when I've tried following those two websites that I linked there were errors that I couldn't understand.

If you can help me out here sometime I'd like to have another attempt.

---

### Post by mc4man on 2010-08-14
> If you can help me out here sometime I'd like to have another attempt.
Should be a piece of cake - you're using 32 bit?

I'm heading out to install some crown - will do a run thru on karmic tonight (early morning your time I believe.

You probably should upgrade your taglib libraires - if you wish to try that now you need three, - dl all 3, place in a folder, cd to that folder on a terminal and run 
```
sudo dpkg -i *.deb
```

If there are any install issues that result in broken packages (doubtful), then open synaptic -> custom filter -> broken and let it fix.
(I really don't think there will be any - 

List of 3 - taken from my karmic install 32 bit
> doug@doug-desktop:~/taglib$ ls *.deb
libtag1c2a_1.6.3-0ubuntu1_i386.deb   libtag1-vanilla_1.6.3-0ubuntu1_i386.deb
libtag1-dev_1.6.3-0ubuntu1_i386.deb

Can be gotten here - be careful to get the right ones - all May 8 2010 or all May 26 2010 or May 27 2010 for amd_64 - I used the May 08 2010 set here as shown above

[http://security.ubuntu.com/ubuntu/pool/main//t/taglib/](http://security.ubuntu.com/ubuntu/pool/main//t/taglib/)

---

### Post by ron999 on 2010-08-14
Hi
Yes I'm using 32 bit.

Those libtags seem to be updated ok now, all dated 26 March v1.6.3-1

:D
> ron@ubuntu:~$ cd ./temp
ron@ubuntu:~/temp$ sudo dpkg -i *.deb
[sudo] password for ron: 
(Reading database ... 223798 files and directories currently installed.)
Preparing to replace libtag1c2a 1.6-2ubuntu2 (using libtag1c2a_1.6.3-1_i386.deb) ...
Unpacking replacement libtag1c2a ...
Preparing to replace libtag1-dev 1.6-2ubuntu2 (using libtag1-dev_1.6.3-1_i386.deb) ...
Unpacking replacement libtag1-dev ...
Preparing to replace libtag1-vanilla 1.6-2ubuntu2 (using libtag1-vanilla_1.6.3-1_i386.deb) ...
Unpacking replacement libtag1-vanilla ...
Setting up libtag1-vanilla (1.6.3-1) ...

Setting up libtag1c2a (1.6.3-1) ...
Setting up libtag1-dev (1.6.3-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ron@ubuntu:~/temp$ 


---

### Post by mc4man on 2010-08-14
> Those libtags seem to be updated ok now

If you want mtp support you'll need to upgrade to lucid versions of libmtp. is so dl from [here]("http://packages.ubuntu.com/lucid/libmtp8") and [here]("http://packages.ubuntu.com/lucid/libmtp-dev"), put in a folder and do the dpgk thing.

Maybe first go to [Andrew's vlc build page]("http://ubuntuforums.org/showthread.php?t=1398119") and install the build deps, then upgrade the above

Am running a test build on karmic in a bit - will post the basic command set in that thread

Am assuming you wish to build x264 transcoding into vlc (see no use for it myself - Andrew has mentioned it's better with shared ffmpeg libs which is beyond the scope here.

---

### Post by ron999 on 2010-08-14
Hi
> If you want mtp support you'll need to upgrade to lucid versions of libmtp.
I don't think I need this just now (because I don't know what it is).

> Am assuming you wish to build x264 transcoding into vlc

Build this into VLC if it's not too difficult, otherwise don't bother.

---

### Post by mc4man on 2010-08-14
Ok - give me a few to test the build and we'll see..

Built fine on karmic - 
> doug@doug-desktop:~$ vlc -vv
VLC media player 1.1.2 The Luggage (revision exported)
[0x9980154] main libvlc debug: VLC media player - 1.1.2 The Luggage
[0x9980154] main libvlc debug: Copyright © 1996-2010 the VideoLAN team
[0x9980154] main libvlc debug: revision exported
[0x9980154] main libvlc debug: configured with ./configure  '--enable-real' '--enable-realrtsp' '--enable-snapshot' '--enable-merge-ffmpeg' '--enable-loader' '--with-live555-tree=/usr/lib/live' '--with-tuning=native'


---

### Post by mc4man on 2010-08-14
Ron - [see here]("http://ubuntuforums.org/showthread.php?p=9721410#post9721410")

---

### Post by gavdari on 2010-08-16
is it ok to add **"ppa:n-muench/vlc" ?**

---

### Post by mc4man on 2010-08-16
> is it ok to add
That would depend on what other apps/plugins  you have that depend on the shared ffmpeg libs which will be updated with that ppa. (or one's you care about
Some may not care, others could break.

The lucid repo mplayer will certainly break - no big loss, can be replaced with a ppa build or self built.

The gstreamer-ffmpeg plugin may complain - again no big deal - the ppa in my sig. will update gstreamer for you if you wish
(superior plugins with no dependency of ffmpeg libs.

There are a handful of other apps that may or may not be affected - really doesn't hurt to try - not too hard to revert.

---

### Post by andrew.46 on 2010-08-17
Hi mc4man,

A very interesting PPA has popped up, looks like Maverick only atm:

Daily Build of master branch 
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

Andrew

---

### Post by gavdari on 2010-08-17
Then I add it and see what happens.

---

### Post by shantiq on 2010-08-17
was trying to find the ppa from christoph korn and found there was a whole hoohaa about it
and that was a shame coz it had worked brilliantly on my machine before
but apparently it had broken packages on some machines

anyway it has been pulled off


the version from here is really easy to use does not even require an install

[http://www.icewalkers.com/download/VLC-media-player/2708/dls/](http://www.icewalkers.com/download/VLC-media-player/2708/dls/)

> Building VLC
============

Once configured, run `make' to build VLC.


Installing and running VLC
==========================

You can install the VLC and its plugins by typing:

   make install

[COLOR="DarkRed"]But you don't need to install it if you don't want to; VLC can be launched
from the current directory as well:

   ./vlc[/COLOR]

size is 115MB   all i had to do was ./configure   and then good to go

and gives you this  


[CENTER][IMG]http://img804.imageshack.us/img804/6177/55539030.png[/IMG]
[/CENTER]

---

### Post by mc4man on 2010-08-17
> A very interesting PPA has popped up, looks like Maverick only atm:

Have been running that in one of my maverick installs for a few days - seems good
The upgrade of ffmpeg in maverick is going to resolve many of the decoding/usability issues people have and somewhat reduce ppa's that break apps - at least for awhile.

---

### Post by Objekt on 2010-08-17
I tried to configure the 1.1.2 build mentioned above.  It simply did not work.  It gave me error after error, saying this or that library was missing ("lua" was the first one).  I tried my best to add the required libraries through Synaptic, but every time I ran the ./configure command, it kept coming up with some other thing that was missing.

Eventually, I couldn't find some of the stuff it wanted, so I had to give up.  Synaptic just didn't have some of the required libraries.  So I don't know how you got VLC 1.1.2 to complete configuring & actually made it run.  Won't work on my 9.10 install.

What is needed is a script to automatically install anything I need to get a VLC executable, if I don't already have it.  It is simply too frustrating and too much work to repeatedly run ./configure, have it go 90%, then quit because I'm missing yet another thing.  And then find that the thing it wants is unknown to Synaptic.

Exactly why don't the VLC guys provide pre-compiled binaries for newer versions??  Since the repository method is broken, can't they just make a version that will run on Ubuntu 9.10 or 10.04 or even 10.10?  It would be better than downloading 115 MB of stuff that doesn't even work.

---

### Post by ron999 on 2010-08-17
:)

---

### Post by shantiq on 2010-08-17
> **Objekt said:**
> I tried to configure the 1.1.2 build mentioned above.  It simply did not work.  It gave me error after error, saying this or that library was missing ("lua" was the first one).  I tried my best to add the required libraries through Synaptic, but every time I ran the ./configure command, it kept coming up with some other thing that was missing.

Eventually, I couldn't find some of the stuff it wanted, so I had to give up.  Synaptic just didn't have some of the required libraries.  So I don't know how you got VLC 1.1.2 to complete configuring & actually made it run.  Won't work on my 9.10 install.

What is needed is a script to automatically install anything I need to get a VLC executable, if I don't already have it.  It is simply too frustrating and too much work to repeatedly run ./configure, have it go 90%, then quit because I'm missing yet another thing.  And then find that the thing it wants is unknown to Synaptic.

Exactly why don't the VLC guys provide pre-compiled binaries for newer versions??  Since the repository method is broken, can't they just make a version that will run on Ubuntu 9.10 or 10.04 or even 10.10?  It would be better than downloading 115 MB of stuff that doesn't even work.

objekt i am sorry it did not work for you

 maybe it has to do with the fact that i am running it in lucid    sorry i failed to see that the title of the thread mentioned karmic    i was  =looking for info on the latest vlc available


anyway on lucid it configure really fast and well couple of things it said it would have to bypass

and it would not make (beacause of the couple of kinks in configure)    but runs so beautifully  no need to install

i agree with you tho    i wished binaries were made for the less technical guys    it would make things easier

you sometimes think programmers want us all to suffer a bit too:KS:KS/:KS:KS:KS    hey might i suggest a move up to lucid and try again?      your call   i remember reading elsewhere on the forum that karmic can only handle up to a certain version of vlc   i cannot remember where the cut off point was but i remember that "the luggage" was beyong its capacity



ps   i had been using the korn luggage one for the last two months    i now see why people have moaned    i always had a line across the bottom of the screen and thought it was my hardware


the picture is much clearer too on this one


also 

on a different note  if anyone fancies a change of icon for vlc

a little big of gimp got me these for variety

right click on present desktop icon/properties/double click on image and change    if anyone fancies that

---

### Post by andrew.46 on 2010-08-19
Just to rub salt into the wound vlc 1.1.3 has now been released :). On Lucid it compiles with no changes from 1.1.2 and I have adjusted the download links in [my guide]("http://ubuntuforums.org/showthread.php?t=1398119").

Andrew

---

### Post by ron999 on 2010-08-19
That's interesting.
I wonder if v1.1.3 will compile in Karmic using the method that mc4man showed me before.

EDIT
The answer is yes.

[IMG]http://img52.imageshack.us/img52/5986/vlc113.png[/IMG]

---

### Post by mc4man on 2010-08-19
> vlc 1.1.3 has now been released
Not sure what the default will be in maverick, but did manage to get the little 'save bookmarks to playlist' patch into 1.1.4
(though I always seem to be on the wrong side of the fence with these fellows.

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290)

---

