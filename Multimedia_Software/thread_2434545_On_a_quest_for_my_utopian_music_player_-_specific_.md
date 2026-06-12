---
title: "On a quest for my utopian music player - specific sorting options &amp; metadata"
date: 2020-01-07
forum: Multimedia Software
---

### Post by camarillo-brillo on 2020-01-07
Hello all,

For the last 15 years, I have been a Mac user, albeit not a Kool-Aid drinking one.:)
Consequently, I am used to using iTunes. 
Most of my music collection consists of CDs & needledrops that I ripped into AIFF. 

Now I am on a quest to find the ideal Ubuntu compatible music player. I have looked at **Clementine**, **Strawberry**, **Rhythmbox**, of course, as well as **Amarok**, and **Quod Libet**, just to name a few. 

So, what am I looking for?

Despite all the hate I often see for iTunes, there were a couple of things I actually liked about it.
In particular, I liked that the metadata in iTunes had '**sort album**' & '**sort artist**' options.

Call me a product of my time, but it drives me crackers when artists appear sorted by their first name.
Elvis Costello should appear *before* Bob Dylan, not *after*.
Robin Trower should appear* after* the Temptations, not *before*. With iTunes, I was able to remedy that.
I was also able to sort albums so they would appear in chronological order, not alphabetical.


Is there an Ubuntu-friendly player that will let me do that? Rhythmbox does allow me to sort the artist, but won't let me play AIFF files. 

I'm also looking for a player that would let me play all my AIFF files, ideally without converting them. 

I've also got high-res files in 24/96 that I would like to be able to play.

I don't subscribe to any streaming audio, so that isn't a need or concern for me. 

Am I asking for too much?

Is there one out there?

---

### Post by CelticWarrior on 2020-01-07
I can't help with the sorting but AIFF support should be possible: [https://askubuntu.com/a/191026/880592](https://askubuntu.com/a/191026/880592)

---

### Post by camarillo-brillo on 2020-01-08
Thanks. I tried the Sox install, but still no dice. 

Anyone else have any suggestions?

---

### Post by tea for one on 2020-01-09
> **camarillo-brillo said:**
> Is there an Ubuntu-friendly player that will let me do that? Rhythmbox does allow me to sort the artist, but won't let me play AIFF files. 

Have you installed Ubuntu or are you using a live session?

Rhythmbox does, indeed, play aif and aiff files (assuming you have added the relevant codecs/plugins)

Did you try the suggestions in your previous thread (post 4, post 11 and post 14):-

[https://ubuntuforums.org/showthread.php?t=2434216](https://ubuntuforums.org/showthread.php?t=2434216)

As a test, please make sure that the music file is in the Music folder of your user directory.

> **camarillo-brillo said:**
> I've also got high-res files in 24/96 that I would like to be able to play.

Unable to help, I have no experience of this.

---

### Post by camarillo-brillo on 2020-01-09
> **tea for one said:**
> Have you installed Ubuntu or are you using a live session?


Using Ubuntu.

> **tea for one said:**
>  Rhythmbox does, indeed, play aif and aiff files (assuming you have added the relevant codecs/plugins)

Did you try the suggestions in your previous thread (post 4, post 11 and post 14):-

I did. 

So, Rhythmbox does everything I need. 
Up until now, it was not playing AIFF files. 


> **tea for one said:**
>  As a test, please make sure that the music file is in the Music folder of your user directory.

THAT was what made it work. Ubuntu is on a 256 SSD.
I have a TB drive that I mounted to the SSD. For whatever reason, when the files are there, it won't read AIFFs. All other files, WAV, MP3, FLAC, etc can all be played & read from that drive without a problem. 
Not sure why, but AIFF files will only play if they are in the Ubunut music folder, but not from anywhere else. 
Other media files, however, are played with no hassles. 

Any ideas?

---

### Post by tea for one on 2020-01-09
Regrettably, I have no idea why AIFF media files have to be placed in username/Music for recognition by Rhythmbox.

Possibly, something to do with Rhythmbox preferences.

However, I suspect that they could be placed anywhere in the user home directory i.e. Downloads or even a specially created folder AIFF_media. 

Subsequently, open the file with right click > Open with Other Application > Select Rhythmbox (or View All Applications and select Rhythmbox)

Time for a little experimentation, methinks.

Nevertheless, it would be greatly appreciated if you could mark the thread (via Thread Tools) as solved to help other users.

---

### Post by camarillo-brillo on 2020-01-09
I have tried all the above suggestions. 

I tried the "open with other application" approach before I posted here - no dice. 

Is there a way to mount the specific folder from the 1 TB drive to the music folder in Ubuntu?

---

### Post by tea for one on 2020-01-09
> **camarillo-brillo said:**
> I have tried all the above suggestions. 

I tried the "open with other application" approach before I posted here - no dice. 

Is there a way to mount the specific folder from the 1 TB drive to the music folder in Ubuntu?

There is probably a way to mount a specific folder but I'm not 100% sure of the procedure. My external drives and USB sticks mount automagically.

I'm sure someone else will step in soon with the answer.

However, I've just put an AIFF file on a FAT 32 formatted usb stick, plugged it into my PC and successfully played the file with Rhythmbox.

What file system do you have on your 1TB drive?

Is it internal or external?

---

### Post by camarillo-brillo on 2020-01-09
> **tea for one said:**
> 
What file system do you have on your 1TB drive?

Is it internal or external?

It's an internal drive, mounted to the 256 SSD

---

### Post by tea for one on 2020-01-10
You did not mention the file system on your internal 1TB drive?

Also, can you check the ownership of the folders containing your AIFF music files?

Select a folder > Right Click > Properties > Permissions

Alternatively, instead of spending hours looking for a solution, why not just transfer the AIFF files to the Music folder in your user directory?

---

### Post by camarillo-brillo on 2020-01-10
First of all, thanks again for your patience & help. 

> **tea for one said:**
> You did not mention the file system on your internal 1TB drive?

TBH, I am not 100% sure. 

> **tea for one said:**
> Also, can you check the ownership of the folders containing your AIFF music files?

Select a folder > Right Click > Properties > Permissions

It has me listed as the owner.

> **tea for one said:**
> Alternatively, instead of spending hours looking for a solution, why not just transfer the AIFF files to the Music folder in your user directory?

I have a lot of music. If I were to put all my music on that drive, I'd have about 6 GB for everything else. The whole point of the TB drive was to keep all the files I use, with the SSD just for boot-up purposes. 


So, here's what's going on:
On my TB drive, I created a music folder. 
In that folder are a number of folders with the names of the artists, with folders for individual albums in the artist folders. WAV, FLAC & MP3 files play without any problems. 
AIFF files will only play if they are in the music folder I created, but not if they are in a sub-folder.

---

### Post by Yellow Pasque on 2020-01-10
I usually delete the Music folder/dir and recreate it as a symbolic link ("shortcut") to my real Music folder/dir. Maybe Rhythmbox (RB) will like that better? There probably is a way you can tweak RB to use something other than ~/Music, but I don't like/use RB, so I don't know off the top of my head.

---

### Post by tea for one on 2020-01-10
Good evening

We're still battling on................

To identify the file system on a drive/usb device:-

Open a terminal

```
sudo parted -l
```

The last letter is lower case L for list.

Only output the file system and then close the terminal because **parted** is a partition editor and I would not want you to accidentally alter your partitions.

Alternatively, there is a GUI application called Disks (gnome-disk-utility). Click on the **Nine Dot Icon** and search for Disks.

Secondly, have you tried changing the library location in the Rhythmbox preferences?

---

### Post by camarillo-brillo on 2020-01-10
> **tea for one said:**
> 

We're still battling on................

To identify the file system on a drive/usb device:-

Open a terminal

I've included a screenshot from Terminal.



> **tea for one said:**
> 
Secondly, have you tried changing the library location in the Rhythmbox preferences?

Indeed. That was the first thing I tried. Before I posted here, I tried everything I could think of, which, admittedly, isn't much...

---

### Post by tea for one on 2020-01-11
We seem to have reached an impasse. Just to recap the pertinent points:-

Your external drive is ext4 system which is fine.
You are the owner of all the files so there is no problem with permissions.
Rhythmbox recognises and plays the AiFF files when they are in a location that Rythmbox expects.

If I were in your position, I would consider:-

[LIST]
[*]Gradually converting my favourite AIFF tracks to a format that plays.
[*]Moving the AIFF files to the top level of the Music folder (your post 11)
[*]Investigating the symlink suggestion by Yellow Pasque (post 12) 
[*]
[/LIST]

If I think of anything else, I'll post here but, as I do not have AIFF files and a 1TB drive, I cannot reproduce your dilemma exactly.

Good luck

---

### Post by camarillo-brillo on 2020-01-13
> **tea for one said:**
> We seem to have reached an impasse. Just to recap the pertinent points:-

Your external drive is ext4 system which is fine.
You are the owner of all the files so there is no problem with permissions.
Rhythmbox recognises and plays the AiFF files when they are in a location that Rythmbox expects.

If I were in your position, I would consider:-

[LIST]
[*]Gradually converting my favourite AIFF tracks to a format that plays. 
[*]Moving the AIFF files to the top level of the Music folder (your post 11) 
[*]Investigating the symlink suggestion by Yellow Pasque (post 12) 
[/LIST]

If I think of anything else, I'll post here but, as I do not have AIFF files and a 1TB drive, I cannot reproduce your dilemma exactly.

Good luck

Thank you again,
And thank you to everyone else that has been incredibly helpful with suggestions.
Normally, I can be pretty stubborn.
I started this thread with the hope that, "there's gotta be a way."
But, I also have work to do, and this obsession is distracting me from getting other stuff done. 

I will take your advice, and slowly convert my music to FLAC. In the long run, it is the easiest solution.

---

### Post by tea for one on 2020-01-13
> **camarillo-brillo said:**
> Thank you again,
And thank you to everyone else that has been incredibly helpful with suggestions.
Normally, I can be pretty stubborn.
I started this thread with the hope that, "there's gotta be a way."
But, I also have work to do, and this obsession is distracting me from getting other stuff done. 

I will take your advice, and slowly convert my music to FLAC. In the long run, it is the easiest solution.

Good evening

It is gratifying to read that you have decided to persevere with Ubuntu and that you have decided to convert your AIFF files.

Does that mean that you are now an Ubuntu convert? :D

You will find that there are some very helpful users on this site and many have extensive knowledge about Ubuntu/Linux/hardware.

Best wishes

---

### Post by camarillo-brillo on 2020-01-13
> **tea for one said:**
> Good evening

It is gratifying to read that you have decided to persevere with Ubuntu and that you have decided to convert your AIFF files.

Does that mean that you are now an Ubuntu convert? :D

Convert? Yes! Let me know where you want me to distribute the pamphlets - I am all in!

> **tea for one said:**
>  You will find that there are some very helpful users on this site and many have extensive knowledge about Ubuntu/Linux/hardware.

Best wishes

Indeed, this very thread has shows me exactly that. I am an eager student, ready to learn.

---

### Post by cmcanulty on 2020-01-13
I like VLC works, no hassles

---

### Post by tea for one on 2020-01-14
> **camarillo-brillo said:**
> Convert? Yes! Let me know where you want me to distribute the pamphlets - I am all in!
Indeed, this very thread has shows me exactly that. I am an eager student, ready to learn.

Splendid, I reckon that you will enjoy your time exploring Ubuntu/Linux.

When you get a little bit of spare time, I wonder if you can conduct a little experiment.

I have assumed that your AIFF files were created using Apple software.

Are you able to create a new AIFF file using Ubuntu software and store the converted file in the usual place on your 1TB drive.

Does it play?

I'm just curious if the Apple software you previously used has somehow "locked" the data to a specific set of circumstances i.e. a certain file location can only be played with a nominated music player.

The command line tool **ffmpeg** is ideal to convert one audio format to another but the syntax can become complicated.

The _basic_ command (to convert aiff to flac) is:-

```
ffmpeg -i input.aiff output.flac
```

Please double check that the metadata (id3 tag) is preserved in your output file.

It would probably be better to start another thread if you want specific advice concerning ffmpeg because there is a huge choice of options/flags to add to the basic command.

Lastly, if you want an application for audio editing with a GUI, then have a look at **Audacity**.

Kind regards

---

### Post by camarillo-brillo on 2020-01-14
that sounds like a great idea. Will give this a try & report back!

---

### Post by camarillo-brillo on 2020-01-22
Here's the long-awaited update!

> **tea for one said:**
> Splendid, I reckon that you will enjoy your time exploring Ubuntu/Linux.

When you get a little bit of spare time, I wonder if you can conduct a little experiment.

I have assumed that your AIFF files were created using Apple software.

Are you able to create a new AIFF file using Ubuntu software and store the converted file in the usual place on your 1TB drive.

Does it play?

I'm just curious if the Apple software you previously used has somehow "locked" the data to a specific set of circumstances i.e. a certain file location can only be played with a nominated music player.

The command line tool **ffmpeg** is ideal to convert one audio format to another but the syntax can become complicated.

The _basic_ command (to convert aiff to flac) is:-

```
ffmpeg -i input.aiff output.flac
```

Please double check that the metadata (id3 tag) is preserved in your output file.

It would probably be better to start another thread if you want specific advice concerning ffmpeg because there is a huge choice of options/flags to add to the basic command.

Lastly, if you want an application for audio editing with a GUI, then have a look at **Audacity**.

Kind regards

Indeed, it does play. 
One problem, however, is that I am unable to edit metadata in WAV or AIFF files.

Consequently, Harry Nilsson appears before Jellyfish, not after. 
More annoyingly, albums appear in alphabetical order.

FLAC files do allow me to edit the metadata, so that's what I'll be moving forward with.

---

### Post by tea for one on 2020-01-22
> **camarillo-brillo said:**
> Here's the long-awaited update!

Indeed, it does play. 
One problem, however, is that I am unable to edit metadata in WAV or AIFF files.

Consequently, Harry Nilsson appears before Jellyfish, not after. 
More annoyingly, albums appear in alphabetical order.

FLAC files do allow me to edit the metadata, so that's what I'll be moving forward with.

That's good news that the conversion worked and the track plays from your chosen location.

Are you using Rhythmbox to adjust your metadata :- left click on a track > Properties > Four Tabs (Basic - Sorting - Details -Album Art)?

There are other metadata tag tools such as **Easytag** and **Ex Falso**.

I have very limited experience with both these because my tag requirements verge on simplicity and Rhythmbox is sufficient for me.

Best wishes

---

### Post by camarillo-brillo on 2020-01-23
> **tea for one said:**
> That's good news that the conversion worked and the track plays from your chosen location.

Are you using Rhythmbox to adjust your metadata :- left click on a track > Properties > Four Tabs (Basic - Sorting - Details -Album Art)?

There are other metadata tag tools such as **Easytag** and **Ex Falso**.

I have very limited experience with both these because my tag requirements verge on simplicity and Rhythmbox is sufficient for me.

Best wishes

Yes, using Rhythmbox. 
While I can access the properties, regardless of what I type, it doesn't save. 
It does save with FLAC, but not with WAV or AIFF

---

### Post by tea for one on 2020-01-23
WAV and AIFF are proprietary formats and most likely protected by their respective authors.

As FLAC gives you the least resistance, then that's the way to go.

Cheers

---

### Post by camarillo-brillo on 2020-01-23
> **tea for one said:**
> WAV and AIFF are proprietary formats and most likely protected by their respective authors.

As FLAC gives you the least resistance, then that's the way to go.

Cheers

The AIFFs are all files from CDs I ripped from my own collection, so there wouldn't be any DRM.
Likewise, the Wav files are ones I created in Audacity (needledrops from my vinyl collection)

I don't think it's a DRM issue, I think it's just a bug in those formats that won't retain all metadata.
In iTunes, for example, I was always able to edit all the metadata in AIFFs. 
With WAVs, on the other hand, I could modify the metadata, but it wouldn't retain. 
If I closed the app & reopened it, the metadata would be lost on WAVS, bit with AIFFs, it would still be there. 

With Rhythmbox, I can edit the metadata, but the changes don't stick.

---

### Post by tea for one on 2020-01-24
> **camarillo-brillo said:**
> 
In **iTunes**, for example, I was always able to edit all the metadata in **AIFFs**. 
With WAVs, on the other hand, I could modify the metadata, but it wouldn't retain. 
If I closed the app & reopened it, the metadata would be lost on WAVS, bit with AIFFs, it would still be there. 

You have identified the dilemma. (I've taken the liberty of highlighting in bold the key words)

AIFF (Apple format) 	        - Apple software works flawlessly
WAV (Microsoft format)	- Apple software fails to remember metadata

You are presented with some choices:-

Leave your AIFF and WAV files intact         = restricted use with open source applications or continue with Apple & Microsoft applications (in their respective platforms)

Convert your AIFF and WAV files to FLAC   = unrestricted use and freedom

---

### Post by camarillo-brillo on 2020-01-24
> **tea for one said:**
> You have identified the dilemma. (I've taken the liberty of highlighting in bold the key words)

AIFF (Apple format)             - Apple software works flawlessly
WAV (Microsoft format)    - Apple software fails to remember metadata

You are presented with some choices:-

Leave your AIFF and WAV files intact         = restricted use with open source applications or continue with Apple & Microsoft applications (in their respective platforms)

Convert your AIFF and WAV files to FLAC   = unrestricted use and freedom

Indeed, I posted earlier in this thread that I would be converting the files to FLAC for that reason.

So far, the only issue I have had with FLAC is that I haven't figured out how to add album art.

---

### Post by tea for one on 2020-01-24
> **camarillo-brillo said:**
> So far, the only issue I have had with FLAC is that I haven't figured out how to add album art.

Regrettably, I don't know how you add album art to converted FLAC files.

If I were you, I would start a new thread with this question to see if more help would be forthcoming.

---

### Post by coffeecat on 2020-01-24
> **camarillo-brillo said:**
> 

So far, the only issue I have had with FLAC is that I haven't figured out how to add album art.

Easytag - it's in the repositories. It's a useful metadata editor. Here's a copy-paste of the easytag package description:

```
EasyTAG is an utility for viewing, editing and writing the tags of
different audio files, using a GTK+ interface.

Currently EasyTAG supports the following:
 - View, edit, write tags of MP3, MP2 files (ID3 tag), FLAC files (FLAC Vorbis
   tag), Ogg Opus, Ogg Speex and Ogg Vorbis files (Ogg Vorbis tag),
   MP4/M4A/AAC files (MPEG-4 Part 10 tag), and MusePack, Monkey's Audio files
   (APE tag);
 - Auto tagging: parse file and directory names using masks to automatically
   fill in tag fields;
 - Cover art support for all formats;
 - Rename files from the tag fields (using masks) or by loading a text file;
 - Process selected files of the selected directory;
 - Ability to browse subdirectories;
 - Recursion for tagging, removing, renaming, saving, etc;
 - Can set a field (artist, title, ...) on all other selected files;
 - Read file header information (bitrate, time, ...) and display it;
 - Undo and redo last changes;
 - Ability to process tag fields and file names (convert letters into
   uppercase, lowercase, etc);
 - Ability to open a directory or a file with an external program;
 - CDDB support (from http protocol);
 - A tree based browser;
 - A list to select files;
 - A playlist generator window;
 - A file searching window;
 - Simple and explicit interface.
```

(I've used code tags to preserve the simple formatting of the text.)

---

### Post by camarillo-brillo on 2020-01-24
> **coffeecat said:**
> Easytag - it's in the repositories. It's a useful metadata editor. Here's a copy-paste of the easytag package description:

```
EasyTAG is an utility for viewing, editing and writing the tags of
different audio files, using a GTK+ interface.

Currently EasyTAG supports the following:
 - View, edit, write tags of MP3, MP2 files (ID3 tag), FLAC files (FLAC Vorbis
   tag), Ogg Opus, Ogg Speex and Ogg Vorbis files (Ogg Vorbis tag),
   MP4/M4A/AAC files (MPEG-4 Part 10 tag), and MusePack, Monkey's Audio files
   (APE tag);
 - Auto tagging: parse file and directory names using masks to automatically
   fill in tag fields;
 - Cover art support for all formats;
 - Rename files from the tag fields (using masks) or by loading a text file;
 - Process selected files of the selected directory;
 - Ability to browse subdirectories;
 - Recursion for tagging, removing, renaming, saving, etc;
 - Can set a field (artist, title, ...) on all other selected files;
 - Read file header information (bitrate, time, ...) and display it;
 - Undo and redo last changes;
 - Ability to process tag fields and file names (convert letters into
   uppercase, lowercase, etc);
 - Ability to open a directory or a file with an external program;
 - CDDB support (from http protocol);
 - A tree based browser;
 - A list to select files;
 - A playlist generator window;
 - A file searching window;
 - Simple and explicit interface.
```

(I've used code tags to preserve the simple formatting of the text.)

Thank you so much! I will give this a shot.

---

### Post by camarillo-brillo on 2020-02-01
Yet another update (that no one was waiting for):

I did try EasyTag, In the end, it didn't allow me to update the information I wanted to.
Personally, I didn't find it to be too user friendly, either. 
The auto-tagging was, for me, a pain in the neck. 


Unrelated: still trying to figure out how to view album art in Rhythmbox. 

Any suggestions?

---

### Post by camarillo-brillo on 2020-02-19
Been getting the hang of Ubuntu, and, I have to say, it really is intuitive when you get the hang of it. 
Very happy that I made the switch.

But, Rhythmbox is the weak link. Honestly, not pleased with the interface. 

So, I'm on the prowl again for a user-friendly music player. 

I apologize if this is blasphemy, but is there anything out there that resembles iTunes more?

---

