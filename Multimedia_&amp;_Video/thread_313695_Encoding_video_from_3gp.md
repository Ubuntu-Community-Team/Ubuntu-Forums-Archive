---
title: "Encoding video from 3gp?"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Cyfr on 2006-12-06
Hello firstly I want to create a .avi video from a mobile phone .3gp one.

Are there any nice gui programs to do that?

Also, is it possible to have a webpage that does this so that people can upload to my server and it'll encode for them? At the moment my host is dreamhost and it allows me to login to control panel and click convert on any avis I have uploaded, then it converts them to flash so I can have it built in to webpage..

Thanks

---

### Post by daniminas on 2006-12-06
you can use ffmpeg.. But you need some codecs:

[http://www.allaboutsymbian.com/archive/t-22589.html](http://www.allaboutsymbian.com/archive/t-22589.html)

:-k

---

### Post by jannol on 2006-12-25
You could also try this>

install mencoder if you don't have it installed already.

open a terminal

```

~$ mencoder "path and filename to your 3gp file" -o "path and filename to your new mpeg or avi filename" -oac pcm -ovc lavc -lavcopts vcodec=mpeg4:autoaspect=1 -ofps  24000/1001

```
avi is just a container so it doesnt really matter if you use .avi or .mpeg on the new filename as it will be an mpeg4.

good luck

---

### Post by gmatt on 2006-12-26
Attached is a script to automate the intallation of ffmpeg so that it is compiled with all the necessary audio codecs.  Just run it as sudo. Then to encode any input to any output use the shell command: 
```
ffmpeg -i input -acodec amr_nb -ar 8000 -ac 1 -ab 32 -vcodec h263 -s qcif -r 15 out.3gp
 
```

where you can mess with any of the options until you are satisfied.

---

### Post by xodeus on 2007-02-06
> **jannol said:**
> You could also try this>

install mencoder if you don't have it installed already.

open a terminal

```

~$ mencoder "path and filename to your 3gp file" -o "path and filename to your new mpeg or avi filename" -oac pcm -ovc lavc -lavcopts vcodec=mpeg4:autoaspect=1 -ofps  24000/1001

```
avi is just a container so it doesnt really matter if you use .avi or .mpeg on the new filename as it will be an mpeg4.

good luck
This works only for the video. No sound

---

### Post by ChangBeer on 2007-05-29
Hi gmatt -

  I tried your script, and it made the directories, downloaded the files, but bombs out on the ./configure ---- command not found.

  I dont see a configure in /usr/src (where the script ends up) or in the new directories made... where am I going wrong?

---

