---
title: "Running X with no config file =)"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by xjas05 on 2007-05-10
right now I have no xorg.conf file... and its doing the job better than my old one that nvidia generated... I can now use my DVI cable and have my monitor running under "Digital" mode... but now I've lost 3D acceleration, I wanna know, where is this "default x config file" that its using? I wanna see what myne is missing, so I can add those options in where needed...

---

### Post by kvonb on 2007-05-10
> **xjas05 said:**
> right now I have no xorg.conf file... and its doing the job better than my old one that nvidia generated... I can now use my DVI cable and have my monitor running under "Digital" mode... but now I've lost 3D acceleration, I wanna know, where is this "default x config file" that its using? I wanna see what myne is missing, so I can add those options in where needed...

You're kidding?

And there is no backup file in /etc/X11 ?

---

### Post by xjas05 on 2007-05-10
lol, I'm serious, I have my original file backed up to my desktop... problem is I can only run my monitor in "Analog" mode and only use the VGA cable with that =[ just spent 300 bucks on this thing this week, and I wanna make the most out of it, and now that I know that it WILL work, I wanna see my current configuration, and make appropriate changes

---

### Post by kvonb on 2007-05-10
This configuration file is searched for in the following places  when  the
       server is started as a normal user:

           /etc/X11/<cmdline>
           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf-4
           /etc/X11/xorg.conf
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf-4
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf-4
           /usr/lib/X11/xorg.conf

Have a look through that lot, from ```
man xorg.conf
```

---

### Post by russell.h on 2007-05-10
> **kvonb said:**
> You're kidding?

And there is no backup file in /etc/X11 ?
Being able to run with no xorg.conf is one of the supposed features of xorg 7.2. Not that I was ever inspired to try it...

---

### Post by xjas05 on 2007-05-10
Is there any other way I can get my monitor to run in Digital mode?

---

### Post by kvonb on 2007-05-10
Try this from the root folder /

```
sudo find . -name *xorg.conf*
```

That will search the entire system for anything with "xorg.conf" in the filename.

Here's some that I found on my system:

./etc/X11/xorg.conf
./etc/X11/xorg.conf.20070414113039
./etc/X11/xorg.conf.backup
./usr/share/xresprobe/xorg.conf
./usr/share/man/man5/xorg.conf.5.gz
./usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
./usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
./var/lib/x11/xorg.conf.md5sum
./var/lib/x11/xorg.conf.roster

---

### Post by xjas05 on 2007-05-10
nothing out of the ordinary =(

```

root@DELL:/# sudo find . -name *xorg.conf*
./usr/share/man/man5/xorg.conf.5.gz
./usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
./usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
./var/lib/x11/xorg.conf.roster
./var/lib/x11/xorg.conf.md5sum
./home/jas/Desktop/xorg.conf.bak

```

---

### Post by kvonb on 2007-05-10
Sorry to keep posting, but this is actually quite exciting :D. 

Maybe try creating a xorg.conf that has ONLY the 3d enabling stuff in it and nothing else, maybe it will simply import that into it's default one?

---

### Post by xjas05 on 2007-05-10
lol, I wouldn't know what to put in, and what not to :p only reason I removed the config file in the first place was because of a google find :p

---

### Post by kvonb on 2007-05-10
Tried it, but it didn't work!

I tried removing my xorg.conf but only got 1024x768 :(

---

### Post by xjas05 on 2007-05-10
k I moved back the xorg.conf file, and now I have the messed up colors, after messing around with nvidia-settings, I'm pretty sure its all that contrast/brightness/gamma settings that are messed up... 32bpp is set for color depth...  the "Reset to hardware defaults" is obviously not right, is there a tool or something that I can use to get correct settings?

---

### Post by baba_oreilly on 2007-05-14
I seem to be having this same problem of a missing xorg.conf file. I don't really know what I'm doing with Ubuntu (and linux in general) since I just installed it an hour ago for the first time, so it could be me. My screen isn't displaying at its max resolution, and in system>preferences>screen resolution there are no options other than 1024x786. I think this means I need to edit my xorg.conf file... right? Anyway, I tried opening it using ```
sudo gedit /etc/x11/xorg.conf
``` and it just opened up to a blank screen. Then, as someone suggested a few posts up, i tried to find it using ```
sudo find . -name *xorg.conf*
``` and it didn't give me any output - it just gave me another command line. Can anyone help me out with whats going on??

---

### Post by baba_oreilly on 2007-05-14
heh, never mind. I didn't realize it was case sensitive. See, I told you I dont know what I'm doing.

---

### Post by kvonb on 2007-05-14
> **baba_oreilly said:**
> heh, never mind. I didn't realize it was case sensitive. See, I told you I dont know what I'm doing.

Hello :)

If you can find out your screens frequency rates, either from the book that came with it, or from an internet search, you can add those to your xorg.conf and you should then be able to get higher rates.

Here is a sample from mine if it helps you:

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection
```You should also have found out what resolutions your screen can support, they can be added to the Screen" section like this:

```
SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
```Hope that helps :)

---

### Post by eentonig on 2007-05-14
baba_oreilly,

You should be better of using gksudo when using a non cli program. You could run in to problems by using plain old sudo for graphical apps.

> gksudo gedit ....

---

### Post by baba_oreilly on 2007-05-14
Thanks for the suggestions. Pardon my ignorance, but what's the difference between sudo and gksudo, and what is a cli program?

---

### Post by kvonb on 2007-05-15
> **baba_oreilly said:**
> Thanks for the suggestions. Pardon my ignorance, but what's the difference between sudo and gksudo, and what is a cli program?

sudo:  Use this from a terminal

gksudo:  You can also run GUI progs that need sudo permissions by pressing <alt><f2> on the desktop and typing: gksudo programme filename, as in: gksudo nautilus for a root capable file browser.  You can also use: gksu if gksudo gives you grief :)

cli programme:  A (usually) text based programme run from the _**C**_ommand _**L**_ine _**I**_nterface, or Terminal as it is called under Linux.  The term CLI was widely used in the Commodore Amiga's operating system :)

---

