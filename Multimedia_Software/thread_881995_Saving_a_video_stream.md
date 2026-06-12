---
title: "Saving a video stream"
date: 2008-08-06
forum: Multimedia Software
---

### Post by patanjali on 2008-08-06
All,

Does anyone know of a way to save a video stream to the PC it is being streamed to?  Is it just a case of saving the buffer as a file?  If so is there a default location in ubuntu where video stram buffers reside?

Any help would be greatly appreciated.

Regards

patanjali

---

### Post by pytheas22 on 2008-08-06
Do you mean a video stream in a website?  If so, which website?  There are some scripts (e.g., youtube-dl) that will grab the video for you on a handful of the popular sites.

If you're streaming the video through a media player, you could always use screen-capture software to get it (most programs can also capture sound).  You'll lose some video quality, but I don't know of a better way to do it.  [recordmydesktop]("http://recordmydesktop.sourceforge.net/about.php") is a nice screencasting program.

---

### Post by marxian on 2008-08-06
You can save a video stream to your HDD using VLC. Simply choose 'Open Network Stream' and paste the URL into the box next to 'customize'. Check the 'Stream/Save' box and go into 'Settings'. Where it says 'Outputs', check the 'File' option and choose your filename and save location. You can specify the file format, too. It is probably best to select 'Dump raw input'.

Hope this helps.

---

### Post by patanjali on 2008-08-06
> **marxian said:**
> You can save a video stream to your HDD using VLC. Simply choose 'Open Network Stream' and paste the URL into the box next to 'customize'. Check the 'Stream/Save' box and go into 'Settings'. Where it says 'Outputs', check the 'File' option and choose your filename and save location. You can specify the file format, too. It is probably best to select 'Dump raw input'.

Hope this helps.
Thanks marxian, I'm going to try that.  I'll post how I get on.

p  :-)

---

### Post by patanjali on 2008-08-06
> **patanjali said:**
> Thanks marxian, I'm going to try that.  I'll post how I get on.

p  :-)
OK so I tried that but all I got was a file of 0 bytes.  Any ideas?

p

---

### Post by patanjali on 2008-08-06
> **patanjali said:**
> OK so I tried that but all I got was a file of 0 bytes.  Any ideas?

p
pythean22 can you give me any details about this youtube.dl script?

p

---

### Post by pytheas22 on 2008-08-06
You can download the youtube script with:
```

sudo apt-get install youtube-dl
```

And run it with:
```

youtube-dl [URL of youtube video that you want to download]
```

It will download the video and save it into your current working directory (by default, your /home folder).

---

### Post by mocha on 2008-08-07
google for "streamsniff" also check the man page of mplayer for the dumpstream option.

---

### Post by patanjali on 2008-08-08
Pytheas22, that script works a treat!  Thank you so much.

P : :-) :-) :-) :-) :-)

---

### Post by ubuntu-freak on 2008-08-08
You can download YouTube vids with KeepVid.com, plus there are some Firefox extensions which allow you to download Flash videos. Also, for all other video formats you can just right-click on them and select "Sava as" if you have Gecko Media Player installed, see my [how-to](ubuntuforums.org/showthread.php?t=766683) for details.

---

