---
title: "lirc iMon ffdc VFD remote -&gt; just can't get it to work right"
date: 2009-08-18
forum: Mythbuntu
---

### Post by daniel.pool on 2009-08-18
Hey guys,

I've been bashing my head against a brick wall most evenings for the past 2 weeks trying to get lirc working with my remote. I've had some successes and some dismal failures. Essentially I've been trying some of these threads/articles both absolutely to the letter or even mixing things up:

[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD) -> Ubuntu article, installing from apt.
[http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474) -> how to get the 0038 version of the iMon remote working from latest CVS build. Should still be relevant to my remote though.
[http://www.xbmc.org/forum/showthread.php?t=40290](http://www.xbmc.org/forum/showthread.php?t=40290) -> XBMC article, where I started. Again installing from CVS.

and others ... OK, so I've proved my ability to google if not anything else. 

So, if I follow the apt-get process I end up installing 0.8.4a of lirc. The remote works perfectly out of the box (yea!) except that the pad and power button don't register. I tried to install the pad2keys patch ([http://brakemeier.de/electronics/vdr/lirc-imon.html](http://brakemeier.de/electronics/vdr/lirc-imon.html)) but it said that the patch had already been applied and would fail if I forced it. I tried the pad2keys option (sorry can't remember the format) in /etc/module.d/options but this just came back being reported as an unrecognised option.

Installation from CVS nets me 0.8.6~7 (the version tagging seems a little fuzzy, I'm guessing it's not been updated properly in all files). On this version lirc will have a few issues starting up. I need to modify the /etc/init.d/lirc script and repoint a few things, chmod /dev/lircd etc. However, despite being able to get lirc to a state where it starts up with no complaints it just doesn't recognise any button presses on my remote. I've tried multiple different sources for the lirc.conf file, but I get no joy at all; irw outputs nothing from my remote.

So, does anyone have any ideas or suggestions? I'm at work right now, so I can't post any logs but will be happy to do so later.

Thanks in advance,
~Dan

---

### Post by daniel.pool on 2009-08-18
I just thought that I'd post an update on progress. I removed the 0.8.6ish cvs version and reinstalled the apt package. Using a suggestion that I found in the launchpad bugs section I added some extra codes. Unfortunately whilst this did help it didn't fix everything. Irw is now registering the MOUSE_S keypress, but not reliably.

I'm now trying a slightly different approach and trying to get my imon it reciever to use a harmony remote configured as either an xbox remote or as an mce remote. I'm not having any luck though as no keys are being registered in ire :-( Has anyone got any experience of trying something similar?

---

### Post by daniel.pool on 2009-08-19
Just to close this off, Eldis helped me out with a fix in [this thread]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=7813441&postcount=90").

I've gone with the 0.8.4a package from apt-get rather than the latest cvs build. Dunno why the cvs code isn't working but meh, if it ain't broke ...

I've got the Harmony being an iMon remote and it generally seems to be OK. I'm going to have to play with the timings to get it perfect. The shame is that I preferred the Harmony layout for the MCE remote ... why I don't get to choose what/where the soft buttons on this remote goes I don't know.

Oh well; thread closed :-)

---

### Post by l2e on 2009-08-20
Daniel, I have been down the same road as you with the ffdc model using MCE remote.  I went as far as getting help from an LIRC developer.  Come to find out that some ffdc models will NOT work with the MCE remote no matter what you do.  We came to this conclusion after a few days of constant back and forth emails.  My suggestion is either live with the Harmony emulating iMON or get an MCE usb dongle and have the Harmony emulate the MCE remote.  Just for the record, I am doing the MCE usb dongle as the iMON has custom timings that the Harmony can't emulate properly.

---

### Post by daniel.pool on 2009-08-22
Hey,

I'm beginning to find that the imon & harmony combo aren't all that accurate :( A lot of the time button presses come through with the same code as other buttons. Very annoying.

I'm considering getting an MCE USB dongle as advised ... I've also seen the OrigenAE cases come with the MCE USB built in ... now if only I could convince my wife we needed one of those :)

~Dan

---

### Post by WolverineFan on 2009-09-01
If you're running Jaunty you might want to look at my LIRC 0.8.6 pre-release package.

Instructions are at the top of this page:
[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

There have been a LOT of improvements for the iMON devices recently.

Feel free to PM me with any questions/issues!

---

### Post by lindend on 2009-09-10
> **WolverineFan said:**
> If you're running Jaunty you might want to look at my LIRC 0.8.6 pre-release package.

I'm trying to use your pre-release package and am having some problems:

My system is a Thermaltake DH 202 which gets identified as a 15c2:0038 device.  I used dpkg-reconfigure to set the system up as a Soundgraph iMON IR/LCD with no IR repeater.

I can get the mouse portion of the PAD remote control to work, but nothing else will work.

My active devices are:

crw-rw---- 1 root root 61, 0 2009-09-10 22:52 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-09-10 22:52 /dev/lircd

Here are my initial questions:

1. Based on some google searches I've done, shouldn't there be a lirc1 also where the non-mouse events are processed or has this changed in the latest lirc?

2. I'm not convinced that the appropriate lirc_imon.ko module is loading.

The package seems to have installed a kernel module here:

-rw-r--r-- 1 root root 44956 2009-09-10 22:24 ./2.6.28-15-generic/updates/dkms/lirc_imon.ko

but I wonder if the lirc module is actually loading from here:

-rw-r--r-- 1 root root 30292 2009-09-10 21:33 ./2.6.28-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko

Thanks for any help you can provide.

---

### Post by WolverineFan on 2009-09-11
> **lindend said:**
> My system is a Thermaltake DH 202 which gets identified as a 15c2:0038 device.  I used dpkg-reconfigure to set the system up as a Soundgraph iMON IR/LCD with no IR repeater.

That should work.  I'd recommend using the iMON PAD selection (yeah, it's not very clear, but that's the kind of remote you're probably using).  I'm pretty sure the PAD selection also enables the volume knob.

> **lindend said:**
> 
I can get the mouse portion of the PAD remote control to work, but nothing else will work.

My active devices are:

crw-rw---- 1 root root 61, 0 2009-09-10 22:52 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-09-10 22:52 /dev/lircd


That all looks great.

> **lindend said:**
> 
1. Based on some google searches I've done, shouldn't there be a lirc1 also where the non-mouse events are processed or has this changed in the latest lirc?


Merging the two devices into one was one of the biggest features of the 0.8.6 release.  This simplifies configuration IMMENSELY and makes most iMON devices work out of the box rather than having to chain lircd processes together like you used to.

> **lindend said:**
> 
2. I'm not convinced that the appropriate lirc_imon.ko module is loading.

The package seems to have installed a kernel module here:

-rw-r--r-- 1 root root 44956 2009-09-10 22:24 ./2.6.28-15-generic/updates/dkms/lirc_imon.ko

but I wonder if the lirc module is actually loading from here:

-rw-r--r-- 1 root root 30292 2009-09-10 21:33 ./2.6.28-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko

Thanks for any help you can provide.

DKMS automatically prepends the updates/dkms path when it compiles new kernel modules.  If it weren't loading the lirc_imon.ko module your mouse wouldn't work.

I suspect the problem you're having is the one that everyone seems to have with lirc:  Every application needs to be configured to recognize it.  For things like XBMC they're already written to use LIRC if it's there, but you have to create a custom config file that tells the program what button corresponds to what action.  Then there are the applications that don't recognize LIRC natively.  Those you can control with lircrcd.

Unfortunately, application configuration is something I'm new at as well, and I haven't really found any great guides.  About all I can tell is that it's a pain to get working but once it's configured it works well...  I suggest googling for the application and lirc, so: xbmc lirc

Good luck and if you have any more problems let me know!

---

### Post by lindend on 2009-09-11
> **WolverineFan said:**
> That should work.  I'd recommend using the iMON PAD selection (yeah, it's not very clear, but that's the kind of remote you're probably using). 

My ultimate goal is to use a Harmony remote.  I'm only using the iMon PAD controller temporarily until I know everything is functional and then I'll switch over the Harmony (which will emulate the iMon remote).

Since the Harmony can emulate either iMon or MCE remotes, what iMON device would you recommend?

My second goal is to get the LCD working with lcdproc.  If I choose iMON PAD selection, will I be able to control the LCD too?


> **WolverineFan said:**
> Merging the two devices into one was one of the biggest features of the 0.8.6 release.  This simplifies configuration IMMENSELY and makes most iMON devices work out of the box rather than having to chain lircd processes together like you used to.

Thanks for the info.  That concern appears to be a non-issue.

The module concern also is a non-issue based on your details.


> **WolverineFan said:**
> I suspect the problem you're having is the one that everyone seems to have with lirc:  Every application needs to be configured to recognize it. 

Not so sure that application lirc configuration is my root cause.  I have some more background info that I should have provided you:

These the primary applications I use/want to work.

1. XBMC
2. Boxee
3. MythTV

On this same system, I previously had an MCE remote working (with USB IR receiver) with all three apps so I know they are lirc enabled and they function in my setup with lirc is properly configured.

However, I'd prefer to dump the excess USB IR receiver and use the one provided by the case (hence my iMon investigation).

I did previously try the iMON PAD option with MythTV but it didn't work.  I didn't try XBMC or Boxee with the iMON PAD option because I assumed that if MythTV didn't work, they wouldn't work either, but I'll retry XBMC first based on your recommendation.

---

### Post by WolverineFan on 2009-09-11
> **lindend said:**
> My ultimate goal is to use a Harmony remote.  I'm only using the iMon PAD controller temporarily until I know everything is functional and then I'll switch over the Harmony (which will emulate the iMon remote).

Since the Harmony can emulate either iMon or MCE remotes, what iMON device would you recommend?

I think the iMON PAD is still the way to go since the Harmony can emulate it.

> **lindend said:**
> My second goal is to get the LCD working with lcdproc.  If I choose iMON PAD selection, will I be able to control the LCD too?

Yes.  All the soundgraph imon selections use the same driver (which is what LCDProc needs).  The only real difference between them is the remote control config file it loads.

> **lindend said:**
> 
Not so sure that application lirc configuration is my root cause.  I have some more background info that I should have provided you:

These the primary applications I use/want to work.

1. XBMC
2. Boxee
3. MythTV

On this same system, I previously had an MCE remote working (with USB IR receiver) with all three apps so I know they are lirc enabled and they function in my setup with lirc is properly configured.

However, I'd prefer to dump the excess USB IR receiver and use the one provided by the case (hence my iMon investigation).

I did previously try the iMON PAD option with MythTV but it didn't work.  I didn't try XBMC or Boxee with the iMON PAD option because I assumed that if MythTV didn't work, they wouldn't work either, but I'll retry XBMC first based on your recommendation.

In the case of XBMC/Boxee (and probably Mythtv as well) the remote control config file, Lircmap.xml, has the name of the LIRC remote in it.  So the section that your MCE remote uses won't be recognized for the iMON remote.

Confusing, I know.  I found a working Lircmap.xml with an iMON section here:
[http://blog.xbmc.org/forum/showthread.php?p=247519#post247519](http://blog.xbmc.org/forum/showthread.php?p=247519#post247519)

That thread probably has other useful info too.

If you get it all working, let me know.  I still have to finish configuring my own machine ;-)

---

### Post by lindend on 2009-09-11
> **WolverineFan said:**
> 
If you get it all working, let me know.  I still have to finish configuring my own machine ;-)

The combo of the PAD and the Lircmap.xml file have both boxee and XBMC working!:D

I still have a lot of tweaking to do with the key mapping, but I will post all of those details when I'm finished.

Thanks so much for your help!

---

### Post by wombo on 2009-09-13
WolverineFan,

How far off do you expect the 0.8.6 release? or is it possible to get the pre-release now via apt-get?

Thanks

---

### Post by lindend on 2009-09-13
> **WolverineFan said:**
> In the case of XBMC/Boxee (and probably Mythtv as well) the remote control config file, Lircmap.xml, has the name of the LIRC remote in it.  So the section that your MCE remote uses won't be recognized for the iMON remote.


I have Boxee/XBMC working quite nicely, but MythTV is still a mess.  


[LIST=1]
[*]It seems to ignore all keys except Ch+/Ch- which get mapped to the Up/Down keys.
[*]I can't control key repeats when using the Harmony remote (the original iMon PAD remote doesn't repeat).
[/LIST]
 For #1, the docs say that the lircrc file in my home directory contains the key mapping and here are some highlights.

```

begin
    remote = iMON-PAD
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch+
    config = Up
    repeat = 0
    delay = 0
end


```and these are the settings in my lircd.conf.  The up/down/left/right appear to be defined twice.  Any idea why they are there twice and could this be causing an issue in MythTV while XBMC and Boxee are ok with the same settings?

```

begin remote

  name     iMON-PAD


# Corrin added
          Space                    0x2B9B15F700002401
          Up                       0xEB53F9B700002401
          Left                     0x6ABAFFBF00002401
          Down                     0x6F9ECBB700002401
          Right                    0x69A281B700002401
# Variants and additions of keys reported by Ryan Gardner
          1                        0x0200001E00000000
          2                        0x0200001F00000000
          3                        0x0200002000000000
          4                        0x0200002100000000
          5                        0x0200002200000000
          6                        0x0200002300000000
          7                        0x0200002400000000
          8                        0x0200002500000000
          9                        0x0200002600000000
          Star                     0x0220002500000000
          0                        0x0200002700000000
          Hash                     0x0220002000000000
          Backspace                0x0200002A00000000
          Select                   0x0200002C00000000
          LeftMenu                 0x0280000000000000
          RightMenu                0x0200006500000000
          Enter                    0x0200002800000000
          Escape                   0x0200002900000000
          LeftClick                0x0101000000000000
          RightClick               0x0102000000000000
          Up                       0x0100800000000000
          Down                     0x01007F0000000000
          Left                     0x0100008000000000
          Right                    0x0100007F00000000

```For #2, the delay and repeat settings don't seem to help.  Any pointers of what to investigate would be appreciated.

---

### Post by WolverineFan on 2009-09-13
> **wombo said:**
> WolverineFan,

How far off do you expect the 0.8.6 release? or is it possible to get the pre-release now via apt-get?

Thanks

Looks like 0.8.6 was released this morning!  Yay!  I'll update my package to 0.8.6.  You can follow the instructions here:

[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

To install the package from my Personal Package Archive (PPA) for now.  When I get the package upgraded to 0.8.6 RELEASE it'll show up automatically in UpdateManager.  Also, when 0.8.6 is updated in the Ubuntu repository it will automatically override my package.  So you shouldn't have any problems.  I hope.

I'm working with the current Ubuntu LIRC maintainer to get the Ubuntu package updated with my changes.

---

### Post by WolverineFan on 2009-09-13
> **lindend said:**
> I have Boxee/XBMC working quite nicely, but MythTV is still a mess.  


1. It seems to ignore all keys except Ch+/Ch- which get mapped to the Up/Down keys.


I've never tried to set up Mythtv so hopefully someone more knowledgeable will chime in here :-)

I found the following on Mythtv and LIRC:
[http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)

Which seems to indicate that Mythtv looks for ~/.mythtv/lircrc then ~/.lircrc 

It's possible (though it doesn't seem likely) that one of two things is happening:
1. The file is named wrong
2. LIRC isn't properly detecting that a client has started reading /dev/lircd and isn't switching the device into "keyboard" mode (the PAD remote has a toggle keyboard/mouse button for the wheel section).  If this is the case, keys like 1-9, play, stop, pause should all be useable, just not the wheel.

Your config looks fine to my novice eyes.  I'd try changing up/down to "Play" and "Pause" just to see if other buttons are working besides ch+-.


> **lindend said:**
> 
these are the settings in my lircd.conf.  The up/down/left/right appear to be defined twice.  Any idea why they are there twice and could this be causing an issue in MythTV while XBMC and Boxee are ok with the same settings?


This file seems truncated.  The default file in /usr/share/lirc/remotes/imon/lircd.conf.imon-pad has a lot more codes listed.  The reason for all the duplicates is that different versions of the remote/device issue different codes.  As long as each CODE is only mentioned once in the file everything is fine.  LIRC has no problem with multiple codes defined for the same button.  LIRC basically just scans the file from top to bottom when it gets a code, and returns the first button name that matches.


> **lindend said:**
> 
2. I can't control key repeats when using the Harmony remote (the original iMon PAD remote doesn't repeat).

For #2, the delay and repeat settings don't seem to help.  Any pointers of what to investigate would be appreciated.
[/QUOTE]

Repeats are one of the issues I've heard people have with Harmony remotes. The iMON PAD remote does repeat, but it seems to do it differently.  I'm pretty sure there are some lirc_imon.ko settings you can define to modify the behavior of the driver so that it handles your Harmony remote better, but I don't have a Harmony so I haven't paid that close attention to the discussions.

I'd try looking over the LIRC mailing list archives for Harmony remotes.  Just the last 3 months worth (since the IMON driver is a whole new animal since 0.8.5).

Mailing list archives are here:
[http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list](http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list)

(which is timing out for me at the moment, but hopefully it'll be back up soon).

Good luck!

---

### Post by lindend on 2009-09-13
> **WolverineFan said:**
> 
Which seems to indicate that Mythtv looks for ~/.mythtv/lircrc then ~/.lircrc 

 ~/.lirc contains the following:

```


include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa


```and ~/.lirc/mythtv is the file I posted highlights of (note: its a partial dump of the file with the problem areas highlighted).

> **WolverineFan said:**
> Your config looks fine to my novice eyes.  I'd try changing up/down to "Play" and "Pause" just to see if other buttons are working besides ch+-. 

They don't work either.




> **WolverineFan said:**
> This file seems truncated. 

I only posted highlights of the file's contents, sorry for not being clearer.  Given your explanation, this isn't the issue.




> **WolverineFan said:**
> I'd try looking over the LIRC mailing list archives for Harmony remotes.  Just the last 3 months worth (since the IMON driver is a whole new animal since 0.8.5).

Mailing list archives are here:
[http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list](http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list)

(which is timing out for me at the moment, but hopefully it'll be back up soon).

Will do.  I currently have the Harmony generating 3 repeats for XBMC/Boxee but this is obviously upsetting MythTV.  I'm going to try to eliminate the repeats and see if MythTV works.  Since I use XBMC/Boxee more, I need to find a solution for all apps.

---

### Post by WolverineFan on 2009-09-14
> **lindend said:**
> ~/.lirc contains the following:

```


include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa


```and ~/.lirc/mythtv is the file I posted highlights of (note: its a partial dump of the file with the problem areas highlighted).


Cool!  Did you create all those yourself or did you find them somewhere?  I'd like a copy :)

> **lindend said:**
> 
They don't work either.


Bummer.  I didn't have much hope it would help, but I was crossing my fingers...

I guess the mailing list is your best bet at this point.

---

### Post by lindend on 2009-09-14
> **WolverineFan said:**
> Cool!  Did you create all those yourself or did you find them somewhere?  I'd like a copy :)

They were generated automatically by the mythbuntu control center when I confgiured the imon PAD remote control.  I haven't tried them get with my imon remote, but I'll do so tonight with vlc and see if this maybe some bad info from the the mythbuntu control center.

Assuming this works, I can email them to you.  Drop me a PM with your email address if you want them.

---

### Post by lindend on 2009-09-14
> **WolverineFan said:**
>  Bummer.  I didn't have much hope it would help, but I was crossing my fingers....

vlc is broken just like mythtv.  This causes my to wonder if something isn't misconfigured in my system.

When I execute irexec, I get this output:

```

sudo irexec
irexec: could not connect to socket
irexec: No such file or directory

```Google search indicates that this may be caused by a mix of the cvs lirc which I compiled and the stock ubuntu irexec.  The link said its due to a socket change from /var/run/lirc/lircd to /dev/lircd.  Sure enough, irw without any parameters doesn't work but if I force it to use /dev/lircd, things work nicely.

Could this be an explanation for the problems I've encountered?

---

### Post by WolverineFan on 2009-09-15
> **lindend said:**
> vlc is broken just like mythtv.  This causes my to wonder if something isn't misconfigured in my system.

When I execute irexec, I get this output:

```

sudo irexec
irexec: could not connect to socket
irexec: No such file or directory

```Google search indicates that this may be caused by a mix of the cvs lirc which I compiled and the stock ubuntu irexec.  The link said its due to a socket change from /var/run/lirc/lircd to /dev/lircd.  Sure enough, irw without any parameters doesn't work but if I force it to use /dev/lircd, things work nicely.

Could this be an explanation for the problems I've encountered?

Doh!

Yes, that's exactly what the problem with irexec/irw is.  Sorry I didn't mention this sooner, someone else complained about this and I haven't had a chance to fix it yet.

It shouldn't be affecting mythtv though.  One of the reasons why I have it creating /dev/lircd instead of /var/run/lirc/lircd is that most of the client programs are still expecting /dev/lircd.

I just had a thought as I was composing this message though. If I let lirc create /var/run/lirc/lircd and then I create a symlink to it called /dev/lircd that might just make everything happy. I'll give that a shot right now and see what happens.  If it works, I'll include that fix in my 0.8.6 release later today.

---

### Post by lindend on 2009-09-15
> **WolverineFan said:**
> 
I just had a thought as I was composing this message though. If I let lirc create /var/run/lirc/lircd and then I create a symlink to it called /dev/lircd that might just make everything happy. I'll give that a shot right now and see what happens.  If it works, I'll include that fix in my 0.8.6 release later today.

I had a similar thought last night, but it was late and I forgot to try it before I left this morning.  I will try manually creating a symlink and see what that resolves.

---

### Post by lindend on 2009-09-15
> **WolverineFan said:**
>  I'll include that fix in my 0.8.6 release later today.

Speaking of the 0.8.6. instructions, I have some questions regarding the use of lcdproc.  You indicate that your package eliminates the need to manually recompile things.  This is true for lirc, but I still had to manually recompile lcdproc with the imonlcd patches to get it to work.  Is manual recompilation of lcdproc still required?  If so, maybe the instructions on the page should indicate that you don't have to follow step 1, but either part 2 or part 3 are necessary.

Also, I'm finding that lots of options (i.e. Hello, ServerScreen = blank etc.) in the LCDd.conf don't do anything.  Are these options in 0.5.3 that aren't supported or is something broken in my config?

---

### Post by WolverineFan on 2009-09-15
> **WolverineFan said:**
> Doh!
I just had a thought as I was composing this message though. If I let lirc create /var/run/lirc/lircd and then I create a symlink to it called /dev/lircd that might just make everything happy. I'll give that a shot right now and see what happens.  If it works, I'll include that fix in my 0.8.6 release later today.

Yep, this seems to fix everything and make all clients happy.  Very cool.

I'm working on the changes now and hope to have an updated package in the next few hours if all goes well.

---

### Post by lindend on 2009-09-15
> **WolverineFan said:**
> Yep, this seems to fix everything and make all clients happy.  Very cool.

I'm working on the changes now and hope to have an updated package in the next few hours if all goes well.

I manually created the symlink and mythtv works!  Unfortunately, the symlink is lost in each boot cycle, so I'll have to wait for your updated package.

---

### Post by WolverineFan on 2009-09-15
> **lindend said:**
> Speaking of the 0.8.6. instructions, I have some questions regarding the use of lcdproc.  You indicate that your package eliminates the need to manually recompile things.  This is true for lirc, but I still had to manually recompile lcdproc with the imonlcd patches to get it to work.  Is manual recompilation of lcdproc still required?  If so, maybe the instructions on the page should indicate that you don't have to follow step 1, but either part 2 or part 3 are necessary.

Also, I'm finding that lots of options (i.e. Hello, ServerScreen = blank etc.) in the LCDd.conf don't do anything.  Are these options in 0.5.3 that aren't supported or is something broken in my config?

Huh.  I had hoped that LCDProc would just work after installing my package.  Honestly the LCD is such a low priority for me though that I haven't bothered to try it yet!  I'll give it a whack tonight.  Now that my 0.8.6 package is out the door (it's building now, so it'll probably show up in the next 15 minutes) I have more spare cycles to try this other fun stuff.

If necessary I'll create a PPA for LCDProc, but I really do hope it won't be necessary.

---

### Post by WolverineFan on 2009-09-16
Yep, lcdproc doesn't work.  I've just started looking, but I think lcdproc 0.5.3 (released 3 weeks ago, coincidentally) includes the imonlcd patch that used to be on codeka.  If it really does, and it works, I can probably come up with a 0.5.3-based Ubuntu package pretty quickly.  Then I can start contacting maintainers and get 0.5.3 into Karmic as well.

I should probably start working with the Debian maintainers while I'm at it and get these changes pushed upstream sooner than later.

Why can't anything just be easy?  :)

---

### Post by SammyC on 2009-09-16
The standard LIRC does work you just need to tell it not to autodetect the display type.

If you modinfo lirc_imon you get a list of options and one of them (can't remember which) forces the display to be the VFD, and then it works fine.

---

### Post by WolverineFan on 2009-09-17
> **SammyC said:**
> The standard LIRC does work you just need to tell it not to autodetect the display type.

If you modinfo lirc_imon you get a list of options and one of them (can't remember which) forces the display to be the VFD, and then it works fine.

I haven't tried this yet, but I did try creating an Ubuntu package based on LCDproc 0.5.3 and I get a swarm of errors in my syslog when I start LCDproc using the imonlcd driver.

I'll try the VFD thing tonight and see if it works with my LCD.  If so at least it's a temporary solution.

To try this, you can create a file /etc/modprobe.d/lirc-imon.conf with the contents:
```

options lirc_imon display_type=1

```

I think :)

---

### Post by SammyC on 2009-09-18
IIRC you defo don't use the lcd driver because it bombs out like you found. for the VFD you just use the normal imon driver but add that option to modprobe and bingo it works. :)

---

### Post by WolverineFan on 2009-09-18
I think my hardware might be defective (based on the very inconsistent errors I'm getting) rather than it being a configuration problem.

I've created an LCDproc 0.5.3 Ubuntu package and updated the Wiki page with installation instructions:
[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

Let me know if you try it and how it goes!  Check your /var/log/syslog after starting /etc/init.d/LCDd to see if you have errors.  I do, but I'm hoping it's just me.

You should NOT have to change the device to VFD from what I can tell.  It certainly doesn't help me.  I think LIRC 0.8.6 addressed that problem.

Good luck folks!

---

### Post by WolverineFan on 2009-09-18
> **WolverineFan said:**
> I've created an LCDproc 0.5.3 Ubuntu package and updated the Wiki page with installation instructions:
[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)


I may have jumped the gun slightly on the announcement.  Usually my new uploads build within 15 minutes but right now it says the estimated build time is 10 hours!  Sheesh.  So I guess it'll show up when it shows up.

If you're impatient, it should compile fine from source on 32bit Ubuntu.  64bit will probably fail due to the libirman.a library being compiled without -fPIC.  I'm curious to see how this works on the build machines actually.

---

### Post by lindend on 2009-09-21
WolverineFan,

I've updated to the new package and lirc isn't loading.  When the box first boots, lsusb shows a Soundgraph device, but none thereafter.

Here's the output of ls /dev/lir*

lrwxrwxrwx 1 root root   19 2009-09-21 22:51 /dev/lircd -> /var/run/lirc/lircd

Any ideas?

---

### Post by WolverineFan on 2009-09-22
> **lindend said:**
> WolverineFan,

I've updated to the new package and lirc isn't loading.  When the box first boots, lsusb shows a Soundgraph device, but none thereafter.

Here's the output of ls /dev/lir*

lrwxrwxrwx 1 root root   19 2009-09-21 22:51 /dev/lircd -> /var/run/lirc/lircd

Any ideas?

That's odd...  And it worked fine with the older package?

I guess first make sure that the version of lirc-modules-source is right:
dpkg-query -W '*lirc*'

At a minimum you should have 'lirc', 'lirc-modules-source' and 'liblircclient0' installed, all at version '0.8.6-0ubuntu1~ppa9' 

If that's working, what does modprobe -l 'lirc*' show you?  Most (not all) of the lirc modules should show up under 'updates/dkms' if everything is installed properly.

If any of that is wrong, just try re-installing the packages using Synaptic.

A shortcut to rebooting is:
```

sudo /etc/init.d/lirc stop
sudo modprobe -r lirc_imon
sudo /etc/init.d/lirc start

```

You can also look in /var/log/syslog to see if there are any interesting lirc lines.

---

### Post by lindend on 2009-09-22
> **WolverineFan said:**
> 

I guess first make sure that the version of lirc-modules-source is right:
dpkg-query -W '*lirc*'

Looks ok to me:

```

dpkg-query -W '*lirc*'
liblircclient0  0.8.6-0ubuntu1~ppa9
lirc    0.8.6-0ubuntu1~ppa9
lirc-modules-source     0.8.6-0ubuntu1~ppa9
lirc-x
mythbuntu-lirc-generator        0.21-0ubuntu1
pulseaudio-module-lirc


```
> **WolverineFan said:**
> If that's working, what does modprobe -l 'lirc*' show you? 

```

kernel/ubuntu/lirc/lirc_cmdir/lirc_cmdir.ko
kernel/ubuntu/lirc/lirc_mceusb2/lirc_mceusb2.ko
kernel/ubuntu/lirc/lirc_pvr150/lirc_pvr150.ko
kernel/ubuntu/lirc/lirc_serial_igor/lirc_serial_igor.ko
kernel/ubuntu/lirc/lirc_gpio/lirc_gpio.ko
updates/dkms/lirc_atiusb.ko
updates/dkms/lirc_streamzap.ko
updates/dkms/lirc_imon.ko
updates/dkms/lirc_sir.ko
updates/dkms/lirc_i2c.ko
updates/dkms/lirc_ite8709.ko
updates/dkms/lirc_bt829.ko
updates/dkms/lirc_sasem.ko
updates/dkms/lirc_dev.ko
updates/dkms/lirc_mceusb.ko
updates/dkms/lirc_igorplugusb.ko
updates/dkms/lirc_serial.ko
updates/dkms/lirc_ene0100.ko
updates/dkms/lirc_ttusbir.ko
updates/dkms/lirc_it87.ko

```
> **WolverineFan said:**
> If any of that is wrong, just try re-installing the packages using Synaptic.

I did try to reinstall, but it just said I had the latest version.  If I uninstall and then reinstall, will I lose all my settings?

> **WolverineFan said:**
> You can also look in /var/log/syslog to see if there are any interesting lirc lines.

```

Sep 22 06:27:12 lindend-desktop kernel: [   75.241375] lirc_dev: IR Remote Control driver registered, major 61
Sep 22 06:27:12 lindend-desktop kernel: [   75.263527] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Sep 22 06:27:12 lindend-desktop kernel: [   75.263545] usbcore: registered new interface driver lirc_imon

```

---

### Post by WolverineFan on 2009-09-22
> **lindend said:**
> Looks ok to me:


Yep, that all looks good.

> **lindend said:**
> I did try to reinstall, but it just said I had the latest version.  If I uninstall and then reinstall, will I lose all my settings?


Since Myth has a dependency on LIRC you can't uninstall without a lot of headaches.  I'm not in front of my machine right now, so I don't know why Synaptic didn't do the right thing.  

Since it looks like you have everything you're supposed to have, I don't know if a reinstall is going to help.  If you're worried about settings, the only settings the lirc packages modify are in /etc/lirc so you can just back up that directory before you try anything.

It's POSSIBLE that somehow your settings files got corrupted.  If so, running 'dpkg-reconfigure lirc' will walk you through the setup process again.

Another option is to reinstall using Aptitude:
```

sudo -H aptitude
/lirc<enter> - search for the string lirc
n - next, until you find the lirc packages
L - mark each package for reinstall
g - make sure the list of actions is what you expect
g - do the reinstall

```

> **lindend said:**
> 
```

Sep 22 06:27:12 lindend-desktop kernel: [   75.241375] lirc_dev: IR Remote Control driver registered, major 61
Sep 22 06:27:12 lindend-desktop kernel: [   75.263527] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Sep 22 06:27:12 lindend-desktop kernel: [   75.263545] usbcore: registered new interface driver lirc_imon

```

That looks a little sparse. Here's what I have:

```

Sep 22 11:14:23 mediapc kernel: [314558.871263] lirc_dev: IR Remote Control driver registered, major 61
Sep 22 11:14:23 mediapc kernel: [314558.876618] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Sep 22 11:14:23 mediapc kernel: [314558.876664] lirc_dev: lirc_register_driver: sample_rate: 0
Sep 22 11:14:23 mediapc kernel: [314558.877201] lirc_imon: Registered iMON driver (lirc minor: 0)
Sep 22 11:14:23 mediapc kernel: [314558.878112] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input7
Sep 22 11:14:23 mediapc kernel: [314558.916082] lirc_imon: iMON device (15c2:0038, intf0) on usb<6:2> initialized
Sep 22 11:14:23 mediapc kernel: [314558.918085] lirc_imon: iMON device (15c2:0038, intf1) on usb<6:2> initialized
Sep 22 11:14:23 mediapc kernel: [314558.918141] usbcore: registered new interface driver lirc_imon

```

My output might be a bit more verbose since I may have turned on the debug flag.  Not sure.

---

### Post by lindend on 2009-09-22
> **WolverineFan said:**
>  It's POSSIBLE that somehow your settings files got corrupted.  If so, running 'dpkg-reconfigure lirc' will walk you through the setup process again.

I did that yesterday and unfortunately, it didn't help.

Is this line still valid in /etc/lirc/hardware.conf or has the device changed locations in this revision?

```

REMOTE_DEVICE="/dev/lirc0"

```> That looks a little sparse. Here's what I have:I suppose that my board could have spontaneously gone bad just when the upgrade occurred, but that seems doubtful.  I am still concerned that lsusb only shows the soundgraph device initially at boot, and then never again.  Are you sure this isn't a problem or should this happen when the new lirc module loads?

There is one data point I forgot to mention.  For reasons still unknown, when I came home yesterday, the updater had updated a variety of applications (mythtv, lirc, etc.) on its own and my root partition was full.  After clearing some space, I don't see any side effects (other than lirc), but its possible that the official 0.8.6 lirc may  not have been installed correctly.

---

### Post by WolverineFan on 2009-09-22
> **lindend said:**
> I did that yesterday and unfortunately, it didn't help.

Is this line still valid in /etc/lirc/hardware.conf or has the device changed locations in this revision?

```

REMOTE_DEVICE="/dev/lirc0"

```


No, that hasn't changed.  Just the socket location.

> **lindend said:**
> I suppose that my board could have spontaneously gone bad just when the upgrade occurred, but that seems doubtful.  I am still concerned that lsusb only shows the soundgraph device initially at boot, and then never again.  Are you sure this isn't a problem or should this happen when the new lirc module loads?

I admit, that's odd.

> **lindend said:**
> There is one data point I forgot to mention.  For reasons still unknown, when I came home yesterday, the updater had updated a variety of applications (mythtv, lirc, etc.) on its own and my root partition was full.  After clearing some space, I don't see any side effects (other than lirc), but its possible that the official 0.8.6 lirc may  not have been installed correctly.

Ok, that sucks.  I had a similar thing happen and I still have a few whacky Boxee problems.  I've been waiting for 9.10 to just reinstall.

So, if you want to try some more heavy debugging, try this:
```

sudo mount -t usbfs none /proc/bus/usb
less /proc/bus/usb/devices

```

You'll be looking for your soundgraph device, which should have a  Vendor=15c2 line.  Look at the I: lines in that block and see what Driver= shows.  When things are working, it shows Driver=lirc_imon.  Sometimes other drivers can take control of the device and cause problems.

If you don't see your soundgraph device at all, that could be a hardware problem.

To verify your installed package, you could try running debsums:

```

sudo apt-get install debsums
sudo debsums -c > /tmp/debsums.out 2>/tmp/debsums.err

```

The "err" file will contain a list of packages that didn't have MD5 signatures on files (probably safe to ignore).  The "out" file will list a ton of ".desktop" files (at least mine does) and anything else where the file checksums don't match the debian packages.

---

### Post by lindend on 2009-09-23
> **WolverineFan said:**
> 
If you don't see your soundgraph device at all, that could be a hardware problem.

I know the odds are astronomical, but it appears as if the hardware went bad simultaneously with the upgrade to 0.8.6 (there's no way the software could have done it right?).  My guess, this is why/how my root partition was full--too many error messages and logs filling up.

Are there any lower level utilities beyond /proc/bus/usb that might see if the hardware is visible/usable?  I can still RMA the iMon SoundGraph LCD/IR Receiver but I don't want to do it before I conclusively prove the hardware has gone bad (and unfortunately, I don't have a copy of Windows to rule out a software fault in Ubuntu).

---

### Post by WolverineFan on 2009-09-23
> **lindend said:**
> I know the odds are astronomical, but it appears as if the hardware went bad simultaneously with the upgrade to 0.8.6 (there's no way the software could have done it right?).  My guess, this is why/how my root partition was full--too many error messages and logs filling up.

Are there any lower level utilities beyond /proc/bus/usb that might see if the hardware is visible/usable?  I can still RMA the iMon SoundGraph LCD/IR Receiver but I don't want to do it before I conclusively prove the hardware has gone bad (and unfortunately, I don't have a copy of Windows to rule out a software fault in Ubuntu).

So sorry to hear that.  I'm sure there are other diagnostic tools available, but I don't know what they might be.

Ideas I have off the top of my head, in order of pain:
1. Turn off the computer and unplug it for a few minutes, then try again.
2. Plug the LCD/receiver into a different USB port
3. Fresh install of Ubuntu and a fresh install of my packages on top (easiest with a small blank hard disk)
4. Windoze... But you already ruled that out

Beyond that, google or maybe a new thread on the forums about USB hardware detection are probably your best bets.

Good luck!

Out of curiosity, had you installed LCDproc yet and gotten it working?  I ask because my LCD turned out not to work very well with the imonlcd driver and I came up with a patch that fixed it.  Without the patch, LCDd was flooding my syslog with errors a hundred times a second...  I could see how that could damage the component after a few days.

I've been swamped and haven't had a chance to fix my lcdproc package yet, but that was one of the things I was going to put in it.

---

### Post by machtok on 2009-10-06
Hi,

I Get exactly the same problem as Lindend. 
I upgraded my MythBuntu box from 8.10 to 9.04 and installed your packages for lirc.
Only get the pad in mouse mode doing something. The hardware shloud be ok as 2 days before it was working with 8.10 (at this time I was using lirc 0.83 with the methodology described here: 
[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)).

here are some datas:
```

$lsusb :
Bus 005 Device 002: ID 15c2:0038 SoundGraph Inc.

```-> the imon LCD
```

$lsmod |grep lirc
lirc_imon              37444  0 
lirc_dev               21320  1 lirc_imon

```-> module is loaded
```

$ls /dev/lirc*
/dev/lirc0  /dev/lircd

```-> device created
```

$ls /var/run/lirc/
lircd  lircd.pid

```-> socket ok
```

 $ /etc/init.d/lirc restart

 * Stopping remote control daemon(s): LIRC                                                                                                        [ OK ] 
 * Loading LIRC modules                                                                                                                           [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                                                                       [ OK ] 

```Then I try to get some data with mode2:
```

$ mode2 -d /var/run/lirc/lircd
^C
 
```=> Playing with the remote control nothing appears....

The same thing with irw

And to finish the syslog seems ok:

```

Oct  6 18:22:26 machtok-htpc kernel: [ 3038.555526] lirc_dev: IR Remote Control driver registered, major 61 
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.564816] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.564886] lirc_dev: lirc_register_driver: sample_rate: 0
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.564999] lirc_imon: Registered iMON driver (lirc minor: 0)
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.565112] input: iMON PAD IR Mouse (15c2:0038) as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input10
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.599893] lirc_imon: iMON device (15c2:0038, intf0) on usb<5:2> initialized
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.601883] lirc_imon: iMON device (15c2:0038, intf1) on usb<5:2> initialized
Oct  6 18:22:26 machtok-htpc kernel: [ 3038.601958] usbcore: registered new interface driver lirc_imon
Oct  6 18:22:26 machtok-htpc lircd-0.8.6[13718]: lircd(default) ready, using /var/run/lirc/lircd
Oct  6 18:24:34 machtok-htpc lircd-0.8.6[13718]: accepted new client on /var/run/lirc/lircd
Oct  6 18:24:34 machtok-htpc kernel: [ 3166.358284] lirc_imon: IR port opened
Oct  6 18:24:45 machtok-htpc lircd-0.8.6[13718]: removed client
Oct  6 18:24:45 machtok-htpc kernel: [ 3177.790799] lirc_imon: IR port closed


```So it seems that we are several to have the same issue ...

---

### Post by WolverineFan on 2009-10-06
> **machtok said:**
> Hi,

I Get exactly the same problem as Lindend. 
I upgraded my MythBuntu box from 8.10 to 9.04 and installed your packages for lirc.
Only get the pad in mouse mode doing something. The hardware shloud be ok as 2 days before it was working with 8.10 (at this time I was using lirc 0.83

Couple questions:
1. Did you install the lirc_modules_source package?  You need that.
2. Have you rebooted since you installed lirc_modules_source?

I'm not sure which problem of Lindend's you're referring to (the latest being his hardware failed and no longer shows up in lsusb) so I'm hoping it's just the initial problem of not having the kernel drivers installed.

---

### Post by machtok on 2009-10-06
Maybe, I was to fast saying that I have the same problem as lindend... I re-read the thread carefully. What is similar is the problem reported in the first post 
> I can get the mouse portion of the PAD remote control to work, but nothing else will work.Otherwise I have installed your packages :
lirc lirc-module-source 
and rebooted after.

And the followong command seems to show that the good driver is is loaded for imon:

```

$less /proc/bus/usb/devices

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0038 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```For the moment I am only focusing on lirc not lcdproc

---

### Post by WolverineFan on 2009-10-06
> **machtok said:**
> Maybe, I was to fast saying that I have the same problem as lindend... I re-read the thread carefully. What is similar is the problem reported in the first post 


You're not the only one guilty of reading too fast.  You said you had the mouse pad working in the first message and I missed that :)

That means everything is fine as far as lirc goes (and my modules).

The rest is LIRC configuration, which is a pain.  It completely depends on the application(s) you want to control.  I presume Boxee/XBMC/Mythtv/VLC are the type of apps you want to control.  You can read through the earlier posts in this thread for help on getting those working (including some sample control files for XBMC/Boxee and a pointer to a tool for MythTV).

Another useful hint:  Google for "lirc <application>", e.g. "lirc boxee"

If you have some existing control files you might need to change your remote lines to
remote = iMON-PAD

Personally I JUST managed to get VLC working to my satisfaction 4 days ago...  So believe me when I say it's a pain :)

Good luck!

---

### Post by machtok on 2009-10-07
You were right, the module seems to work perfectly.
In fact I was misleaded by the fact that mode2 -d /var/run/lirc/lircd was not giving any output; it seems that the lircd daemon needs to be shutdown and mode2 connected to /dev/lirc0 in order to have it (mode2) outputting something.
Tried that this morning and it gives beautiful remote control codes :P

My goal is mainly to configure mythtv with the remote which should not be to difficult has I already managed to get it working with ubuntu 8.10 . I hope ....
And thank you for the packages, I remember the pain it was to patch/compile/configure the lirc 0.83 to get the remote working

---

### Post by WolverineFan on 2009-10-07
> **machtok said:**
> You were right, the module seems to work perfectly.
In fact I was misleaded by the fact that mode2 -d /var/run/lirc/lircd was not giving any output; it seems that the lircd daemon needs to be shutdown and mode2 connected to /dev/lirc0 in order to have it (mode2) outputting something.
Tried that this morning and it gives beautiful remote control codes :P

See, that should have been my second clue...  All you should have had to run to test is "irw".  Sorry I botched my advice so badly :oops:

> **machtok said:**
> My goal is mainly to configure mythtv with the remote which should not be to difficult has I already managed to get it working with ubuntu 8.10 . I hope ....
And thank you for the packages, I remember the pain it was to patch/compile/configure the lirc 0.83 to get the remote working

You're welcome.  The pain was why I did it.  I had 2 machines to get LIRC working on, and it was just too much bother to compile it manually twice.  So instead I spent 3 weeks working on a package.  I'm crazy like that.  :)

Good news:  My package has been nominated to get into Karmic.  I don't honestly understand the whole process, but I hope it makes it.

---

### Post by lindend on 2009-10-08
> **WolverineFan said:**
>  Beyond that, google or maybe a new thread on the forums about USB hardware detection are probably your best bets.

Got my rma replacement iMon today and lirc is working once again.  :popcorn:

> **WolverineFan said:**
>   Out of curiosity, had you installed LCDproc yet and gotten it working? 

The old lcdproc is working.  I will try the new one, but unfortunately for me, my HDMI audio stopped working after one of the Ubuntu packages updated (not sure which one at this point).  After I get audio working again, I'll take a look at lcdproc.

It is very frustrating that I can't keep my HTPC in a functional state due to a crazy number of unlikely occurrences. :confused:

---

### Post by machtok on 2009-10-10
Thanks for help, the remote works again (with mythtv)!
I have the remote Veris rm200. for the people interested, the conf file can be found at:
[http://lirc.sourceforge.net/remotes/imon/lircd.conf.imon-antec-veris](http://lirc.sourceforge.net/remotes/imon/lircd.conf.imon-antec-veris)
and below the conf for mythtv located at ~/.lirc/mythtv:

```


begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 3
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 3
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 3
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 3
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 3
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Timer
    config = F8
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Go
    config = O
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Zoom
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_ENTER
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PREVIOUS
    config = Page Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_NEXT
    config = Page Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 3
    delay = 0
end




```I am now trying the LCDproc. I added your ppa path in the sources.list and updated but it still show me the official package:

```

$ apt-cache show lcdproc
Package: lcdproc
Priority: extra
Section: universe/utils
Installed-Size: 1144
Maintainer: Ubuntu MOTU Team <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jose Luis Tallon <jltallon@adv-solutions.net>
Architecture: amd64
Version: 0.5.2-0ubuntu2

```going to the ppa archive, it seems empty, Am I wrong or this package doesn't exist ?

---

### Post by WolverineFan on 2009-10-11
> **machtok said:**
> I am now trying the LCDproc. I added your ppa path in the sources.list and updated but it still show me the official package:

```

$ apt-cache show lcdproc
Package: lcdproc
Priority: extra
Section: universe/utils
Installed-Size: 1144
Maintainer: Ubuntu MOTU Team <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jose Luis Tallon <jltallon@adv-solutions.net>
Architecture: amd64
Version: 0.5.2-0ubuntu2

```going to the ppa archive, it seems empty, Am I wrong or this package doesn't exist ?

For reasons I haven't had time to investigate, the LCDproc package didn't build properly on the package build servers.  I might have some time today to investigate.

---

### Post by WolverineFan on 2009-10-11
> **WolverineFan said:**
> For reasons I haven't had time to investigate, the LCDproc package didn't build properly on the package build servers.  I might have some time today to investigate.

Ok, problem investigated...  There was a missing dependency.  I've uploaded a new version of the package which should build in a few hours.  We'll see how it goes.

EDIT:  The new version built fine.  This one includes my timer patch for older iMON LCDs

---

### Post by lindend on 2009-10-13
[Hulu desktop]("http://www.hulu.com/labs/hulu-desktop-linux") for Linux recently came out.  It works with lirc out of the box, but two changes are required to get it to work with lirc and imon devices.

the hardware.conf must be modified with this change:

```

REMOTE_LIRCD_ARGS="--release"

```and the .huludesktop file must be modified (these are my changes for my iMon device using a harmony remote--the repeat settings may not work for everyone)

```

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = iMON-PAD
lirc_release_suffix = _UP
lirc_repeat_threshold = 5
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = Enter
button_name_menu = Menu

```WolverineFan,

Any idea why they require lirc args to be release?

---

### Post by lindend on 2009-10-13
WolverineFan,

Another thing.  I had to tweak the lirc.conf.imon-pad file to get the Menu key to work on the remote (I got these values from another thread on the ubuntu forums).  Should these keys have worked or does my mod need to be added to your package? 

```

# Linden added
          MyDVD                    0x29A395B700000101
          Menu                     0x2BA395B700000101

```

---

### Post by lindend on 2009-11-29
WolverineFan,

My system recently updated to the latest Jaunty kernel.  Unfortunately, neither of your lirc packages will install with this new kernel.  This is the error I see:

```

sudo apt-get install lirc-modules-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lirc-modules-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lirc-modules-source (0.8.6-0ubuntu3~ppa2) ...
WARNING: /usr/lib/dkms/common.postinst does not exist.
WARNING: /usr/share/lirc-modules-source/postinst does not exist.
ERROR: DKMS version is too old and lirc-modules-source was not
built with legacy DKMS support.
You must either rebuild lirc-modules-source with legacy postinst
support or upgrade DKMS to a more current version.
dpkg: error processing lirc-modules-source (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Do I need to recompile the packages?

---

### Post by SammyC on 2009-11-30
I've got the same thing too, remote no workie now! :(

I'm assuming its something to do with the new kernel?

---

### Post by WolverineFan on 2009-11-30
> **lindend said:**
> WolverineFan,

Another thing.  I had to tweak the lirc.conf.imon-pad file to get the Menu key to work on the remote (I got these values from another thread on the ubuntu forums).  Should these keys have worked or does my mod need to be added to your package? 

```

# Linden added
          MyDVD                    0x29A395B700000101
          Menu                     0x2BA395B700000101

```

Not sure why I didn't get email about your last 2 posts Lindend (especially annoying since I discovered both things myself recently).  I'll see what I can do about getting the config file updated. It turns out getting the package into Karmic was the easier part...  Getting the Karmic packages updated is harder.

As for Huludesktop and why they require --repeat, I have no clue.  I'm just glad that --repeat doesn't break XBMC/Boxee :)

---

### Post by WolverineFan on 2009-11-30
> **SammyC said:**
> I've got the same thing too, remote no workie now! :(

I'm assuming its something to do with the new kernel?

I'm not running Jaunty anymore, so thanks for the heads-up!  I'll bump the PPA revision and re-submit (with Lindend's config file patch!) and see if that fixes the problem.  Odd problem tho :(  With all the hassle that Ubuntu is putting me through to get a small change to the LIRC module in Karmic released I'm shocked they'd send out a kernel/DKMS update that breaks DKMS.

I'll update this post with the new version has been uploaded.

---

### Post by SammyC on 2009-11-30
Many thanks WolverineFan, I'll let you know if it fixes the problem.

I'm assuming its these two lines that pin it down:
```

ERROR: DKMS version is too old and lirc-modules-source was not built with legacy DKMS support.
You must either rebuild lirc-modules-source with legacy postinst support or upgrade DKMS to a more current version.
```

---

### Post by SammyC on 2009-12-01
Ok, managed to fix this on my install. It s a bit involved but basically means going back to the previous version provided by WolverineFan.

Firstly I had to remove the broken lirc-modules-source package but any attempt to use aptitude to do this fail ... because it was broken. Not very helpful! So I did it manually by deleting the source from  /usr/src/lirc-0.8.6 and then the dpkg stuff for it in /var/lib/dpkg/info/.

I then did aptitude remove lirc-modules-source which should complain a bit but still complete. I think used dpkg directly to install the previous version that I still had in my apt cache:

/var/cache/apt/archives/lirc-modules-source_0.8.6-0ubuntu1~ppa9_all.deb

This installed fine for me and my remote is now working again.


For WolverineFan, I think the problem is in the latest build, there is a comment in the change log about changing the dkms scripts being used and I wonder if these have affected it somehow.

---

### Post by WolverineFan on 2009-12-01
@SammyC:  I don't think the dkms changes to the package are the cause of these new errors.  My bet is that simply removing DKMS and re-installing lirc-modules-source from scratch is what fixed the problem (no matter what version you install).

So, I'm still hopeful that a simple update to a new version number will get everyone working again.  To that end, I've uploaded ~ppa4 (3 was mistakenly compiled just for Karmic...  Oops).

**NEWS:**  I'm attempting to release for Hardy/Jaunty/Karmic this time.  Mainly because I want to use my own PPA and I'm running Karmic now :)  I'm queued up for an hour waiting for a build, but if all goes well it should be available on all 3 releases soon.

Thanks for your patience folks!

Oh, and if this does work for all 3 releases, I'm planning to incorporate a few patches in the current CVS and possibly a new driver for Hauppauge folks (who are having lots of problems with the Karmic kernel)

**EDIT:** Sheesh that's more complicated than it needs to be :)  Ok, so the final version that worked is ~ppa5~jaunty1 (or whatever your flavor is).  Let me know if you update to this version and it doesn't fix the kernel modules!!
E

---

### Post by SammyC on 2009-12-02
I have no plans to try this at the moment seeing as all is working again for me, the WAF needs to recover a bit before I start fiddling again! :)

---

### Post by Termo on 2009-12-05
It's installing fine now on Ubuntu Jaunty with the new kernel 2.6.28-17

Thank you very much!!!

Was to fast - it seemed to install fine BUT!!

sudo aptitude upgrade gave me:

```
The following partially installed packages will be configured:
  lirc-modules-source 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up lirc-modules-source (0.8.6-0ubuntu3~ppa5~jaunty1) ...
WARNING: /usr/lib/dkms/common.postinst does not exist.
WARNING: /usr/share/lirc-modules-source/postinst does not exist.
ERROR: DKMS version is too old and lirc-modules-source was not
built with legacy DKMS support.
You must either rebuild lirc-modules-source with legacy postinst
support or upgrade DKMS to a more current version.
dpkg: error processing lirc-modules-source (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Back to square one.

---

### Post by lindend on 2009-12-13
> **WolverineFan said:**
> 
**EDIT:** Sheesh that's more complicated than it needs to be :)  Ok, so the final version that worked is ~ppa5~jaunty1 (or whatever your flavor is).  Let me know if you update to this version and it doesn't fix the kernel modules!!
E

Unfortunately, version 5 of the package doesn't install as is for me..pretty much the same errors as before:

```

sudo apt-get install lirc-modules-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
lirc-modules-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 52 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lirc-modules-source (0.8.6-0ubuntu3~ppa5~jaunty1) ...
WARNING: /usr/lib/dkms/common.postinst does not exist.
WARNING: /usr/share/lirc-modules-source/postinst does not exist.
ERROR: DKMS version is too old and lirc-modules-source was not
built with legacy DKMS support.
You must either rebuild lirc-modules-source with legacy postinst
support or upgrade DKMS to a more current version.
dpkg: error processing lirc-modules-source (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SammyC on 2009-12-14
Well its as I said, the DKMS parts of the install scripts are expecting the DKMS scripts to be in a different place to where they are actually installed in 9.04. So I just can't see how it will work.

I should just say at this point, the hack I posted is still working perfectly.

---

### Post by kenni on 2010-01-02
> **WolverineFan said:**
> 
Ok, so the final version that worked is ~ppa5~jaunty1 (or whatever your flavor is).  Let me know if you update to this version and it doesn't fix the kernel modules!!
E

It doesn't fix the problem... :( I've just activated your PPA on a clean and up-to-date Mythbuntu 9.04 box and I receive the following error message:
```
WARNING: /usr/lib/dkms/common.postinst does not exist.              
WARNING: /usr/share/lirc-modules-source/postinst does not exist.    
ERROR: DKMS version is too old and lirc-modules-source was not      
built with legacy DKMS support.                                     
You must either rebuild lirc-modules-source with legacy postinst    
support or upgrade DKMS to a more current version.
```


> **SammyC said:**
> Well its as I said, the DKMS parts of the install scripts are expecting the DKMS scripts to be in a different place to where they are actually installed in 9.04. So I just can't see how it will work.

I should just say at this point, the hack I posted is still working perfectly.

Ok, removing the old files and installing "any" version of lirc-modules-source from scratch (as WolverineFan suggested) didn't solve the problem. Would it be possible for you to upload the package lirc-modules-source_0.8.6-0ubuntu1~ppa9_all.deb somewhere? I would like to give it a test, it doesn't seem like you can download old versions of the compiled packages from the PPA.

Thanks...

---

### Post by WolverineFan on 2010-01-04
Ouch!  Sorry for the continued problems everyone!  I don't know why the darn forum didn't email me when there were replies to this thread :(  Thanks to kenni for PMing me to let me know there were updates!

This error message confuses me...  I don't understand why it's failing (and I don't have a Jaunty box to test it on myself anymore).  Since the ppa9 build worked I should be able to go back and see what all has changed since then though.

I don't think there's any way to retrieve old builds from launchpad so I think the fastest way to fix this will be to fix the current build rather than trying to put up an old build.

Hopefully I'll have some time on Monday or Tuesday to look into the problem and get a fresh build out.  Sorry again for the delays!

---

### Post by brundles on 2010-01-07
Sorry to piggy back on this thread but there seems to be a ton of good stuff here for lirc/lcd problems with iMon in the current builds.

After having problems with a bad XBMC/Nvidia combination I finally upgraded from 8.04 to 9.10 today and since then have been spending time removing all of the hacks I'd put in place to get this stuff working on 8.04. The only one that's giving me grief is the LCD display.

I'm running the iMon VFD display using the standard Karmic packages for LCDd and lircd. The remote works fine but the display refuses to display anything other than garbage. 

Something that may be related is that syslog doesn't seem to be showing anything different even when debugging is turned on so I'm not convinced it's picking up /etc/modprobe.d/lirc.conf properly.

I'm going to carry on poking it this evening to see what I can get out of it but any thoughts would be appreciated.

---

### Post by SammyC on 2010-01-07
I think in the newer versions of LIRC the imon driver needs some options to be set so that it works with the VFD. I have the VFD and using the latest LIRC package built by WolverineFan I'm sure I have to set some options in the module to get it to work.

To get the list of options supported by your build of the module execute modinfo on the module:

modinfo lirc_imon 

and then these need to be in an appropriate module option file. As I recall there might be some fiddles with getting options set in 9.10, I have a feeling that the option file needs to be named the same as the module file. But I could be wrong.

HTH

---

### Post by brundles on 2010-01-07
Thanks for the quick reply Sammy. I've set the lirc_imon.conf file up as documented on the KArmic install for it and double checked the options with modinfo but no luck so far. I'll try some variations of the filename and see how I get on.

*Edit:* No idea what gives, but a full power down with cable pull seems to have done the trick. No idea why it needed the power physically pulled, but it's working now.

Thanks for the help though! :)

---

### Post by lindend on 2010-02-23
Hi WolverineFan,  > **WolverineFan said:**
>  Hopefully I'll have some time on Monday or Tuesday to look into the problem and get a fresh build out.  Sorry again for the delays!  Just curious to see if you've made any progress on an updated lirc iMon package.

---

### Post by WolverineFan on 2010-02-24
> **lindend said:**
> Hi WolverineFan,    Just curious to see if you've made any progress on an updated lirc iMon package.

Sorry, no, I suck :)  I haven't done anything with anything for way too long.  I've dropped the ball on like 5 projects.

With 10.4 LTS coming up I really need to get back on the ball and make sure any recent fixes make it in.  Thanks for the reminder!

---

### Post by rodercot on 2010-02-25
Hey Guys,

 You really should check out this post on the Boxee Forums. I am running a Gyration Remote 2 event devices into one, MCE Usb Dongle for transmitting and My IMON_LCD ffdc device for lcdproc.

 Dutchhome did a ton of work here and rewrote the whole lirc init.d script to accept multiple remotes FROM the hardware.conf file. Read my notes on the post as well, there are some things you have to add back into the hardware conf like remote modules etc.. This all works on Karmic (mythbuntu 9.10 just fines)

 I am also suspending and resuming perfectly now with pm-suspend. Myth-tv works great with the gyration or any other remote through the ir rcvr in the remote if I so wish. I tested EVERY possible combo of configuration last night to see if I could break it, and I think dutchhome should get a medal for how easy this is now to setup multiple devices. 

 This is setup for a gyration remote as is. you can change that to whatever /dev/lirc device you have so IE the 0038 needs 

 lirc0 and lirc1 I believe so you would enter those in remote section and remote1 sections - load your module and restart lirc now create your lircd.conf file for the remote you want to use with the Imon Ir rcvr add it in and restart lirc and you should be good to go, all symlinks to /var/run/lirc/lircd, lircd1, lircd2 etc will be automagically created via dutchhomes new lirc init script.

 link: Start reading from post #6.

  [http://forum.boxee.tv/showthread.php?p=85695](http://forum.boxee.tv/showthread.php?p=85695)

 hope it helps, it completely works for me and is just AWESOME to setup. 
 
 Regards,

 Dave

---

### Post by lindend on 2010-04-19
WolverineFan,

> **WolverineFan said:**
> 
With 10.4 LTS coming up I really need to get back on the ball and make sure any recent fixes make it in.  Thanks for the reminder!

Just pinging you again to see if there's been any update to your lirc package.

---

