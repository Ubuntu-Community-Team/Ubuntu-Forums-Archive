---
title: "Howto/Script: Cuesheet Splitter for Lossless Audio files"
date: 2008-07-08
forum: Multimedia Software
---

### Post by ariel on 2008-07-08
[B][Update: cue-splitter 0.2 re-written in python/pyGTK > GUI, Batch Processing]
[/B]**[2011/04: 0.2.3 added split-to-FLAC, simplified GUI]**
**[2011/06: 0.2.4 added [File > Show the Log File] ****]**

[B] 

My use case[/B]

Some time ago I started converting my CD collection to FLAC for playback in my Linux media center. 

I chose to rip my CDs to single FLAC files + cuesheets, in order to preserve the inter-track gaps (classical CDs can be rendered un-listenable without this).

Every now and then, I upload a few of my CDs to my portable digital audio player. For this, I needed a practical tool to cut the single FLAC into Ogg & MP3 files. 

**The tool I needed**

Since I am not a real geek, I wanted to use Nautilus' context menu for this. I also wanted my tool to handle FLAC, APE and Wavpack (wv) files, as some of my older rips were in those formats. What's more, I wanted the tool to ask me the output base folder, in which a sub-folder would be automatically created based on the Artist and Album names. A standard gnome filechooser dialog would be used for this.

And pushing the boundaries even more, I wanted the ID3 tags in the generated MP3 files to be automatically filled-in based on the cuesheet file information, so my tiny new Sansa Clip player would be able to index the songs per album and per artist.

**The lossless audio file + cuesheet splitter script I wrote**

Unfortunately, I couldn't find any existing tool to suit my exact needs, so I wrote my own tool, which does all the above, and using the nautilus-scripts package, can be nicely integrated into nautilus.

The cue-splitter script I wrote provides support for UTF and non-UTF-encoded cuesheet files, properly handling accented characters in filenames and songnames (tested with spanish and french accents), generating non-accented filenames for the mp3 cuts, but preserving the accents in the ID3 tags.

**Update**: as a Python-learning exercise, I rewrote the original bash script in python/pyGTK, adding a GUI (pardon my total lack of GUI-designer skills), allowing easy selection of the output codec and quality, and also adding intuitive (or so I think) batch-processing functionality, allowing drag and drop of cuesheet files from Nautilus. Besides that, by using the neat python-mutagen library, the resulting MP3 files now have ID3v2 tags instead of ID3v1. Integration with Nautilus context menu using nautilus-scripts is still supported and practical but no longer mandatory. For new command line options, run "cue-splitter --help"

I'm guessing there must be someone out there with similar needs to mine, so here's my script...



**Installation of Dependencies**

```
sudo apt-get install shntool lame flac wavpack vorbis-tools nautilus-script-manager python-mutagen
```Download the script (attached to this post) and move it (or link it) to this folder in your home folder:

```
~/.gnome2/nautilus-scripts
```To use it, use nautilus to navigate to the folder that contains the .cue and the lossless audio file, right-click on the .cue, and select Scripts > cue-splitter, then select the output base folder (a sub-folder will be automagically generated), and wait for the pulsating bar to disappear. Enjoy.

This has been tested in Ubuntu 10.04 but should work in other variants and Linux distros as well, provided the dependencies are met.

Please beware of my rusty coding style, and use at your own risk : )  The code is GPL'd. More info inside the script file.
If you improve the script, fix bugs &c, feel free to post back the new code.


[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=188615&stc=1&d=1302396951[/IMG]
[/CENTER]
 

-----------------------
News:
Version 0.2.4: added [File > Show the Log File] option in the menu
Version 0.2.3: added split-to-FLAC support; simplified GUI (smaller footprint)
Version 0.2.2: missing DATE in cuesheet no longer causes trouble with the cuesheet parser
Version 0.2.1: major GUI improvements; better handling of long folder names for the splitted output (limits to 44 chars, which is what the Sansa Clip+ player can safely handle)
Version 0.2.0: script completely rewritten in python/pyGTK, now with a GUI, batch processing and ID3v2.4 support
Version 0.10: added some python code to support "REM GENRE" and "REM DATE" tag transfer from cuesheet to ogg track file (cuetag does not support "REM *" tags)
Version 0.9: changed output to ogg vorbis quality 6 and added dependency to vorbis-tools; now converts the cuesheet to UTF-8 encoding
Version 0.8: stopping the script by selecting "Cancel" in zenity's destination folder selection now works; better guessing of destination folder 
  Version 0.7 - fixed issue with filenames with multiple dots - 20080914
  Version 0.6 - improves handling of accented song titles - 20080913

---

### Post by atmartin50 on 2008-09-09
Hi ariel,

First off, thanks! This looks like a great script and a tool that I'd use often. However, how do I get to the point where I can select it under scripts after right-clicking? What do I need to do to make cue-splitter accessible?

Your help is much appreciated!

Thanks,
Aaron

---

### Post by atmartin50 on 2008-09-11
Hi ariel,

OK, I did some quick research and I've got the script working. Thanks again! It's a very useful tool. One question, however...

Being a bit of an audio snob, I'd like to have my files split into a) individual FLAC files, b) 256 kbps or 320 kbps Ogg Vorbis files, or c) higher bit-rate mp3 files (256 or 320). Is there any way to do this?

Thanks a lot!
Aaron

---

### Post by ariel on 2008-09-13
> **atmartin50 said:**
> Hi ariel,

OK, I did some quick research and I've got the script working. Thanks again! It's a very useful tool. One question, however...

Being a bit of an audio snob, I'd like to have my files split into a) individual FLAC files, b) 256 kbps or 320 kbps Ogg Vorbis files, or c) higher bit-rate mp3 files (256 or 320). Is there any way to do this?

Thanks a lot!
Aaron


Nice to know the script was useful for you. I just uploaded my newest version (0.6) which fixed problems handling non-english characters in song and album names much better than before.

To answer your question, while it is certainly possible to change the output format to flac or ogg, I would have to rewrite the part of the script that handles the ID3 tagging and filters out the non-ascii chars in filenames etc. But changing the bit rate of the generated mp3s is quite easy, here's how:


[LIST]
[*]Open the script with gedit
[*]Locate the line that says:
[/LIST]
```
shntool split -f "$1" -o 'cust ext=mp3 lame --quiet -b 192 - %f' -t "%n - %t" -d "$temp_folder" "$lossless_filename" \
```
[LIST]
[*]Replace the part that says:
[/LIST]
```
-b 192
```
[LIST]
[*]With (e.g., for 320Kbps)
[/LIST]
```
-b 320
```
[LIST]
[*]Save the script, and do a new split of your lossless audio rip
[/LIST]

... and enjoy your higher quality mp3s :)

---

### Post by atmartin50 on 2008-09-13
Hi ariel,

Thanks a lot for your quick reply! This sounds easy enough. At the end of the day, a higher bit-rate means more to me than audio format (as long as it's not .wma:)). Thanks again!

Aaron

---

### Post by listener on 2008-09-13
Ariel, I appreciate this very much, I'm glad I ran across it.  I work with audio files a lot, as a hobby mostly, and like good nautilus-scripts too.  I am recently coming from Windows, where at least there are tons of tools for doing this sort of thing.  I've found all the command-line tools already, and was interested in learning some scripting myself, or taking up C here under Linux, which I have been working in over there.  

I will be studying your script and using it, probably only modifying the bitrate as shown, for now.  So it is a helper for me all-round.

There is a nice nautilus-script for doing conversions, although I haven't checked out that much of it, I think it transfers tags where possible.  It does nothing with cuesheets however.  I think it is called 'audio-convert'.  I see a great deal of requests for splitting and tagging from cuesheets.  

Thanks again

Bob

---

### Post by edv on 2008-09-23
Thank you for the script! It did exactly what I wanted to do.

---

### Post by evencoil on 2009-02-23
thanks, works great for me and does just what i wanted!

---

### Post by dannymichel on 2009-08-28
im sure im not doing anything wrong. it just doesnt work. i select the 'base folder' and nothing happens... the folder it says its going to create is created but other than that... nothing

---

### Post by ariel on 2009-08-28
> **dannymichel said:**
> im sure im not doing anything wrong. it just doesnt work. i select the 'base folder' and nothing happens... the folder it says its going to create is created but other than that... nothing


I've run into that sort of behavior a few times and AFAIR all issues were related to malformed cuesheets. Cuesheets have a very simple structure and you can quickly spot whether there is something wrong with it. For example, sometimes the cuesheet has a FILE entry that points to a .wav file instead of a flac or ape (BTW, to handle monkey's audio, you need a special library installed, this is described inside the script).

Other times, cuesheets contain many FILE entries. Other times the TITLE is not surrounded by quotes and so on. I've used the script literally hundreds of times and it seems to do the job well. If one day I have the time I'd like to rewrite it in Python.

---

### Post by atomicscissors on 2010-04-15
Works fine.  Thank you for the script, Ariel.

Are you going to rewrite the script to output to FLAC?

---

### Post by ariel on 2010-04-15
> **atomicscissors said:**
> Works fine.  Thank you for the script, Ariel.

Are you going to rewrite the script to output to FLAC?


Well I have the idea to rewrite the script in Python for far better maintenability, one day.

For now, if you need to output flac, you can try the changes below (note that I haven't tested them, so this has a fair bit of guessing):

Where it says:

```
shntool split -f "$1" -o 'cust ext=ogg oggenc --quiet -q 6 - -o %f' -t "%n - %t" -d "$temp_folder" "$lossless_filename" \
```

Try changing to:

```
shntool split -f "$1" -o 'cust ext=flac flac --quiet - -o  %f' -t "%n - %t" -d "$temp_folder" "$lossless_filename" \
```

And where it says:

```
cuetag cuesheet-split.cue *.ogg
```

Try:

```
cuetag cuesheet-split.cue *.flac
```

Let me know if it does the trick.

---

### Post by vaul on 2010-06-26
Hello, ariel.

Currently there are quite a vacuum in the area of GUI .cue splitters in GNU/Linux, at last I was unable to find one, and I put some effort into finding them.

Your script offers the best functionality around, but still needs some manual editing to work, and could be configured only manually.

Could you please write a GTK interface for this tool?

This would help to create a useful app with functionality no yet implemented with GUI.

---

### Post by ariel on 2010-06-29
> **vaul said:**
> Hello, ariel.

Currently there are quite a vacuum in the area of GUI .cue splitters in GNU/Linux, at last I was unable to find one, and I put some effort into finding them.

Your script offers the best functionality around, but still needs some manual editing to work, and could be configured only manually.

Could you please write a GTK interface for this tool?

This would help to create a useful app with functionality no yet implemented with GUI.

Well I agree a GUI is needed and that is included in the future plans, as part of a python / pygtk rewrite. It's been in the in my TODO list since I learnt some python/pygtk last year but I didn't find the time to get that done or even started. Part of the "problem" is that the bash script + nautilus integration still does the job well (for me) even with the latest and greatest ubuntu. One of the niceties of using linux I guess.

---

### Post by vaul on 2010-06-30
That sounds quite reasonable.

Maybe it's worth an effort to make a package for the official Ubuntu repository that would include this script and its dependencies?

Software Center is certanly most obvious place to look for tools like this, and there are packages that include Nautilus scripts already.

---

### Post by ariel on 2010-09-21
Update: complete rewrite of the script using python/pyGTK - with a GUI, batch processing and ID3v2.4 support.

See the first post for the latest version.

---

### Post by vaul on 2010-09-22
That's just great, thank you!

---

### Post by jamesisin on 2010-10-05
I have written a script for converting APE/FLAC album-length files into FLAC track-length files en masse:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

### Post by vaul on 2010-10-06
That is great, thank you, jamessin.

What about an idea of integration of those two scripts? 

For instance, I would have liked Cue Splitter not only split cuesheet files, but also have a checkbox for conversion of resulting audio tracks into the FLAC, or OGG if they are in APE or MP3, if option were availiable.

Besides, ariel, have you though about taking your script into the Ubuntu repositories? If you do not want to bother with packaging and all that stuff I think you would want to contact [Masters of Universe]("https://launchpad.net/~motu") on the Launchpad or elsewere.

---

### Post by jamesisin on 2010-10-07
@vaul - Thanks.  Glad you like my script.

[RANT]Never convert from a lost format (mp3, ogg, aac, &c) into anything.  Converting lost to lost compounds loss while converting lost to lossless creates a lie.  The only way to preserve quality is by using FLAC (or some other lossless format) from the original source.  The lost formats are, in a word, disposable.[/RANT]

---

### Post by vaul on 2010-10-09
Sorry if I wasn't precise.

Of course I didn't convert a lossy audio file into a lossless one, thinking that a converter will magically restore the missing parts of the file.

---

### Post by jamesisin on 2010-10-10
> **vaul said:**
> I didn't convert a lossy audio file into a lossless one, thinking that a converter will magically restore the missing parts

Excellent news.

---

### Post by vaul on 2010-10-10
> **jamesisin said:**
> Excellent news.

I am glad you liked them.

---

### Post by ariel on 2010-10-11
New Version 0.21: major GUI improvements (on DND); better handling of long folder  names for the splitted output (limits to 44 chars, which is what the  Sansa Clip+ player can safely handle), improved log generation

---

### Post by Buying_Some_Time on 2011-02-05
Thank you so much for this!

---

### Post by W29 on 2011-03-21
This is a very good script, but a bit useless for me. I was looking for a script that could split a cue file into separate flac files...

---

### Post by jamesisin on 2011-03-21
> **W29 said:**
> I was looking for a script that could split a cue file into separate flac files...

A cue file is an informational file which carries (among other things) split points for a different file (such as an APE file or a FLAC file).  You need the other file upon which to work and the cue file to know where to do the splitting.

Can you describe what you are trying to accomplish and perhaps we can point you toward a better script or solution.

---

### Post by Bierphysik on 2011-03-22
Nice script... but I can't use it on my netbook. The vertical resolution is too small thus the lower parts of the GUI are out of the lower screen border and I cannot resize the window to get them. Hence you should maybe consider not a complete vertical layout but a more horizontal layout for people who have 16:9/10 screens.

Thanks anyhow.

---

### Post by jamesisin on 2011-03-23
Perhaps ariel could create a tabbed format for the next version.  A General tab for the Split and Quit buttons, an Input tab for the cue and batch processing information, and an Output tab for the file type and quality information.  This should make the final window dimensions small enough for nearly any conceivable screen size.

---

### Post by JLTH on 2011-04-03
Thank you so much for taking your time in making this tool!!

---

### Post by ariel on 2011-04-09
New version 0.2.3 posted. 

[LIST]
[*]Support for splitting one (or many) single file lossless+cuesheet into per-track FLACs has been added (finally!); now you can choose between OGG, MP3 or FLAC
[*]simplified the GUI a little bit to make it smaller and less confusing, hoping it will fit the screen of smaller devices; it now requires 442x673 pixels - should somehow fit 1024x768 netbooks
[/LIST]
Enjoy!

---

### Post by annda on 2011-04-30
Thank you very much, ariel! After cleaning up some CUE files I could finally bring some order to my music collection.

In case you need suggestions as to how to perfect the GUI, I'd suggest adding a button to show the log file in case of errors. It's not that difficult to find, but it would be a nice touch. (This is not a complaint, I really do appreciate your work.)

---

### Post by intel352 on 2011-06-02
Use Flacon instead, has gui, is in Software Center, works well on FLAC/APE/CUE.

---

### Post by ariel on 2011-06-02
> **annda said:**
> Thank you very much, ariel! After cleaning up some CUE files I could finally bring some order to my music collection.

In case you need suggestions as to how to perfect the GUI, I'd suggest adding a button to show the log file in case of errors. It's not that difficult to find, but it would be a nice touch. (This is not a complaint, I really do appreciate your work.)


Version 0.2.4: added the [File > Show the Log File] option in the menu

---

### Post by rich1842 on 2012-07-27
This looks great but is it a big deal for you to make a deb file for idiot newbies like me who can't install from grown-up tar files - please?

---

### Post by jamesisin on 2012-07-27
In this particular case, the tarball you are downloading is just a container (much like a zip file) which contains the script you will use.  Essentially you just extract the script (files) from the tarball and save them to a particular location.  The instructions posted by the author are pretty direct.  Let us know if you encounter any troubles.

Alternatively you could look at my script which is purely on the command line.  You will find a link to that script on the second page of comments in this thread.

---

### Post by oldos2er on 2012-07-27
Old thread closed.

---

