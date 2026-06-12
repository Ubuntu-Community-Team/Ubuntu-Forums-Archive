---
title: "lirc_mod_mce &amp; gutsy"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by bmilleker on 2007-10-26
I am trying to get my windows 3 in 1 keyboard working with my htpc ([http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038)). I have a USB-UIRT. LIRC is working with my 2.6.22 kernel (had to recompile and do some magic to get it going). 

I am using this lircd.conf [http://mod-mce.sourceforge.net/lircd.conf](http://mod-mce.sourceforge.net/lircd.conf). You think that the remote functions of the keyboard would be working, but they are not and I have no idea why. This is just half of my problem, I would like to get the kb and mouse working as well.

#I grabbed the lirc_mod_mce source and I tried compiling it but get these warnings when compiling: ```

:~/mod_mce/lirc_mod_mce# make
make -C /lib/modules/2.6.22.969/build SUBDIRS=/root/mod_mce/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "lirc_register_plugin" [/root/mod_mce/lirc_mod_mce/lirc_mod_mce.ko] undefined!
WARNING: "lirc_get_pdata" [/root/mod_mce/lirc_mod_mce/lirc_mod_mce.ko] undefined!
WARNING: "lirc_unregister_plugin" [/root/mod_mce/lirc_mod_mce/lirc_mod_mce.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'

```

It creates the module, but I cant insert it. I get this error:
```

#:~/mod_mce/lirc_mod_mce# insmod lirc_mod_mce.ko 
insmod: error inserting 'lirc_mod_mce.ko': -1 Unknown symbol in module

```

Can anyone give some advice as to what is happening here.

Thanks.

---

### Post by bmilleker on 2007-11-01
I got this working. Basically, I ended up buying a MCE receiver and remote to go with the keyboard, because I don't think it will work with a USB-UIRT receiver. My reason for thinking this is that the lirc_mod_mce is based off of lirc_mceusb2, and the fact that I could get it working after switching devices is a pretty good reason.

Here is what I did to go from USB-UIRT to MCE.

1. Turn off lirc.
2. Followed this guide [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) to get the lirc_mceusb2 drivers built. I stopped following the guide at "Create a lircd.conf". I used the lircd.conf and lircrc files located here: [http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048).
3. Download the lirc_mod_mce source from [http://mod-mce.sourceforge.net/](http://mod-mce.sourceforge.net/).
4. Copy over /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.h into the directory with your lirc_mod_mce source files in. 
5. Go to the source for lirc_mod_mce and type 'make' to build the module.
6. Type 'insmod lirc_mod_mce.ko' to test the module to see if it inserts.
7. If all goes well in 6, then copy lirc_mod_mce.ko to /lib/modules/$YOURKERNEL/misc
8. depmod -a
9. Restart, unplug & plug back in, or modprobe lirc_mod_mce.
10. You probably need to update your /etc/lirc/hardware.conf, and then start lirc and test with IRW. The mouse and keyboard will be working at this point without LIRC on.

Everything should be pro now.

---

### Post by psiu on 2007-11-08
Holy crap! Got it working!

On my wife's computer anyway, but this means I can get serious about my media box again! (LOL--we just canceled cable too until we move to a new apartment in the spring).

Few things I had to fiddle with to get it working on a Gutsy upgraded from Feisty install:

1.    Had to download lirc-modules-src, then extract it to the generic directory,
The Gutsy LIRC install directions end up not downloading it...hard to find the lirc_dev.h when it's not there.

2.    Ignore the errors that popped up regardless.
2.5   Whenever there is an error, sudo whatever you're doing to make sure it's not a permissions issue.
3.    Reboot.

Optional: Cackle with glee when you first notice the cursor moving on screen \\:D/

Thanks! 
msg posted with MS MCE keyboard & mouse!

---

### Post by MarkyDyL on 2008-01-17
I installed lirc-0.8.2 with apt-get. I set lirc_mceusb2 driver. Remote control worked.

Then I installed lirc_mod_mce. 

Now I have problem because remote control and keyboard doesnt work together. Sometimes /after reboot/ multimedia keyboard is working, but remote control doesnt working and sometimes RC is working and keyboard doesnt.

I checked drivers with lsmod and both modules /lirc_mod_mce and lirc_mceusb2/ is loaded. Is it correct?
Where can be a problem?

---

### Post by MarkyDyL on 2008-01-23
I installed lirc via apt-get

sudo apt-get install lirc lirc-modules-source

then I chose mce remote philips new. Remote control is now working.

but next point is problem:
Copy over /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.h into the directory with your lirc_mod_mce source files in. 

I dont have lirc_dev.h anywhere. Package lirc is in lib/modules/2.6.22-14-generic/ubuntu/media/lirc. But in lirc_dev I dont have lirc_dev.h

Thanks for reply

---

### Post by jsundqui on 2008-01-25
I'm no noob (12 years with Linux, and back in the old days, we had to compile everything!).  But I just can't figure out how to compile lirc_mod_mce

The problem may be that I am running mythbuntu 7.10, which I thought was pretty much a stripped down gutsy with the mythtv stuff added.

Of course it doesn't come with much of a compiling set up, so I installed the kernel headers, kernel souce, lirc_modules source, etc.

Interestingly, installing the kernel source and the lirc_modules source just dumped the tar.[gz|bz2] files into usr/src; I had to unzip them myself.  No biggie but strange.

Anyways, when I try to build lirc_mod_mce I get errors.

The first was that there was no /lib/modules/2.6.22-14-generic/build directory, so I made the build directory; no big deal.

edit----

OK, that was mm problem.  I had to install the headers first!  That is what created the build directory, which is a symlink to the headers source.  I found that out after checking in on another "regular" gutsy install.

Typing this now on the MCE keyboard.

---

### Post by MarkyDyL on 2008-01-28
> **jsundqui said:**
> 
OK, that was mm problem.  I had to install the headers first!  That is what created the build directory, which is a symlink to the headers source.  I found that out after checking in on another "regular" gutsy install.

Typing this now on the MCE keyboard.

What kind of package did You install? Linux-headers?
Because when I try to make lirc_mod_mce I get errors about undefined lirc-register plugin

---

### Post by psiu on 2008-02-02
> **jsundqui said:**
> I'm no noob (12 years with Linux, and back in the old days, we had to compile everything!).  But I just can't figure out how to compile lirc_mod_mce

The problem may be that I am running mythbuntu 7.10, which I thought was pretty much a stripped down gutsy with the mythtv stuff added.

edit----

OK, that was mm problem.  I had to install the headers first!  That is what created the build directory, which is a symlink to the headers source.  I found that out after checking in on another "regular" gutsy install.

Typing this now on the MCE keyboard.

I actually got it working on my Myth install by doing a Gutsy install and THEN doing the Mythbuntu packages--because I am a Linux noobie :P

Mark, ignore the errors about the undefined plugin--I had em and keyboard/mse and remote work.

---

### Post by arjay1 on 2008-04-07
> **bmilleker said:**
> I got this working. Basically, I ended up buying a MCE receiver and remote to go with the keyboard, because I don't think it will work with a USB-UIRT receiver. My reason for thinking this is that the lirc_mod_mce is based off of lirc_mceusb2, and the fact that I could get it working after switching devices is a pretty good reason.

Here is what I did to go from USB-UIRT to MCE.

1. Turn off lirc.
2. Followed this guide [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) to get the lirc_mceusb2 drivers built. I stopped following the guide at "Create a lircd.conf". I used the lircd.conf and lircrc files located here: [http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048).
3. Download the lirc_mod_mce source from [http://mod-mce.sourceforge.net/](http://mod-mce.sourceforge.net/).
4. Copy over /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.h into the directory with your lirc_mod_mce source files in. 
5. Go to the source for lirc_mod_mce and type 'make' to build the module.
6. Type 'insmod lirc_mod_mce.ko' to test the module to see if it inserts.
7. If all goes well in 6, then copy lirc_mod_mce.ko to /lib/modules/$YOURKERNEL/misc
8. depmod -a
9. Restart, unplug & plug back in, or modprobe lirc_mod_mce.
10. You probably need to update your /etc/lirc/hardware.conf, and then start lirc and test with IRW. The mouse and keyboard will be working at this point without LIRC on.

Everything should be pro now.

Thanks for this very helpful guide.  I have the same setup: mce remote, keyboard and receiver, and have got to the stage where I can get the keyboard and the remote keys working.  But I just cannot get the mouse pointer and click keys to work.

Do these work OK for you and if so - how did you do that?  It would help me a lot if you could post the mouse section of your xorg.conf.

Cheers

RJ

---

### Post by Skinner_au on 2008-06-08
Hi all,

I have had some success with this, however am missing one piece of the puzzle.

I followed as much of the guide posted by bmilleker as I could (the hauppauge link was dead) and after a change to my harware.conf (to read MODULES="lirc_mod_usb" & reboot both my remote and keyboard are recognised at the same time, however any key pressed on the keyboard results in it remaining on forever. I also received the compile warnings about an undefined module but everything seems to be recognised ok, its just the keys stay "down" once you've pressed them. Moving the MCE Keyboard's mousepointer or pressing some of it's custom buttons will stop the 'key down' action.

I'm not sure if this is an Xorg or LIRC issue but as a bit of a newb I don't really know how to go about fixing it. Although I have inserted an "AutoRepeat" setting into the standard keyboard declaration in Xorg.conf, I'm a bit confused whether its actually an "AutoRepeat" or IR signaling function.

Anyone able to help?

Thanks

Skinner

UPDATE:
I just noticed when I do an "irw" that the custom keys on the MCE keyboard come up with the correct codes and driver name corresponding to the correct keys, but when I push the standard keyboard keys only the key's letter appears on the screen (and then autorepeats forever). This makes me think that the key-presses aren't being intercepted by the LIRC daemon, but again I don't know how to go about fixing that :(

---

### Post by arjay1 on 2008-06-08
Sorry to be the bearer of bad news.  This is a common problem with the driver. I have exactly the same issue and have been in prolonged correspondence with the author (see links below).  Lovely guy, who has done a lot to try and help, including updating the driver, but I still can't get it to work.  I have now given up and bought another wireless keyboard which has an integrated mouse and which works just fine.  Little in the way of media keys, but the keyboard keys can be setup for most things and the rest - well I learned not to want them!

Here are a couple of links - hope they come out OK.  A bit of a newbie myself <g>.  Good luck trying to read the threads - it is a Sourceforge forum and I never got the hang of how to read in order, reply to the right one etc.  You may have to dig through them all, as the repeating keys issue is mixed in with other stuff about compile issues.

Not sure I can help much more but ask if you need anything.

BTW - the author (Florian Demsku) is a very busy guy and doesn't want much to do with the driver now.  He is looking for someone to take the take it over if there is anyone out there who could do this!

Richard 

[https://sourceforge.net/forum/message.php?msg_id=4913390]("https://sourceforge.net/forum/message.php?msg_id=4913390")

[https://sourceforge.net/forum/message.php?msg_id=4921655]("https://sourceforge.net/forum/message.php?msg_id=4921655")

[https://sourceforge.net/forum/message.php?msg_id=4929311]("https://sourceforge.net/forum/message.php?msg_id=4929311")

---

### Post by Skinner_au on 2008-06-08
Wow, thanks so much for the reply. 
I had almost given up (it's 3am) when I discovered a workaround buried in the threads.

For anyone else who has this problem, the continuous AutoRepeat problem is fixed by executing :

```


xset r off

```

Sure it means there's no autorepeat, but I figure thats a small price to pay for a working keyboard and remote. Hooray for the ubuntu forums (and its contributors).

Thanks again,

Skinner

---

### Post by arjay1 on 2008-06-09
Glad the threads were of help.  I should have mentioned this workaround, which I did use for a while.  I found that it is fine if all you are doing is using mythtv, but I also use the same PC for more general work including getting and replying to emails etc.  I got so fed up with not being able to autorepeat when deleting, that I gave up in the end.

BTW - there are suspicions that this problem only occurs with ubuntu-based os's - for example mythbuntu.  I did try to investigate if it happened with mythdora but could not get the driver to install properly.  Not sure if it is worth changing distro just to get the MS keyboard working but it might be for others.

---

### Post by Skinner_au on 2008-06-10
My box, fortunately, is almost solely used as a mediacentre/NAS and the main reason I wanted the keyboard access was for when something goes wrong so I could enter the username/password to log back in without having to plug in a keyboard. Most of the time I remote control it when I need to work on it, but sometimes thats just not possible - which is where the MCE keyboard comes in.

I'm still running 7.10 desktop - I've wasted too many hours over the years due to my upgrade-itis and I'm scared the upgrade to 8.04 will break something in MythTV or MySQL. I might do it when support ends for 7.10, but for now everything is working which is a minor miracle given I hadn't really used unix for almost 15 years and newbie-blundered my way through it all. An install on a new OS is out of the question!
Well, maybe when I get my dev-box up and running... but who really has time...

Thanks again for the help.

---

### Post by arjay1 on 2008-06-10
I take it that either you are using an older version of mythbuntu, or you built your mythtv on top of ubuntu 7.10.  Just FYI I did a clean install of the latest mythbuntu (based on 8.04) and it installed flawlessly.  Much easier, of course, that DIY.  You could always think about partitioning your HDD (or sticking in a second HDD) and trying the newer mythbuntu there?

---

