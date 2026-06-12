---
title: "[SOLVED] Noise lines on iso files"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by Yuck on 2007-08-12
Hi,
I've been using DeVeDe to create iso files of avi and divx files,  then left click the iso and "write to disc". This method had been working fine until recently. I'm not sure if I have changed a setting or something, but I'm getting visual noise on the output file. The avi or divx files play fine in their original form but after going through DeVeDe they have 20 or so thin horizontal noise lines. Any help in plain english as I'm new to Ubuntu would be greatly appreciated.

Thanks

---

### Post by davidbenson on 2007-08-12
I had the same problem...  Unfortunately, the repository version is 2.1 and lacks some of the advanced features in the latest version...  Here is what I did (there is probably a much simpler way)...

1. Remove DeVeDe using Synaptic
2. Download latest from: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
3. Open a terminal and cd to folder with downloaded package
4. Execute: sudo -s   (to become root, requires your password)
5. bunzip and untar the downloaded package
6. Execute: ./install.sh

At this point, the script will run and it looks like nothing happens...  That's just because all it does is copy files around and stop...  Unless you got specific errors, you can just hit CTRL+D twice to exit out of the terminal.

The only wierdness that I had was the menu icon refused to show up right away even though the script had created an entry for it...  I solved this with the following steps:

1. Left click on the Applications menu and choose 'Edit Menus'
2. Click on 'Sound & Video' on the left side
3. Locate the entry for DeVeDe on the right
4. Uncheck it...
5. Wait a few seconds... (it will change to italic text)
6. Replace the check that you removed in step 5 (to re-enable it)
7. Wait for it to change back...
8. Close the menu editor...

* You could probably have accomplished the same by logging out and back in...

Okay, now that you've got the latest version (DeVeDe 3.01), it's time to get rid of the horizontal lines.  Those lines are caused when you encounter video that is interlaced...  So you want to de-interlace it...  Here is how...

1. Launch DeVeDe as you normally would
2. Create a new Video DVD project and select your interlaced file
3. Expand the Advanced options and you should now see a row of TABS
4. Click the "Quality Options" tab
5. From the De-interlacing group, select "Linear Blend"
6. Run a 15 second preview and see if the lines are gone
7. If not, try another de-interlace filter (there are a total of 3)

Good luck!

---

### Post by Yuck on 2007-08-13
Thanks David for the explanation. I actually have 2.9 and the interlacing options are there. I'm going to try and burn a file now and see how it turns out, the preview looks fine.

---

### Post by Yuck on 2007-08-13
Selecting Linear Blend has worked, thanks for the tip :)
I must have changed that option when I've been poking around, and not changed it back.

---

### Post by davidbenson on 2007-11-05
I know this has been solved but there is another way to go about mastering your AVI for DVD and I wanted to share that here.  Forgive me if this is not proper forum protocol...

One problem that I've encountered with DeVeDe is that the final ISO may produce DVD's with jerky playback on _older players_.  This is especially true for older low-budget models.  The solution that I use now to overcome this is to master the mpg files outside of DeVeDe and then use it to assemble the final ISO and menu...

The steps are as follows:
1. Decide on a format (16:9 with black bars or 4:3 with black bars)
2. Encode the file with mencoder
3. Use DeVeDe to create the final ISO with a menu (or without)

*Note: You should not need to worry about horizontal noise lines as I've never seen them when this method is used.*

You need to know the following:
a) Is your TV a widescreen (16:9) or a normal screen (4:3)?
b) Is your AVI file sound track in AC3 or MP3?

The first one (a) is easy...  For the second (b), you might be able to view the file properties of your AVI (right-click, select properties,  click on the Audio/Video tab).  If you have the proper codecs installed then you should see it listed in the Audio section.

Depending on the audio codec of the input file and the desired screen size, you will use **ONE of the following commands** (modify the filenames and paths at the end):

**AC3, Normal**
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf expand=aspect=4/3,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=4/3 -ofps 30000/1001 -o /path/to/output.mpg /path/to/input.avi
```

**AC3, Widescreen**
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf expand=aspect=16/9,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9 -ofps 30000/1001 -o /path/to/output.mpg /path/to/input.avi
```

**MP3, Normal**
```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf expand=aspect=4/3,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=4/3:acodec=ac3:abitrate=192 -ofps 30000/1001 -o /path/to/output.mpg /path/to/input.avi
```

**MP3, Widescreen**
```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf expand=aspect=16/9,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:acodec=ac3:abitrate=192 -ofps 30000/1001 -o /path/to/output.mpg /path/to/input.avi
```

When that command finishes, you should have a proper MPG file that DeVeDe can use without any further conversion.  So, open DeVeDe and add the MPG track as you normally would **[COLOR="Red"]BUT[/COLOR]** be sure to check the checkbox for "This file is already in MPEG-PS format..." in the "Misc." tab of the Advanced Options.

The rest is the same...  Make your menu if you want one, add more tracks if you have them, create the ISO and burn it to a DVD...  I have tested with several older APEX and Phillips players that had exhibited the jerky playback behavior and it seems to be gone.  Using DeVeDe to prep and encode the file always produced discs that would play fine on newer players but not on older hardware...

As a side note, it seems that Totem has the same playback issue.  So if you see jerky playback in Totem, you will probably see it on older players...  VLC and MPlayer played everything I threw at them...

As always, your mileage may vary...  Hopefully this helps somebody...  If nothing else, you've got a nice mencoder command to add to your toolbox...

Cheers!

---

