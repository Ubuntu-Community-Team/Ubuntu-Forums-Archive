---
title: "[SOLVED] Limewire Wont Start"
date: 2008-08-21
forum: Multimedia Software
---

### Post by kieonsegg on 2008-08-21
Just installed limewire, downloaded JRE, loads into a white screen for the window and just the taskbar. wont load and i can click like the different things in the window but i cant see wut they are. also tried frostwire, happens in both

---

### Post by kieonsegg on 2008-08-21
please someone, so far havent really got any help from my about 10 posts
could someone please help?????

---

### Post by b9k9kiwi on 2008-08-22
> **kieonsegg said:**
> please someone, so far havent really got any help from my about 10 posts
could someone please help?????

I can't help I'm quite new to Linux - but I do know from experience that patience has it's own reward in these forums.

You have to wait for three things - users to logon who now about the problem you have, that one or more of those users actually reads your message and that one or more of those users is inclined or has the time to help (might not be inclined or have the time today, but maybe in a few hours or tomorrow).

I do hope that you have not left 10 posts all about the same subject :)

---

### Post by rainwalker on 2008-08-22
[www.frostwire.com](www.frostwire.com)

FrostWire is based off of LimeWire, but it's as fast as LimeWire's "Pro" version and it's free. Plus, it comes in .deb format for easy installation

---

### Post by Gondee on 2008-08-22
Are you using wine? 

If not ```
sudo apt-get install wine
```

then try the install again. If that is not the case use the latter post

---

### Post by OutOfReach on 2008-08-22
> **Gondee said:**
> Are you using wine? 

If not ```
sudo apt-get install wine
```

then try the install again. If that is not the case use the latter post

LimeWire is available for Linux. ;)

---

### Post by gandaran on 2008-08-22
> **kieonsegg said:**
> Just installed limewire, downloaded JRE, loads into a white screen for the window and just the taskbar. wont load and i can click like the different things in the window but i cant see wut they are. also tried frostwire, happens in both

I have never used limewire, but I know it uses sun java, so first your should rule out if it's really a java problem.
how did you install java, the sun bin package or synaptic's sun-java6-jre and sun-java6-plugin?
check also that you don't have open-java installed, if you have both installed, open-java and sun-java your system could be configured to use open java.

---

### Post by kieonsegg on 2008-08-22
> **rainwalker said:**
> [www.frostwire.com](www.frostwire.com)

FrostWire is based off of LimeWire, but it's as fast as LimeWire's "Pro" version and it's free. Plus, it comes in .deb format for easy installation

read my first original post before answering
already tried frostwire...

---

### Post by kieonsegg on 2008-08-22
> **gandaran said:**
> I have never used limewire, but I know it uses sun java, so first your should rule out if it's really a java problem.
how did you install java, the sun bin package or synaptic's sun-java6-jre and sun-java6-plugin?
check also that you don't have open-java installed, if you have both installed, open-java and sun-java your system could be configured to use open java.

i installed jre from synaptic package manager. i dont think i have installed open-java. ill try running it in terminal
thanks

*edit* tried running in terminal and searching for it with the gnome finder and i have nothing under open-java.
any other ideas???

---

### Post by rainwalker on 2008-08-22
> **kieonsegg said:**
> read my first original post before answering
already tried frostwire...

Ah, sorry, missed that part
For me, FrostWire didn't work correctly unless I installed the ubuntu-restricted-extras package and set my Java version...I think the command was something like "sudo update java alternatives"

---

### Post by kieonsegg on 2008-08-22
> **rainwalker said:**
> Ah, sorry, missed that part
For me, FrostWire didn't work correctly unless I installed the ubuntu-restricted-extras package and set my Java version...I think the command was something like "sudo update java alternatives"

didnt work, do u remember hte guide that helped you or know the link???

---

### Post by gandaran on 2008-08-23
> I think the command was something like "sudo update java alternatives
you only need to run this command if you have both sun-java and open-java installed, it sets up which java the system uses.
open-java gets installed with the ubuntu-restricted-extras packages, it's best you just have one java installed 

kieonsegg
 try starting limewire in the terminal/console and post the output errors here.

---

### Post by kieonsegg on 2008-08-23
> **gandaran said:**
> you only need to run this command if you have both sun-java and open-java installed, it sets up which java the system uses.
open-java gets installed with the ubuntu-restricted-extras packages, it's best you just have one java installed 

kieonsegg
 try starting limewire in the terminal/console and post the output errors here.

K first the input was this, and it loaded the screen for limewire:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_15]
Configuring environment...
Loading LimeWire:
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xafd0b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xafd0b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xafd501bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe3fdce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe29d77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe29ef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xafe2a136]
#7 [0xb25c5bfa]
#8 [0xb25bfb3b]
#9 [0xb25bfb3b]
#10 [0xb25bd219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb777c2bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7890ed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb777c0ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77d9b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb757130d]
#16 [0xb25c54ab]
#17 [0xb25bfa64]
#18 [0xb25bd219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb777c2bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xafd0b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xafd0b81e]
#2 /usr/lib/libX11.so.6 [0xafd4f518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xafd460a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe290b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe29303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xafe29fa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xafe2a136]
#8 [0xb25c5bfa]
#9 [0xb25bfb3b]
#10 [0xb25bfb3b]
#11 [0xb25bd219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb777c2bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7890ed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb777c0ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77d9b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb757130d]
#17 [0xb25c54ab]
#18 [0xb25bfa64]
#19 [0xb25bd219]


Then the loading screen stopped and the terminal showed:
******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Client VM (build 1.5.0_15-b04, mixed mode, sharing)

I downloaded the latest version of jre im confused because before it didnt show this

*edit* i tried starting it normally (not in terminal), after a really long time, like 2 min, it started limewire setup, i went throught that, all good. But i cant see the limewire window, i can see the tip of the day, and the window asking for limewire pro but thats it. The main limewire window is blank white, and when i move my cursor around it, i can click different parts of the screen (like a hyperlink) im gonna wait about an hour to see if i can see anythign but im really stuck :(

---

### Post by mike1234 on 2008-08-23
Why would anyone want to use Limewire? It's a joke. Use a real torrent program instead. Deluge. 

M.

---

### Post by gandaran on 2008-08-23
kieonsegg 
open your synaptic package manager and scroll down to sun java, remove all sun-java5 packages (complete removal) and install the sun-java6 packages, .jre, .bin and the plugin too, there are both java5 and java6 packages there.

---

### Post by kieonsegg on 2008-08-24
> **gandaran said:**
> kieonsegg 
open your synaptic package manager and scroll down to sun java, remove all sun-java5 packages (complete removal) and install the sun-java6 packages, .jre, .bin and the plugin too, there are both java5 and java6 packages there.

THANKS, fixed the problem perfectly, i should have thought of that the first time!

---

