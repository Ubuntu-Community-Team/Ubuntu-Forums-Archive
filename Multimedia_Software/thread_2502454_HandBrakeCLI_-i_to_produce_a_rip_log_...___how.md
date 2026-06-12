---
title: "HandBrakeCLI -i to produce a rip log ...   how?"
date: 2024-11-15
forum: Multimedia Software
---

### Post by shantiq on 2024-11-15
been banging my head trying to work it out?    any of you know that?   thanx

I use:


```
HandBrakeCLI -i /dev/sr1 -o /home/shan/Videos/"Name".mkv --main-feature -e ffmpeg2 -b 3000 -E copy  -r 30 -s "1,2,3"
```

if i add ```
--json > log.txt
```  or ```
--json 2> log.txt
```  anywhere in there nothing happens


what is the correct syntax; the --help does not say

---

### Post by 1fallen on 2024-11-15
Activity Logs on the command line

HandBrake’s command line interface outputs to the standard streams stdout and stderr, with encode progress information routed to the former and log messages routed to the latter.

To capture HandBrake’s log messages to a file, simply redirect stderr:

HandBrakeCLI ... 2> my-activity-log.txt

Source: [https://handbrake.fr/docs/en/latest/help/activity-log.html](https://handbrake.fr/docs/en/latest/help/activity-log.html)

---

### Post by shantiq on 2024-11-16
[CENTER]i have seen all this before where please do you put this on this line was my question at the start at the end before -o where thanx 1fallen. Please kindly show me the full line with the request for a log    thanx

[/CENTER]
[COLOR=#000000]HandBrakeCLI -i /dev/sr1 -o /home/shan/Videos/"Name".mkv --main-feature -e ffmpeg2 -b 3000 -E copy  -r 30 -s "1,2,3"

[/COLOR]
[CENTER]

[/CENTER]

---

### Post by 1fallen on 2024-11-16
If you have  seen all this before then why aren't you using a script with "stdout and stderr,"
The CLI version of Handbrake will need that script to work, it's not included with HandBrake CLI version. I know the older versions did though.  .08 and I think .09 was capable of that.

EDIT Yep, It was removed during the development of 1.0.x.

The 0.9.x series was the last that would generate a batch file directly from the queue window.

I'm not a fan of Handbrake, but I use "MakeMKV" no need for Handbrake on my end. It has changed hands 3 times now, with features added and removed.

That Log I included was the GUI Handbrake, I forgot to write that in my first post sorry.

---

### Post by shantiq on 2024-11-17
> 
it's not included with HandBrake CLI version. I know the older versions did though

might be the answer :KS   Why in all that is holy would they remove that from the software; I too distinctly remember using it with log i think
Does anyone know differently?

As regards stdout stderr could someone show an example of how to use that (i have no idea) tagged on to my line in OP   (unless it means having to knock up a script in which case forget it :)


Thanx




shan

---

