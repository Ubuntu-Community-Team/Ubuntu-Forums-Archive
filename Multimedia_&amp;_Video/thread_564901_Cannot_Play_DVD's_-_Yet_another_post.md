---
title: "Cannot Play DVD's - Yet another post"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by rodgerpb on 2007-10-01
Hello - I am yet another new user having trouble getting any DVD's to play

I have tried installing M-Player using the following sequence

sudo gedit /etc/apt/sources.list
enter these two lines and save your file
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

sudo apt-get update
sudo apt-get install mplayer

I installed libdvdcss2 and w32codecs as follows

sudo gedit /etc/apt/sources.list

then edited the sources.list file with
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

I entered the following line
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Not quite sure what that does - but it responded OK from the terminal

and then typed

sudo apt-get update
sudo apt-get install w32codecs libdvdcss2

Following from another thread, I also checked  that I had 
libdvdnav4
libdvdread3
libdvdplay0

using Synaptic.  Some of these were not installed - so I allowed Synaptic to install them

I can also see from Synaptic that 
W32Codecs is installed (Version 1:20061022-0.1)

As it stands M-Player just stres at me and does nothing.

I previously had Totem and Totem-Xine
I uninstalled them from Synaptic and then Unintsalled and re-installed M-Player.

Please help - this is really frustrating.

My DVD is a brand new Panasonic multiburner - my previous one had a hardware fault and was not mounting volumes correctly.

This is my sources.list file
```

## Added next four lines October 2007 and commented out the two lines after that

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe
## deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.debian-multimedia.org etch main

```

---

### Post by Cariboo1938 on 2007-10-01
Hi all,
I join in rodgerpb's cry for help...Cannot Play DVD's in my new Feisty 64-bit installation...
I went through all the posts I could possibly find and ended up installing "gxine" (see [HERE]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd")). 
Now I get the message from gxine that no "demuxer" is found.. (see attachment)
What on earth does this mean?

---

### Post by TheThinker on 2007-10-02
> **Cariboo1938 said:**
> Hi all,
I join in rodgerpb's cry for help...Cannot Play DVD's in my new Feisty 64-bit installation...
I went through all the posts I could possibly find and ended up installing "gxine" (see [HERE]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd")). 
Now I get the message from gxine that no "demuxer" is found.. (see attachment)
What on earth does this mean?

Oh, that's normal. It's a bug in Gxine that prevents it from loading the demuxer when it automatically starts up after you place a DVD inside the drive. If you have all of the necessary files (such as libdvdcss2, libdvdnav and libdvdplay) then you should be able to play the DVD anyway. Just exit out of that error message and select the DVD drive from gxine's play menu.

As for you, Rodgerpb, my best guess is that you're missing the MEncoder package. Here a link to the wiki for more info:

[https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder)

Have you tried playing different DVDs to see if you get the same results? These players and their necessary files are designed to play MOST DVDs. This means that some DVDs (roughly 20% in my experience) will utterly fail, and they're typically brand new DVDs that just came off the box-office. That's more likely due to the advanced encryption methods the newer DVDs tend to have, so if you want to play say KING KONG for example it might not work. But that doesn't mean all the new movies won't play! Others like BATMAN BEGINS played flawlessly on my gxine player. :popcorn:

---

### Post by vinutux on 2007-10-02
go to add/remove programs and install all "gstreamer" plugins  [ie ugly bad etc]

everything working with totem after that


if u want install alternative media players install vlc[the best],mplayer or xine [xine-ui not xine lib]

............................

and not needed to add any lines to anywhere just select pakage from add/remove it will automatically ask and enabled restricted and other repos ............

:guitar:

---

### Post by rodgerpb on 2007-10-02
Thanks for your replies:  I have tried various remedies - unfortunately without success

This is applicable to all DVDs (including unregionalised copies).  I have particularly kept to older discs which might have newer encryption like Sony ArCoSS

Installed the MEncoder package

Also installed VLC (some difficulties with that at first with not finding libraries and then it seemed to work from the Command Line).  That installed OK.

With MPlayer - the console at first says "No Media Opened".  When I attempt to "Open" the DVD using Right Click ->Open I get an error box which says "Failed To Open DVD://1"

With the VLC player when I Click on the "Play" button it brings up an "Open" multitab box which has got the the DVD (menus) radio button checked, and the device name /dev/hdc and full mrl of dvd:///dev/hdc filled in.

It just will not play any DVDs

Is this still a CODECS issue or is there something in the DVD setup that is wrong.

You can see the directories and the files in the Computer icon

The burner is a new Panasonic burner (added after Ubuntu was installed).  The hardware manager does correctly see the burner (make and model).

All help from the experts and experienced recieved.

Thanks

Rodger

---

### Post by Cariboo1938 on 2007-10-02
> **rodgerpb said:**
> Thanks for your replies:  I have tried various remedies - unfortunately without success
--------------------------.
Rodger
Hello Rodger,
I went through all that and was about to give up until I found "VLC media player" which I installed with 'Synaptic Package Manager' (I guess you know how to handle that). It worked well for me and I can play any commercial DVD now.
Good luck

---

### Post by Cariboo1938 on 2007-10-02
> **TheThinker said:**
> Oh, that's normal. It's a bug in Gxine that prevents it from loading the demuxer when it automatically starts up after you place a DVD inside the drive. If you have all of the necessary files (such as libdvdcss2, libdvdnav and libdvdplay) then you should be able to play the DVD anyway. Just exit out of that error message and select the DVD drive from gxine's play menu.

Thanks TheThinker,
before I read your reply here I un-installed gxine and installed VLC media player instead. It works well for me and I didn't  have the nerve to try out your suggestions although I still have installed all the files you mentioned above. Do you know VLC? what would you prefer, VLC or Gxine?
Thanks anyway for the response.

---

### Post by Cariboo1938 on 2007-10-02
> **vinutux said:**
> 
if u want install alternative media players install vlc[the best],mplayer or xine [xine-ui not xine lib]
............................
:guitar:Thanks vinutux,
I installed VLC and it worked inmediately.
Thanks for the hint.

---

### Post by TheThinker on 2007-10-03
I'm still a little bit of a newbie, so I've yet to try out VLC let alone MPlayer. Gxine, being my first player to have, is actually quite good. There are many plugins installed to make the viewing experience more enjoyable, such as a post-video-processing plugin that adjusts the contrast, color, etc (definitely useful  when you're watching old anime vids). At the same time the settings are easy enough to understand without you needing to grab a manual of some sort. It's open-source as far as I can tell and is quite reliable.

Gxine isn't perfect of course. My brother has a desktop-laptop hybrid for a computer (just imagine a desktop tower that is half the size and you'll get the picture). For some reason, despite having the same files as I do, his Gxine fails to play any DVDs which suggests to me that it's a hardware issue. It would just say "Bad DVD" or something to do with the decoder not working. Very Strange. I sometimes run into that same problem with my player but I usually attribute it to my DVD drive being defective (it will sometimes open and close on its own, fail to detect CDs/DVDs, and it's done this even on Windows).

So I guess my answer to you Cariboo is to keep whatever works for you. If you ever do get tired of VLC try out Gxine, Totem-Xine, or any of the other free players out there. When it comes to that hardware issue I mentioned, sometimes  a different player will be the solution.

---

### Post by Cariboo1938 on 2007-10-07
> **TheThinker said:**
> Oh, that's normal. It's a bug in Gxine that prevents it from loading the demuxer when it automatically starts up after you place a DVD inside the drive. If you have all of the necessary files (such as libdvdcss2, libdvdnav and libdvdplay) then you should be able to play the DVD anyway. Just exit out of that error message and select the DVD 
Thank you, The Thinker 
I tried Gxine again as you recommended (select the DVD from the menu) - but no, it doesn't work! It still complains about the "demuxer". I'm certain that the packages you mentioned are installed. Do you know what could be wrong with my installation? VLC works fine, although I have to open the DVD from the menu here too.

---

### Post by TheThinker on 2007-10-08
> **Cariboo1938 said:**
> Thank you, The Thinker 
I tried Gxine again as you recommended (select the DVD from the menu) - but no, it doesn't work! It still complains about the "demuxer". I'm certain that the packages you mentioned are installed. Do you know what could be wrong with my installation? VLC works fine, although I have to open the DVD from the menu here too.

If you're certain that you have all of the files necessary, yet VLC works, what kind of computer are you running? That kind of info will help you to look through Gxine's configuration and tailor it to your specifications.

I don't have my computer in front of me (using my university's Mac) so please try to follow where I'm coming from. Gxine has a configuration window you can open through the first tab labeled file ( I think). Anyway, it lets you set your preferences. On that window there are many tabs, which can be confusing because a few of them are not named and are quite small. One of them, labeled DVD, has options that allow you to alter how the DVD drive works and how the DVD is decoded. The decoder option should be set to "Key" by default; try changing that to something else, saving it, and restarting Gxine to see if it works.

I finally got King Kong to work by this method. It turns out that the decoder option may be different for certain DVDs (probably most DVDs). I set it back to "key" (I had changed it to "Disk") and voila, the hairy guy is back in action!

If all else fails, check out Gxine's main website. Here's a link to their documentation page:

[http://xinehq.de/index.php/faq](http://xinehq.de/index.php/faq)

There are lots of other preferences you can change in that same window I mentioned. One thing to note: if you have a video card that is currently supporting Open GL graphics you may want to set Gxine's video driver to OpenGl; doing so made my video playback be very responsive to the controls. Other than that all I have left to say is experiment, experiment, experiment. Just don't forget to save and restart Gxine to see the results.

---

### Post by TheThinker on 2007-10-29
Here's an update for the help I just mentioned. I just installed Gxine on my brother's computer and realized the common denominator that is preventing your Gxine from working. You need the libxine-ffmpeg file from the Ubuntu repositories. Get that installed and it should be able to decode ffmpeg and others like Quicktime. I find that without libxine-ffmpeg the program gives me that same error message "Demuxer not found". I hope this finally nails your problem Cariboo.

---

### Post by Cariboo1938 on 2007-10-30
**[COLOR="Blue"]Gxine DVD Media Player[/COLOR]**
The following packages are needed:
build-essential
debhelper
fakeroot
gxine
gxineplugin
libdvdcss2
libdvdread3
libxine1-ffmpeg
libxine1-gnome

I used -->Synaptic Package Manager to install them. 
One also could run the command 'sudo apt-get install <packages>' in the Terminal. 

I don't use VLC media player anymore and un-installed it.
 
Thanks to the terrific support of "TheThinker" I have the Gxine, i.e. DVD movie playing, running to my satisfaction.
For me, the Case is closed!:)

---

### Post by TheThinker on 2007-10-30
Don't forget to mark this thread as "solved" using the tools located above your first post. This helps others flock to this thread in case they need similar help. And you're very very welcome! :)

---

### Post by Cariboo1938 on 2007-11-01
> **TheThinker said:**
> ........ mark as "solved" using the tools located above your first post.  :)
How do I have to do that?
I can't find the "tools located above my first post"
Sorry, maybe I'm a little slow today....:(

---

### Post by seachnasaigh on 2007-11-01
Rodger ... this may seem like a stupid and somewhat late response, but somewhere in your thread you mentioned that Ubuntu doesn't see your Panasonic drive, and that you installed it after you'd installed Ubuntu. Does it show up under /dev/mnt? Could this be a simple mount problem? Just a late-night thought ... I'm relatively new to Ubuntu (though not to Unix in general).

---

### Post by TheThinker on 2007-11-02
> **Cariboo1938 said:**
> How do I have to do that?
I can't find the "tools located above my first post"
Sorry, maybe I'm a little slow today....:(

Forget it. I forgot that rodgerpb started this thread, and so only he can mark it "solved". In case you're wondering, it's the button marked "thread tools" locaed above the first post. Yes, I've been quite slow too! (sigh) College is wearing my memory down quite a bit it seems.

---

### Post by jwo7777777 on 2007-11-02
I am running kubuntu and xine gives the same "demux" error trying to play DVDs (even though I have tried all the blah,blah,blah install gstreamer, uninstall gstreamer, install codecs, uninstall toilet_flusher_plunger_multipass_bin_marvelous_thing.1.2.3.6.5vBETA1rc3 and whatnot)

This ffmpeg hint sounds like a winner.  Under windows running different players I have occasionally run into having to use ffmpeg to get output to go to the correct codecs.

I'll try it later today and confirm or deny.

---

### Post by digitalgecko on 2007-11-02
download automatix at [www.getautomatix.com](www.getautomatix.com)

It works for me

---

