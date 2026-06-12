---
title: "vlc 1.0.2 - Cannot reorder files in playlist in 9.10 (karmic) and other playlist bugs"
date: 2010-02-27
forum: Multimedia Software
---

### Post by rifter on 2010-02-27
I am running the 32-bit version of Ubuntu 9.10 (Karmic) and VLC 1.0.2, which is the version supplied in that release.

If you load a list of files into a playlist (via add file or add directory) in that version, you can't change the order of the files.  What I mean by that is normally in vlc if you drag a filename from its place in the list to another spot, the file moves up or down in the list. Instead what happened with this is that vlc just ignores it and will not move the file.  So you have to manually add individual files to get the right order (which is bad).

Originally I was posting this in hope of finding a solution; however I have managed to find one that works for me, which I have posted _[color=blue][post=8892843]here[/post][/color]_.  This also fixed a lot of other bugs in vlc playlists which have annoyed me for years.  Since I previously found no help on the problem of ordered playlists, I'm posting this hoping people who have the same problem will find a solution.

One additional note. In my post I refer to a solution posted earlier in the thread for changing the gui of vlc to fix another issue with playlists. That process is necessary for this fix as well (I think), so be sure to follow those instructions also.  I linked all the posts that I refer to so you can easily find what you need.

Thanks for all the people whose posts helped and good luck to anyone who is struggling with these issues.

UPDATE 03-05-2010: The bugs came back ... all of them.  Maybe an update knocked the fixes out, but it wasn't a vlc update.   In any case what I had to do to fix this was go to the qt4 settings, pick a different GUI style from the one I had (cleanlooks) (I picked windows for this test), save, and the bugs went away. Then I was able to switch back to cleanlooks, save, and the bugs were still gone.  I don't know if this had to be redone because of a recent unclean reboot that I had to do or what, but that is how I got things back to normal.

New update: It seems that this fix did not completely work after all.  The reordering didn't work right (in that any file I tried to move to a different place in the playlist moved to the top of the playlist instead), and I can't save playlists that I reordered.  It's weird because when I did the above fix (changing the gui style back and forth) I tested and the playlist edited and saved fine.  But when I quit vlc again and started it up again it was broken again.  I think I may have to do the gui style change before I launch vlc every time in order for the fixes to stick, which would be bad. But like I said before, all of these playlist bugs in vlc are cross-platform (well at least windows and linux) and have been there for a long time (or at least repeatedly pop up).  
     I don't think making the playlist work is a high priority for vlc devs because if it was the playlist would cease being such a red-headed stepchild.  One other bug I hate that has never been fixed: when you select multiple files to add in the add file dialog they appear in semirandom order in the playlist.  This is especially a pain in conjunction with the other bugs.  Essentially the only way to guarantee you will be able to watch videos in the right order in vlc is to have them all in the same directory with names that enforce their order.  That is a kind of dumb hack/requirement.

---

