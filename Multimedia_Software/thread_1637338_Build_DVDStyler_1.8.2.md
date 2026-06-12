---
title: "Build DVDStyler 1.8.2"
date: 2010-12-04
forum: Multimedia Software
---

### Post by VideoRoy on 2010-12-04
Has anyone successfully built DVDStyler 1.8.2 for AMD64?  Actually I not sure the x86 version would not work but my current platform is AMD64.

I am currently using 1.8.1 that I installed from Ubuntu 10.10  repository.  I just saw version 1.8.2 at Sourceforge with a number of fixes and updates  I would like to have but I cannot find a place to install.  I tried to  compile from source on AMD x64 but I get a number errors that I mostly  corrected except for missing wxsvg which seems to be a common error when searching around.

I use quite a number of DVD tools but I like this package for my current work stream.  I am hoping maybe the new version will be supported in the Ubuntu repository but when I install 1.8.1 it gives a message like it will not.

Any help with this version of DVDStyler (not recommendations for other packages please!) would be appreciated.

---

### Post by mc4man on 2010-12-04
Don't see any ppa's as of yet, saw note of one but the build failed.

Have successfully built on maverick/natty (32bit), I don't think the arch should matter.
Initially tried on natty which is my current main install but there is an issue w/ libjpeg I can't work around as of yet. (edit - resolved

Some notes
You must use wxsvg 1.0.7 - the 1.0.5 in maverick will not work
I'd suggest you build wxsvg as a dep package set, this will insure fPIC
(more below on wxsvg
You **must install flex** or you will error on a failure to find (build actually) dvdvml.c
For dvdstyler wx-config needs to be 2.8, though you may also need 2.6 installed for wxsvg 1.0.7 (haven't the time to ck. fully
see here on how to ck. set wx-config, set at 2.8 if not already
[http://ubuntuforums.org/showthread.php?t=1440472](http://ubuntuforums.org/showthread.php?t=1440472)


In regards to wxsvg 1.0.7 - 
source here
[http://www.dvdstyler.org/index.php?option=com_content&view=article&id=50&Itemid=57&lang=en](http://www.dvdstyler.org/index.php?option=com_content&view=article&id=50&Itemid=57&lang=en)
There is an included debian folder you can use, It has an outdated changelog.
I edited the changelog to build higher version than in mav., didn't edit the control and the build appears to have used the 2.6 version of libwxgtk - I may have a chance later to see if removing the 2.6 libs affects anything

For the changelog you can make a new entry or because this is a personal build just edit the existing one - this should suffice, added blue in place of existing
> wxsvg ([COLOR="Blue"]1:1.0.7+nmu1[/COLOR]) stable; urgency=low
So install the build-deps for wxsvg, edit the changelog, and you can use this to build
fakeroot debian/rules binary
Should produce as seen in screen 1 ( then remove your current libwxsvg-dev, and install the 2 new packages

Then install build-dep for dvdstyler, including bison and flex, should build ok. - if not post complete configure and if build error - the error lines and some lines previous to.

(( just redid on natty using a wxsvg built off of libwxgtk2.6-dev and the build of dvdstyler succeeded. 
So to recap ( as best as I see atm

Make sure that both libwkgtk2.6-dev and libwxgtk2.8-dev are installed prior to building anything **or** make sure only libwxgtk2.8-dev is installed and see below
Also install flex
Check that your wx-config is set to 2.8 as shown in link
Build wxsvg as mentioned, then build dvdstyler (you can use checkinstall if desired for dvdstyler, just add --fstrans=no to checkinstall command


===========================================================================

The issue on natty turned out not to be that wxsvg was built off of the 2.8 libwxgtk but that there is atm a linking error. for natty this configure fixed
```
./configure  LIBS=-ljpeg
```


I think you could go either way in maverick. If you wish to just use libwxgtk2.8 then before building the wxsvg source remove libwxgtk2.6-dev if installed.
Then in the wxsvg debian folder you'll need to edit the control file. All references to libwxgtk2.6* must be changed to 2.8 and adjusting the version (..) or again, as this is a personal build you could carefully just remove the references altogether, in part or fully
Ex. - changing to 2.8, removing ( >=version #)
> Source: wxsvg
Section: libs
Priority: optional
Maintainer: Uwe Bugla <uwe.bugla@gmx.de>
Build-Depends: quilt (>= 0.46-4.1), patch (>= 2.5.9-5), debhelper (>= 7.0.9), fakeroot (>= 1.9.5), automake (>= 1:1.10.1), libtool (>= 1.5.26), libwxgtk2.8-dev, libwxbase2.8-dev, libavformat-dev (>= 3:20080610-0.0), libavcodec-dev (>= 3:20080610-0.0), libswscale-dev (>= 3:20080610-0.0), libart-2.0-dev (>= 2.3.20), libpango1.0-dev (>= 1.20.2)
Note there are 6 references that need editing in the control file

---

### Post by VideoRoy on 2010-12-05
mc4man,
Thank you very much for the reply!!!  You have given me a lot of clues as to what may be going wrong.

I will give your suggestions a go and report back.

Thanks! :biggrin:

---

### Post by VideoRoy on 2010-12-05
Well I got further along but I am afraid I may give up and wait for a PPA to pop-up.  I built this video editing computer to be as clean as possible and each time I resolve one dependency I hit the next and I am afraid I will mess up what I have working with all the other packages I have installed.  I am just not good enough a building / developing on Linux to know what I may be messing up or how to keep things separate.

I need to either either triple boot (already have Win7 & Ubuntu10.10) and build a development build instance or find another computer to do this work on.  I do have an old, old 32bit machine I could setup as a build computer but I am not sure if my 64bit instance would like all the packages.  I know some work but not all.

Thanks for your help.

---

### Post by fmdex2011 on 2011-04-02
I see there is an amd64 deb  file here:

[https://launchpad.net/ubuntu/+source/dvdstyler/1.8.2.1-0ubuntu1/+buildjob/2273644](https://launchpad.net/ubuntu/+source/dvdstyler/1.8.2.1-0ubuntu1/+buildjob/2273644)

for Natty 11.04   I will try it on my mavrick amd64 and see if it works

DVDstyler 1.8.3 is out as well if you care to compile it for me :)

Thanks in advance!

---

### Post by fmdex2011 on 2011-04-02
**Update**:    

Well I tried to install the package dvdstyler_1.8.2.1-0ubuntu1_amd64.deb and it came up with a bunch of dependencies that you need to install first

Depends on:

    * dvd+rw-tools
    * dvdauthor
    * dvdstyler-data (= 1.8.2.1-0ubuntu1)
    * genisoimage
    * libavcodec-extra-52
    * libavcodec52 (>= 4:0.6-1~)
    * libavformat52 (>= 4:0.6-1~)
    * libavutil50 (>= 4:0.6-1~)
    * libc6 (>= 2.7)
    * libexif12
    * libfontconfig1 (>= 2.8.0)
    * libgcc1 (>= 1:4.1.1)
    * libjpeg62 (>= 6b1)
    * libstdc++6 (>= 4.1.1)
    * libswscale0 (>= 4:0.6-1~)
    * libwxbase2.8-0 (>= 2.8.11.0)
    * libwxgtk2.8-0 (>= 2.8.11.0)
    * libwxsvg0 (>= 1:1.0.7)
    * mjpegtools

So then I started installing some of the dependencies and found out they had dependencies from the same list

To move on I tried to install those dependencies and found out they broke other dependencies and you have to remove a lot of other stuff

(somebody get me a diaper)

Now I am trying to figure out if there is some logical order to install these dependencies without breaking my system

Or do I have to install Natty 11.04?

I may just take a crack at version 1.8.3rc2 which has fixes for 1.8.2

Does anyone have some suggestions?

---

### Post by VideoRoy on 2011-05-04
> **fmdex2011 said:**
> **Update**:    

Well I tried to install the package dvdstyler_1.8.2.1-0ubuntu1_amd64.deb and it came up with a bunch of dependencies that you need to install first

Depends on:

    * dvd+rw-tools
    * dvdauthor
    * dvdstyler-data (= 1.8.2.1-0ubuntu1)
    * genisoimage
    * libavcodec-extra-52
    * libavcodec52 (>= 4:0.6-1~)
    * libavformat52 (>= 4:0.6-1~)
    * libavutil50 (>= 4:0.6-1~)
    * libc6 (>= 2.7)
    * libexif12
    * libfontconfig1 (>= 2.8.0)
    * libgcc1 (>= 1:4.1.1)
    * libjpeg62 (>= 6b1)
    * libstdc++6 (>= 4.1.1)
    * libswscale0 (>= 4:0.6-1~)
    * libwxbase2.8-0 (>= 2.8.11.0)
    * libwxgtk2.8-0 (>= 2.8.11.0)
    * libwxsvg0 (>= 1:1.0.7)
    * mjpegtools

So then I started installing some of the dependencies and found out they had dependencies from the same list

To move on I tried to install those dependencies and found out they broke other dependencies and you have to remove a lot of other stuff

(somebody get me a diaper)

Now I am trying to figure out if there is some logical order to install these dependencies without breaking my system

Or do I have to install Natty 11.04?

I may just take a crack at version 1.8.3rc2 which has fixes for 1.8.2

Does anyone have some suggestions?
I am afraid I cannot help on the dependency side but I have upgraded to Natty.  I have not touched DVDStyler since I posted the original here.  In general I got tired of not response and not able to compile due to all the problems with missing files.

I will give the .deb a try that you posted here.  Thanks for the link.

---

