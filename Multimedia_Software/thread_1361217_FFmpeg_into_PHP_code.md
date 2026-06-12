---
title: "FFmpeg into PHP code"
date: 2009-12-21
forum: Multimedia Software
---

### Post by fosheezy on 2009-12-21
I'm trying to get an ffmpeg command into PHP code using any of the different calls in PHP to run a system command. None of them are working. Is there something special I'd have to do to get ffmpeg to run in the PHP code? I know my page is ok, because it loads up and will print text out. The ffmpeg command will not run, however. I have an HTML form that submits variables to the PHP page to insert into ffmpeg.

It actually is a dvgrab stream into ffmpeg, but even just a simple ffmpeg won't run. How would I get the response back, like if I run it in the terminal and there is an issue it'll tell me, how can I display that text?

Here's the code I'm trying. The variable comes from the HTML page, but even without the variable it won't run.
```
<?php
	
	//run the ffmpeg command
	system(escapeshellcmd('dvgrab -format dv1 - | ffmpeg -i -d 10 -ac 2 -acodec vorbis -vcodec libtheora ' + $sermonTitle + '.ogv')
	printf($sermonTitle);
	
?>	

```

I know the code isnt anything special - I really need to get the basic functionality working before it gets any more complex (to output multiple formats, insert the variables, etc.)

Should I just try to get the variables into a perl script that the PHP calls? Would that be easier?

Sorry if this is in the wrong section.

---

### Post by fosheezy on 2009-12-21
I figured this one out. had some weird permissions on the folder everything was in.

Anyone know about dvgrab? I can't get it to run as any other user except the user I installed the program as.

---

