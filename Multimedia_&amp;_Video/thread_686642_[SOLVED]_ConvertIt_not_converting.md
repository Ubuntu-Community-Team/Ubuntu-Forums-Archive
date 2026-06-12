---
title: "[SOLVED] ConvertIt not converting?"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2008-02-03
Hey.

My issue is rather simple.

I use convertIt a lot and sometimes I go to convert a video - and it doesn't even attempt to convert it, it just says "conversion complete" as soon as I press "convert" and nothing happens.  It seems to be with random files, random directories, random path names, etc.  I can't find a pattern onto why it's doing it, though it's only happened twice, and both have been with converting .flv files to .avi.

The last time it just "magically" worked the next day when I tried it again..nothing was changed.

Any info?

---

### Post by Creative2 on 2008-02-04
plz search Fuoco tools 
[http://fuocotools.byethost13.com/index.php](http://fuocotools.byethost13.com/index.php)

, convertIT is in developing,  rewriting in phyton and gtk glade, and it has some problem for now; yuo should write about that problem in its own  official topic...not here or noone will see it

---

### Post by Syndacate on 2008-02-05
> **Creative2 said:**
> plz search Fuoco tools 
[http://fuocotools.byethost13.com/index.php](http://fuocotools.byethost13.com/index.php)

, convertIT is in developing,  rewriting in phyton and gtk glade, and it has some problem for now; yuo should write about that problem in its own  official topic...not here or noone will see it

Oh.

I'll check out Fuoco tools, I didn't realize convertIT was in its development stages (didn't get the memo).

What do you mean by "official" topic - opposed to an unofficial topic?  Not sure I'm quite following.  I didn't know it was an in progress development.  I was just wondering if maybe a setting was off or something, didn't know it was still being made therefore was glitchy.

---

### Post by Creative2 on 2008-02-08
well, i have written most of commandline for convertIT , but now i have started my personal project and i left converIT...so i don't support anymore it.

Now brus46 is starting to develop convertIT2 in gtk and phyton , and so i think convertit is left to itself..because he has no time...but you can try to write in that topic 

ConvertIT has its official topic, in this forum search ConvertIT and you will find it...and write about that problem, maybe brus46 will answer.

convertIT is a beta release :) so it WAS still in developing but i repeat it is dead... :) it will not developed anymore ...but one day it will be  ConvertIT2 ...just wait or use Fuoco tools , i support only that project

---

### Post by Syndacate on 2008-02-11
> **Creative2 said:**
> well, i have written most of commandline for convertIT , but now i have started my personal project and i left converIT...so i don't support anymore it.

Now brus46 is starting to develop convertIT2 in gtk and phyton , and so i think convertit is left to itself..because he has no time...but you can try to write in that topic 

ConvertIT has its official topic, in this forum search ConvertIT and you will find it...and write about that problem, maybe brus46 will answer.

convertIT is a beta release :) so it WAS still in developing but i repeat it is dead... :) it will not developed anymore ...but one day it will be  ConvertIT2 ...just wait or use Fuoco tools , i support only that project

Yeah, I'm sorry, didn't know, I read it all on the site.

I use Fuoco tools - it works fine - I encountered the same error but this time it's fixable - it just won't do it if there's no extension on it - but that wasn't the problem with ConvertIT.

Anyways, thanks, your program is epic, btw.

---

### Post by Creative2 on 2008-02-15
plz if there is a problem you must be more accurate , do a log and post ti with every usefull information.
cheers

---

### Post by Syndacate on 2008-02-16
There is no log..

According to the program everything went 100%.

"Completed Successfully" sort of thing - except it did absolutely nothing except flash the command dialog.

Not sure how much more specific I can get.

1)  I hit "convert" (the burning penguin in Fuoco Tools)
2)  The typical shell dialog pops up that always pops up when you convert something - it doesn't completely open - just flashes briefly (you can see it for <1 second), then it goes away.
3)  It says it's "finished"

According to it, there is no error.

---

### Post by Creative2 on 2008-02-16
that you can see briefly is xterm , if you want create a log 

plz------>Extra and option---------> create a log--------->select your prefered text editor here there is a example:

[http://www.youtube.com/watch?v=xXhQ8XU4gw0](http://www.youtube.com/watch?v=xXhQ8XU4gw0)


ps
i have used xterm because some time it's usefull see % of conversion but you can  turn off it from extra and option ....
cheers :)

---

### Post by Syndacate on 2008-02-17
> **Creative2 said:**
> that you can see briefly is xterm , if you want create a log 

plz------>Extra and option---------> create a log--------->select your prefered text editor here there is a example:

[http://www.youtube.com/watch?v=xXhQ8XU4gw0](http://www.youtube.com/watch?v=xXhQ8XU4gw0)


ps
i have used xterm because some time it's usefull see % of conversion but you can  turn off it from extra and option ....
cheers :)

I found the error.

Not that I don't feel like a complete idiot or something.

The GUI basically just activates command lines - that's all it does in reality - apparently the ampersand (&) is something important in the command line ^_^ - like designating input and output files.

The file name was qwerty&abc.wav - in the log it said qwertyINPUTabc.wav - then it was like " could not file location - blah blah blha - qwertyOUTPUTabc.wav at one point.

I renamed the files and it worked.

ha, sorry, I feel like an idiot.

---

