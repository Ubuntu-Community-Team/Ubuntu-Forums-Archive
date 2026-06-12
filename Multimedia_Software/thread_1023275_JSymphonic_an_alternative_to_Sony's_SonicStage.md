---
title: "JSymphonic: an alternative to Sony's SonicStage"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Skiro'n on 2008-12-27
Hello everyone !

I create this topic to advertise and group comments about JSymphonic. (I'm the main developer)

JSymphonic is an alternative to SonicStage to transfer music from/to Sony's MP3 players. It is only useful for Walkmans which need SonicStage, last generation of Walkmans (expect Japanese ones) are MTP/UMS and ARE NOT supported by JSymphonic.

JSymphonic is a JAVA application (running on Linux/Windows/MacOS) meant to be stored on the Walkman itself to be launched from any computer having a JVM (Java Virtual Machine).

**How to get JSymphonic**
To get last version of JSymphonic, please visit  [the SourceForge's download page [here]]("http://sourceforge.net/project/showfiles.php?group_id=190494").

To get Java on Ubuntu, [read this]("https://help.ubuntu.com/community/Java").

**JSymphonic features**
Version 0.3.0a1
- Import files from the computer to the walkman (supported formats: .OMA, .MP3, .OGG, .FLAC, .MPC, .WMA)
- Export files from the walkman to the computer (supported formats: .OMA, .MP3)

Under development
- AAC support
- cover support (for generation with a skin)
- playlist support
- embedded player for preview

---

### Post by 3rdalbum on 2008-12-28
As the new Walkmans are drag and drop UMS, why can't you support them too? I'd like something that can automatically find a cover for my ripped albums and chuck them into the ID3s before sending it to my Walkman. I thought of writing it myself but I don't transfer music that often.

---

### Post by Skiro'n on 2008-12-28
Well, reason is quite simple: I don't have time to do so.

Moreover, most users prefer managing their players from the jukebox they're using (rythm box, amaroK, ...). And since there are many solutions to transfer music to MTP/UMS MP3 players, it is not a priority for me to implement a MTP or/and UMS support.

But, all is ready to support any king of players in JSymphonic (MTP, UMS, iPod,...) so if you want to join the team to implement the few missing things to enable all Sony's walkman generation, you are welcome !!

---

### Post by Verve on 2009-01-19
Hi Skiro'n!

First of all, thanks for giving me some hope not having to buy a new MP3 player because I abandoned Windows almost completely.
I have a NW-E407 and totally love the hardware - but the software it needs is pure crap.

So I tried to run JSymphonic but didn't succeed completely.
I managed to be able to see the files on the player and to ex and import - but if I export files, they can't be played and if I import a mp3, I get a "MG Error" message on the player.

Searching the web, I saw you already dealt with that problem on other boards, telling people they need the DvID.dat file on their player - which I have.

I'm running Ubuntu 8.10 (Intrepid Ibex) here and I followed the instructions for additional packages to be installed as written in the README.

Is there anything else I can do?

Thanks a lot.

---

### Post by kyoto on 2009-01-29
Thank you so much!

I have tried it and it works great with my NW-A3000. 
No VirtualBox for my NW needs anymore :p
I love it.

---

### Post by Skiro'n on 2009-02-24
@ kyoto: thanks ! Keep in mind that development is still in progress !!

@ Verve: I've already received positive returns from people having the same walkman as yours, so I'm sure it works !

As you said, you need this DvID.dat file (case is important). It must be in the same folder as JSymphonic's .jar or in its initial place, in the MP3FM folder.

Have a check of the configuration, and if you can't figure out what's going on, send me an e-mail, I will make you run some test (email: nicolas_cardoso <AT> users "dot" sourceforge "dot" net).

---

### Post by Skiro'n on 2009-03-13
I'm doing some code improvements and I need to have precise information about each walkman. I have already some info, [stored here]("http://symphonic.svn.sourceforge.net/viewvc/symphonic/documentation/NW walkman historic/Walkman_historic.jpeg?revision=271&view=markup").

Can you please all:
- check that your walkman is listed
- check that info about your walkman are correct
- complete cells with a "?"

and return me all comments.


Thanks for helping.

---

### Post by binbash on 2009-03-13
Nice software, however i do not like java based softwares and i prefer gtk or qt

---

### Post by Skiro'n on 2009-03-13
Well, to be honnest, me neither... but this is my first software and Java is quite easy to begin with and it is a simple way to make multi-OS apps.

But, as soon as JSymphonic will be in version 1.0, I will join the other developers who are making a C++ lib to control Sony's walkman. Once this lib will be ready, a plugin for amaroK could be developed (and a Qt or Gtk front-end may be developed!)... 

But I don't expect to release a version 1.0 before one or two years considering the current development speed... I hope that my walkman will last so long !!

---

### Post by x33a on 2009-03-13
hi, thank you for this awesome software. it is way better than the crappy sonic stage. i have been using this for the past 2 yrs, and only a few times has it given me problems. keep up the good work.

---

### Post by digbickman on 2009-03-30
I got JSymphonic_0.3.0alpha2.zip

When i transfer more than half say error and check log for more details

i go to help -> log
i get no log file

Now every single song title shows up as (unkown), well some show up as g or a)....very strange song titles

But when i play a track the proper ID shows up weird

and the files that say error on jsymphonic transfer show up on my player but it fails to play.

---

### Post by Skiro'n on 2009-04-08
First thing concerning the log file: it is only saved if configured so in the preference windows ("Interface" tab, "Log to file" check box should be checked).
Also, I'm using Kubuntu 8.10, and there were no file association between ".jar" files and the JVM so I did it myself. So, when I click on the app, it just starts. But I've noticed that the log file is saved in my home instead of being saved near to the program...

Concerning your trouble, I noticed quite the same recently when I tried to transfered lots of files. There is a problem with the database. I'm currently working on. I will let you know when a new build will be ready for test.

---

### Post by digbickman on 2009-04-10
Nice :guitar:

i'll be keeping an eye out for the next release

---

### Post by Skiro'n on 2009-04-14
OK, I confirmed that a bug is present on version 0.3.0a2 : MP3 files encoded with VBR method just can't be transfered.

We are close to release a 0.3.0beta version, I don't know yet if I will release a 0.3.0a3 version without this bug...

To wait, just browse the [SVN repository (click here)]("http://symphonic.svn.sourceforge.net/viewvc/symphonic/jsymphonic/branches/v0.3/") where I regularly build JSymphonic from the last sources. Builds in the repository are numbered with the date. Please note that the bug described here has been corrected in version 20090414 (today...)

---

### Post by jachy on 2009-05-05
I have same problem, waiting for a fix :)

Thanks for a great piece of software! \\:D/\\:D/\\:D/

---

### Post by Skiro'n on 2009-05-07
To wait for version 0.3.0 beta version, I made a quick and dirty 0.3.0 alpha 3 release.

This release is not official (there is no README file, and it is not available from sourceforge download page).

You can download it _[from here]("http://symphonic.sourceforge.net:80/download.php?list.3")_.


And it's a good occasion to announce that _[JSymphonic has now a website]("http://symphonic.sourceforge.net")_!! 
Well, the graphical designer and the webmaster are quite busy and they didn't have time to customize the theme... sorry for that...

---

### Post by digbickman on 2009-05-07
Hey thanks now i can transfer VBR mp3, glad you found out the problem

Im guessing you are still working on how the file names are not showing up in my player

---

### Post by Skiro'n on 2009-05-14
@ digbickman: You still have "unknown" title song !? Even with last version ?
If so, can you please try to reset your player and regenerate the database with last version of JSymphonic (just launch JSymphonic and click on the Apply button to generate the database again).

You should have "unknown" song title only when browsing your music. When you play a file, information should be correct. Am I right ?

What is your player ?

Note that the "unknown" bug was supposed to be solved (but only after reseting). At least, I didn't succeded to make the bug re-appear...

---

### Post by digbickman on 2009-05-14
> **Skiro'n said:**
> @ digbickman: You still have "unknown" title song !? Even with last version ?
If so, can you please try to reset your player and regenerate the database with last version of JSymphonic (just launch JSymphonic and click on the Apply button to generate the database again).


> You should have "unknown" song title only when browsing your music. When you play a file, information should be correct. Am I right ?
Yes that is how it shows up. Was this fixed?

> 
What is your player ?
I have the NW-A3000

> Note that the "unknown" bug was supposed to be solved (but only after reseting). At least, I didn't succeded to make the bug re-appear...


Should i press the reset button on the bottom of the player with a toothpick or go into the player's menu settings and press reset?

I did the toothpick reset and regenerated the database with the latest but didnt work.
I'll try with the players menu reset

Thanks

---

### Post by Skiro'n on 2009-05-15
> Yes that is how it shows up. Was this fixed?
Yes, it is exactly what I thought was fixed :-(

> Should i press the reset button on the bottom of the player with a toothpick or go into the player's menu settings and press reset?
I didn't know it was even possible to reset from the player's menu !? Try both.

If the "unknown" field are still present after reseting and regenerating the database with JSymphonic's last version, could you please send me all the database files so I can look at them !?
The database files are all the files in the OMGAUDIO folder WITHOUT the "10Fxx" folders (replace "xx" by an hexadecimal number: 01, 02, 03, ... 09, 0A, 0B,...). I don't need to see the music files which are in the 10Fxx folders, and you couldn't send me all your music ;-).
You'll find my email address [here]("http://sourceforge.net/users/nicolas_cardoso").

---

### Post by digbickman on 2009-05-15
ok so JSymphonic_v0.3.0a3.jar is not working for me... i know it's not official but just thought id like to let you know.

I do not have my walkman with me but i just noticed a 5/5/09 release JSymphonic_v0.3.0a2_build20090505.jar

I believe i have not tried that one out. Will try it and let you know what happens

---

### Post by digbickman on 2009-05-15
i just checked and JSymphonic_v0.3.0a2_build20090505.jar is giving me the same error as JSymphonic_v0.3.0a3.jar
the error is as follows exactly as spelled:
```

Error(s) during database updating
04CNTINFfile cannot be create
Consult the log file to have more info.
```

---

### Post by Skiro'n on 2009-05-16
I have changed the way this file is written, but I've checked it and even now, I don't succeed in making this bug appear.
Can you please send me the log file when this error is displayed ([click here to know more about the log file]("http://symphonic.sourceforge.net:80/page.php?2#12"))

---

### Post by digbickman on 2009-05-23
Ok so i have been busy with school finals and haven't been able to send the database. I sent it to your email (hopefully correctly).

A bit of an update
The pre-beta _build20090523
gets me the same error as stated above 

if i go back and use JSymphonic_v0.3.0a2_build20090414
it works successfully yet the songs show up unkown

I have attached the database and log file with the error on build20090523


EDIT: I just realized you cannot attach .log file 

here it is copy and pasted 

```
23 May 2009 12:14:21 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : Initializing JSymphonic...
23 May 2009 12:14:21 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:mountDevice : Mounting the device "disk-2"
23 May 2009 12:14:21 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
23 May 2009 12:14:21 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/disk-2/OMGAUDIO
23 May 2009 12:14:21 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : JSymphonic is ready!
23 May 2009 12:14:26 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
23 May 2009 12:14:26 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/disk-2/OMGAUDIO
23 May 2009 12:14:26 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
23 May 2009 12:14:26 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/disk-2/OMGAUDIO
23 May 2009 12:14:26 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInTread : Exportation started.
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInTread : Deleting files started.
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInTread : Import files started.
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChanges : decodeThread has started
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:decodeTitlesInThread : decodeThread has finished
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChanges : encodeThread has started
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:encodeTitlesInThread : encodeThread has finished
23 May 2009 12:14:42 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInTread : Writing database started.
23 May 2009 12:14:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInTread : Writing database finished.
23 May 2009 12:14:49 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
23 May 2009 12:14:49 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/disk-2/OMGAUDIO
23 May 2009 12:14:49 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
23 May 2009 12:14:49 [WARNING] org.naurd.media.jsymphonic.device.sony.nw.NWGeneric$1:run : [Ljava.lang.StackTraceElement;@1eacdc4null
23 May 2009 12:14:53 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
23 May 2009 12:14:53 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/disk-2/OMGAUDIO
23 May 2009 12:14:53 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
```

---

### Post by merlin_ie on 2009-05-28
Hi all. I've recently started to use Ubuntu (Jalopy). When I used Jsymphonic in Ubuntu 8.04, it worked fine. Now when I use it, if I transfer a song to my mp3 player (nw-a1200 model) it does not show in transfered list. I right click and check file size of song on desktop and it says 4.3mb but when I right click the song in transfer window of Jsymphonic, it says 0kb. I've included screenshots so you can see what I mean. It also says 0kb for ALL my music collection, but the songs play in Rhythmbox, Amarok, Movie Player etc. Now, I'm not sure if it is something I'm doing wrong, but if anyone can shed some light on this matter it would be excellent as I don't want to have to dual boot to winblows

[IMG]http://i198.photobucket.com/albums/aa307/simply-delta/filesize1.png[/IMG]

[IMG]http://i198.photobucket.com/albums/aa307/simply-delta/filesize2.png[/IMG]

---

### Post by Skiro'n on 2009-05-28
As surprising as it could be, this "0kb" stuff is not THE problem (I explain at the end of the post). 
Can you please try the last pre-beta version downloadable [_here_]("http://symphonic.svn.sourceforge.net/viewvc/symphonic/jsymphonic/branches/v0.3/") and confirm me the bug.

It is strange that it stops working after an upgrade... You say that once you pressed the "import" button, the selection you made in the local folder doesn't show up in the device side, right !? Are you sure to use the local folder and not the export folder !?

Can you please provide [_a log file_]("http://symphonic.sourceforge.net/page.php?2#12") when the bug occurs (with last pre-beta please).


*Concerning the "0kb": it can be explained because the local files are not scanned to read the info, so info are left as default: duration at 3:30, bitrate at 128kbps, size at 0kb, no format,...*

---

### Post by merlin_ie on 2009-05-28
Thank you for quick reply Skiro'n. I managed to get the problem sorted. I downloaded a tar ball from your site and I got the v0.3.0b to work so all is ok. There was a problem with one song, but hey, life goes on lol

in regards to sending output file, I wouldn't have first idea how to lol (only using Ubuntu FULLY for 2 weeks now so I'm still on steep learning curve) but if I have any more problems, I'll research and give you full details of problem

Keep up the great work :D

---

### Post by Skiro'n on 2009-05-29
How to provide log file is explained [_here_]("http://symphonic.sourceforge.net:80/page.php?2#12").

> There was a problem with one song
Can you please send me the file so I can correct the bug !? (nicolas_cardoso <at> users (DOT) sourceforge.net)

---

### Post by merlin_ie on 2009-05-29
Sorry Skiro'n but I don't have the mp3 anymore. I (think) I deleted it and got a new copy instead and it worked fine. I was converting some youtube videos to mp3's and that was the only one to not transfer. In the off chance I have a copy of it somewhere, I'll gladly send it to you or try same video again and see if I can reproduce the error

---

### Post by Skiro'n on 2009-05-30
OK ! Don't worry if you can't reproduce the bug.
I was just asking because I'm planning to release a beta version next week and a stable version not so far after. 
I know that JSymphonic works just fine in every day situations. What I'm looking for to release the stable version is "extreme situation".
;)


EDIT:
And I forgot to say that we have solved the problem digbickman was encoutering. It was an isolate case, but if you have the same problem, the next beta will solve it.

---

### Post by Skiro'n on 2009-06-01
Version 0.3.0 beta is out !!

[Link to download this version]("http://symphonic.sourceforge.net/download.php").

A stable version will follow soon, so please, report any bug!

---

### Post by meeples on 2009-06-02
hey first just to say im so happy i found this. ive been using ubuntu for a year and havent been able to use my walkman once because i couldnt transfer files so thank you for this :D

but i do have a problem. i downloaded 0.3.0beta last night. and its working fine i transfered an album and applied changes. but on the mp3 player although the songs are all there, when i press play i get "mg error" :( im usiing the NW-E407


edit: just reading back the forum. where do i get a DvID.DAT file? i dont have one...


but again THANKS:)

---

### Post by Skiro'n on 2009-06-02
The answer is written in [_the FAQ, here_]("http://symphonic.sourceforge.net/page.php?2#5").

---

### Post by meeples on 2009-06-02
thanks im trying to run MP3FM in virtual box xp but it cant find my mp3 player. think im gonna have to install xp on a partition :O

---

### Post by Skiro'n on 2009-06-02
Can't you borrow someone's computer (with Windows) for 5 minutes !?

---

### Post by Alex Kay on 2009-08-11
Thanks for a fantastic peace of software, it works flawlessly with my NW-E405! It even supports UTF8-encoded tags and file names (unlike sonic stage)

---

### Post by Optimus_Jazz on 2009-08-23
Hi,i've downloaded Jsyphonic no problem and reading the README.txt,it says i have to compile folders by typing a command into the console,but what console is this :oops:

---

### Post by Skiro'n on 2009-09-06
> it says i have to compile folders
If the README says so, you have downloaded the SOURCES !!

To not have to compile the program, just download the regular files.

---

### Post by ub_Kurt on 2009-11-30
Hi - First, Thanx !!!

I have question:  Where do the profiles get stored ?  After I got done with my profile, I started setting up one for my wife, and I saw that it was very similar to mine.  So I thought it might be easier to just copy mine and modify it for her.  Of course, I've spent ever-so-much more time looking for this than it would have taken to just go through the "standard" way.  But hey, that's the main point of me going to linux in the first place.  Also, having the profile location would also allow me to back them up.

Thanks, Kurt

---

### Post by ub_Kurt on 2009-11-30
Sorry - I'm a big dope - I just found "JSymphonic.xml", and it appears to be what I was looking for (right under my nose).

Thanks again, Kurt

---

### Post by Skiro'n on 2009-11-30
;)

That's right! JSymphonic creates a JSymphonic.xml file where it is launched to store the configuration.

---

### Post by pierolinux on 2010-01-03
Hi Skiro,
    thank you for the software. My NW-HD3 was unused for ages (I cannot stand SS) until I found your great SW on sourceforge.

I have tested it for a while now, and the only problem I have is I cannot playback the songs I export FROM the walkman back to my laptop. I am not sure this is related to JSymphonic itself however, here it is the bug description:

- Select a mp3 album on my laptop and import to my NW-HD3. The album is playable on my ubuntu 8.04;

- Apply the changes and try to play the album from the walkman: no problem at all. It plays and ID tags are there;

- Try to export the album from the walkman to my laptop: JS creates a folder with band/album and places all the files there. Files are named correctly, but they do not play as they are not recognized as Mp3. The error I get from Totem: "An error occurred - Could not determine the type of stream"

I am using:
- Ubuntu Hardy
- Sony NW-HD3
- JS 0.3.0b

I have the same problem if I repeat the steps above in Windows. What do you think? Might a walkman format help (the latest SonicStage asks for that if I try to use it).

Please let me know your opinion. I hope my experience will help you to improve the software.

Thanks in advance for reading this :)

---

### Post by Skiro'n on 2010-01-03
The bug you mentioned has been brougth to my attention not so far ago... and it is confirmed to be a bug in version 0.3.0beta.

The bug is corrected in the SVN repository, and I'm currently working on releasing a stable 0.3.0 version.

Waiting for this version, you can use the lastest build from the SVN repository, which can be found in the following folder:
[http://symphonic.svn.sourceforge.net/viewvc/symphonic/jsymphonic/branches/v0.3/]("http://symphonic.svn.sourceforge.net/viewvc/symphonic/jsymphonic/branches/v0.3/").
Just download the file named "JSymphonic_v0.3.0_extrabuild_DATE.jar" with the lastest date.

Thanks for using JSymphonic and reporting bug !

---

### Post by pierolinux on 2010-01-03
WOW! That was fast! :P

Thank you very much for the hint, it worked well.

I've also noted a problem with the ID3 tags. Let me know if you are interested in the description of the issue and I'll post it here. If ID3 tags are simply not 100% supported yet, just discard this last comment.

Thank you again for the support,

Piero

---

### Post by Love2MeetU on 2010-01-05
I installed Jsymphonic with Synaptic Manager, but although it comes up with the Menu click, I am unable to move files. It says "The path is not valid"

---

### Post by Love2MeetU on 2010-01-08
Hello? Any suggestions? Any at all?

---

### Post by Love2MeetU on 2010-01-09
After a lot of fiddling around, I discovered that the folder "OMGAUDIO" was *missing*. I had to create the folder, link to it in jsymphonic, then the problem was solved.

---

### Post by Skiro'n on 2010-01-11
@pierolinux: well, it depends in which direction you are talking... When importing music (from the computer to the player), all kind of tags should be correctly read.
When exporting music (from the player to the computer), there is nothing implemented yet. (Concerning MP3, tags ID3v2 are always missing, and tags ID3v1 are the same as they were in the original file)

@Love2MeetU: 
> Hello? Any suggestions? Any at all? 
No answer means no time to read your post, it doesn't mean that I have nothing to suggest. Anyway, developing JSymphonic is not my job, so please give me at least one week to answer... Secondly, the answer was in the documentation -> 4) Using JSymphonic -> 4.2) First run -> "If the device is plugged with an "OMGAUDIO" folder in it", so instead of lots of fiddling around, take the reflex to look for developers' documentation.

---

### Post by pierolinux on 2010-01-11
> **Skiro'n said:**
> @pierolinux: well, it depends in which direction you are talking... When importing music (from the computer to the player), all kind of tags should be correctly read.
When exporting music (from the player to the computer), there is nothing implemented yet. (Concerning MP3, tags ID3v2 are always missing, and tags ID3v1 are the same as they were in the original file)

Hi Skiro,
     that's exactly my experience, I guess. 

- PC --> Player 100% working
- Player --> PC 
.             | 
.             | --> No tag, if the original Mp3 was created using iTunes or SonicStage, 
.             | 
.             |--> working if the tags in the original Mp3 where written in Linux with EasyTag.

Glad to hear that's not a bug. I wish you all the best with future development. I'm sorry I cannot contribute to the project, but Java is not my cup of coffee ahem... tea, I meant :D

On the other hand, let me know if you need a tenacious tester ;)

---

### Post by jouni_ on 2010-02-06
Skiro'n

Thanks so much for this - can't wait to see the stable version.

In the readme html page, it says that you can store the jsymphonic.xml right on the device, but it always defaults to my home folder

Is there any way currently to store my xml file on the device or at least somewhere other than my home?

Not a huge deal but would be nice to at least hide away in something like ~/.jsymphonic/

---

### Post by chameleonate on 2011-01-22
First off -thanks so much for this software -it's truly awesome -and *almost* works!

One problem I'm having is that as I've ripped many albums with Wavelab it didn't preserve the meta info. I've placed the mp3's in my local folder in a subfolder entitled 'Alice in Chains' (eg) but when I transfer to my Sony NW a3000 it's simply called Unknown Artist.

I then unmount but when I check the Sony it simply has songs and not even an untitled playlist.

I've tried creating a titled .m3u file but still no joy. What am I doing wrong?

Cheers;)

---

### Post by chameleonate on 2011-01-27
No one has an answer to this?? Come on guys, save me from Sonic Stage!!!!

---

### Post by tgalati4 on 2011-01-27
Try using easytag and filling in the ID3 tags.  Sounds like Wavelab didn't use standard ID3 tagging or stored the data in a separate database.

And yes, Sonic Rage is as bad as it sounds.

Open a terminal:

sudo apt-get install easytag
easytag

---

### Post by Skiro'n on 2011-01-28
**jouni_ :** yes, you're right, JSymphonic config file could be hidden. The reason why it is not is because it is meant to be stored into the walkman, so as the program. This way, it is not so annoying to have it not hidden.

I guess you're lauching JSymphonic by double-clicking on it ? If you do so, Ubuntu recognizes that it is a java application and ask to the JVM to run it, BUT the default working directory of the JVM is then your home folder, whatever the java app location is. And since JSymphonic is storing the config file in the working directory (thinking it is launched from the walkman), it is why the config file appears in your home folder.

Waiting for me to release a new version with a hidden config file (and only god knows when that gonna happen...), if you want to change that behaviour easily (assuming JSymphonic.jar is indeed into the walkman), just write a shell script with the command "java -jar JSymphonic.jar". Launched this way, the working directory will be the folder were the JVM was called...


**chameleonate :** tgalati4 is right, one way to solve your problem is to fill in the meta data within your audio files. And I also encourage you to use EasyTag, which I consider as the best audio file tagger program I've ever used.

But there's another way, JSymphonic can guess the artist/album/title from the folders structure (for instance, "Artiste/Album/XX - Title.mp3"). To do so, open the properties window, go to the Transfer tab and under the section Tag utilization, pick the Never read tags option. You can set the folder pattern you're using (if you need help to build the pattern, just let me know).

---

### Post by chameleonate on 2011-01-29
thanks for that. I used another set of files with Tags in place and used a .m3u playlist which again wasn't recognised by the player. I made sure I exported this along with the files but the player failed to recognise it.

I am now using the Winamp fix which works really well but Jsymphonic is so much more straight forward that I'm determined to make it work!

Am I using the wrong playlist format here?

Cheers!

---

### Post by zyvy on 2011-04-18
hi
when I install MP3FM on dropdown list he dont see my NW-E407
I try that on virtualbox (winxp)
and on my friend;s comp with windows xp same thing
is there something I can do ?

---

### Post by Skiro'n on 2011-04-21
**chameleonate :** m3u playlist files are not handled by JSymphonic v0.3.0. Playlist file support is under development for the next release. 

**zyvy :** you are talking about MP3FM, but the MP3 File Manager program has been released by Sony, and I can't help you about it.
However, if you are actually talking about JSymphonic, your player NW-E407 belongs to the 3rd generation, and it is listed as "NW-E4xx".

---

