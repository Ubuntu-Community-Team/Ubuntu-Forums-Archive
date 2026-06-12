---
title: "Newbie learns to author &amp; burn simple DVD video from avi &amp; mpg DIY"
date: 2012-01-13
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-01-13
My Lenovo Thinkpad X61t doesn't even come with an optical drive so it was just recently that I learned how to author, convert, and burn DVD-video format files on Ubuntu.

While I realize there are many ways to create a DVD, I write this short DIY simply to help others as new as I was, and, perchance, improvements to the process may be suggested by the experts.

**STARTING POINT:**
We assume the simple starting point is any number of large avi or mp4 files comprising one or more 'titles' that the user wishes to burn to DVD format DVD media, with menus & subtites, such that the movies will play in any standard NTSC or PAL DVD player.

**PROGRAMS:**
We assume the following programs are installed:

[LIST]
[*]sudo apt-get install devede
[*]sudo apt-get install brasero
[/LIST]
**UBUNTU FORUM REFERENCES:**

[LIST]
[*] [ubuntu]                          [What do you use to verify a DVD image was successfully burned to optical disc?]("http://ubuntuforums.org/showthread.php?t=1907232")
[*][SOLVED]                          [Is there a conversion program that can flip an avi file 180 degrees?]("http://ubuntuforums.org/showthread.php?t=1905318")
[*] [SOLVED]                          [What 'magic' is needed to play a movie with subtitles (when srt files exist)?]("http://ubuntuforums.org/showthread.php?t=1905312")
[*] [SOLVED]                          [What player or converter do I use to play/convert a 'bin' and 'cue' video file?]("http://ubuntuforums.org/showthread.php?t=1905315")
[*] [SOLVED]                          [How to mount a video *.img file in Ubuntu so that you can use it]("http://ubuntuforums.org/showthread.php?t=1907182")
[*] [ubuntu] [Can you provide insight as to the intermediate files of DeVeDe DVD authoring]("http://ubuntuforums.org/showthread.php?t=1906577")
[*] [ubuntu]                          [Who decides where in the menus any particular application resides by default?]("http://ubuntuforums.org/showthread.php?t=1907274")
[/LIST]
                        **WALK THROUGH:**
Let's assume you have three AVI files comprising one movie title, and you have two MP4 files comprising a second movie title. Let's create a DVD disc suitable to play in any DVD player, with menus & subtitles as desired.

**SUMMARY:**

[LIST]
[*]Movie Title 1 (movie1a.avi, movie1b.avi, movie1c.avi), total size roughly 2.5 GB
[*]Movie Title 2 (movie2a.mp4, movie2b.mp4), total size roughly 2.5 GB
[*]We will create a DVD-format ISO image on your hard disk of these two movies (< 4.7 GB)
[*]Then we will burn that DVD-format ISO image to a single-layer DVD media DVD-format disc (< 4.7 GB)
[/LIST]
**Applications -> Sound & Video -> DeVeDe DVD/CD Video Creator:**

[LIST]
[*]Start the DeVeDe DVD/CD Video Creator program
[*]Select "Video DVD" (Creates a video DVD suitable for all DVD home players)
[*]Select "Title 1" in the "Titles" section
[*]In the associated "Files" box for Title 1, press the "Add" button (or drag & drop) to add the three related AVI
[LIST]
[*]Optionally, as you add, check various encoding options, e.g., PAL vs NTSC
[*]Optionally, as you add, click on the "subtitles" "Add" button to add subtitle files of the following formats: .sub, .srt, .ssa, .smi, .txt, .aqt, .jss or .a s s
[*]Note it's important to manually specify the LANGUAGE for subtitle files!
[/LIST]
 
[*]Back in the "Titles" section, press the "Add" button to create "Title 2" and then "Add" (or drag & drop) the three related AVI files for Title 1 into the "Files" box.
[LIST]
[*]Optionally check options and add subtitles as before.
[/LIST]
 
[*]Optionally check "[x]Create a menu with the titles" and select "Menu options" & "Preview menu" to customize your menu to pop up whenever the DVD is started, and whenever a movie title has completed (which is the default menu operation)
[*]Doublecheck your work (you won't lose anything by browsing the options menus)
[LIST]
[*]Optionally change the default wording of the titles in the "Title" section to the respective names of the two movies.
[/LIST]
 
[*]When you're ready, Press the "Adjust disc usage" button (IMPORTANT STEP!)
[*]Press the "Forward" button to choose the DVD video image name (e.g., MyDVD.iso)
[*]That's it!
[LIST]
[*]After about as much time as the movie would take to play, you'll have a DVD-format ISO image file on your computer hard disk.
[/LIST]
 
[/LIST]
**Applications -> Sound & Video -> Brasero Disc Burner:**

[LIST]
[*]Start the Brasero Disc Burner program
[*]Select "Burn Image: Burn an existing CD/DVD image to disc"
[*]For "Select a disc image to write", navigate to your movie.iso file
[*]For "Select a disc to write to", navigate to your hardware DVD burner
[*]Press "Create image".
[*]That's it!
[LIST]
[*]After about 10 to 15 minutes, you'll have a DVD-media DVD-format disc that is suitable to play on any DVD player.
[/LIST]
 
[/LIST]
**RESULTS:**
When you pop your newly burned DVD into any DVD player, the menu will show asking which title you wish to play. When you select that title, it will play. At the end of the movie, it will pop you back to the menu (by default), so that you may select the second movie to play.

Please comment and/or improve these simple steps to authoring your first video DVD!

---

### Post by rocksockdoc on 2012-01-13
Looks like I'm limited to 5 screenshots per post so I have to reedit the authoring screenshots down to just five.
- [**How does one most simply vertically concatonate <10 differently sized screenshots?**]("http://ubuntuforums.org/showthread.php?p=11608894#post11608894")

Start DeVeDe:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210786&stc=1&d=1326491893[/IMG]
Press the "Video DVD" button:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210787&stc=1&d=1326491893[/IMG]
Add the 3 AVI files for the first title:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210788&stc=1&d=1326491893[/IMG]
DeVeDe will automatically create a single movie out of the three AVI files:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210802&stc=1&d=1326506353[/IMG]

For each movie, there are settings you can change - but the defaults are just fine for most of us:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210804&stc=1&d=1326506473[/IMG]
Ooops. I am limited to five (5) screenshots. I'm not sure I can continue until I figure out how to concatenate screenshots;
- [**How does one most simply vertically concatonate <10 differently sized screenshots?**]("http://ubuntuforums.org/showthread.php?p=11608894#post11608894")

---

### Post by rocksockdoc on 2012-01-13
Here are the 'just-five' sequential screenshots for the burning of the ISO file to a DVD media DVD format disc:

Start Brasero:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210779&stc=1&d=1326490314[/IMG]
Choose to burn a DVD:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210780&stc=1&d=1326490314[/IMG]
Select the input movie.iso and the output blank optical DVD disc:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210781&stc=1&d=1326490314[/IMG]
When you hit "Burn", it will take about 10 minutes to complete:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210782&stc=1&d=1326490314[/IMG]
Voila!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210783&stc=1&d=1326490314[/IMG]

---

