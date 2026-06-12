---
title: "Is there a player than can both work on Ubuntu and also play multimedia files?"
date: 2009-05-26
forum: Multimedia Software
---

### Post by siddartha on 2009-05-26
I used to test a lot of multimedia players. 

All meaning in fact only one codec list maintained by the MPlayer community and hijacked (or used if you preffer) by all the others.

All meaning mplayer backend, xine backend and it seems that VLC uses its own backend. Oh, and gstreamer which is as interesting as the windows libs for the two bit programmers, but not very useful.

17 years after the introduction of avi, they all are able to play in decent conditions the avi format. And the bugs are always shifted on the shoulders of the initial designers who didn't bother to think about multimedia 10 years after.

Now, my files are in Matroska. That is a decent format with a decent documentation and mature although being less than 10 years old it's hard to be supported by the Linux programmers.

So, from all the junk installed over the time, all from the same category of multimedia players and all doing wonderful and buggy playlists while trying to clone WinAmp or some other Windows software this is that I have on:

* Mplayer. Wonderful work. The ones who do bother to have the codecs. The first working player for Linux. One thing: it has pulse support, yet Ubuntu doesn't output any sound. It's not the only one affected by this change. The hot-heads over at the Ubuntu HQ decided to push pulse audio. The first time it was almost unusable - 8.04. The second time around they fixed their choice of apps and not much more - 8.10. In the list of 9.04 there is no mention of "we finally made pulse work at least as well as esd" so probably 10.10 would be the distro of choice. So far - excellent display, yet no sound.

* Gnome Mplayer. Nice interface. Got it through getdeb. All the advantages of Mplayer above... and no sound. Guess Gnome in the name stands for cute Gnome interface buttons and not actual integration of mplayer. Useless.

* Kaffeine. Used to be the only choice for Gnome. Everything works. But the sound. Otherwise bloated and slow to start.

* Movie Player. Or how the people over at Ubuntu try to mask the Totem player and escape the problems. I have no idea who was the guy who chose that one to be the main player. It used to have stability and display issues. Now, some of the visual problems still exist - like making full screen means keeping some artefacts around the display area. Thank God the issues with Gnome notifications making a black unusable rectangle in the display window is gone. Hehehe - official player of Gnome and it can't handle the Gnome pop-ups. That makes me scared with the overnight Ubuntu hack of unified notifications which are not supported by Gnome. The sound is good. The player is too dumb to use anything but the default sound card. Most matroska files are unplayable. But we can download junk from utube as of 8.10.

* VLC media player. On the outside it seems to be almost as good as Kaffeine. Even the sound does work. But they are using their own work for back end. And as with all guys who do graphical interfaces - that is way over their league. A movie that works well with mplayer or xine will have ghosting (especially with matroska) meaning it will skip some important frames and the action is put on top of the landscape 10 seconds ago. Also it will play well both the sound and the cute little time bar yet the image will stay frozen for up to 2 minutes. And loading a subtitle file manually would lead to funny happenings. VLC used to pause the film and the subtitles would go on and when you unpause the the film the subtitles are not resynced. Now it might pause the subtitles and not the film with the same no-sync when you unpause. This is the only example who begs for leaniency as it is a Windws program ported to other systems (the same thing as with Firefox which shouldn't be packed with a Linux distro). A few sub-versions ago you were unable to use the keyboard shortcuts unless you selected the time bar, meaning you had to use the mouse meaning you could use the mouse for the other commands as well.

So - is there a player that can meet up the challenge and do the jobs its supposed to do also on an Ubuntu system?

---

### Post by siddartha on 2009-06-12
Finally found the answer to these issues. Ubuntu finally reached the Windows '95 milestone. As implied, it does all sorts of assuming and autodetecting under the hood and the results are unpredictable. The reality is that I have two sound cards activated on my system. And pulse assigns by its own algorithms which is the card to be used. Of course, the windowish "control panel" gives the option of choosing a main output/input device. Still, some apps are assigned a different choice. Just go over to "pulse audio device chooser", click on the new icon popping up in the system tray and choose volume control. In the playback tab you will have a list of applications that use the sound system and you can redirect the output to a different card. In the recording tab you can do the same for choosing the input for the given app.

For real easy systems you can get at the supermarket it would work out of the box the same as with Win95. Give it a more complex system and it will give you the option to waste a few nights digging through various apps as there is almost nobody ready to help with anything more complex than how do I change my brownish background?

---

### Post by sandy8925 on 2009-06-12
You are using 7.10 which is quite old. The problems you had with sound might have been fixed already in the newer versions.

You could try using Geexbox. It's pretty nice,uses mplayer and is around 19 MB now. It's a separate OS and not an app.

---

### Post by siddartha on 2009-06-14
My mistake. Recently upgraded to 9.04. Before that things seamed to go fine. With 7.10 there were less issues.

---

### Post by doas777 on 2009-06-14
have you installed teh ubuntu-restricted-extras package and the medibuntu repositories?

---

### Post by siddartha on 2009-06-15
Yes, in order to get updates and the restricted codecs.

---

### Post by siddartha on 2009-09-05
Actually even better is SMplayer. KDE team once more beating Gnome. It has all the features of Mplayer, even the ones added in the last year (something Medibuntu never heard of). It can even remember where you stopped a certain file.

As for my problem everything seems related with this stupid idea of installing pulse. OSS4 goes somehow better than alsa plus pulse and a bit lighter on the CPU than alsa without pulse.

---

