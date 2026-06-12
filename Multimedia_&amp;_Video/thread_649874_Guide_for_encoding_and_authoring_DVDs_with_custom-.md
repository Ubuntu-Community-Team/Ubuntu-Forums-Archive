---
title: "Guide for encoding and authoring DVDs with custom-edited audio"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by hurtstotalktoyou on 2007-12-25
Hi, all.  Normally I just come here to ask questions.  Now I thought I'd return the favor, and post a guide based on my experiences trying to author a DVD from internet video files, but with custom-edited audio.

The files I downloaded were *.mov files using the "H.264 / AVC" video codec (426x240 res @ 24 fps) and "MPEG-4 AAC" audio codec (44.1KHz stereo).  As of this writing (2007-12-25), you can find still them [here](http://richarddawkins.net/article,2025,THE-FOUR-HORSEMEN,Discussions-With-Richard-Dawkins-Episode-1-RDFRS).  I saved them to my desktop, which I think makes them easy to find and use.  However, this should work for a wide variety of video file types.

Please note I'm using Ubuntu Studio Gutsy Gibbon, but everything described should work pretty much the same on other recent variants of Ubuntu, including the main distro.

Now, the first thing I did was try to play the video in Totem, but Totem demanded that I first download a couple of codecs.  The process was highly automatic; all I did was go along with the pop-ups, checking the boxes for all suggested codec packs.  I assume this step is necessary to make sure your system has the required codecs not just to play, but also to encode them.

Once it was playing in Totem, I then turned to non-bundled software.  So I downloaded DeVeDe (newbies:  download software by going to System > Administration > Synaptic Package Manager; make sure you comply with all pop-up recommendations).  Then I performed the following steps:

1.  Run DeVeDe (Applications > Sound And Video > DeVeDe)
2.  Click on "Video DVD"
3.  Click "+ Add" under the top-right frame; this will open a new window
4.  Under "file," navigate to and select the video source file to encode
5.  Choose an appropriate video bitrate.  For low-quality internet files, I find 1,000 kbps is plenty.
6.  The audio bitrate doesn't matter in the end, but choosing 128 kbps speeds up the process slightly
7.  Make sure "store at full length" is selected under "file split"
8.  You MUST select NTSC if you live in the United States.  It will NOT be selected by default, so don't forget this one!
*9.  Click on "advanced options"
*10.  Click on the "quality options" tab
*11.  Uncheck the "Use Trellis Searched Quantization" box
*12.  Under "MacroBlock decision algorithm" select "Use MBCMP"
13.  Click "OK."  This will return you to the original window.
14.  Under "Action," select "Only convert film files to compliant MPEG files"
15.  Click "Forward"
16.  Choose your destination folder and file name.  I suggest using the desktop, and a generic file name like "movie" (which is the default)
17.  When the "Job done" notice pops up, click "Quit"

*- Steps #9-12 are optional but recommended, as they will speed things up significantly with minimal quality loss

Now you have a brand new *.mpg file.  But you also will see two other files, one ending with *.mpg.idx and the other with *.xml.  You MUST delete these (it will be important later).  Leave only the actual *.mpg file.

Now, we're going to want to use the original audio to edit.  That means extracting it losslessly from the original video source file.  We do this with a program called Avidemux, which unless you've already done so will need to be installed from the Synaptic Package Manager, just like we did with DeVeDe.  Once it's installed, follow the following instructions:

1.  Run the program (Applications > Sound & Video > Avidemux)
2.  Click on "open"
3.  Navigate to the original video source and select it by clicking "Open"
4.  A warning message may pop up.  Just click on whichever button allows you to continue (with the example I used the button reads "Use that mode").
5.  Under the "audio" settings on the left (not on the top), where it says "Copy," instead select "Wav PCM"
6.  Under the same "audio" settings area, click on "Configure".  This will open a small window.
7.  Under the "Resampling" heading, select "Resample to hz 48000"
8.  Under the "Mixer" heading, select "Stereo"
9.  Click "OK".  That will return you to the original window.
10.  Click on the "audio" drop-down menu (on the top) and select "Save..."
11.  Choose a save location (I prefer the desktop) and type in a file name.  Make sure you type ".wav" at the end of the file name, as it will not be added automatically.  Then click "Save."
12.  When the file is finished saving, close Avidemux

Now you have a *.wav file in 48KHz stereo, which is the proper format for DVD audio.  You can use whichever program you'd like to edit it.  I like Audacity.  I find compression is very helpful for some videos; the SC4 compressor VST effect (in Audacity) has the quickest attack short of look-ahead,  Then you can use hard limiting to smooth out any sharp peaks.  Just make sure that when you're done it's still a 48KHz stereo waveform.

Now we need to combine the new audio with the *.mpg file we made earlier.  To do this, we'll again use Avidemux, following these instructions:

1.  Run the program (Applications > Sound & Video > Avidemux)
2.  Click on "open"
3.  Navigate to the new *.mpg video and select it by clicking "Open"
4.  You should get a pop-up warning which reads "This looks like mpeg Do you want to index it?"  If you do not get that warning, go back and make sure the *.mpg.idx and *.xml files you created with the *.mpg file are both deleted.  When you see the warning, click on "Yes".
5.  When the indexing finished, click on "audio" in the top drop-down menu, and select "main track"
6.  Click where it says "audio track" and select "External PCM (Wav)"
7.  Click "OK".  This will open a new window.
8.  Navigate to the *.wav file you made with Audacity (or whichever other program you chose to edit with) and select it by clicking "Open".  This will return you to the original window.
9.  Under the "Audio" heading on the left, click where it says "Copy" and instead choose "FFm MP2".  Keep in mind, though, that you can use whichever format you wish; just make sure it's something DVD-compliant like MP2, AC3 or WAV.
10.  Under the "Audio" heading, click on "Configure"
11.  Choose the desired bitrate.  For low-quality internet videos, I find 128 kbps is just fine.  Click "OK" when done.
12.  Under the "Format" heading on the left, click on the button (it probably says "AVI" by default) and choose "MPEG-2 PS A+V"
13.  It should be selected by default, but just make sure that under the "Video" heading on the left it reads "Copy"
14.  Click on the "Save" button
15.  Type in the desired file name.  You'll need to make sure it ends with ".mpeg".  Also choose a save location (I prefer the desktop).  Then click "Save".
16.  When it finished saving, click "OK"
17.  Close out of Avidemux

Now you have a new mpeg file with custom-edited audio which is fully DVD-compliant.  You make as many of these as you like, and they will all function as chapters or titles, whichever you prefer.  This is pretty neat, because I haven't found any Windows freeware which can combine separate MPEG files as chapters within a single DVD title.

The next program we're going to use is called QDVDAuthor.  Like DeVeDe and Avidemux, we'll have to install it using Synaptic Package Manager.

*END PART ONE*

I'll type up the second part of this guide later today or tomorrow.  I may append it to this original post, or add it as a reply, depending on the situation.  I hope part one was helpful!

---

