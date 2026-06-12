---
title: "Mediatomb, mkv and the DSM-750"
date: 2009-04-22
forum: Multimedia Software
---

### Post by theluddite on 2009-04-22
Mediatomb was working ok with my D-Link DSM-750.  I was having sync issues with pretty much all of my avi files and I had to transcode mkv on the fly to get them to play, contrary to the hardware's literature.

Then I realized that the line that refers to the DSM in the config.xml is incomplete.  It says it simply needs to be uncommented, but in fact you need to change redsonic.com to [http://www.redsonic.com](http://www.redsonic.com).  

Suddenly my sync issues were gone, and I was able to play mkv files without transcoding except if the audio was the A_DTS codec -- then no sound.  The other issue that I had was that my the Video container in my database was overwritten whenever I imported music or images so I'd need to navigate to the PC directory to play movies.

Well, in trying to fix my database issues, I reinstalled and reimported everything.  Not only did I not succeed in fixing the database problem, but now none of my mkv files will play.

Does anyone have any suggestions as to how to fix my database?  I've tried a number of different iterations of the import.js (although I'm not a java coder) and I'm fairly certain that's not my problem.  It has something to do with how that one line ([http://www.redsonic.com](http://www.redsonic.com)) interprets my database.  Can anyone tell me what that line of the script actually does? 

I also need to figure out how to get mkv files playing again, especially with A_DTS audio.  Is there a way to transcode only the audio to AC3 using ffmpeg?  Can anyone suggest how adding that [http://www.redsonic.com](http://www.redsonic.com) line fixed my mkv files in the first place?  I've tried to recreate the circumstances (i.e. importing files with the line commented, then uncommenting it), which allowed me to play them for a brief time but it didn't work a second time.  I've spent hours on this and it's really getting me down because I know it's possible!!!

---

### Post by theluddite on 2009-04-23
Well I'm able to play my mkv files again -- but still without sound.  I still need someone to give me a hand with the ffmpeg command that'll transcode **only one of the audio streams** from DTS to AC3.

And I still need someone to suggest what the "redsonic.com" line in config.xml does so I can figure out why it screws up reading my database.

---

### Post by theluddite on 2009-05-07
Here's the link I used to figure out how to transcode the audio from DTS to AC3:

[http://http://www.networkedmediatank.com/wiki/index.php/Convert_DTS_to_AC3]("http://http://www.networkedmediatank.com/wiki/index.php/Convert_DTS_to_AC3")

It doesn't transcode on the fly but whatever, it doesn't take very long.  So now my only problem is that my hardware is still not properly reading the database.  Again, I need someone to tell me what the "redsonic.com" line in Mediatomb's config.xml file does.

---

