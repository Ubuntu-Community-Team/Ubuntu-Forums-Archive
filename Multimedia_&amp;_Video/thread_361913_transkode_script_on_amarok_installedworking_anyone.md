---
title: "transkode script on amarok? installed/working anyone?"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by jetpeach on 2007-02-14
after installing traskode 0.6 in amarok 1.4.5 when i ran the script, first it errored, said it needed libpng.so.3
i installed libpng3 from the repositories (i had other libpng's installed already, but libpng3 said it was for backward compatibility in code) and that fixed that problem.
but now there is no context menu anywhere and transferring flac to an ipod still doesn't work (this is my end goal, it seems there are numorous bugs on this
[http://bugs.kde.org/show_bug.cgi?id=133669](http://bugs.kde.org/show_bug.cgi?id=133669)
[http://bugs.kde.org/show_bug.cgi?id=138850](http://bugs.kde.org/show_bug.cgi?id=138850)
but they are unresolved...)
anyway, if anyone has the traskode script working, can you please tell me how?

i also posted this at the kubuntu forums
[http://kubuntuforums.net/forums/index.php?topic=13804.0](http://kubuntuforums.net/forums/index.php?topic=13804.0)
but it is relevant to anyone running amarok...i will update this if anyone there knows anything either, but those forums don't get as much use compared to these so please help!

thanks!

---

### Post by sygin on 2007-05-05
Hi,

I use Amarok and the Transkode script to convert wma to mp3 (aac) 
for my IPod. When transcoding track it stalls after a few tracks.

I have tried many things but still no luck. I have noticed that clicking
on other windows gets it to work again (for a while).

This did work with the old version of Amarok and Transcode though
(using Feisty now).

I will keep trying to find a solution.

Cheers,
Sygin.

---

### Post by ivantorres on 2007-05-07
Any solutions jet? My problem is even worse... transcode option from "/Settings/Configure Amarok/Media Devices" is disabled!!!

---

### Post by ivantorres on 2007-05-07
Sorry. I didn't know that you must run the script first. Also I couldn't find a tutorial on how to configure the script (TransKode), but after a few mins. of experimentation my iPod (nano) is breathing again! Thanks anyway!

---

### Post by sygin on 2007-05-23
Hi,

"I use Amarok and the Transkode script to convert wma to mp3 (aac)
for my IPod. When transcoding it stalls after a few tracks."

The problem seems to be that Transkode uses Mplayer to decode wma files, this may also be the case for flac files. Mplayer has a habit of failing silently, causing the stalling problem.

I managed to fix the wma problem by hacking the Transkode source code to use ffmpeg instead of mplayer. I can now use Transkode for my wma files.

I have contacted the author of Transkode and he says that he is in the middle of a major changes to how Transkode works to better support multiprocessor platforms. This new version will not be complete for a while.

If you really need me to I could look into how FLAC files are processed and perhaps get a workaround working to solve you problem jetpeach, let me know.

Cheers
Sygin

---

### Post by attendant on 2007-08-10
transkode 0.7beta is out (no binary package to download from Amarok yet though).
if anyone feels like giving it a try, i'd like to know if you're still having problems with it.

attendant, transKode developer.

---

### Post by jetpeach on 2007-08-14
configured, compiled and installed just now. took a while but it completed everything.  had to install to a root directory (sudo make install) since i didn't know how to put it in ~/.kde/share/amarok/scripts/. (probably could've used a flag on configure?... i started configuring before i read all the install file though...) but that is ok, i just have to uninstall manually.
after installing, testing it i found that ogg encoding was set by default to "bypass" so needed to change the various encoding profiles to make them work. simply changes the profile and hitting the OK button though didn't work - perhaps this is a stupid gripe but i was a bit confused for a while, as i would reopen the configuration for transkode and see it back on bypass... then i realized you have to hit the save button, then you can hit OK. perhaps i will try to add a dialog if there have been changes make to profiles so if they hit OK they are notified that they should save any changes first or they will be lost...

but after that (and it was really only 30 minutes), it worked great! so next, i need to test with my ipod.  my ipod isn't here though so i will have to test that later.

i would be glad to share the binary files necessary since i have them compiled (feisty fawn, standard x86 so i think it should work for most people) but i'm not sure how/what to put into the .tar file that others can easily install from the script manager in amarok.

thanks for the work on the script, it is very useful!
jet

---

### Post by jetpeach on 2007-08-14
well no luck with the ipod, but transkode works fine now. i am on the #amarok IRC chat hoping to find a solution for transferring to the ipod still.

---

### Post by pwaldo on 2008-01-08
I struggled with this one for a while and finally got amarok to allow the transcoding option.  It is not obvious, but what you have to do, once transkode is installed, is start it running within amarok.

Go into Script Manager, select transkode, then select Run.  The transcode checkbox in the Configure Device dialog is now selectable. Certainly not intuitive, but it works...

---

