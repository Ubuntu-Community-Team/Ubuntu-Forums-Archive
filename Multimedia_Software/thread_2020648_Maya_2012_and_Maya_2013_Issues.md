---
title: "Maya 2012 and Maya 2013 Issues"
date: 2012-07-08
forum: Multimedia Software
---

### Post by skullmunky on 2012-07-08
I have Maya 2012 installed and it's been working fine for a while now.

Today I upgraded to Precise Pangolin, and now Maya crashes whenever I try to import an image file to use as a texture.

Here's the crash log.  It looks like the culprit is Qt's JPEG loader.

Loading Targa files works fine.


```

//====================================================
//last tool: nurbsSelect
//====================================================
//panel with focus: hyperShadePanel1
//visible panels:
// modelPanel4 hyperShadePanel1 
//====================================================
  /lib/x86_64-linux-gnu/libc.so.6(+0x364c0) [0x7fd8a7e844c0]
  jpeg_CreateDecompress
  /usr/autodesk/maya2012-x64/qt-plugins/imageformats/libqjpeg.so(+0x3a47) [0x7fd894691a47]
  /usr/autodesk/maya2012-x64/qt-plugins/imageformats/libqjpeg.so(+0x4bff) [0x7fd894692bff]
  /usr/autodesk/maya2012-x64/qt-plugins/imageformats/libqjpeg.so(+0x4c8c) [0x7fd894692c8c]
  QImageReader::read(QImage*)
  QImageReader::read()
  QPixmapData::fromFile(QString const&, char const*, QFlags<Qt::ImageConversionFlag>)
  QPixmap::load(QString const&, char const*, QFlags<Qt::ImageConversionFlag>)
  QPixmap::QPixmap(QString const&, char const*, QFlags<Qt::ImageConversionFlag>)
  QmayaFileDialogImagePreview::previewForFile(QString const&)
  QmayaFileDialogImagePreview::qt_metacall(QMetaObject::Call, int, void**)
  QMetaObject::activate(QObject*, QMetaObject const*, int, void**)
  QFileDialog::currentChanged(QString const&)
  /usr/autodesk/maya2012-x64/lib/libQtGui.so.4(+0x6def97) [0x7fd8ab864f97]
  QFileDialog::qt_metacall(QMetaObject::Call, int, void**)
  QmayaFileDialog::qt_metacall(QMetaObject::Call, int, void**)
  QMetaObject::activate(QObject*, QMetaObject const*, int, void**)
  QItemSelectionModel::currentChanged(QModelIndex const&, QModelIndex const&)
  QItemSelectionModel::setCurrentIndex(QModelIndex const&, QFlags<QItemSelectionModel::SelectionFlag>)
  QAbstractItemView::mousePressEvent(QMouseEvent*)
  QWidget::event(QEvent*)
  QFrame::event(QEvent*)
  QAbstractScrollArea::viewportEvent(QEvent*)
  QAbstractItemView::viewportEvent(QEvent*)
  /usr/autodesk/maya2012-x64/lib/libQtGui.so.4(+0x694438) [0x7fd8ab81a438]
  QCoreApplicationPrivate::sendThroughObjectEventFilters(QObject*, QEvent*)
  QApplicationPrivate::notify_helper(QObject*, QEvent*)
  QApplication::notify(QObject*, QEvent*)
  QmayaApplication::notify(QObject*, QEvent*)


//====================================================
//Memory usage:
//  718.578 Mb  Free Memory
// 2147.484 Mb  Free Swap
//  108.141 Mb  Heap
//   45.312 Mb  MEL
//    0.062 Mb  Arrays
//    0.135 Mb  arguments
//    0.125 Mb  Transforms
//    3.139 Mb  Pixel Map
//    3.504 Mb  Render Cache
//    0.332 Mb  Data Blocks
//====================================================

```

Also, Maya 2013 hangs when I try to launch it, and doesn't get to the splash screen.  Has anyone gotten either of these running Ubuntu 12.04?

---

### Post by cougar1622 on 2012-07-21
I am having same problem.  I have both 2012 and 2013 installed on 12.04 Studio and they work great.  I've been working with it everyday modeling all kinds of stuff.  Yesterday I tried to load a image file for a texture and crash.  Every time!!!  I loaded different files and different images and same result.  I am new to Linux and really don't know how to fix this.  Any help would be great.

---

### Post by skullmunky on 2012-07-26
You're doing better than I am, I can't even make Maya 2013 run at all - it just hangs, never even gets to the splash screen.  But anyway ... 

I looked in the Maya launch script (/usr/autodesk/maya2012-x64/bin/maya), there's a line where it disables loading Qt plugins.  I commented that out, but it still crashes.  

(Qt is the cross-platform UI toolkit that Maya now uses).  Note in the stack trace this does seem related:

/usr/autodesk/maya2012-x64/qt-plugins/imageformats/libqjpeg.so(+0x3a47) [0x7fd894691a47]

libqjpeg.so is the plugin that loads JPEGs, and it's part of the Qt toolkit - or rather, the version of the Qt toolkit that comes with Maya.  

Here are some folks using ArchLinux who have the same problem:

[https://bbs.archlinux.org/viewtopic.php?id=127833](https://bbs.archlinux.org/viewtopic.php?id=127833)

"Well removing the /usr/autodesk/maya2012-x64/qt-plugins make maya use the system libs and don't crash but i still can't load jpegs."

cougar1622, are you using Ubuntu or Kubuntu?  I'm on Kubuntu so using KDE and I think Arch Linux does too.  KDE is built on Qt so maybe there is a conflict between Qt versions or something, which maybe doesn't happen to people running Gnome.

---

### Post by skullmunky on 2012-07-26
And it turns out that link led me to a solution :)  Thanks Archlinux Community!  

Short solution:

1. edit the maya launcher script
```

sudo pico /usr/autodesk/maya2012-x64/bin/maya

```

2. scroll down and look for the lines that say 
```

# Set up the location of the libquicktime plugins
setenv LIBQUICKTIME_PLUGIN_DIR "$MAYA_LOCATION/lib"

```

3. after that line, add this:
```

setenv LD_PRELOAD /usr/lib/x86_64-linux-gnu/libjpeg.so.62

```

4. save and exit pico, and launch maya.

The problem is in jpeg loading, but messing with the Qt plugins didn't solve it for me.  What did solve it is making sure the system JPEG library is loaded first before Maya runs.

This uses the LD_PRELOAD environment variable, which you can use to load a library before a program launches.  The trick is to preload the library libjpeg.so.62. This used to live in /usr/lib, but now seems to be in /usr/lib/x86_64-linux-gnu/.  

You can find it using locate:

```

$ locate libjpeg.so

/usr/lib/i386-linux-gnu/libjpeg.so.8
/usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/libjpeg.so
/usr/lib/x86_64-linux-gnu/libjpeg.so
/usr/lib/x86_64-linux-gnu/libjpeg.so.62
/usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
/usr/lib/x86_64-linux-gnu/libjpeg.so.8
/usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2

```

To test if this trick will work, you can temporarily do the preload from the terminal before launching maya:

```

$ export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libjpeg.so.62
$ cd /usr/autodesk/maya2012-x64/bin
$ ./maya

```

If that solved it, edit the maya launch script and insert the preloading permanently.  (note the difference in how it's done in the terminal vs. in the script, it's the difference btwn BASH shell and CSH shell and their syntax for setting env variables).

---

### Post by slegrand on 2012-08-10
Thanks for the jpeg fix guys. This was doing my head in. On another note has anyone else got this weird problem with Maya not being able to open a file after opening it. 

If I launch it at trerminal like:

```
maya somefile.ma
```

It opens it up just fine but if I go to the file open dialog or try to open using the mel command:

```
file -o -f "somefile.ma";
```

I get a crash.

```
maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/username.20120810.1320.ma

```

---

### Post by KoticR on 2012-08-27
**[SOLVED:]** But seriously i got no idea what i did, i've done so much different things. The last thing i did was deleting the Maya.env in "/home/<yourusername>/maya/maya2012-x64/" hope it helps someone.


Hey guys im pretty new to ubuntu, i know not another one ;P
Anyways i've managed it to install Maya2012 x64 on my Ubuntu 12.04 machine. Im pretty happy about the point that i've fixed all those lib problems by my own! 
But now when i try to run maya through the terminal by typing maya it seems that it wont start at all. It spits out no error or anything else like that. See the screenshot for better explanation of what i get.

[IMG]http://ubuntuone.com/6d0u2kwMx9lvPxzL19tKYR[/IMG]

It's not doing anything for ages their is no splash screen or maya window opening. Let me know if you need any more informations i've followed on how to install maya those guides [Maya 2012 x64 on Ubuntu 11.04]("http://stefanobolli.blogspot.de/2011/05/maya-2012-x64-on-ubuntu-1104.html") and on some parts this one [How to install Autodesk Maya 2011 on Debian / Ubuntu]("http://etoia.free.fr/?p=1611")

The only differences that i made was to allocate the new lib files like instead of libtiff.so.4.3.3 i linked them to libtiff.so.4.3.4 and so forth.

Any help on how to fix it would be great!
Thanks in advanced :)

Sincerely
Chris.R

---

### Post by skullmunky on 2012-12-06
> **slegrand said:**
> Thanks for the jpeg fix guys. This was doing my head in. On another note has anyone else got this weird problem with Maya not being able to open a file after opening it. 

If I launch it at trerminal like:

```
maya somefile.ma
```

It opens it up just fine but if I go to the file open dialog or try to open using the mel command:

```
file -o -f "somefile.ma";
```

I get a crash.

```
maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/username.20120810.1320.ma

```

Hi, sorry, haven't checked back in a while - I ran into this problem too and solved it by upgrading my nvidia driver.  For me, I could always open 1 scene initially in Maya, but then attempting to either open another scene or create a new scene would crash it.

I resolved it by manually downloading and installing the latest driver from the nvidia website.  None of the driver options available through Ubuntu's Restricted Drivers tool solved it, but for some reason the old-school manual install method did.  I expect that's just a temporary situation.

Also, by the way, I mentioned having trouble running Maya 2013 at all; it would just hang at the command line and never do anything.  I solved by running it once as root - 

```

sudo /usr/autodesk/maya2013-x64/bin/maya

```

then quit, then after that it's been fine running as a normal user.  I think during first run it tries to set some configurations that need root.  Or else it's installing a rootkit.  (Only half-joking, there is actually some bizarre usage stats phone-home thing that autodesk has started bundling in, but I don't know really what it does).

The same steps resolved the same problem for mudbox 2013 for me.

---

### Post by richardvdoost on 2013-03-17
I was having the exact same problems, running maya 2013 on ubuntu 12.04. Maya didn't even start, what seemed to work for me was installing nvidia-experimental-304 drivers. I also tried the nvidia-current and nvidia-experimental-310 without luck. Maya starts now, however I'm still having the following error (and crash) when I try to open a file:

```
maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/username.20130317.1633.ma

```

---

### Post by slegrand on 2013-06-26
> **richardvdoost said:**
> I was having the exact same problems, running maya 2013 on ubuntu 12.04. Maya didn't even start, what seemed to work for me was installing nvidia-experimental-304 drivers. I also tried the nvidia-current and nvidia-experimental-310 without luck. Maya starts now, however I'm still having the following error (and crash) when I try to open a file:

```
maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/username.20130317.1633.ma

```

Yeah this is still happening to me too. I've had some luck at one point after installing the binary drivers from the nvidia site and installing packaged ones in the midst of it all I had it all working. I could file open without any problem. I had no idea what exactly it was that made it work but it did. Then I had a software update and file open broke again. It's infuriating. Can anyone shed some light on what could be causing that issue?

EDIT: this is happening for maya 2012, 2013 and 2014.

---

### Post by slegrand on 2013-06-26
Well. Sorry for the double post but tonight was my lucky night. I worked out what the problem was. I'm recording it here in case any of you guys still need to fix this.

It was relatively simple.

For Ubuntu 12.04 and Maya 2011 - 2014 and geforce 500 series

remove all installed nvidia drivers via apt

```
sudo apt-get remove nvidia-*
```

now remove the nouveau drivers (That's what was causing me issues)

```
sudo apt-get remove xserver-xorg-video-nouveau
```

now download [this driver version ]("http://www.nvidia.com/object/linux-display-amd64-304.60-driver")(apparently the best one with most autodesk products, that's the one my studio is using)

remember where you downloaded it. 

now kill x (of course don't do this now while you are still reading as this will kill your x session):

```
ctrl+alt+backspace
```

login

kill you display manager:

```
sudo service kdm stop
```
or
```
sudo service gdm stop
```

login again

then go to you nvidia driver directory:

```
cd ~/Downloads
```

and run the installer:

```
sudo ./NVIDIA-Linux-x86_64-304.60.run
```

During the install chose yes for everything EXCEPT creating an xorg.conf file. Click no for that.

once that's done, make sure you have no xorg.conf file

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

and reboot

```
sudo reboot
```

That did it for me. The trick was to remove the nouveau drivers.

---

### Post by ragtag on 2013-09-22
I've found a solution to this problem with Maya crashing when either trying to make a new file, or opening a file. It seems to be because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/943162").

The package libgl1-mesa-dev creates a symlink /usr/lib/x86_64-linux-gnu/libGL.so -> /usr/lib/x86_64-linux-gnu/mesa/libGL.so, which seems to break Maya, and apparantly causes problems with using OpenGL in dynamic languages. What I've done is simply remove the symlink /usr/lib/x86_64-linux-gnu/libGL.so, after which Maya runs fine.

I guess uninstalling libgl1-mesa-dev would also work, but I need it around for compiling some stuff.

---

### Post by abudaan on 2013-11-03
After I had installed libjpeg62:

```
sudo apt-get install libjpeg62
```

Maya still didn't launch. 

But as su it works fine:

```
sudo maya
```

On 13.10 with Nvidia drivers 319.32 (did not de-install nouveau drivers)

---

### Post by bangsi on 2014-05-14
> **abudaan said:**
> After I had installed libjpeg62:

```
sudo apt-get install libjpeg62
```

Maya still didn't launch. 

But as su it works fine:

```
sudo maya
```

On 13.10 with Nvidia drivers 319.32 (did not de-install nouveau drivers)

Installing libjpeg62 did the trick for me, after installing Maya with this script:  [https://gist.github.com/bthj/138fb093e66c1582eaa9](https://gist.github.com/bthj/138fb093e66c1582eaa9)

Thanks!

---

