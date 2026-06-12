---
title: "[HOWTO] VHS to DVD w/ PVR-250"
date: 2007-08-10
forum: Multimedia Production
---

### Post by watermark on 2007-08-10
Overview to the Overview
--------------------------------
I spent a good deal of time with research, trial and error, and made a few coasters.  This is written in the hopes you save a penguin somewhere by the production of fewer coasters.  See an error?...throw me a line...used this?...throw me some love.

Overview
---------------
If you want to convert VHS to DVD and have a capture card that has hardware mpeg2 encoding (ie. Haugepauge PVR-250) then this is for you.  I run Ubuntu Feisty 7.04, if you run something different, you're prob on your own.  And I'm throwing out the "I'm a noob" disclaimer...so there maybe better/quicker ways to handle this, but this is the way that I finally found to work.  I also assume you know enough about A/V that you can hook up a VCR correctly 0_o.  Due to the length of these processes, you will require a mountain dew/beer in order to keep your nerve.  I also think this will only work for NTSC players, it may need some tweaking for PAL.

Connect VCR to Capture Card
-----------------------------------
I have a VCR, a coax cable, and a stereo analog to computer input adapter.  The coax is a no brainer, but it took a second to find that the sound hooks to an audio port on my PVR-250 instead of the mic port of the mobo.

Get your capture card working
--------------------------------------
IVTV is built into feisty, so all I did was plug-in my card, bring the box up, and it was detected and installed to /dev/video0.  Completely painless.  Set the channel to your VCR channel with "ivtv-tune --channel=3".

Test the setup
-----------------------
You can test your card with "cat /dev/video0 > test.mpg" and then run "mplayer test.mpg" in another window.  If it plays what you have on the VCR, you're golden.  Otherwise you prob need to search the forums a bit.

Capture your video
--------------------------
I've been running "cat /dev/video0 > capture.mpg & sleep 210m ; kill $!" to capture my video.  That will record from the VCR for 210 minutes to a file called capture.mpg.  Don't worry about the static crap on the ends of the video, we edit it off later.  So run that command, press play, and wait.

Format the video
-------------------
As it is now, the MPEG2 video we have is almost DVD compatible, but the audio isn't and it's probably too large to fit on a DVD5 disc...and we have that static garbage on the ends.  I used Avidemux to handle all of these needs.  Run "sudo apt-get install avidemux" if you don't have it already.  It installs to Applications->Sound & Video -> Avidemux.

Start it up and load your captured VHS mpeg.  Let it index and press no if it asks about merging other mpegs.  Edit out the static by finding stopping and ending points to the static by using the << and >> at the bottom.  They find keyframes where you can cut the mpeg.  Use the "set A" and "set B" buttons to mark the start and end points.  When they are marked, goto edit -> cut, and they're gone.  Do this multiple times until you're happy.

Find your ideal bitrate with a bit rate calculator,  [like this one]("http://www.videohelp.com/calc.htm").  Input your video length, the PVR-250's default audio bit rate is 224 kbs, but correct this if that's not true on your card.  Keep the computed numbers somewhere you can get to them.

Go back to Avidemux and select "DVD (lavc)" in the video drop down at the top left.  Click Configure.  Set the encoding type to "single pass - bitrate".  Set the target bitrate to the calculated bit rate and change the max bitrate to the calculate max.  Leave the min bitrate at 0.  Leave the rest of the defaults alone and press ok.  On on bottom left, change the format to "mpeg ps a+v".  Mpeg2 audio is not always supported (if ever?) on NTSC DVD players, change your audio codec to AC3 and keep the bitrate under 448bps (224 is more than enough for VHS, and I'd not go lower than 128).

Now click the save button and pick a location and file name ending in .mpg.  Wait.  My videos have been taking around 2 1/2 hours.

Author the DVD
----------------

I've been using DVDStyler for this.  It's offered the easiest UI with the best results.  Unfortunately, this program isn't in the ubuntu repos, but they do provide a deb that worked for me.  Goto [their website]("http://www.dvdstyler.de/downloads.html") and download the dvdsyler deb and the wxsvg deb.  Install the wxsvg deb then the dvdstyler deb by double clicking them and giving your password.  Again unfortunately, the debs don't install shortcuts to your apps menu, so you have to start it through the shell by typing dvdstyler.

Select your background for your menu by double clicking it.  Drag your converted video to the timeline at the bottom of DVDStyler.  Add text and pictures as you see fit.  Add a button, this defaults to playing the first video you added to your timeline (which is what we want).

I like to make an iso for backup purposes and in case the burn fails for one reason or another.  So press burn and select make iso and pick a location and filename.  Click OK.  After it finishes creating the menus and VOBs, it will preview the video for you.  Make sure this displays correctly and then exit it.  Say yes to the prompt asking if you want to continue.  Wait some more.

Burn the iso
-----------------
Put in a blank dvd, right click the iso you created and click "write to disk".  Wait some more.

Some props
-----------------
[http://stream.uen.org/medsol/dvd/pages/dvd_format_audio4DVDvideo.html](http://stream.uen.org/medsol/dvd/pages/dvd_format_audio4DVDvideo.html)
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)
[http://www.videohelp.com/calc.htm](http://www.videohelp.com/calc.htm)
[http://ubuntuforums.org/showthread.php?t=521303](http://ubuntuforums.org/showthread.php?t=521303)

---

### Post by dabl on 2007-08-11
Nice writeup --- thanks!

Here's what I wrote -- I had some trouble figuring out how to get the signal through my PVR-150 correctly: [http://kubuntuforums.net/forums/index.php?topic=3085164.0](http://kubuntuforums.net/forums/index.php?topic=3085164.0)

I'm using Devede to make the ISO file for the DVD.  But your process looks great. :)

---

