---
title: "Yet another java plugin problem"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by SneakyWho_am_i on 2008-03-10
After reading what felt like a hundred threads on installing java and a java plugin, and countless offsite things, I've gone through quite a bit of work to try get java and stuff running.

Some of my (naughty) applications require sun java, which easily installs from the repository OR from sun's website. So far so good.

Also the gcj browser plugin and other free alternatives all work fine in Firefox.

SO what's the problem? Well, I need to be able to see this for work:
[http://www.operamini.com/demo/](http://www.operamini.com/demo/)

OK so I don't NEED to, but when I can't use that I have to use REAL Opera Mini, and that's not very pleasant as it costs me by the megabyte. A couple of months ago it was by the kilobyte so it's getting cheaper gradually but I can't afford to wait two years to continue with my work, and sadly I can't really install windows just for the sake of running java just so I can look at one applet on one site.

Anyway, yeah, the free plugins won't load that for me. gcj can kinda load it, but it crashes partway through.

Enough background here are my symptoms:
- Java is installed, and I can use SUN java or in fact whichever java I choose from the console. SUN java is my "preferred" VM, I'm trying java 6 at the moment and it's the one I've had the most success with so far. As I'm not actually developing any java software, that's not such a bad thing ;)
- Firefox can detect the java plugin in about:plugins, and it is definitely enabled.

Applets don't load. On the opera mini site, it displays a lovely "please install java" message (NB from html,not the browser)
SUN's own java tester thing just displays, well, nothing. no "plugin is missing" or anything like that. Nothing. I believe that the plugin is being called, because the applet appears in the DOM but I am not prompted to install anything. It just doesn't actually play.


Just getting FIrefox to acknowledge the plugin took a certain amount of symlinking things and setting permissions for some reason, so I'm sure I'm close.

My system:
Hardy Heron with all updates
32 bit processor
KDE4
Firefox 3.0b3

Yes, yes, I'm running all alpha and beta software and trying to work. I get what I deserve.
Nonetheless if anyone can tell me where to look for messages on what's going wrong, I will fetch them, post them here, let you know what works for me et cetera.

It should be noted that I can run java on the desktop, standalone, but I can't use the plugin in Opera, Epiphany or Firefox. I wonder if I have a permissions problem or something.

I apologize for adding ANOTHER post on java and Firefox.
Thanks in advance.

---

### Post by gtdaqua on 2008-03-10
wow! i mean, this is the same problem that I have and was feeling too sleepy to post this. now am awake! I am also experiencing the same. 

Java didnt work for me on my Kubuntu Hardy Alpha 5. KDE 3.5.9. I followed 
[this]("http://ubuntuforums.org/archive/index.php/t-621864.html") post. In a nutshell, after installing java CLEAN, i did this on the konsole.

```

sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so

```

and now i am able to execute 'jar' files. But plugin on Firefox 3.0b3 wont work!

---

### Post by SneakyWho_am_i on 2008-03-10
@gtdaqua:
I was wondering for a while if this bug was related:
[https://bugs.launchpad.net/ubuntu/+bug/197387](https://bugs.launchpad.net/ubuntu/+bug/197387)

Aa change in java causes locking problems for some applications. Could Firefox 3 be one of those applciations?
I tried the workaround listed there and it gave me no joy, but maybe it might make a difference for you.***

I'm trying to get something meaningful out of Konsole at this point, but no joy.
It's amazing that somebode replied so quickly :D

**** summarily, try closing firefox... make suire it's totally dead:
```
killall firefox
```

Now run this through konsole and see what comes up:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
firefox
```

As I said I don't think it will help but it's worth a shot; I don't know much about this sort of thing ;)
It should be noted that the workaround has some sort of security implication, although it's probably trivial. the bug report @ launchpad (frostwire and java) links to more informaiton on that.

---

### Post by caver1 on 2008-03-10
make sure you have gcjwebplugin installed. Its in synaptic. You may have gcjwebplugin-4.1 or4.2 but you also need the first one without the numbers.
caver1

---

### Post by SneakyWho_am_i on 2008-03-11
Yes, thank you caver1. Indeed, I can install gcjwebplugin and use it in Firefox; however it doesn't at this time play nicely with certain specific applets which i would like to use, particularly the Opera Mini Simulator.

> **caver1 said:**
> make sure you have gcjwebplugin installed. Its in synaptic. You may have gcjwebplugin-4.1 or4.2 but you also need the first one without the numbers.
caver1

I wonder if I could do it with a virtual machine somehow... :)

---

### Post by gtdaqua on 2008-03-11
> **SneakyWho_am_i said:**
> @gtdaqua:
I was wondering for a while if this bug was related:
[https://bugs.launchpad.net/ubuntu/+bug/197387](https://bugs.launchpad.net/ubuntu/+bug/197387)

Aa change in java causes locking problems for some applications. Could Firefox 3 be one of those applciations?
I tried the workaround listed there and it gave me no joy, but maybe it might make a difference for you.***

I'm trying to get something meaningful out of Konsole at this point, but no joy.
It's amazing that somebode replied so quickly :D

**** summarily, try closing firefox... make suire it's totally dead:
```
killall firefox
```

Now run this through konsole and see what comes up:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
firefox
```

As I said I don't think it will help but it's worth a shot; I don't know much about this sort of thing ;)
It should be noted that the workaround has some sort of security implication, although it's probably trivial. the bug report @ launchpad (frostwire and java) links to more informaiton on that.

It works! It works not! What is strange is when I verify Java installation in java.com, it used to keep checking and time out - means firefox cant see java plugin. After executing "export LIBXCB_ALLOW_SLOPPY_LOCK=1" and "firefox" on the command line - i verified again on java.com and was successful! But if i run firefox from K Menu or from the Quicklauncher, verification in java.com fails! 

I have to do the "export" command and execute firefox from the command line for a successful verification!  I changed the shortcut command from default "firefox %u" to simply "firefox" but still no luck. 

Sorry for the late reply though, I was tied up!

---

### Post by gtdaqua on 2008-03-11
> **caver1 said:**
> make sure you have gcjwebplugin installed. Its in synaptic. You may have gcjwebplugin-4.1 or4.2 but you also need the first one without the numbers.
caver1

tried. doesnt work! :-(

---

### Post by SneakyWho_am_i on 2008-03-20
That's odd, I reckon :D It didn't work at all for me.

If it works when you type both from the command line then your fix should be fairly easy I think. The problem is (anybody feel free to correct me) that when you export (set) that variable in the terminal, it only applies for that terminal session (and starting firefox from a menu is a different session with different variables)

To set it globally you can say this:

> For a workaround, put this in your /etc/environment
export LIBXCB_ALLOW_SLOPPY_LOCK=true

You'll need to source the file or restart your xserver session for the changes to apply.

That is to say, edit the file and then log out and hit CTRL+ALT+Backspace.

This still did not fix it for me :( But I'm glad if it gets it working for you. :)


EDIT: This isn't a real solution but I'm going to try a fresh install. Maybe there's a ghost in the machine.

---

### Post by SneakyWho_am_i on 2008-03-28
I installed yet another Hardy um.. installation.

I installed the Xubuntu Daily (Nightly?) build - i386 Alternate.
Started Firefox, visited [http://www.operamini.com/demo/](http://www.operamini.com/demo/)

And lo and behold, what happened? I clicked the "you need a plugin, jerk" sign, and I had not zero like in my last install, but FOUR options to choose from!!!
I chose Sun Java 6 of course because I am an evil not-totally-free software user. Closed Firefox, Opened it, and .... The Opera Mini simulator WORKED PERFECTLY FIRST TIME. In fact, not only is it $10/MB cheaper than doing it on my phone (used to be more but last month they stopped charging by the kilobyte) but it is also 10x more pleasant to use.

So the moral of the story is........
If you need a non-free(ish) version of a plugin and it won't work even after checking the symlinks and permissions and setting preferred applications, and even after the browser acknowledges that it's installed, and even with sloppy locking enabled....
Reinstall your operating system, it will get that plugin working.

Yeah, yeah, I know, I was probably missing something obvious....
But hey, it was the experimental, Alpha Version of Hardy Heron that I'd initially installed. This sort of thing is expected in Alphas.
At least the plugin works now :) and I didn't lose anything.

:guitar:

---

