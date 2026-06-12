---
title: "I want 1080i or 720p"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by stefansjs on 2007-09-22
I am using an nvidia 6150 integrated graphics card.  It took me forever to get dvi working at all for this graphics card to my HDTV.  After all my effort I can only get it to output to dvi using 1024x768.  This is very disappointing because I bought the tv in order to show 1080i (or 720p if necessary), but the TV just freaks out.  Does anybody have any idea why this grahpics card would not be able to detect the proper display settings, or why it would not output properly to the TV?  I really want hd.
thanks

---

### Post by markywmson on 2007-09-22
I'm not sure if it's the video card or the tv's problem.  What kind of tv is it first off?  I have an RP HDTV and it only has a DVI-I (i think) input.  Basically, I can't even connect my computer to it because it's got the wrong kind of DVI connector.  Like I said, this probably doesn't apply to you, but it's something to check at least before banging your head against the wall for too long... ](*,)

---

### Post by C@bb@ge on 2007-10-12
What cable are you using to link to your hdtv? dvi-vga or dvi to hdmi? either way it seems ubuntu is unable to detect max / native resolution on some hdtv's, or it can set a higher resolution in the nvidia settings, but the max resolution is listed as 1024*768 so try the following:

edit your 'xorg.conf' and set the max resolution, i.e probubly 1360 * 768 for your hdtv, below is some basic instructions, if you need more detail search for editing xorg.conf on this forum:

open up the console and navigate to:


        /etc/X11/xorg.conf


use an editor like nano and search for a group of lines that look a bit like this:


	SubSection "Display"
		Depth		24
		Modes	       "1024x768" "800x600" "640x480"
	EndSubSection


now add ' "1360x768"' to the listed resolutions:


	SubSection "Display"
		Depth		24
		Modes	       "1360x768"  "1024x768" "800x600" "640x480"
	EndSubSection


Now if you try to asve i MAY stop you form over righting the file, so save it to your user directory and move the file back to /etc/X11/xorg.conf using the 'mv' command, you will need admin rights so type 'sudo' beforehand:

       sudo mv xorg.conf /etc/X11/

And that should work, if you still have trouble, you may need to install the nvidia drivers, so try the restricted driver section :-), if you have any problems then look this up elsewher eon the fourm as i am a newb to this myself and my instructions arn't as clear as others out there.

---

