---
title: "Cannot play CD/DVD"
date: 2011-10-05
forum: Multimedia Software
---

### Post by beew on 2011-10-05
Hi,

I popped an audio CD into the CD drive and a window popped up asking me what to do with it. I chose vlc and then nothing happened. So I open the CD instead with the file manager and tried to play the individual track from the terminal and got these errors

> vlc cdda://sr0/Track1.wav
VLC media player 1.1.11 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x99f4914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-james", 1)
Warning: call to srand(1317155633)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:23541): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0x9d563a4] main input error: open of `cdda://sr0/Track1.wav' failed: (null)
It has nothing to do with codecs because I can rip the CD and play the files in any media player just fine. But I just can't play any CD or DVD with any media player.

Thanks.

This is Lubuntu 11.04, I am testing it for my friend.


**EDITED:** Just booted Ubuntu 11.04 off tthe same machine and CDs play flawlessly, so it is not a problem of the machine or the CDs.

---

### Post by beew on 2011-10-06
Hi,

I am able to play cds on the terminal with commands such as "mplayer cdda://" and "vlc cdda://", but cannot play with the gui (when cd is inserted there is a pop up that ask what to do with it, click say "open with vlc" and nothing happens if I choose open with file manager then it opens, but try to play the actual music file by right clicking nothing happens)

It seems that for some reasons the music players are not able to find the cdrom for some reasons in Lubuntu. 

Any thought? Thanks.

---

### Post by beew on 2011-10-09
Is this because the media players have troubles recognizing the cdrom? I noticed that Lubuntu is quite buggy in mounting media including external drives, some time it works some time it doesn't..

---

### Post by beew on 2011-10-11
Bump!

---

### Post by WorBlux on 2011-10-11
> **beew said:**
> Is this because the media players have troubles recognizing the cdrom? I noticed that Lubuntu is quite buggy in mounting media including external drives, some time it works some time it doesn't..

No, it's because cdda, isn't a real filesystem, and when you try to access it like it is, it doesn't work. Use the open disc menu feature and it should work without any problems.

When you try to open with a file manager, modern ones are smart enough to fake it and present each track as a file, however the media players don't access them that way.

I have no idea how to actually fix the file manager to get it to differentiate cdda disks from discs with actual file systems like iso9660 and behave accordingly. .

---

### Post by beew on 2011-10-11
Actually the open disc menu feature doesn't work but command line does (like "vlc cdda://) That is my issue here.

Also, as said above, if I choose open with file manager on the open disc menu, I can see the files but still cannot play it, right click "open" vlc throws  a lot of errors saying that it cannot access the files and freezes, gnome-mplayer just stops. But with "mplayer cdda://" or "vlc cdda://" I can play the CD with no problem.

---

### Post by amjjawad on 2011-10-12
> **beew said:**
> Actually the open disc menu feature doesn't work but command line does (like "vlc cdda://) That is my issue here.

Also, as said above, if I choose open with file manager on the open disc menu, I can see the files but still cannot play it, right click "open" vlc throws  a lot of errors saying that it cannot access the files and freezes, gnome-mplayer just stops. But with "mplayer cdda://" or "vlc cdda://" I can play the CD with no problem.

So everything is perfectly fine **ONLY** when you play the content of that Audio CD from LXTerminal?

---

### Post by amjjawad on 2011-10-12
I never ever use Audio CDs but luckily, we have some at home.

1- I brought one and inserted in my CD/DVD Drive

2- A Pop-up Window showed up and I choose VLC Media Player

[IMG]http://i56.tinypic.com/30tjjo0.jpg[/IMG]



3- I clicked "Play Button" and then a new window popped up:

[IMG]http://i52.tinypic.com/4f7d5.jpg[/IMG]



4- I clicked on the 2nd Tab (Disc), I chose "Audio CD" then finally I clicked "Play" on the same window and ... it works like a charm.

[IMG]http://i55.tinypic.com/mku5uh.jpg[/IMG]



Hope that will help :)

---

### Post by beew on 2011-10-12
Hi, 

It works! Thanks a lot   my friend! Turns out I have not picked audio CD from vlc expecting that it would be able to pick the media type like in Ubuntu. I guess I am spoilt by gnome. :)
 
Is it possible to choose other applications to open audio CD instead of those listed? Is it possible to set it up so that if I instert a CD it will just play like Ubuntu? I am setting this up for someone who is not very keen on tinkering so the least work the better. :) 

Lubuntu is really fast, this machine has 1.6GH cpu and 1g of ram and it takes 5 minutes to open Firefox in Vista and nothing really works, with Ubuntu it is a lot faster, but with Lubuntu it is lightning fast, it is like a new computer. :)

---

### Post by amjjawad on 2011-10-12
> **beew said:**
> Hi, 

It works! Thanks a lot   my friend! 

Glad to know that. You most welcome :)

> I guess I am spoilt by gnome. :)
 
+1 :P :P


> Is it possible to choose other applications to open audio CD instead of those listed? Is it possible to set it up so that if I instert a CD it will just play like Ubuntu? I am setting this up for someone who is not very keen on tinkering so the least work the better. :) 
My guess it's Applications Related issue not a Desktop Environment but I may be wrong.
I'll do some search and get back to you as soon as I can :)


> Lubuntu is really fast, this machine has 1.6GH cpu and 1g of ram and it takes 5 minutes to open Firefox in Vista and nothing really works, with Ubuntu it is a lot faster, but with Lubuntu it is lightning fast, it is like a new computer. :)

I have a feeling that sooner or later, you'll fall in love with it and use it as your primary OS ;)
Thanks for your nice words ... that's why I joined Lubuntu Team because it simply rock.

---

### Post by sideburn on 2012-01-14
> Is  it possible to choose other applications to open audio CD instead of  those listed? Is it possible to set it up so that if I instert a CD it  will just play like Ubuntu? I am setting this up for someone who is not  very keen on tinkering so the least work the better. :smile:                                 

> My guess it's Applications Related issue not a Desktop Environment but I may be wrong.
I'll do some search and get back to you as soon as I can :smile:Did you find out if it is possible to setup so that if inserted CD or DVD it will automatically execute VLC as default player and then VLC autoplays the media?

---

### Post by amjjawad on 2012-01-14
> **sideburn said:**
> Did you find out if it is possible to setup so that if inserted CD or DVD it will automatically execute VLC as default player and then VLC autoplays the media?

Actually I did not find time for that but I do hope I can get the answer soon!

---

### Post by sideburn on 2012-01-20
Thanks to Vaphell [http://ubuntuforums.org/showthread.php?t=1911452](http://ubuntuforums.org/showthread.php?t=1911452) I figured a way that is very close to autoplay after inserting Audio CD or Video DVD.  This is a crude method that only needs one mouse click after inserting CD/DVD disc.  If it doesn't find audio CD or video DVD,  it will either open a file browser to browse the files or nothing happens. This is my second time to write bash code so use it at your own risk.  Also,  whenever you need to eject the disc,  always unmount via file browser first then if needed press physical eject button.

1. Right click on whitespace of file browser, select 'Create New...' then select 'Blank File'

2. Right click on newly created blank file and select 'Rename'.  Rename the file so that it would be impossible to be the same name as existing command names (or future installed commands). And don't name it with an extension such as .sh.  This is to prevent conflicts.

3. Right click on renamed file, select Properties, select Permission Tab then check mark 'Make the file executable'

4. Open renamed file with your favorite editor such as leafpad. Enter code similar to this then save it.  You might need to tweak to fit your needs:
```
#!/bin/bash
checkforaudio=`gvfs-info -f cdda://sr0/ | grep "filesystem::type: cdda"`
checkfordvd=`find /media/*/ -name "VIDEO_TS" | grep "VIDEO_TS"`
checkforanyfiles=`ls /media`
if [ "$checkforaudio" == "  filesystem::type: cdda" ]; then
    vlc cdda:///dev/sr0
elif [ ${checkfordvd:(-8)} == "VIDEO_TS" ]; then
    vlc dvd:///dev/sr0
elif [ "$checkforanyfiles" != "" ]; then
    pcmanfm /media/$checkforanyfiles
fi
exit 0
```5. Use terminal to copy this file to /usr/bin with cp command as sudo. For example
```
sudo cp your-new-script /usr/bin
```6. With a file browser open (pcmanfm), select 'Edit', Select 'Preferences', Click 'Volume Management' tab then uncheck 'Show available options for removable media when they are inserted' This will remove an extra mouse click.

7. Now you can insert your newly created command name to launcher icon for dock such as AWN or lxpanel :-)

8. Enjoy One Click 'Play' Button!

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-12
> **amjjawad said:**
> Actually I did not find time for that but I do hope I can get the answer soon!
I hope you found out and will post it soon.  I have been looking all over the internet for a way to autoplay DVDs.  I have been really trying to tweak Lubuntu into the really nice DE I want it to be, (because LXDE and Lubuntu are sooooooooooooo much better than they used to be.)  I have wanted to use Lxde and it is now really useable and stable. 

Please find out a way, and implement it into the standard distro!!

---

