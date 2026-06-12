---
title: "workaround for flash mouse problem (bug #410407)"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Cyan_Fire on 2009-11-02
Just wanted to post this here for everyone's benefit (and hopefully less spam in the [bugreport]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")).

In [comment #143]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143"), Edward posted a workaround which works for me as well as others. However, I have an alternative workaround which doesn't involve creating files that the package manager won't know about (bad thing):

Edit /usr/lib/nspluginwrapper/i386/linux/npviewer to include a line, "export GDK_NATIVE_WINDOWS=1".

Step-by-step instructions:

1) Run "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer" with Alt-F2.
2) Add the "export GDK_NATIVE_WINDOWS=1" **immediately before** the last line of text.
3) Save and exit.

You should then be golden! Please post here if it doesn't work. Also, please remember to revert the npviewer script to its original state when next upgrading your system.

For reference, my npviewer script looks like:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386

# dgt 02 Nov 2009
export GDK_NATIVE_WINDOWS=1

. /usr/lib/nspluginwrapper/noarch/npviewer
```

---

### Post by jimbo7 on 2009-11-02
I was experiencing the same issue with iceweasel on debian.

to workaround i would execute the following command:

```
GDK_NATIVE_WINDOWS=TRUE iceweasel
```

as a semi-permanant fix, i created an alias in my [FONT="Courier New"]~/.bashrc[/FONT] file

```
alias iceweasel='GDK_NATIVE_WINDOWS=TRUE iceweasel'
```

---

### Post by SilverWave on 2009-11-03
> **Cyan_Fire said:**
> ...

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386

# dgt 02 Nov 2009
export GDK_NATIVE_WINDOWS=1

. /usr/lib/nspluginwrapper/noarch/npviewer
```

Worked for me - Thanks :)

The original worked as well but this is less to change.

---

### Post by robau on 2009-11-03
I took this script, it fixes the firefox flash stuff by downloading the latest version from adobe itself

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Ja&#353;a Bartelj jasa.bartelj@gmail.com
 
echo "Stopping any Firefox that might be running."
sudo killall -9 firefox
 
echo "Removing any other flash plugin previously installed."
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
	 
echo "Installing Flash Player 10."
sudo cd /tmp
sudo wget http://labs.adobe.com/downloads/flashplayer10.html
sudo wget `cat flashplayer10.html | egrep -o "http:.*"|cut -d\" -f1|grep linux-x86_64.so.tar.gz`
ARCHIVE=`ls libflashplayer-*.linux-x86_64.so.tar.gz`
echo "Version is $ARCHIVE."
sudo tar zxvf $ARCHIVE
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
echo "Linking the libraries so Firefox and apps built on XULRunner can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/
# now doing some cleaning up:
sudo rm -rf flashplayer10.html
sudo rm -rf libflashplayer.so
sudo rm -rf $ARCHIVE


```

---

### Post by Cyan_Fire on 2009-11-03
Hi robau,

I don't personally recommend using that script as it performs filesystem operations without the package manager's knowledge. This can leave your system in an inconsistent state.

It's also downloading the 64-bit Alpha from Adobe, which works for some people, but not others (including me... I get crashes on some flash websites).

---

### Post by mwolfgang on 2009-11-04
I am also experiencing this problem with Ajax. I have replicated the issue on multiple machines, but primarily with firefox.  I have yet to experience the issue with Opera or Chromium.  

This fix does not resolve my issue.

Matt

---

### Post by Cyan_Fire on 2009-11-04
Hi mwolfgang,

That's probably a different issue. I haven't had a problem with AJAX mouse recognition at all. You should probably file a separate bug report.

Hope it helps.

---

### Post by rich97 on 2009-11-08
Thanks! Worked like a charm. :D

---

### Post by Nikos.Alexandris on 2009-11-10
> **robau said:**
> I took this script, it fixes the firefox flash stuff by downloading the latest version from adobe itself

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Jaša Bartelj jasa.bartelj@gmail.com
 
echo "Stopping any Firefox that might be running."
sudo killall -9 firefox
 
echo "Removing any other flash plugin previously installed."
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
	 
echo "Installing Flash Player 10."
sudo cd /tmp
sudo wget http://labs.adobe.com/downloads/flashplayer10.html
sudo wget `cat flashplayer10.html | egrep -o "http:.*"|cut -d\" -f1|grep linux-x86_64.so.tar.gz`
ARCHIVE=`ls libflashplayer-*.linux-x86_64.so.tar.gz`
echo "Version is $ARCHIVE."
sudo tar zxvf $ARCHIVE
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
echo "Linking the libraries so Firefox and apps built on XULRunner can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/
# now doing some cleaning up:
sudo rm -rf flashplayer10.html
sudo rm -rf libflashplayer.so
sudo rm -rf $ARCHIVE


```

It works! Thanks, Nikos

---

### Post by kobudo on 2009-11-20
Thanks Cyan! Did the trick nicely! :D

---

### Post by jsangilve on 2009-12-08
thanks cyan. I've been trying with differents methods, but just this works great

---

### Post by Intlex on 2009-12-11
Worked great for me. Thank you very much !

---

### Post by bartman on 2009-12-12
> **Cyan_Fire said:**
> I don't personally recommend using that script as it performs filesystem operations without the package manager's knowledge. This can leave your system in an inconsistent state.

It's also downloading the 64-bit Alpha from Adobe, which works for some people, but not others (including me... I get crashes on some flash websites).

Well yes, that's why it is called alpha! But I've been using this for 2 months now and haven't had any problems. I supposed that anyone using this script knows what they are doing and could handle any new packages that might come down the line.

Unfortunately what happens on the net:
- copying without attribution (backlink to blog)
- using tips without understanding them
- depending on non-permalinks

Read more here: [http://constcuriosity.blogspot.com/2009/10/automatic-adobe-flash-on-amd64.html#comments](http://constcuriosity.blogspot.com/2009/10/automatic-adobe-flash-on-amd64.html#comments)

EDIT: Ah, I see you found a way to make nspluginwrapper work. You make some good points about "soiling" the system, every user should uninstall this when installing the flashplugin-nonfree.

---

### Post by rich97 on 2009-12-12
Actually, I don't understand why people are using that script in the first place. The first solution is easier and it has worked perfectly for me.

---

### Post by bartman on 2009-12-13
I use it because it's native and newer version for 64-bit Linux systems. I never even tried flash on 64 bit with nspluginwrapper because I knew adobe released a native version.

It has been working well for me and until they release a more stable version, that gets included into the repos I will use it. I know about this so it won't be a problem to upgrade whenever the time comes but it is safe to assume all will not.

I'll put a warning about that into the blog.

---

### Post by Lloyd09 on 2009-12-13
> **Cyan_Fire said:**
> Just wanted to post this here for everyone's benefit (and hopefully less spam in the [bugreport]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")).

In [comment #143]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143"), Edward posted a workaround which works for me as well as others. However, I have an alternative workaround which doesn't involve creating files that the package manager won't know about (bad thing):

Edit /usr/lib/nspluginwrapper/i386/linux/npviewer to include a line, "export GDK_NATIVE_WINDOWS=1".

Step-by-step instructions:

1) Run "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer" with Alt-F2.
2) Add the "export GDK_NATIVE_WINDOWS=1" **immediately before** the last line of text.
3) Save and exit.

You should then be golden! Please post here if it doesn't work. Also, please remember to revert the npviewer script to its original state when next upgrading your system.

For reference, my npviewer script looks like:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386

# dgt 02 Nov 2009
export GDK_NATIVE_WINDOWS=1

. /usr/lib/nspluginwrapper/noarch/npviewer
```

worked like a charm, thanks man

---

### Post by Cyan_Fire on 2009-12-13
@bartman: Yeah, there's nothing inherently *wrong* about using that script. The reason why I suggested against it in this thread is because my point here is not to help people that want to experiment but people who just want flash to work. :)

---

### Post by s5cressey on 2009-12-14
After much fuss trying other things this worked great. Thanks Cyan.

---

### Post by fiklein on 2009-12-29
I had no problems with five 32 bit computers, but the two 64 bit computers needed this solution:
Step-by-step instructions:

1) Run "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer" with Alt-F2.
2) Add the "export GDK_NATIVE_WINDOWS=1" **immediately before** the last line of text.
3) Save and exit.

WORKED FLAWLESSLY!!!

Many thanks!!

---

### Post by WaCope on 2010-01-03
Thanks for the quick fix. 
I thought was gonna haunt me until 10.04.

---

### Post by capnion on 2010-02-02
Here works great, very elegant solution!

---

### Post by sarvan.rb on 2010-02-07
> **Cyan_Fire said:**
> Just wanted to post this here for everyone's benefit (and hopefully less spam in the [bugreport]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")).

In [comment #143]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143"), Edward posted a workaround which works for me as well as others. However, I have an alternative workaround which doesn't involve creating files that the package manager won't know about (bad thing):

Edit /usr/lib/nspluginwrapper/i386/linux/npviewer to include a line, "export GDK_NATIVE_WINDOWS=1".

Step-by-step instructions:

1) Run "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer" with Alt-F2.
2) Add the "export GDK_NATIVE_WINDOWS=1" **immediately before** the last line of text.
3) Save and exit.

You should then be golden! Please post here if it doesn't work. Also, please remember to revert the npviewer script to its original state when next upgrading your system.

For reference, my npviewer script looks like:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386

# dgt 02 Nov 2009
export GDK_NATIVE_WINDOWS=1

. /usr/lib/nspluginwrapper/noarch/npviewer
```

this really solved the problem.. Thanks a lot

---

### Post by deibu76 on 2010-06-12
Adobe took the 64-bit linux alpha off their site a couple of days ago when they released Flash 10.1 - so that script to download it in post #3 won't work any longer.

Prior to installing that 64-bit Flash, despite being an Alpha, it worked great and got rid of the mouse problems and tons of terrible video tearing issues...  And now it's gone! 
:(

I backed up my flashplugin.so file just to be safe, and decided I would go ahead and give the NEW 32-bit 10.1 a try.  And, it worked!  It runs MUCH more smoothly than all previous linux versions I've used, 32 or 64-bit.  Also, despite being 32-bit, no more annoying mouse problems either.  And, I can watch Hulu!


YMMV, but I definitely recommend trying to "downgrade" to the  32-bit "upgrade" plugin, and see if it works better...  Make sure you backup the old 64-bit flashplugin.so file first though, since Adobe won't let you download it anymore :mad:!

---

### Post by Mozenrath on 2010-06-30
This solution worked great!  I had to dump the 64-bit version of Flash, but at least I can now control the settings and stuff like that!

---

