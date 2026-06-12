---
title: "[SOLVED] Feisty mpg play not working"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by ajgreeny on 2007-03-31
Can someone help, please.  I have installed the beta feisty 3 days ago, added kubuntu-desktopas an added desktop, and all is great except that i can't get any mpg or avi streams or downloads to play, though mp3 and wmv are no problem.  I have installed the restricted-extras, libdvdcss and w32codecs along with all the gstreamer packages that appear to have any bearing on the problem but still no go.

Can I presume that easyubuntu will be available at some time in the future to ease things along in this department.  As it happens, I have added the medibuntu repos so I assume that I can get all the packages that will be available in easyubuntu when it comes.

Am I missing something that I just haven't thought about or is this a known problem of feisty at the moment.  A search of the forums seems to suggest thst I have done everything needed to get my media player to work with all video formats but perhaps I'm wrong.

Any thoughts anyone?

Otherwise great version of the best linux distro.

---

### Post by johnny4north on 2007-03-31
i had the very same problem, but the resricted-extras fixed mine.  do updates twice, restart pc, then add/remove AptonCD{to back up Packages}.  use AptoCD to burn current packages to an Cd.  I made a mess of my ubuntu, im suprised it didnt crash.  The AptoCD will save you alot of time if you need to reinstall.  r u using mplay or totem?  mplayer- i had to set the Preferences-Audio to "OSS/ioctl audio output"  Video to "xv X11/Xv" and checked the "Enable direct rendering" Click OK restart Mplayer ..  the only other thing i can think of is to check your system for restricted drivers loc=panel,system,administration, then restricted drivers manager. please post your errors if possible. i follow up later tonite.  johnny out..thank you Ubuntu

---

### Post by ajgreeny on 2007-04-01
Thanks for your comments.  I actually use kde and not gnome mostly though I do find totem-xine a good small video player.  Usually, however, kaffeine or mplayer are my choice for video playback.  I haven't fiddled with the config of either yet except for trying several of the video decoders in mplayer (none worked).  I use the kaffeine-xine engine, which is brilliant in dapper, and seem to have everything almost the same in both installs, so am completely baffled.

What i find so unusual is that wmv will play with no problems but mpg, mpeg, mov and avi will not.  I will try reinstalling the codecs a nd restricted-extras again to see if it helps.  I'll report back when I've tried it all out.

---

### Post by ajgreeny on 2007-04-02
Still not working as I would like, but at least I have managed to get the files to play using vlc.  This really bugs me when I have done everything that others have without the same success.

Seeing as this is a test bed for the beta install, I may start again frim scratch and try without putting kubuntu-desktop on top of ubuntu.  Perhaps this is confusing the system, it is only beta after all.

Thank goodness everything works superbly in dapper, and it's a good job that this will be supported for such a long time.  It is going to be very hard to beat!

---

### Post by richbarna on 2007-04-02
> **ajgreeny said:**
> Still not working as I would like, but at least I have managed to get the files to play using vlc.  This really bugs me when I have done everything that others have without the same success.

Seeing as this is a test bed for the beta install, I may start again frim scratch and try without putting kubuntu-desktop on top of ubuntu.  Perhaps this is confusing the system, it is only beta after all.

Thank goodness everything works superbly in dapper, and it's a good job that this will be supported for such a long time.  It is going to be very hard to beat!

Just another suggestion:
> sudo apt-get install alsa-oss

I know you have probably already done this, but it's good to check anyway.

---

### Post by ajgreeny on 2007-04-03
I have alsa-oss but that doesn't do the job.

---

### Post by sdowney717 on 2007-04-03
run from a terminal window mplayer nameoffile and gmplayer nameoffile and see if you get decoder errors etc...

---

### Post by Marsolin on 2007-04-03
I installed libxine1-ffmpeg, libxine1-kde, and libxine1-plugins to get mpg playback working in Kaffeine.

---

### Post by ajgreeny on 2007-04-03
WOW!  Thanks Marsolin, that did the trick.
The only question the whole saga raises is why on earth are those libraries not required as a dependency of something already installed theoretically to play wmv, avi, mpg, etc etc.  Anyway that was exactly the answer I needed, so I am now almost in a position to replace my dapper with feisty when I'm ready, I'm just not sure if I want to do it yet, with dapper all set up exactly as I want.

Maybe when Linux Format magazine in the UK gets feisty on its cover disk I'll take the plunge, and avoid some of the hundreds of updates from beta ubuntu which I've already downloaded, to full updated ubuntu/kubuntu.  I have a download limit which means I need to be a bit careful  of overdoing the downloads of big iso files.

Thanks to everyone for all the help and specially to Marsolin for the eventual solution.

---

### Post by Ateo on 2007-05-16
> **Marsolin said:**
> I installed libxine1-ffmpeg, libxine1-kde, and libxine1-plugins to get mpg playback working in Kaffeine.



All you really need are the first 2. libxine1-plugins pulls in a bunch of gnome deps.

---

