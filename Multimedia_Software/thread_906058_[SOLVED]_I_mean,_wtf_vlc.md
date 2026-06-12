---
title: "[SOLVED] I mean, wtf vlc?"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Elephantman5 on 2008-08-31
I've Never had problems with this player.
But today I pop in some anime flick after configuring all my progs on this relatively newly installed ubuntu distro.
And what?

_[[img=http://img528.imageshack.us/img528/7091/screenshotac1.th.png]](http://img528.imageshack.us/my.php?image=screenshotac1.png)_
[[IMG]http://img528.imageshack.us/img528/screenshotac1.png/1/w1280.png[/IMG]]("http://g.imageshack.us/img528/screenshotac1.png/1/")

I tried installing all the gstreamer stuff and running Move player but that wouldn't play it. Looed for the dvdcss thing in synaptic too, everything. Vlc won't work, Mplayer won't work, nothing will play this movie. But it runs in Window.
What a joke.

---

### Post by Elephantman5 on 2008-08-31
I even went and added 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Stuff that I never had to add before, and it installed stuff, but vlc still isn't doing anything.

---

### Post by Cresho on 2008-08-31
vlc?  I don't like it as well but that isn't saying that is not working on my end because it is.

VLC has its own libraries so nothing else is needed.

do this.

go to your userhome directory, in nautilus, view, show all files, delete .vlc

and you can start over again.


I frankly love viewing my movies in xine-ui but it took me a week configuring and learning all the curves.  It tops vlc.

---

### Post by Elephantman5 on 2008-08-31
> **Cresho said:**
> vlc?  I don't like it as well but that isn't saying that is not working on my end because it is.

VLC has its own libraries so nothing else is needed.

do this.

go to your userhome directory, in nautilus, view, show all files, delete .vlc

and you can start over again.


I frankly love viewing my movies in xine-ui but it took me a week configuring and learning all the curves.  It tops vlc.

Yeh, I've had VLC for quite awhile and I've never had a problem.
I nautilus'ed and everything, purged, and autoremoved...
Then installed: [http://paste.ubuntu.com/42084/](http://paste.ubuntu.com/42084/)

And yeh, nothing.
[[img=http://img524.imageshack.us/img524/5456/screenshotiy6.th.png]]("http://img524.imageshack.us/my.php?image=screenshotiy6.png")

I've tried this on other dvds too. 
Interesting thing. Even though I close vlc, my dvd-r is very much still going. And it won't let me open.

---

### Post by mc4man on 2008-08-31
Why don't you open vlc from the terminal, then try to open the dvd (file -> open disk) and post terminal output.

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> Why don't you open vlc from the terminal, then try to open the dvd (file -> open disk) and post terminal output.

ajzimmerman@ajzimmerman-desktop:~$ vlc
VLC media player 0.8.6e Janus
file -> open disk

No output...blank. cd drive is still reading away, Not quite sure what it's doing though.

---

### Post by mc4man on 2008-08-31
was looking at your pastebin which looks fine
Quick question - you went file -> open disk in vlc or in the terminal?

---

### Post by Elephantman5 on 2008-08-31
I've tried both [mc4man]("http://ubuntuforums.org/member.php?u=320715") 
Selecting disk in vlc brings me this:
[http://img520.imageshack.us/img520/9287/screenshotbx1.png]("http://imageshack.us")

(Then I pressed ok)
[http://paste.ubuntu.com/42089/](http://paste.ubuntu.com/42089/) 
(Now it works...)
[[IMG]http://img527.imageshack.us/img527/1130/screenshot1mj1.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshot1mj1.png)

Before, I had done the same thing, and nothing would come up.
So, I guess the solution was;

Nautilus to home directory after purging vlc, delete configuration files, and reinstalling.

Thanks. 
[]("http://g.imageshack.us/img520/screenshotbx1.png/1/")

---

### Post by Elephantman5 on 2008-08-31
No, now it might work in opening manually, but it still goes gray
[[IMG]http://img375.imageshack.us/img375/8159/screenshotih7.th.png[/IMG]](http://img375.imageshack.us/my.php?image=screenshotih7.png)

When I right click the disk in My Computer and open with.

---

### Post by mc4man on 2008-08-31
So i'm gathering your good.
Note; going file -> open disk in the terminal would produce/do nothing.

If you have any navigation problems with your dvds let me know and we'll change your launch command for vlc

edit ; didn't see last post, describe what happens.

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> So i'm gathering your good.
Note; going file -> open disk in the terminal would produce/do nothing.

If you have any navigation problems with your dvds let me know and we'll change your launch command for vlc

edit ; didn't see last post, describe what happens.

So, meandering over to My Computer, the center. And right click the Dvd drive. This drive contains the movie.
Open With

Vlc.

(Up pops Vlc!) But it doesn't play. [[IMG]http://img370.imageshack.us/img370/5610/40132487ic8.th.jpg[/IMG]]("http://img370.imageshack.us/my.php?image=40132487ic8.jpg")
Freezes, in fact. Immediately.

---

### Post by mc4man on 2008-08-31
From what could  be seen from screenshot 3 posts back your getting some sort of video error. 
If you want to post some info like terminal output then just copy and paste it into your reply. Then highlight it and choose the code box (#)  in reply task bar. Much easier to read and see everything.

Forget the r.click open with for the moment , can you playback a dvd 'normally' as in open vlc from the app menu,file, open disk?
see screen

---

### Post by sloggerkhan on 2008-08-31
Don't know what Paprika encode you have, but I've got one in mkv container, plays back fine. If it's the DVD, use a player that supports menus well like xine-ui. (VLC is getting menu support, but last I checked was less than optimal.)

I watch a fair bit of anime and the best player I've found is the smplayer mplayer front end. With VLC I had a lot of subtitle problems, but smplayer makes it easy to use ***/SSA formatted subs.

Anyway, good luck.

PS: I like xine-ui tons, too, but its subtitle rendering makes it bad for anime. 
I use to play back all my DVDs, though. My top 2 linux media players are def smplayer, then xine-ui.

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> From what could  be seen from screenshot 3 posts back your getting some sort of video error. 
If you want to post some info like terminal output then just copy and paste it into your reply. Then highlight it and choose the code box (#)  in reply task bar. Much easier to read and see everything.

Forget the r.click open with for the moment , can you playback a dvd 'normally' as in open vlc from the app menu,file, open disk?
see screen

Ok, I'll remember the code posting preference.
Yes. Opening vlc in terminal and opening DVD from the file menu works.

Because it works, I don't think it's a video problem. I realize this way is actually faster. But it bothers me I can't open the Dvd from clicking on the Dvd icon. Going through the individual VOB files, I see horrible quality, so it seems in that way to be a video problem. I'm not quite sure why though. Proprietary drivers are installed (nvidia). Unless I should be getting them from Nvidia directly. (If that is the possible reason then tell me)
Terminal Output when running vlc, opening dvd:```

ajzimmerman@ajzimmerman-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PAPRIKA
libdvdnav: DVD Serial Number: 37469312
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ajzimmerman/.dvdnav/PAPRIKA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00008ce4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001dc85a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001dc86e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001dd923
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001dd937
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001dd96d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001dd981
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001e48cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001e48e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001e4937
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001e494b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003479c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003479ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00347e20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00347e34
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0034f80a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0034f81e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0037f059
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0037f06d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00387c69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00387c7d
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
[00000355] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000351] main decoder error: decoder is leaking pictures, resetting the heap
[00000352] main video output error: picture 0xde44c8 refcount is -1
[00000352] main video output error: picture to date 0xde4218 has invalid status 6
[00000352] main video output error: picture to display 0xde4218 has invalid status 6
[00000352] main video output error: picture 0xde4218 refcount is -1
[00000351] main decoder error: decoder is leaking pictures, resetting the heap
[00000352] main video output error: picture to date 0xde40c0 has invalid status 6
[00000352] main video output error: picture to display 0xde40c0 has invalid status 6
[00000352] main video output error: picture 0xde40c0 refcount is -1
[00000352] main video output error: picture 0xde4370 refcount is -1
[00000289] main playlist: stopping playback
ajzimmerman@ajzimmerman-desktop:~$ 

```I don't know if this is different, but I don't remember seeing errors last time.
But then I run again and ```

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PAPRIKA
libdvdnav: DVD Serial Number: 37469312
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ajzimmerman/.dvdnav/PAPRIKA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00008ce4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001dc85a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001dc86e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001dd923
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001dd937
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001dd96d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001dd981
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001e48cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001e48e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001e4937
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001e494b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003479c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003479ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00347e20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00347e34
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0034f80a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0034f81e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0037f059
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0037f06d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00387c69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00387c7d
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
[00000355] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000



```The thing is, the video may be f#cked up when I browse the individual VOBs, but when I play the movie through, even scroll through and everything, it goes fine.
And I'm doing each individually.

[[IMG]http://img253.imageshack.us/img253/7991/screenshot2fq2.th.png[/IMG]]("http://img253.imageshack.us/my.php?image=screenshot2fq2.png")
[[IMG]http://img84.imageshack.us/img84/7581/screenshot1nv8.th.png[/IMG]]("http://img84.imageshack.us/my.php?image=screenshot1nv8.png")

---

### Post by Elephantman5 on 2008-08-31
> **sloggerkhan said:**
> Don't know what Paprika encode you have, but I've got one in mkv container, plays back fine. If it's the DVD, use a player that supports menus well like xine-ui. (VLC is getting menu support, but last I checked was less than optimal.)

I watch a fair bit of anime and the best player I've found is the smplayer mplayer front end. With VLC I had a lot of subtitle problems, but smplayer makes it easy to use ***/SSA formatted subs.

Anyway, good luck.

PS: I like xine-ui tons, too, but its subtitle rendering makes it bad for anime. 
I use to play back all my DVDs, though. My top 2 linux media players are def smplayer, then xine-ui.

I found this earlier, and thought it was funny. 
[http://www.veoh.com/videos/v14227375XD2gcN2Y](http://www.veoh.com/videos/v14227375XD2gcN2Y)

I plan to look into xine. I've had it before, but the gstreamer shite kind of turns me off, even if I already have them installed, I'm used to vlc like a mofo.
I know what you mean about the subtitles and all that though.
And the menus. ;)

---

### Post by mc4man on 2008-08-31
Did you do any thing to try to make vlc the default dvd video player?
When your trying to play to play the individual .vobs they're **[B]not**[/B] being decrypted. Could be a couple of reasons, including related to above ?

Can you also try a different dvd to see if there's similar behavior?

---

### Post by forger on 2008-08-31
Close all your media related programs
Execute this in terminal:
```
sudo apt-get install --reinstall lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3 libdvdnav4
```
It will reinstall all your codecs.
Now try mplayer or any other media player (this does not apply for vlc)

You could try install and playing the file with ogle-gui
```
ogle - DVD player with support for DVD menus
ogle-gui - User interface to ogle (Gtk)
```

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> Did you do any thing to try to make vlc the default dvd video player?
When your trying to play to play the individual .vobs they're **[B]not**[/B] being decrypted. Could be a couple of reasons, including related to above ?

Can you also try a different dvd to see if there's similar behavior?

> **forger said:**
> Close all your media related programs
Execute this in terminal:
```
sudo apt-get install --reinstall lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3 libdvdnav4
```It will reinstall all your codecs.
Now try mplayer or any other media player (this does not apply for vlc)

You could try install and playing the file with ogle-gui
```
ogle - DVD player with support for DVD menus
ogle-gui - User interface to ogle (Gtk)
```


I just set VLC as default Multimedia player.

With other Dvd's VLC will continue to freeze when I right click and try to open from My Computer. (Also in the process locking my DVD-drive and not allowing me to open it. Even if I xkill VLC.)

I don't see why I should be bothering with any other player, when all the other players wouldn't open my dvd's. 
I mean, Before this I had installed all the gstreamer sh!t and had both xine and kmplayer, and also gnome's default movie player. None of them would open my dvd.
And now all of a sudden vlc *kind of* opens it, but doesn't work when opening the disk from anything other then manually inside vlc. I will restart in a second, now that I've set vlc as default, even though I don't think it will do anything. I mean, thanks forger, for recommending the command, and I will refer back to it, but I don't understand why everything is having problems with opening from the context menu; as well as, the other programs wouldn't even playt he dvds by opening from the inside of them as well.
So, even if I terminalled to some other player, say mplayer, and tried to open the disk, it would say "Seek failed", or xine would say some other sh!t.

---

### Post by mc4man on 2008-08-31
> Opening vlc in terminal and opening DVD from the file menu works.

Is that still true?


> I just set VLC as default Multimedia player.
How exactly did you do that and have you done this more than once?

 > VLC will continue to freeze when I right click and try to open from My Computer. (Also in the process locking my DVD-drive and not allowing me to open it. Even if I xkill VLC.)
possibly related to above


If you set it to default then what happens when you insert the disk. Does vlc autoplay properly?

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> Is that still true?

Yes

How exactly did you do that and have you done this more than once?
----Preferences, preferred applications
 
possibly related to above


If you set it to default then what happens when you insert the disk. Does vlc autoplay properly?
When I insert the disk, nothing pops up, it just has the disk mounted on the desktop, and when I right click, it shows Open, and it Opens like a data folder, doesn't show VLC or any other program in the shell context. 
When I go to open with (Which I can only do in My Computer, not on the Desktop), it does the same thing, freezes and locks my drive, and runs the disk in the background in spite of my xkill.

---

### Post by mc4man on 2008-08-31
> I just set VLC as default Multimedia player. 
> How exactly did you do that and have you done this more than once?

Would be most helpful

---

### Post by Elephantman5 on 2008-08-31
I answered your questions, they were embedded inside my quoting of you. ;)

 					Originally Posted by **mc4man** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5698602#post5698602") 				
 				[I]Is that still true?

Yes

How exactly did you do that and have you done this more than once?
----Preferences, preferred applications
 
possibly related to above


If you set it to default then what happens when you insert the disk. Does vlc autoplay properly?[/I]

---

### Post by sloggerkhan on 2008-08-31
Pretty sure xine does not use gstreamer framework.

---

### Post by mc4man on 2008-08-31
>  I answered your questions, they were embedded inside my quoting of you
I skip over myself.
> Preferences, preferred applications
That won't do much. (which is a good thing

> Is that still true?
Yes
Then nothing's wrong with vlc

Go here and follow intsr. **exactly**, it's late I may or may not hang

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by Elephantman5 on 2008-08-31
I installed xine again, and up it pops when I put the dvd in.
So, unless there's a reason to keep vlc, then I guess I should switch over.

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> I skip over myself.

That won't do much. (which is a good thing


Then nothing's wrong with vlc

Go here and follow intsr. **exactly**, it's late I may or may not hang

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

I have a surreal feeling that it will be just fine anyway.
I think this will work, and if it does, I'll post results, and close the thread. Thanks for your help mc4man

---
Yep. Turns out everything worked out. Changing the GNOME defaults list sure saved the day.
Really glad I figured that out. Cool beans.

---

### Post by mc4man on 2008-08-31
> I installed xine again, and up it pops when I put the dvd in.
So, unless there's a reason to keep vlc, then I guess I should switch over

There is a difference between having a particular app set as default **choice** and having them as a default **choices**.

For instance right now I have vlc set as default player in file management.
I have as default choices for dvd playback - totem-xine, vlc, gmplayer, and auto running a script.

All default choices are available from r. click menu.

The default player is what runs when you insert a disk. (and can be any of your choices

Holding down the shift button while inserting a disk will give you a pop up of all your default choices

---

### Post by Elephantman5 on 2008-08-31
> **mc4man said:**
> There is a difference between having a particular app set as default **choice** and having them as a default **choices**.

For instance right now I have vlc set as default player in file management.
I have as default choices for dvd playback - totem-xine, vlc, gmplayer, and auto running a script.

All default choices are available from r. click menu.

The default player is what runs when you insert a disk. (and can be any of your choices

Holding down the shift button while inserting a disk will give you a pop up of all your default choices

Thanks for piecing this together with me.
I've spent all day tinkering around. Got Foobar working, and such.
[http://ubuntuforums.org/showthread.php?t=906047](http://ubuntuforums.org/showthread.php?t=906047)

Yeh, I'm slowly getting the commands for linux. I think I have to go into Configuration Editor to make a Send to Trash keyboard shortcut.

And your little tutorial totally made things easier. Now all my windows are in list with small icons. ;)

Another thing I'm going to try to configure, is what Fluxbox does with the resizing of the windows to the contents of the folder. And maybe that thing where it shrinks it to the title bar like macintosh has.
I don't really like the thought of switching back and forth between windows managers, so I'll try to get it done in GNOME eventually somehow.
I'm sure there has to be a way.
GNOME is way better I think. It feels homey, don't like Fluxbuntu or Xubuntu.

---

