---
title: "[SOLVED] Audacity - no export to mp3 option?"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by tech9 on 2008-01-24
After looking through other threads, I still haven't found the solution I am looking for.

I am trying to export cut or selected music to an mp3.

There is no export to mp3 or save as mp3 option.

I have some gstreamer plugins installed, but not all.

if this is what I need to see the export to mp3 option, then can some one tell me the code to install all gstreamer plugins?

---

### Post by Mze on 2008-01-24
since you're using Hardy Alpha, I don't know if this would be of help. It applies to Feisty though.

from the [Ubuntu Guide: Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins")

---

### Post by ron999 on 2008-01-24
Hi
I think this is because you need to give Audacity access to lame mp3 encoder.
I had to do this.
Open Audacity, choose Edit > Preferences > File Formats
Then search for the mp3 library.

---

### Post by tech9 on 2008-01-24
> **ron999 said:**
> Hi
I think this is because you need to give Audacity access to lame mp3 encoder.
I had to do this.
Open Audacity, choose Edit > Preferences > File Formats
Then search for the mp3 library.

Hi ron999,

Thanks for the advice, but when I point the file to 

/usr/lib/libmp3lame.so.0

I still do not see an option from the file menu level.

---

### Post by tech9 on 2008-01-24
> **Mze said:**
> since you're using Hardy Alpha, I don't know if this would be of help. It applies to Feisty though.

from the [Ubuntu Guide: Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins")

actually, this is on 7.10 - I don't install my main apps on the dev box

Thanks anyway

---

### Post by tech9 on 2008-01-25
I am still not seeing the export the mp3 option. Is it suppose to be under File from the menu level?

I select libmp3lame.so.0 from path  /usr/lib/

after I click ok to the file and then to the path, I look under file and still do not see an option to export as mp3.

Anyone have anymore ideas?

---

### Post by LinChapulin on 2008-01-25
On my laptop after installing the lame encoder and getting audio captured I just do File Save As and then I can choose the format I want.

---

### Post by thecrwth on 2008-01-25
I have a similar problem.  I chose to export as Audacity and it says 

"Audacity does not export MP3 files directly. but instead uses the freely available LAME library to MP3 file encoding.  You must obtain libmp3lame.so separately by downloading it or building it from the sources, and then locate the file for Audacity....Would you like to locate libmp3lame.so now?"

I don't have this file even though I have LAME installed.  I looked at LAME-extras and it says "LAME Ain't an MP3 Encoder
Lame is a program which can be used to create compressed audio files. (Lame
aint MP3 encoder). These audio files can be played back by popular mp3
players such as mpg123. To read from stdin, use "-" for <infile>. To write
to stdout, use a "-" for <outfile>."

When I go to Audacity>Edit>preferences, I only have the option to chose a record and playbakc device.  Do I perhaps have outdated versions?

I use  Dapper Drake.  Is that version getting outdated?

Thanks

---

### Post by tech9 on 2008-01-25
I figured it out... thank you all for your help!

:)

---

### Post by tech9 on 2008-01-25
> **thecrwth said:**
> I have a similar problem.  I chose to export as Audacity and it says 

"Audacity does not export MP3 files directly. but instead uses the freely available LAME library to MP3 file encoding.  You must obtain libmp3lame.so separately by downloading it or building it from the sources, and then locate the file for Audacity....Would you like to locate libmp3lame.so now?"

I don't have this file even though I have LAME installed.  I looked at LAME-extras and it says "LAME Ain't an MP3 Encoder
Lame is a program which can be used to create compressed audio files. (Lame
aint MP3 encoder). These audio files can be played back by popular mp3
players such as mpg123. To read from stdin, use "-" for <infile>. To write
to stdout, use a "-" for <outfile>."

When I go to Audacity>Edit>preferences, I only have the option to chose a record and playbakc device.  Do I perhaps have outdated versions?

I use  Dapper Drake.  Is that version getting outdated?

Thanks

Is lame installed? if not run

```
sudo apt-get install lame
```also you can go into synaptic and check to make sure that liblame0 and liblame-dev are installed.


after going back into Audacity>Edit>Preferences
finally make sure that your path is /usr/lib/lipmp3lame.so.0

also: you may want to upgrade your OS - Dapper is old

---

### Post by rosegarden78 on 2008-01-25
Interesting ... FFMPEG by Fabrice Bellard is great for making music & video conversions.  Same author as WINE I use it to make animated GIFS.  But I like that you can put LAME in Audacity.

---

### Post by tech9 on 2008-01-28
> **rosegarden78 said:**
> Interesting ... FFMPEG by Fabrice Bellard is great for making music & video conversions.  Same author as WINE I use it to make animated GIFS.  But I like that you can put LAME in Audacity.

yep, audacity uses lame for mp3 support :)

---

### Post by SteveJM on 2008-01-31
> **tech9 said:**
> Is lame installed? if not run

```
sudo apt-get install lame
```also you can go into synaptic and check to make sure that liblame0 and liblame-dev are installed.


after going back into Audacity>Edit>Preferences
finally make sure that your path is /usr/lib/lipmp3lame.so.0

also: you may want to upgrade your OS - Dapper is old

I had the same issues.  Lame installed but audacity still couldn't export to mp3

Used synaptic to install liblame0 and liblame-dev and all now works fine.

Fantastic.  Thanks all.

---

### Post by tech9 on 2008-02-01
> **SteveJM said:**
> I had the same issues.  Lame installed but audacity still couldn't export to mp3

Used synaptic to install liblame0 and liblame-dev and all now works fine.

Fantastic.  Thanks all.

shweet! glad to see you got it working!

Audacity ROCKS!
:guitar:

---

### Post by vianneytoo on 2008-02-28
I see that the problem was solved but not the solution - and maybe my problem is different.

I have Ubuntu 7.10, Audacity 1.3.3-Beta built 28-Jan-2008, lame 3.97, liblame0 3.97 and liblame-dev 3.97 installed.  In Audacity, I've clicked on Edit > Preferences > File Formats and with Find Library , set the "Location of libmp3lame.so.0" to /usr/lib/libmp3lame.so.0 (which **is** where this Shared Object is).  Restarting Audacity, and looking at the File menu, I see Export..., Export Selection..., Export Labels..., and Export Multiple... but not Export as MP3.. as various posts here and at Audacity Forums says should exist.

One reply ([here]("http://audacityteam.org/forum/viewtopic.php?f=18&t=1235#p4540")) to a AudacityTeam Forum post indicated that not finding MP3 in the File > Export implies that Audacity was compiled with MP3 support disabled.  The codecs listed in Help > About Audacity for me are: 
[LIST]
[*]Libmad: Enabled
[*]Ogg Vorbis: Enabled
[*]LibID3Tag: Enabled
[*]FLAC: Disabled
[*]LADSPA: Enabled
[*]Libresample: Enabled
[*]PortAudio v19
[*]wxWidgets 2.6.3
[/LIST]
but no MP3.

Ideas?

---

### Post by hrisk on 2008-02-28
to vianneytoo

Follow the steps in the screen shots

---

### Post by Joe_Atlanta on 2008-03-04
I had a very similar experience, but I found that my real problem was a **change in menus** from the earlier version of Audacity I was using in Windows.

Once you you have found and selected your lame driver, the export to mp3 is now buried two layers down in the export menu.

file/export**/browse for other folders**

At the bottom right of the folder screen is a menu that says "Wave, AIFF and other uncompressed types" . Hi the the arrow and it will display the other choices of mp3 and ogg. THEN you can select options for that particular type of export.

Not really intuitive, huh?


good luck,
Joe


> **vianneytoo said:**
> I have Ubuntu 7.10, Audacity 1.3.3-Beta built 28-Jan-2008, lame 3.97, liblame0 3.97 and liblame-dev 3.97 installed.  In Audacity, I've clicked on Edit > Preferences > File Formats and with Find Library , set the "Location of libmp3lame.so.0" to /usr/lib/libmp3lame.so.0 (which **is** where this Shared Object is).  Restarting Audacity, and looking at the File menu, I see Export..., Export Selection..., Export Labels..., and Export Multiple... but not Export as MP3.. as various posts here and at Audacity Forums says should exist.

Ideas?

---

### Post by tech9 on 2008-03-05
> **vianneytoo said:**
> I see that the problem was solved but not the solution - and maybe my problem is different.

I have Ubuntu 7.10, Audacity 1.3.3-Beta built 28-Jan-2008, lame 3.97, liblame0 3.97 and liblame-dev 3.97 installed.  In Audacity, I've clicked on Edit > Preferences > File Formats and with Find Library , set the "Location of libmp3lame.so.0" to /usr/lib/libmp3lame.so.0 (which **is** where this Shared Object is).  Restarting Audacity, and looking at the File menu, I see Export..., Export Selection..., Export Labels..., and Export Multiple... but not Export as MP3.. as various posts here and at Audacity Forums says should exist.

One reply ([here]("http://audacityteam.org/forum/viewtopic.php?f=18&t=1235#p4540")) to a AudacityTeam Forum post indicated that not finding MP3 in the File > Export implies that Audacity was compiled with MP3 support disabled.  The codecs listed in Help > About Audacity for me are: [LIST]
[*]Libmad: Enabled
[*]Ogg Vorbis: Enabled
[*]LibID3Tag: Enabled
[*]FLAC: Disabled
[*]LADSPA: Enabled
[*]Libresample: Enabled
[*]PortAudio v19
[*]wxWidgets 2.6.3[/LIST]but no MP3.

Ideas?

when you click export, you may name the file anything you want. From the extensions drop down box, choose MP3 Files and then click Save.

---

### Post by frame45 on 2008-03-05
> **vianneytoo said:**
> I see that the problem was solved but not the solution - and maybe my problem is different.

I have Ubuntu 7.10, Audacity 1.3.3-Beta built 28-Jan-2008, lame 3.97, liblame0 3.97 and liblame-dev 3.97 installed.  In Audacity, I've clicked on Edit > Preferences > File Formats and with Find Library , set the "Location of libmp3lame.so.0" to /usr/lib/libmp3lame.so.0 (which **is** where this Shared Object is).  Restarting Audacity, and looking at the File menu, I see Export..., Export Selection..., Export Labels..., and Export Multiple... but not Export as MP3.. as various posts here and at Audacity Forums says should exist.

One reply ([here]("http://audacityteam.org/forum/viewtopic.php?f=18&t=1235#p4540")) to a AudacityTeam Forum post indicated that not finding MP3 in the File > Export implies that Audacity was compiled with MP3 support disabled.  The codecs listed in Help > About Audacity for me are: 
[LIST]
[*]Libmad: Enabled
[*]Ogg Vorbis: Enabled
[*]LibID3Tag: Enabled
[*]FLAC: Disabled
[*]LADSPA: Enabled
[*]Libresample: Enabled
[*]PortAudio v19
[*]wxWidgets 2.6.3
[/LIST]
but no MP3.

Ideas?


I am having the same issues. On my Dell XPS M1330 laptop. I can record audio just fine, but I can't export to anything but WAV or AIFF. I did sudo apt-get install lame. I pointed it to /usr/lib/libmp3lame.so.0 and so on but it's not working for me. :confused:

I would like to be able to export my audio to 128kbps and 64kbps .mp3 and .ogg files. What else do I need to do to get this working. Any help on this would be great. Thanks,

---

### Post by frame45 on 2008-03-05
> **hrisk said:**
> to vianneytoo

Follow the steps in the screen shots


Also on a side note, What program is that dock that you are running in your screenshots? Thanks

---

### Post by tech9 on 2008-03-05
> **frame45 said:**
> Also on a side note, What program is that dock that you are running in your screenshots? Thanks

the dock is called AWN(**[[B]Avant Window Navigator**]("http://getdeb.net/release.php?id=1865"))
[http://getdeb.net/release.php?id=1865](http://getdeb.net/release.php?id=1865)

.....
[/B]
back to your problem

when you click File>Export , you don't see a drop down box near the save button?

You should be able to choose MP3 Files and then click save, if you select libmp3lame.so.0 from path  /usr/lib/

---

### Post by Joe_Atlanta on 2008-03-05
> **frame45 said:**
> I am having the same issues. On my Dell XPS M1330 laptop. I can record audio just fine, but I can't export to anything but WAV or AIFF. I did sudo apt-get install lame. I pointed it to /usr/lib/libmp3lame.so.0 and so on but it's not working for me.,

Once you go to menu:
**edit/preferences/file formats/MP3 Export Setup**
and find lame, then it's a matter of negotiating the confusing Export menu (see my _[previous post]("http://ubuntuforums.org/showpost.php?p=4455907&postcount=17")_).

Here's a vid that explains it pretty well:
_[http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html](http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html)_

good luck,
Joe

---

### Post by frame45 on 2008-03-14
Thanks, I got I figured out.

---

