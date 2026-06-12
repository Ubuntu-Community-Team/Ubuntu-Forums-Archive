---
title: "mplayer command for Pirates"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by Innova on 2008-01-21
I just rented Pirates of the Caribbean:  At world's End.  However, I can not seem to get the disk to play in mplayer.  Mplayer reports two chapter's on the disk.  When I try Chapter 1, I get the special features, chapter 2 gives me a black screen.

I need to use mplayer, because it is the only program that I could get to send DD 5.1 out the optical out on my sound card.

Here is the command that I am using:

mplayer -ac hwac3 -aid 128 -fs -ao alsa:device=plughw=0.1 dvd://1

Am I doing something stupid here?

---

### Post by kko1 on 2008-01-22
Hello.

I'd suggest (if you still have the rented disc and haven't solved the issue yet) trying the *-v* and *-osdlevel 3* switches to get the most information out of *mplayer*. (You can also change the *osdlevel* by pressing '*o*' while playing.)

When using the *-v* (verbose) switch, you get most information on the data (titles, chapters, etc) on the disc. *One note, I'm not sure if you're aware of it or not.* The primary units on a DVD are "titles" (not "chapters"), and one title can contain a number of chapters. So be sure to search the text output for the mention of "titles", and see how many there are.

(I don't have the disc, but I'd venture a guess that it would contain at least 5-8 "titles", probably more, some of which would be trailers for other movies, etc. etc. At least most mainstream movie DVDs I've seen do.)

This was just a 'stab in the dark', but - hope this helps, or hope you solved the issue yourself! :)

kko1

---

### Post by foresto on 2008-01-22
Just in case you overlooked this approach: 
You might try playing the dvd in vlc, and changing the Audio -> Audio Device menu setting *after* the main movie has started.  On my system, vlc likes to reset that setting every time a different video clip begins playback, which made me think for quite a while that it couldn't use my 4.1 speakers.

---

