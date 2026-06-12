---
title: "Creating video playlist in shell"
date: 2008-07-31
forum: Multimedia Software
---

### Post by gizm0 on 2008-07-31
I have about 20 .flv video files on my server. I would like to create playlist in shell environment, so that it would create new playlist(from the same directory) once a week.

Is there a program or a script to do this? I'm using JW Player for Flash to play these files on my server.

---

### Post by aeiah on 2008-07-31
well, what kind of playlists can jw player read?

---

### Post by gizm0 on 2008-07-31
> **aeiah said:**
> well, what kind of playlists can jw player read?

For example ASX,SMIL,XSPF ([http://code.jeroenwijering.com/trac/wiki/FlashFormats](http://code.jeroenwijering.com/trac/wiki/FlashFormats))

---

### Post by Vishal Agarwal on 2008-07-31
can u attach the play list with your post. And what is the .ext is required for play list ?

---

### Post by gizm0 on 2008-07-31
> **Vishal Agarwal said:**
> can u attach the play list with your post. And what is the .ext is required for play list ?


You can find examples here:
ASX: [http://www.jeroenwijering.com/upload/asx.xml](http://www.jeroenwijering.com/upload/asx.xml)
SMIL: [http://www.jeroenwijering.com/upload/smil.xml](http://www.jeroenwijering.com/upload/smil.xml)
XSPF: [http://www.jeroenwijering.com/upload/xspf.xml](http://www.jeroenwijering.com/upload/xspf.xml)

For more information look at: [http://code.jeroenwijering.com/trac/wiki/FlashFormats](http://code.jeroenwijering.com/trac/wiki/FlashFormats)

---

### Post by aeiah on 2008-07-31
so really you need a script that will 
1: create the top of the xml document (asx in this example)

```
- <asx version="3.0">
  <title>ASX playlist title</title> 
  <moreinfo href="your website" /> 
```


2: iterate over the contents of your video folder and write the entry stuff. i imagine a lot of the fields can be left blank, and perhaps can be missed out all together. for the sake of avoiding errors you probably should include them to begin with but just have them empty or something.
in pseudocode:
```

for $file in directory:
append to playlist.xml "
- <entry>
  <title>$file</title> 
  <author></author> 
  <abstract></abstract> 
  <moreinfo href="" /> 
  <ref href="http://website.com/videos/$file" /> 
  <param name="captions" value="" /> 
  <param name="type" value="video/x-flv" /> 
  </entry>
"

```
3: create the closing tag
```
</asx>
```


i dont mess around with bash, perl or php scripts much so i havent actually put any real syntax in there. i guess you'd either want to trigger this playlist formation either every time you upload a new video, at certain times in the day/week, or every time someone views a certain page. its probably best just to run it when you've finished uploading videos. im sure you can encorporate it into an upload script or something.

edit: i see you said once a week. in that case just set it as a cron job. but writing the script in a language a computer understands instead of my rough overview of what you need to do will be the first step :p

---

### Post by gizm0 on 2008-08-01
Thank you! I just made my own script:

> #!/bin/bash
cd /var/www/temp/
echo '<ASX version = "3.0">' > test.xml
for X in *.flv
do
let Y=$Y+1
echo -n "<Entry>" >> test.xml
echo -n "<title>Video $Y</title>" >> test.xml
echo -n '<Ref href = "' >> test.xml
echo -n "http://xx.xx.xx.xx/temp/videos/$X" >> test.xml
echo -n '"/></Entry>' >> test.xml
echo "" >> test.xml
done
echo "</ASX>" >> test.xml

So this case is now solved.

---

### Post by ricardisimo on 2012-08-21
Can VLC make use of this shell, or another like it?

---

### Post by overdrank on 2012-08-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

