---
title: "Transcoding to 3gp problems."
date: 2008-05-01
forum: Mythbuntu
---

### Post by SniperKIng on 2008-05-01
Hey guys

Been trying to convert myth recordings to 3gp format so that i can play them on my mobile. Problem is iv looked online and the few tutorials that there are dont seem to get the job done for me.

i tryed using a myth3gp script tho setting it as a user job and then running it results in the file being queued and then becoming 'Completed Successfully' in about a minute. I may be doing something wrong but i followed as best i could.

There is one tutorial mentioning the use of ffmpeg3gp i think but it tells, to CD into ffmpeg but where will that be?

So im really just after someone who has already set this up and has it working who can guide me through this. Right now im going to freshly install mythbuntu onto my computer so i have a clean slate.. please help

---

### Post by SniperKIng on 2008-05-03
Anyone ?

Also im not sure if its just me but changing channels leaves me with a 5 or more second wait. is this normal? i have seen youtube videos of mythtv in action taking 1 second or less to change

---

### Post by vgrisham on 2008-05-04
I need help with this as well. My Palm Centro takes videos. I can play them back in Ubuntu, but the sound is all white noise.

Edit: Oops. I just re-read your post. You're trying to convert to 3gp. I'm trying to get 3gp to playback with audio. Sorry. At least you got a bump!

---

### Post by SniperKIng on 2008-05-05
lol thanks tho im all set with mine now. what code are u using to convert ur files?

---

### Post by peakpc on 2008-11-15
nice post how about sharing with the rest of us:(

---

### Post by lank23 on 2010-02-27
I also wanted this so I could put some videos on my phone for those boring days at work..lol or when you son wants to watch Thomas the tank engine at the Airport....lol.  So this is how you get it going.

I first started here with this nice script 

[http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video]("http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video")

but found that it did not work out of the box due ffmpeg was not compiled with support for 3gp / 3g2 files.  So after a little digging I found you have to do these three things to get a Mythtv recording to a 3gp / 3g2 file for your phone.

1: Follow this guide for installing ffmpeg with full support
  [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

this worked on my 10.04a but in step 2 change libxvidcore4-dev for libxvidcore-dev due the package has been renamed.

2: Get the above script myth_3gp and make some edits at line 6 and  44 so they read like below

Code Change at line 6
```

if [ -z "$VIDEOIN" -o -z "$FILENAME.3g2" ]; then

```

Code Change at Line 44
```

/usr/local/bin/ffmpeg -i "$OUTDIR/$FILENAME.tmp" -ac 2 -acodec aac -ar 32000 -qscale 3 -r 15 -s qcif -metadata title="$FILENAME" -f 3g2 "$OUTDIR/$FILENAME.3g2"

```

a: I have changed the file type to "3g2" instead of "3gp" due my phone Samsung Rouge likes it better.
 b: The "/usr/bin/ffmpeg" has been changed to "/usr/local/bin/ffmpeg" to match the fresh install location of ffmpeg.

3: Setup the Job in Mythtv as detailed on the scripts page and you are done. On my box an one hour SD show takes about 9 minutes and gives me a 40 - 50 mb file with out the commercials at 176 x 144

```

lank23@MythServer:~/Videos/Capture/mythtv/convert_to_phone$ ls -l
total 528496
-rw-r--r-- 1 mythtv mythtv 51997870 2010-02-27 01:27 The X-Files-Terms of Endearment.3g2
-rw-r--r-- 1 mythtv mythtv 46788936 2010-02-27 01:36 The X-Files-The End.3g2
-rw-r--r-- 1 mythtv mythtv 62410185 2010-02-27 01:18 The X-Files-The Rain King.3g2
-rw-r--r-- 1 mythtv mythtv 43909775 2010-02-27 00:56 Thomas & Friends-Achievement.3g2
-rw-r--r-- 1 mythtv mythtv 41372867 2010-02-27 00:33 Thomas & Friends-Bravery.3g2
-rw-r--r-- 1 mythtv mythtv 40079383 2010-02-27 01:02 Thomas & Friends-Celebration.3g2
-rw-r--r-- 1 mythtv mythtv 37454323 2010-02-27 00:50 Thomas & Friends-Change.3g2
-rw-r--r-- 1 mythtv mythtv 40331800 2010-02-27 01:08 Thomas & Friends-Helping.3g2
-rw-r--r-- 1 mythtv mythtv 39800096 2010-02-27 00:39 Thomas & Friends-Lost and Found.3g2
-rw-r--r-- 1 mythtv mythtv 42723907 2010-02-26 23:02 Thomas & Friends-Loyalty.3g2
-rw-r--r-- 1 mythtv mythtv 34611478 2010-02-27 00:45 Thomas & Friends-Night and Day.3g2

```

If you have issues you can check you /var/log/mythtv/mythbackend.log to see what is going wrong.

---

