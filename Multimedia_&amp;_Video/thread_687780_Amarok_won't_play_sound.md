---
title: "Amarok won't play sound"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by HammerHed on 2008-02-04
I have installed Amarok and had it playing fine, RhythmBox plays fine,  but it was taking forever to update the collection. So I installed MySql and set it up in Amarok and since then I cannot do anything to get it to play any MP3 at all.

I have Xine engine installed and have gone through all the support pages on the web I could find and installed all the necessary packages for Ubuntu 7.10 related to Audio, and still no joy.

I am ready to dump Amarok but it looks like it is a great tool, so where to from here.

Xine-check gives me no problems, see output: 

xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.1.7 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd0
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 I420 UYVY

What to do????

---

### Post by mandrill on 2008-02-04
Does going back to sqlite solve it?

---

### Post by HammerHed on 2008-02-05
No, I retried sqlite now but it takes forever to update my 20gb collection and does not play now either.

RhythmBox plays fine.

---

### Post by mandrill on 2008-02-05
HammerHed,

I have 20.7 gb on my slave on Ubuntu, and the pc is an antique (but effective). I use Amarok, too, I think its the best player out there, and you can mod it to not look kde-ish for us Gnomers. I also load all the music from my windows box (and vice versa), use SQLite,
never had a  problem. This sounds like a server config issue.I am not an expert with that, but  using Synaptic, I think I would opt to completely remove amarok, remove the (hidden) config files, use *sudo apt-get autoremove* to finish the cleanup, and do a fresh install, but stick with SQlite. Config files can be hidden in home folder and also /usr/share. 

Remember, if you didn't break it, you're not trying hard enough! post back if something blows up....

Good Luck!

---

### Post by HammerHed on 2008-02-05
Thanks for the feedback, will try and reinstall now. 

I'll keep you posted.

---

### Post by HammerHed on 2008-02-06
Well that was fun!

I marked Amarok for uninstall and accidentally removed most of my desktop, I could not stop the uninstall and panicked and switched off the PC, what a mistake as I could not boot into the Gnome.

So basically did a complete re-install of Ubuntu, and here I am back at the point of Amarok having no sound. 

Mmmmmmm this is a headache, although I have learned something, make sure you are certain as to whether you are removing the correct stuff.

I should have the music collection copied over in a few hours so will try again with Amarok later.

---

### Post by mandrill on 2008-02-06
I am laughing with you not at you because you have no idea how many times I have had to re-install Ubuntu!  No kidding, probably 6-7 times. They put out the new version before I finally got it somewhat right.

So, you made me curious today, and I installed mysql. It took it awhile and lots of cpu cycles before it settled down, but everything's cool. I did lose a couple decibels on the default sound, but fiddling around with the alsa settings fixed that. However, I noticed no increase in speed, or only slightly - I guess 20gb is small change for it. Here is the link to the guide that I used to install it, but lets get some sound out of it first. Do all the basics, you know, wires, set to alsa, seeing if it sees your sound card, codecs (thats what I'm betting on) etc....Anyway, I gotta run, its 1:50am. Post back if you have a mind to or PM me. Peace. 

[http://www.howtogeek.com/howto/linux/speed-up-amarok-with-large-music-collections/](http://www.howtogeek.com/howto/linux/speed-up-amarok-with-large-music-collections/)

---

### Post by HammerHed on 2008-02-06
Yea, I tried everything checked all the settings in Amarok Xine engine Alsa and still no joy.

If I run from a terminal: $ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x810d430 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x810d430 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)


I get no errors if I run: ~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.1.7 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd0
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 I420 UYVY

I have loaded all the related Mp3 drivers, such as libxine1-ffmpeg, gstreamer0.10-plugins-ugly, libxine-extracodecs, gstreamer0.8-mad, ubuntu-restricted-extras, etc.

And still nothing....

Quite a mystery really.....

I don't seem to have system sounds though, although RthyhmBox is annoyingly still fine..

---

### Post by mandrill on 2008-02-06
This jumped out at me : QObject::connect: Incompatible sender/receiver arguments. Are you KDE or GNOME? Did you leave it at sqlite?
 
Are you able to play radio streams? Are you getting the annoying little messages at the bottom left that says something like "unsupported file format" or, " no available demuxer"?

Do you have all your repositories opened up? Running amarok on gnome installs a bunch of  kde dependencies, and it won't work without them. (Strangely, I have been getting "tutorial dialogues" in my display since I installed mysql - stuff like "This is the Playlist" & "These are the Browsers"????? WTF?)

Anyway, I think you should make sure you have all the repos enabled, and then: time to get medieval....

*sudo apt-get update*......then, consider doing a complete obliteration of amarok, and re-install it from the command line. (You know - synaptic - mark for complete removal, then install and use gtkorphan (its safe), wipe the .amarok file in your home folder.....then use terminal to install amarok again. I've looked around quite a bit and have not found any definitive answers. Seems to me I had problems at first, as well.

I realize uninstalling and installing are a pain in the ***, but....you already have one.

---

### Post by mandrill on 2008-02-06
I ran $ amarok, just to see it - looks the same as yours.- you could try to re-install it over itself.....that's worked before on a couple things.....

---

