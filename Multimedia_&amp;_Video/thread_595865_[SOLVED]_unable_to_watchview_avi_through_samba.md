---
title: "[SOLVED] unable to watch/view avi through samba"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by mandrill on 2007-10-29
I'll try to state the problem simply, although I'm sure the answer(s) will not be.....

I am sharing the slave/media drives of an xp pro machine and a gutsy machine, wirelessly.  So far, I am able to see/access each in both directions with relatively little difficulty. (the xp box is slower to do so, but eventually gets there) I can watch/play video stored on the gutsy box on the xp box, (but not without it freezing occasionally), however, I cannot watch/play any files from the xp box on the gutsy box. I installed mplayer to cover the video codec issue, but totem keeps opening, even if I am trying to play music. Out of curiosity, I  tried to play the files on gutsy *from* the gutsy box logged in through samba and it did not work. 

Therefore, I have to conclude that this is probably a samba issue, a samba issue plus a codec issue, or some combination of both, or all of the above with a bunch of my own ignorance thrown into the mix. Lots of googling did me no good. 

Or, it could be that I am just delusional, and this will never work, no matter what. (see my threads on nvidia drivers and crashing X, or installing madwifi if you want some laughs)

Anyway, anybody know how to fix?

---

### Post by daengbo on 2007-10-29
Do you have any other kinds of files on the XP box that you could test, e.g. a text file that could be opened to see if there's a file permission problem or not?

Double-clicking on a music or video file will open Totem by default, unless you've changed which program to use under the Properties of the file.

MPlayer doesn't work 100% over the network, especially if you are using the standard Ubuntu method of connecting to a Windows share. If the connection requires authentication, MPlayer doesn't know how to do that.

You might try opening a terminal, typing mplayer, and copying the file (or dragging it) into the terminal. You should see a lot of information pass by. Some of it might contain the cause of your porblem. Paste that output in here, and I'll take a look at it.

Incidentally, you can try to click [this link]("apt:ubuntu-restricted-extras"), install the restricted extras package, and see if the videos will then play in Totem.

---

### Post by mandrill on 2007-10-30
Sorry about late reply. Events have been conspiring against me.

I can, in fact view msoffice docs and ldif files. No problem.

I had already tried changing the default program to open - no luck - it kept insisting on opening totem, and when I did get vlc to open, it  just sat there - no joy.

I ran mplayer from terminal - got no output string, just the Totem failure message stating that (for video) I needed the divx5 codec and (for audio) I needed the mpeg layer 1 cbr.....

I installed restricted when I installed Gutsy.

Apparently, I *am* delusional.

---

### Post by mandrill on 2007-10-30
Check this out:

 [http://ubuntuforums.org/showthread.php?t=306829](http://ubuntuforums.org/showthread.php?t=306829)

I would try it, but am not knowledgeable enough yet to quite figure out exactly how to do it.

Other research suggests cifs(?) or cfs(?) I can't remember exactly. Anyway, this is a known issue,   that may have more than one cause/solution, and I'm really not sure which one is correct/best, and even if I did I don't know how to do it/them.

---

### Post by kvonb on 2007-10-30
Yes, this is a rather silly problem that  really should be looked at by the developers.

The problem is that you have to "mount" the shared folder in order to be able to play movies from it, or even open/edit a text file.

Something Windows does automatically.

The good news is that it is quite easy to do.

First let's enable the extra repositories, on the menu, goto: menu->System->Administration->Software Sources, enter your normal login password when asked, then select all the boxes.  Quit and it will remind you that you have to update, let it do that.

Next open Synaptic Package Manager from your main menu under: menu->System->Administration->Synaptic Package Manager, enter your normal login password if asked.

Now use the search button in Synaptic and search for ***neigh***, it should show both LinNeighborhood and PYneighborhood.

I use PYneighborhood, but either will do the job.

Select it for installation and click on apply to download and install it.

When finished, look on your menu under System Tools, it should be in there, load it.

You will have to check it's configuration or settings menu I think to put any info in, like network names etc', but it is quite straightforward.

You should then be able to double click on a network shared folder and it will mount it on your machine, and you can use it as if it was actually attached to your computer :).

---

### Post by mandrill on 2007-11-01
First, let me say that this community is the best. Thank you to everybody. The help has been needed and appreciated.

Second, unfortunately, the fix described above did not work. Probably because it was not (for me) as straight-forward as it would  be for more experienced users. That, and its 4am.

In any case, I was already able to open documents and such before -  but either I failed to configure Pyneighborhood correctly, or something else is wrong. I still cannot play music, or view a video stored on the Windows box. Same codec errors as before. There are 3 machines on this LAN, but I don't see that as being an issue. Anyway......

 I'm going to bed now, and maybe the Linux Fairy will leave me the answer under my keyboard.

---

