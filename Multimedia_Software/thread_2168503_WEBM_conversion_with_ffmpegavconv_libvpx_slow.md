---
title: "WEBM conversion with ffmpeg/avconv libvpx slow"
date: 2013-08-18
forum: Multimedia Software
---

### Post by chaemil on 2013-08-18
Hi. I have problem with converting flv to webm with avconv. I'm using libvpx to convert to webm with "threads -4" parameter. But it won't run on 4 cores. It's running only on one core on my quadcore amd or dualcore intel. Is there a way to enable multithreaded encoding or is there any other conversion tool that i can run without GUI (server-side)? 

Thanks

---

### Post by andrew.46 on 2013-08-19
> **chaemil said:**
> Hi. I have problem with converting flv to webm with avconv. I'm using libvpx to convert to webm with "threads **[COLOR="#FF0000"]-[/COLOR]**4" parameter. 

Was that a typo? The actual parameter should be:

```
-threads 4
```

My apologies if this is simply a typo :)

---

### Post by chaemil on 2013-08-19
Yes that's only a typo :/

---

### Post by chaemil on 2013-08-27
anyone?...

---

### Post by Yellow Pasque on 2013-08-28
libvpx is really slow for me too (at least with ffmpeg).

---

### Post by Yellow Pasque on 2013-08-28
Out of curiosity, I tried vpxenc (found in vpx-tools package) and was able to get it running on all 3 cores (I have a PhenomII X3). That sped things up considerably.

---

### Post by chaemil on 2013-08-28
cool! How did you exactly use it? With ffmpeg? just -v:c vpxenc -threads -3?

---

### Post by Yellow Pasque on 2013-08-28
No, I couldn't get ffmpeg to use multiple threads. I just used vpxenc like so and it pegged all 3 cores:
```
vpxenc -o test.webm -w 720 -h 480 -t 3 <inputfile>
```

---

### Post by chaemil on 2013-08-28
ok thanks... but it's crucial for me to get somethink like this working

```

avconv -i ./input_file.flv -y -c:v libvpx -b:v 450k -c:a libvorbis -b:a 128k ./output_file.webm 1> ./log/conv/log_file.txr 2>&1 &

```

bcs i'm "listening" to the percenatge of the conversion from php to display it using ajax on the web (the conversion procces is runnng on server and user can display percentage trough browser)

can the vpxenc log conversion process somehow?

---

