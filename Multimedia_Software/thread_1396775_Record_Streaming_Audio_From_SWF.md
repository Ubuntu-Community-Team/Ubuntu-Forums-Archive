---
title: "Record Streaming Audio From SWF"
date: 2010-02-02
forum: Multimedia Software
---

### Post by Vinny_P on 2010-02-02
Hi all,

I would like to record the audio from a streaming audio swf file. The site is: [http://www.z1035.com/player.php](http://www.z1035.com/player.php).

I found how to record audio from flash files (ie. youtube) but not streaming from swf. Would anyone know how to do this?

Thank you,
Vinny P

---

### Post by ajgreeny on 2010-02-02
I've just tried this to make sure it works, and it does.

So-, when the flash is streaming audio a file is produced in /tmp called Flashx#x#x#x (that's a random alphanumeric at the end, I think)  You can copy that Flash file to your home manually with nautilus, or using a script:-
```
#!/bin/bash
cp /tmp/Flash* /home/username
```but you must run the script or manually copy before you stop that flash stream, because once you stop it the file in /tmp is lost for ever.

Just a thought, though.  Perhaps the download-flash add-on (can't remember its full name) for firefox would do the same.

---

### Post by Vinny_P on 2010-02-02
ajgreeny,

Thank you for the reply. Now that I know where the source is for the flash audio stream. What format is it and how do I convert it to mp3?

Thank you,
Vinny P

---

### Post by ajgreeny on 2010-02-02
ffmpeg seems to do that though it does throw up a long list of errors when doing so.  The error is as follows, repeated again and again:-
> [aac @ 0x9d49d40]SBR not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.The mp3 file produced seems to play fine, though it may not be as good a quality as it would be if the newer version of ffmpeg were installed.

The command I used was ```
ffmpeg -i FlashRkcUte -acodec libmp3lame -ab 128k file.mp3
```from the folder where the flash file was.  You will need the unstripped versions of several libs for this to work, libavcodec, libavformat and libavutil.

---

### Post by Vinny_P on 2010-02-02
ajgreeny,

I figure that out... now i'm looking into creating a script that will automatically record at a show at a time I specify. I found the gnome-schedule app but not sure how that is?

Thank you,
Vinny P

---

### Post by Vinny_P on 2010-02-03
Hi all,

I finally got the script working. The launch_seamonkey script will launch the streaming application and the finalyze_recording script will:
-copy the stream file to a directory
-kill the streaming applcation launched in launch_seamonkey
-convert the stream file to mp3
-remove any old files

However when I run them under crontab the launch_seamonkey works fine but the finalyze_recording script does not convert the full stream file. I suspect that the ffmpeg process is killed before it finishes but I have a wait command that doesn't seem to solve it. Would anyone know why the ffmpeg does not convert the full file when executed with  crontab but the ffmpeg command convert the full file within the script

Thank you,
Vinny P

---

### Post by VertexPusher on 2010-02-03
Some things to note here:

- The FlashXXXXXX files in /tmp will only be created for FLV streams, not for raw MP3 broadcasts. However, if the FlashXXXXXX file is missing you may be able to find the original MP3 stream URL in your browser cache. Enter "about:cache" in the address field and look for URLs ending in ".mp3".

- FLV files contain either MP3 or AAC audio. Both types can be extracted without reencoding. **Do not use "-acodec mp3lame".** Use "-acodec copy" instead and write the stream to an .mp4 container, if necessary. This will retain the original quality of the broadcast.

---

### Post by Vinny_P on 2010-02-03
VertexPusher,

Thank you for your input. I found a mp3 in the cache but not the one I was looking for ;-). And still, using crontab I still do not have the full flv converted.

I'm using this command:
ffmpeg -i ~/Record/Music/Flash* -f mp3  ~/Record/Music/$(date +"%a-%b-%d-%y-Time:%I:%M").mp3

Still searching :-)
Vinny P

---

### Post by Vinny_P on 2010-02-04
Hi all,

I fixed the issue.

Thank you,
Vinny P

---

