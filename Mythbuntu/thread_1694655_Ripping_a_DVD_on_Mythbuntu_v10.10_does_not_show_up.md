---
title: "Ripping a DVD on Mythbuntu v10.10 does not show up in Library"
date: 2011-02-24
forum: Mythbuntu
---

### Post by sparafucile17 on 2011-02-24
Hello,

I have recently built a HTPC with brand new components and have loaded Mythbuntu v10.10 (clean install).  After getting the video/HDMI audio working on the DVD Player, I starting looking at the DVD ripping feature.  Right out of the box I am having difficulties getting the videos to show up in the Video Library.

I can start the ripping process and it completes no problem.  I even navigate to the folder and can see the file is present.  However, when I return to the DVD Library menu, it can't find the video!  Is there something simple I am doing wrong?  I assumed this would just work out of the box, but I guess not.  I have ripped a DVD as both a .ISO and .VOB thinking it was the format, but neither file is displayed.

I am very new to Linux (see experience level below) so please bear with me.  It is very possible, that some very simple thing is not setup right.  Any help is much appreciated...



My experience level:
NEVER installed or run Linux in my life.
Been working on PC's for the last 20 yrs.
Been writing code as a Software Engineer for 10yrs.
I am familiar with Cygwin, because we use gmake and gcc at work.


- Jeff

---

### Post by tgm4883 on 2011-02-24
> **sparafucile17 said:**
> Hello,

I have recently built a HTPC with brand new components and have loaded Mythbuntu v10.10 (clean install).  After getting the video/HDMI audio working on the DVD Player, I starting looking at the DVD ripping feature.  Right out of the box I am having difficulties getting the videos to show up in the Video Library.

I can start the ripping process and it completes no problem.  I even navigate to the folder and can see the file is present.  However, when I return to the DVD Library menu, it can't find the video!  Is there something simple I am doing wrong?  I assumed this would just work out of the box, but I guess not.  I have ripped a DVD as both a .ISO and .VOB thinking it was the format, but neither file is displayed.

I am very new to Linux (see experience level below) so please bear with me.  It is very possible, that some very simple thing is not setup right.  Any help is much appreciated...



My experience level:
NEVER installed or run Linux in my life.
Been working on PC's for the last 20 yrs.
Been writing code as a Software Engineer for 10yrs.
I am familiar with Cygwin, because we use gmake and gcc at work.


- Jeff

Is this machine a frontend and backend? Where does the file show up in the file system? If you hit M, then scan for changes when in mythvideo does the file show up?

---

### Post by sparafucile17 on 2011-02-24
> **tgm4883 said:**
> Is this machine a frontend and backend? Where does the file show up in the file system? If you hit M, then scan for changes when in mythvideo does the file show up?


D'Oh!  Well I didn't even know that there was a"M" option.  I knew I was being stupid about something.  Are there any more secret keys that I should be aware of in MythTv?  Anyways, scanning for files did the trick.  But I have two follow-up questions...

1.) Is there a way to have the scan option happen automatically?  Or at least after the completion of a DVD rip operation?
2.) Now that I see the movie... How do I get the metadata?  I seethe setup option to go to IMDB, but I haven't a clue how to trigger the IMDB fetch.  Does it matter if I only ripped a single DVD Title?

Thanks so much!  You Linux guys rock!

- Jeff

---

### Post by tgm4883 on 2011-02-25
> **sparafucile17 said:**
> D'Oh!  Well I didn't even know that there was a"M" option.  I knew I was being stupid about something.  Are there any more secret keys that I should be aware of in MythTv?  Anyways, scanning for files did the trick.  But I have two follow-up questions...

1.) Is there a way to have the scan option happen automatically?  Or at least after the completion of a DVD rip operation?
2.) Now that I see the movie... How do I get the metadata?  I seethe setup option to go to IMDB, but I haven't a clue how to trigger the IMDB fetch.  Does it matter if I only ripped a single DVD Title?

Thanks so much!  You Linux guys rock!

- Jeff

IIRC, You would need to configure Jamu to automatically scan teh videos and grab the metadata for you. It doesn't do it when you rip it, instead it is done on a schedule. I believe you can set this up in mythbuntu-control-centre.

The M key also allows you to grab metedata. It's one of the options, but I don't recall which one right now.

---

