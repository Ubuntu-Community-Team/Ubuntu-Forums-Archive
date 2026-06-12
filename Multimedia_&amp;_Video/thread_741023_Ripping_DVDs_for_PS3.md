---
title: "Ripping DVDs for PS3"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Agent Graves on 2008-03-31
Hey everyone!

I'm a new Ubuntu user running Gutsy and i'm trying to complete a project that seems a lot harder than it should be so I figured I'd bring my issue to you fine super users and see what your take on it is. 

I'm trying to set up a media center using my PS3. My plan is to digitize all of my DVDs and put them onto 2 external HDDs. I've tried a few different programs to facilitate a good rip from my dvds to a supported PS3 format, but so far the only thing that's worked is using DVD Shrink under WINE and ripping the main dvd to a single .VOB file with the reauthor funtion. This works fine (even though I have to restart my computer after almost each rip with DVD shrink for some reason) but i'm thinking that there's a better solution out there. 

I've tried most of what I can find of the Ubuntu native programs, and nothing seems to do it in a way that I need it to. 

Just to make things a little easier, Here are the supported PS3 video formats:

MPEG-1, MPEG-2 (PS,TS), H.264/MEPG-4 AVC, MPEG-4 SP

I'm looking for a program that can do the following:
-rip to one of the above formats
-rip it so that the file size isn't overwhelming
-rip the dvd in a way that won't take forever. (this may be unavoidable, and I understand that)

Like I said, I've tried most of the native Ubuntu programs, and maybe I just don't have the settings right. If that's the case what would really help me out is a program suggestion and the appropriate configuration. 

Thanks for taking the time to help me out!

---

### Post by dantrevino on 2008-04-01
HandBrake GTK, aka RippedWire is what you're looking for.  Its quick, an has presets for PS3, among others.  The deb available below works on gutsy, however, i have not actually tried to view the results on a PS3.

[http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322&release_id=553070](http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322&release_id=553070)

dan

---

### Post by Agent Graves on 2008-04-01
I did find Handbrake, but i've been having a heck of a time getting it installed. I've read over all of the documentation and I just can't get it right. When I try to double click the handbrakegtk file, it tries to open under WINE. Another thing I noticed was that handbrakegtk requires handbrakeCLI to work properly, and I haven't figured out how to get that installed either. Handbrake doesn't seem to have any suitable documentation on how to install either of these programs. Can you help me out with that?

---

### Post by Agent Graves on 2008-04-01
Never mind that last post, I just got it working. I'll give it a try and see how it works, then report back with how it went.

---

### Post by Agent Graves on 2008-04-01
Alright, here's what i've got for anyone who might be having the same issue.

As dantrevino suggested before, I installed the handbrakeGTK GUI with the .Deb package on the link listed above. Just run it through the installer and it's good to go. 

Open up Handbrake and put your DVD in the drive. open the disk and make sure that the settings are set to MPEG4 for both the Video codec and format selections. Start the disk and it'll rip the file. This filetype will play on the PS3.

---

