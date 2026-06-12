---
title: "Updated to Karmic -- no taskbar or nothing on desktop"
date: 2010-05-14
forum: Mythbuntu
---

### Post by yzfr1 on 2010-05-14
I recently updated to Karmic.. 

I rebooted and now I have no taskbar or icons on my desktop.  Just a background image...

I have looked for a while and can't find anything..  

Still have command line ability but don't know what to do to get gdm or xfce to work so I can use the desktop again...

Anyone have any ideas?

Please help.

---

### Post by cbecker78 on 2010-05-14
Is it possible to right-click and add a panel?  If not, can you boot in verbose/text mode and see if the OS is trying to start gnome?

---

### Post by yzfr1 on 2010-05-14
> **cbecker78 said:**
> Is it possible to right-click and add a panel?  If not, can you boot in verbose/text mode and see if the OS is trying to start gnome?

I can't right click at all..  does nothing.

How do I boot in verbose/text mode?  And what would I look for?  I have access to a terminal via ssh and I have restarted gdm but that doesn't seem to help.

---

### Post by cbecker78 on 2010-05-14
I think alt+F2 during boot will do it.  If not, from grub, hit e, then... erm, I haven't done this in a month or so and can't quite remember.  I don't have access to my machine right now to try it either. I think it is like, hit "e" twice, then remove "quiet splash" from the kernel you want to boot, then hit "b"... not sure that is right though.

you would look for something like "starting gnome... [OK]"...  

I wonder if there is an issue with your graphics card here?  Can you boot a 10.04 live CD?  May be worthwhile to ssh in and check dmsg and see if it's complaining about anything.

---

### Post by uncle hammy on 2010-05-14
Don't take offense to a simple query.  Is it possibly hidden due to overscan?  i.e. is it there, but WAY up out of view beyond the upper limit of your tv?

Move the mouse up tot he top of the tv, then keep going.  Right click up there in the nether region, and see if the bottom of the context menu pops up.

---

### Post by yzfr1 on 2010-05-18
> **uncle hammy said:**
> Don't take offense to a simple query.  Is it possibly hidden due to overscan?  i.e. is it there, but WAY up out of view beyond the upper limit of your tv?

Move the mouse up tot he top of the tv, then keep going.  Right click up there in the nether region, and see if the bottom of the context menu pops up.


sorry been out for a few days..  

I thought of the overs scan problem already.  could not find this was an issue.  I did move my mouse to the top of the screen and tried to keep going.  i did click to see if I could get the context menu to show, However, nothing happened....

In response to cbecker78...

I have booted into grub once or twice trying to figure this out...  I have not tested your question on whether gnome is starting.  I will do that as soon as I get home this evening...  I would think that gnome is starting though as I have a background image on the desktop when I boot up.  

I also thought this might be a graphics card so I removed the add on graphics card and just used the vga card that is on the mobo.  I still get the same thing.  I also, looked in dmesg originally and I have never seen it complaining about anything..  at least not that I can tell.

Thanks for you help guys.. if you can think of something else for me to try I will most definitely do it..

---

### Post by yzfr1 on 2010-05-18
Ok.. I have an update on this problem..  I still cannot get my desktop to show any icons or taskbar but I got MythFrontend to run.  I just would like the rest of it to display.  

I am assuming the issue here is gnome, gdm, or XFCE.  So what now?  Anyone?  How might I get this to show up....

Note: I saw a few posts where some say to run gnome-panel.  I tried that, however, I don't have that command installed.  Should I?  I ran apt-get install gnome-panel and it the install wanted install a lot of other programs as dependencies.  Didn't follow through with the install because I did not want to install a bunch of things I just don't need.

:?

---

### Post by uncle hammy on 2010-05-18
I accidentally deleted my taskbar on my Ubuntu laptop the other night.  This [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html) worked like a charm.  Worth a try anyways.

---

### Post by yzfr1 on 2010-05-18
> **uncle hammy said:**
> I accidentally deleted my taskbar on my Ubuntu laptop the other night.  This [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html) worked like a charm.  Worth a try anyways.


Ok..  here is what I did...  

Tried to go through the steps in this link..  I got gnome command not found on all of that...

so I did sudo apt-get install gnome-panel

It installed...

so I tried those steps and again nothing...

so I tried just gnome-panel for which I was saw on some other posts.. here is what I got

> gnome-panel: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

I have looked a lot of places earlier because saw this when trying to start firefox from the command line but I have not found what causes this error or a way to fix it...

Any ideas?

---

### Post by sccar_support on 2010-05-18
I'm seeing the exact same behavior over the past few days and still cannot see any icons on the dekstop or right-click.  From what I've read, this is a glib issue.  Try running the ubuntu software center manually from the command line.  I see the following:

(1) [~] > /usr/bin/software-center

GLib-ERROR **: /build/buildd/glib2.0-2.22.3/glib/gmem.c:156: failed to allocate 3855203796 bytes
aborting...
Abort

I'm dying for a fix here!

---

### Post by yzfr1 on 2010-05-19
Ok..  everyone..  I seemed to have fixed my problem.. I do not know what all this about but I just followed the instructions on this link...

[https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/176318](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/176318)

Basically I deleted all instances of freetype in /usr/local/lib/

then I ran

```
sudo apt-get --reinstall libfreetype6
```

I then ran 

```
sudo gnome-panel
```

and the taskbars showed up!

---

### Post by Senkoboy on 2010-05-23
I had the same problem. Had to reinstall everything.  Glad you figured it out.

---

