---
title: "Solution to problems converting FLAC files to mp3 on-the-fly"
date: 2009-09-23
forum: Multimedia Software
---

### Post by dardar on 2009-09-23
I have had problems over the last year or two getting applications like Rhythmbox and Soundconverter to convert my FLAC files to mp3 encoding, for example during the transfer of files from my home Ubuntu server to an iPod or other portable device that can't play FLAC files natively.  (FYI, I have ripped my >1500 CD music collection to FLAC-encoded files on my server and typically stream that music to various Squeezeboxes on my home network using Squeezecenter software on the server, but I also like to copy music to my portable music players without having to duplicate everything as MP3s on the server.) 

Despite my best efforts at getting the settings right in Gnome Audio Profiles (i.e., deleting all profiles except my MP3 profile, unchecking the "Active?" box in all non-MP3 profiles, etc.), the files would be transferred as FLAC files without transcoding.  Since iPods can't normally recognize FLAC-encoded files, this was not what I wanted.  (Not surprisingly, I would prefer not to use my iPods just as USB storage devices for carrying around music without playing it...)

Yesterday, I was finally able to get to the bottom of my problem.  After piecing together information from a bunch of different posts, I figured out that some of my ripping and tagging software (e.g., Grip, Easytag) would insert ID3 tags into the FLAC files (which technically should NOT contain ID3 tags--see [http://flac.sourceforge.net/faq.html](http://flac.sourceforge.net/faq.html)).  Applications such as Rhythmbox would therefore incorrectly think that those files were actually MP3 files and would not bother to transcode them as they were transferred to my portable music players.

Assuming you have installed the necessary software to transcode your files appropriately (e.g., LAME, etc.), but you are still having problems transcoding files on-the-fly as they are transferred to your portable music player, the first thing to do is to check the properties of the FLAC file you are trying to convert.  I wasn't able to find the relevant information from a GUI browser such as Nautilus (e.g., by looking at the "properties" of the FLAC file), but the command line is your friend here.  Specifically, run the command "file" on the FLAC file that is failing to convert:  

     ```
file music-file.flac
```

For example, here are results for a file that does not contain ID3 tags:
     ```
user@computer:/music-path$ file 03_Action.flac 
03_Action.flac: FLAC audio bitstream data, 16 bit, stereo, 44.1 kHz, 7422324 samples

```

Here are results for the same file into which ID3 tags have been inserted:
     ```
user@computer:/music-path$ file 03_Action.flac 
03_Action.flac: Audio file with ID3 version 2.4, MP3 encoding

```

Note that files containing ID3 tags are incorrectly described as MP3 files, even though they are actually FLAC files, and that presumably confuses the transcoding software.

If this has happened to you, check your preferences settings in Easytag,  Grip, or any other software that can write ID3 tags to your files to make sure that any settings for writing ID3 tags to FLAC-encoded files are turned off.

If you need to strip ID3 tags from any FLAC files that contain them, a convenient command is "id3v2".  (You may need to install this, but it should be in the universe repositories.)  Run it with the -D option to delete all ID3 tags:

     ```
user@computer:/music-path$ id3v2 -D 03_Action.flac 
Stripping id3 tag in "03_Action.flac"...id3v1 and v2 stripped.
```

This command should not affect any FLAC Vorbis tags that may also be in the file. 

Once you have stripped the ID3 tags out of the FLAC file, it should be properly transcoded to MP3 on transfer to an iPod in Rhythmbox, assuming all other MP3 settings are selected appropriately.

Hope this saves someone else some time.  It drove me nuts!

---

