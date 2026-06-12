---
title: "VLC not playing DVD"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Mike1056 on 2010-03-28
Okay, it's no longer crashing, but now VLC isn't playing the DVDs.  It's giving me these issues...

 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

Not sure where to go to check the log, but this is what it's saying.  I have installed Ubuntu-Restricted-Extras and libdvdread4 from the Synaptic Package Manager, but it's still giving me this issue. :(  Any suggestions?

---

### Post by yetiman64 on 2010-03-28
> **Mike1056 said:**
> Okay, it's no longer crashing, but now VLC isn't playing the DVDs.  It's giving me these issues...

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

Not sure where to go to check the log, but this is what it's saying.  I have installed Ubuntu-Restricted-Extras and libdvdread4 from the Synaptic Package Manager, but it's still giving me this issue. :(  Any suggestions?

Sounds to me like you may need to install libdvdcss2 from medibuntu. Check out how to here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) -this will also show to set up other codecs like w32 (Windows formats) as well. Have a good read on this page- it has worked for me before including with vlc- and follow the instructions all the way through but choosing only what you need.

For the logs you can view error messages through the vlc GUI Tools menu > Messages.

Good Luck as vlc is worth it for playing dvd's.

---

### Post by Mike1056 on 2010-03-28
Is that what I should do if I'm running 64-bit?  I noticed that it was w32 which I'm assuming is 32-bit.  Thanks for your reply!

---

### Post by yetiman64 on 2010-03-29
Seeing as you're on 64 bit (same here) you can skip the w32 codecs (w32 is for 32 bit - Yes) and either install the w64 pack (that's if the restricted extras package hasn't already installed them - check 1st in synaptic).
[COLOR=Blue]However it seems the vlc problem should only need libdvdcss2 to fix, which is only available from Medibuntu AFAIK.[/COLOR] 
The other codecs are "just nice to have available".
[LEFT]There are quite a few other packages available only from medibuntu - some are worth checking out - maybe later after you sort out VLC ?.

[/LEFT]

---

### Post by Mike1056 on 2010-03-29
libdvdcss2 was already installed so I reinstalled it as well as installed kubuntu and xubuntu restricted extras.  The problem is unchanged, though.  So, I tried uninstalling and reinstalling vlc and...whalaaa!!  It didn't work. :(  I've come so far since the install last night.  Sound wasn't working, got that finally.  Got it modified to a Mac OS X theme and it looks and works great.  This really is the last thing I can think of to make it a nice and functional machine!  I appreciate all the help I've gotten thus far!  BTW...although I still use windows, I just built a hybrid dedicated specially to Ubuntu!  We're looking at a 2.4 Quad Core (AMD...I only work with AMD unless I HAVE to) with 8 GB RAM and a 1 GB Video Card running Ubuntu 9.1 64-bit!  Blows both my windows xp and windows 7 machines put together out of the water!  And they're from within the last 15 months!

---

### Post by yetiman64 on 2010-03-29
Sorry so long to respond, but the time I'm taking keeps getting me logged out.
Will need to work on some ideas offline and get back to you asap.

---

### Post by yetiman64 on 2010-03-29
I've had a similar problem with getting vlc up in the past.
How are you installing (Terminal, software centre or Synaptic) ?

---

### Post by yetiman64 on 2010-03-29
Have a read of this thread, it may help you particularly post #3
[http://www.uluga.ubuntuforums.org/showthread.php?p=8705036](http://www.uluga.ubuntuforums.org/showthread.php?p=8705036)

But 1st also try taking out the 2 extra restricted extra packages for Xubuntu and Kubuntu Definitely not needed here.
Good luck once again.

---

### Post by Mike1056 on 2010-03-29
Sorry it took so long.  Finally ended up going to bed and then woke up and had a few errands to run first thing.  AI unstalled vlc with the Ubuntu Software Center.  I will take Kubuntu and Xubuntu restricted extras off as soon as I click send.  The board is not well supported in Ubuntu (Asus M4A77D) and the one that I had in here before it got fried (didn't use a surge protector because I thought it would be okay for a day or two until I could get one :(  Apparently I was a little off on that), but prior to that, the sound was perfect.  A replacement to that is going to be here tomorrw and I'll plug it in.  I'm wondering if that could be what my problem with this is.  I'm debating on doing a fresh install.  It would probably only take me about two hours to get it back to where it's at now (I've modified it to look like a Mac and gotten some software installed and updates done, etc.)  On my old board, VLC was playing videio.  I'm sure this board will be great when it becomes better supported by Linux but until then, I'm debating very seriously over sticking with the other one when the replacement comes in tomorrow.  Any thoughts on that?  Thanks!

Mike Schroeder

---

### Post by yetiman64 on 2010-03-29
Hi Mike, 
Yeah I just woken up myself now, so back into it.
I doubt your vlc problem is exclusively hardare as it comes up occasionally in these forums. A good way to see this is with Google - paste in

> p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]and check some of the links (a lot of them will come from around here), hence the link in my previous post #8 where a user "carbonbased" fixed his problem with vlc using synaptic.

Although software centre is good, and easy to use, I've found using System > Administration > Synaptic Package Manager to be extremely useful where any hassles occur. Particularly on a modified system (I note you've changed themes etc, however I don't think this should be too much of a worry). A note of warning though, it is very powerfull and can do damage if you let it remove the wrong packages, which can happen due to dependency issues. Always take notes if it wants to remove essential packages eg. ubuntu desktop etc. and ask further questions on the forums. Always remember the first entry in the UF CoC Technical Support Policy states;

> There are no stupid questions. You're not a stupid person simply because you do not know how to do something, or do not have the answer to a question. Everyone was a green user at one point in time. :)Personally I wouldn't bother with a fresh install just yet, unless other system problems are apparent.

One last note is that packages of the same name from different sources eg, libdvdcss2 from libdvdread4, may not necessarily be the same, usually for legal reasons. So maybe you should consider enabling the Medibuntu Repo and instal libdvdcss2 from there.

Nev

---

### Post by lidex on 2010-03-30
With ubuntu-restricted-extras installed run this command in a terminal:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Now in nautilus navigate to "~/.dvdcss" Select the contents of this folder and delete.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

If you're using ppa version of vlc, try using the standard ubuntu repo version. Are you able to play dvds in mplayer or xine?

---

### Post by gsimpson on 2010-06-02
Solution here worked for me

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

