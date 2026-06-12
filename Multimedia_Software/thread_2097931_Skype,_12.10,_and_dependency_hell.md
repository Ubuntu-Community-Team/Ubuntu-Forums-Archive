---
title: "Skype, 12.10, and dependency hell"
date: 2012-12-24
forum: Multimedia Software
---

### Post by johnzbesko on 2012-12-24
Recently upgraded from 12.04 64b to 12.10 64b. Skype used to work fine. Now, it was not part of the upgrade and synaptic only shows a "skype" package that requires "skype-bin" which is non-existent.

Researching and trying googled solutions lead me into dependency problems with ia32-lib, etc. I'm hoping the Canonical and Skype/MS people can work these problems out.

Any suggestions?

---

### Post by The Spectre on 2012-12-24
Try downloading Skype from [http://www.skype.com/](http://www.skype.com/).

[http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)

I am running Ubuntu 12.10 x64 and Skype is running correctly for me.

---

### Post by johnzbesko on 2012-12-25
Lucky you! I did (and repeatedly) downloaded skype 4.1 and attempted to install, using GDebi. I get an error, "Cannot install 'libqtwebkit:i386'"

This the start of the dependency hell...

---

### Post by drpjkurian on 2012-12-25
Hi
Please install this package from synaptic package manager. It should be fine after that

---

### Post by The Spectre on 2012-12-25
> **johnzbesko said:**
> Lucky you! I did (and repeatedly) downloaded skype 4.1 and attempted to install, using GDebi. I get an error, "Cannot install 'libqtwebkit:i386'"

This the start of the dependency hell...

Instead of using GDebi try installing Skype using the Ubuntu Software Center.

I just started up Ubuntu 12.10 x64 in VirtualBox and installed Skype using the Ubuntu Software Center and it installed and is starting up fine (See attached picture).

---

### Post by xc3RnbFO8P on 2012-12-26
Do you have  **skype-bin:i386 4.1.0.20.0-0ubuntu0.12.04.2** installed?

Run
> sudo apt-get install -f
and show the output

---

### Post by johnzbesko on 2013-01-01
Another holiday goes by...

None of the suggestions work.

:/tmp$ sudo dpkg -i skype-ubuntu*amd64.deb
Selecting previously unselected package skype.
(Reading database ... 253152 files and directories currently installed.)
Unpacking skype (from skype-ubuntu-precise_4.1.0.20-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.

dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 skype


When I attempt to install the 386 version, it conficts and messes up the x64 version. Where do I find the :386 version that installs with the other 386 libraries on an x64 system?

---

### Post by The Spectre on 2013-01-01
> **johnzbesko said:**
> dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.

Did you try installing the Dependency Package (libqtwebkit4) that it is looking for?

It is already installed on my computer and it was also on another Computer that does not even have Skype.

Use the Ubuntu Software Center to install libqtwebkit4.(See Attached Picture)

---

### Post by johnzbesko on 2013-01-02
Making progress. Some libraries, eg. libQtWebkit and the gstreamer group, fail to install using anything based on apt into the /usr/lib/i386-linux-gnu/ directory. (Instead, I was asked to remove my most of my KDE desktop to be replaced with the i386 version.)

So, I used Ark to manually copy the relevent libraries to /usr/lib/i386-linux-gnu/ from the respective i386.deb packages. I was guided by the commandline:

ldd /usr/bin/skype|grep found

which (not) found the missing libraries.

So, Skype now works, sort of. It makes sounds and detects my webcam. However, I cannot make a test call. In fact, I don't even hear the test operator. However, I am able to make a video call to my son. ;-)

---

### Post by xc3RnbFO8P on 2013-01-02
> **johnzbesko said:**
> Making progress. Some libraries, eg. libQtWebkit and the gstreamer group, fail to install using anything based on apt into the /usr/lib/i386-linux-gnu/ directory. (Instead, I was asked to remove my most of my KDE desktop to be replaced with the i386 version.)

So, I used Ark to manually copy the relevent libraries to /usr/lib/i386-linux-gnu/ from the respective i386.deb packages. I was guided by the commandline:

ldd /usr/bin/skype|grep found

which (not) found the missing libraries.

So, Skype now works, sort of. It makes sounds and detects my webcam. However, I cannot make a test call. In fact, I don't even hear the test operator. However, **I am able to make a video call to my son**. ;-)
Without sound?

---

