---
title: "Frostwire Problems"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by mwacky on 2007-08-24
When I try to start frostwire it hangs on the splash screen.  It used to work fine, Limewire will do the same thing.  I suspect it is a Java problem, but not sure.  Tried to reinstall Java 5 jre and install Java 6 jre from Synaptic, then reinstall frostwire.  No Luck, here is what the terminal says:

```


frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_11]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct


```

---

### Post by DemoN3x on 2007-08-26
Yep I'm having the exact same problem.  Was working fine.  Don't know what has changed.

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_02]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct

```

---

### Post by GSF1200S on 2007-08-26
wow, I wish I could tell you. How are you guys installing it? I cant find it in the repos despite many people saying its in there... I installed it by deb package before, but I cant do that now because I have a ubuntu kernel/kde-core thing going on...

I would suggest replacing .frostwire and reinstalling it along with java as if it were the first time.

---

### Post by mwacky on 2007-08-27
I installed Java from Synaptic and used the .deb to install frostwire.. I will try your suggestion, thanks!

---

### Post by Gaius Rex on 2007-08-28
I'm forewarning all of you guys: I'm a total newb here. Sorry if this sounds dumb.

I'm having these same issues, and I'd like to try removing frostwire and java and reinstalling, but I'm not sure (okay, almost entirely ignorant) of how to do that. 

Is this something I do through Synaptic, or is the terminal a better bet?

---

### Post by mwacky on 2007-08-29
You should be able to remove Java through Synaptic, search for sun-java.

If you look in your .frostwire folder in the home directory (if that's where frostwire is installed) there should be an uninstall script you can run to remove frostwire.

I'm still having issues with the setup: installing java from synaptic and frostwire from the deb package, even after trying several re-installs, let us know if your re-install works.  Thanks!

---

### Post by Gaius Rex on 2007-08-29
I successfully removed frostwire, but the issue i'm having is that everytime I try to install a new package, the terminal shows me an error message saying I need a JRE file off of the java website: jdk-1_5_0-loc.zip jdk1_5_0-doc.zip

This file isn't apparently oavailable on the Java site, and I can't uninstall the packages I apparently have for Java without the error message showing up.


I've not actually encountered your issue, and sadly, I'm much too inexperienced to begin to know how to help you out.

Wish I could be of assistance myself, and thanks for all the help I've been getting from the community. You guys rock.

---

### Post by Gaius Rex on 2007-08-29
I may have just made headway. I went under the System Tab in the toolbar up top, and under Preferences I found Sun-Java Plugin Control Panel and Sun Java Policy tool.

This didn't make sense to me, because I'd used Synaptic to clear out the java packages. I opened the Control Panel and under the Java tab there's a JNPL Runtime settings button. I clicked Find and it came up with several files located at 

         "/home/garrett/.wine/drive_c/windows/profiles/mydocuments... "

          ....over and over again a full 38 times(!) from where it first says /.wine before it finds                                        

        ".wine/dosdevices/z:/usr/libj2se/1.4/jre/bin/java"        

This is odd to me, because although I was a Windows user in the last iteration of this pc, I've since replaced both the motherboard and hard drive, so there shouldn't be a C partition anyways, much less anything sullied by Microsoft's greasy paws.

Again I'm perplexed, but I'm thinking that if I uninstall Wine, I'll not be able to access these old versions of Java, and thus be able to properly install the Linux versions.

Is this a wise choice? I have no idea.

As always, any and all advice would be greatly appreciated.
Thanks, Ubuntu people!

---

### Post by Gaius Rex on 2007-08-29
Okay, so now I most definitely own the most recent Java for Linux, and WINE is gone, gone.

And I now get this whenever I try to run Frostwire:

"garrett@garrett-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com"

---

### Post by DemoN3x on 2007-08-30
You can install JRE 1.5 from synaptic.

I tried with 1.5x, 1.6x.  Tried all sorts and still had the same problem.  I had to reinstall ubuntu which obviously sorted the problem but not much help to you guys :(

---

### Post by mwacky on 2007-09-03
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Okay, interesting results... Frostwire comes to life if I start it (where it hangs), then i suspend my laptop, when resume from suspend Frostwire is awake.  Recently have had problems with Google Earth and Suspend with my laptop (HP Pavilion zv6000).  See this [thread.]("http://ubuntuforums.org/showthread.php?t=451960")  Something I did by changing the settings in /etc/default/acpi-support changed how  Frostwire/Limewire initializes.  Anyway I know the trick to start Frostwire and Google Earth is working in and out of suspend so I'm happy...

---

### Post by mwacky on 2007-09-03
Here is my Terminal Output from this:


```
mwacker@Nelson:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_11]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct

#This is the point where frostwire hangs.  Here on is after resume from suspend.


java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@e41bc3
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@e41bc3
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
SponsorLoader._loadBanners() exception java.net.UnknownHostException: sponsors.frostwire.com
SponsorLoader._loadBanners() exception java.net.UnknownHostException: sponsors.frostwire.com
```

---

### Post by alnhntr29 on 2007-09-03
Had the same problem, heres what I did, 
Removed ALL jre with synaptic along with frostwire completely.
Reinstalled jre6 then reinstalled frostwire. Then I ran frostwire from the terminal, closed the terminal
then ran frostwire from the menu. works fine now. hope that helps

---

### Post by ray bot on 2007-09-04
This is odd... I have Ubuntu Feisty and Kubuntu Feisty both installed on the same box. Both have all updates installed and are using the same jvm (sun-java6), yet I only experience this bug in Kubuntu. Also, it doesn't only affect LimeWire and FrostWire. I tried running Dr. Java, and it also hangs for several minutes before actually appearing.  Could it have something to do with the way KDE and Java interact?

---

### Post by mwacky on 2008-04-23
Back again, frostwire is hanging on Gutsy now.  Something is up with Java.  Anybody out there have this issue (frostwire hanging on start up with the splash screen visable) and successfully tweak the Java Control Panel settings to get it to work properly?  A reinstall is not that much fun.

---

### Post by don762003 on 2008-04-23
used sudo update-java-alternatives -s java-6-sun and it worked for me. maybe this will help.

---

### Post by mwacky on 2008-04-25
> **don762003 said:**
> used sudo update-java-alternatives -s java-6-sun and it worked for me. maybe this will help.

Thanks for the tip!  But no luck still, your on the right track, here's my output.  A reinstall will work, but...

```
sudo update-java-alternatives -s java-6-sun
No alternatives for appletviewer.
No alternatives for apt.
No alternatives for extcheck.
No alternatives for HtmlConverter.
No alternatives for idlj.
No alternatives for jar.
No alternatives for jarsigner.
No alternatives for javac.
No alternatives for javadoc.
No alternatives for javah.
No alternatives for javap.
No alternatives for java-rmi.cgi.
No alternatives for jconsole.
No alternatives for jdb.
No alternatives for jhat.
No alternatives for jinfo.
No alternatives for jmap.
No alternatives for jps.
No alternatives for jrunscript.
No alternatives for jsadebugd.
No alternatives for jstack.
No alternatives for jstat.
No alternatives for jstatd.
No alternatives for native2ascii.
No alternatives for rmic.
No alternatives for schemagen.
No alternatives for wsgen.
No alternatives for wsimport.
No alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using `/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide `jcontrol'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceape-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceweasel-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `midbrowser-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `xulrunner-javaplugin.so'.
mwacker@Nelson:~$ frostwire 
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

---

### Post by mwacky on 2008-05-01
Ran the upgrade to Hardy and it works again.  Must have cleared up my java issues.  But my output is now asking me to submit a bug report, so maybe that was part of my issue before, maybe not.  Anyway it works again so I'm happy.

---

