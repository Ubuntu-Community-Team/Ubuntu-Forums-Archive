---
title: "Command line DVD interaction..."
date: 2009-04-10
forum: Multimedia Software
---

### Post by jmap82 on 2009-04-10
[B]Please disregard this thread.  I thought my problem had something to do with a program, but the problem seems to be limited to my scripting ability.  

My solution was to remove the `back ticks` from the command.  Somewhere along my process I added them in when they weren't necessary and it broke my script.

That's 2 points for stupidity in 2 weeks....  Maybe I'll get a break someday.[/B]

For any who are interested, my completed script can be found at this site: [http://script.jmap82.com](http://script.jmap82.com)

----------------Original Post Below-----------------



Question: What program will provide title and duration information from a DVD in a way that can be captured when run inside a script.

Background:

I know there are a number of programs out there that do various things with Video DVDs.  I tend to like HandBrakeCLI for ripping DVDs into the MP4 file format.  I've written several scripts to help automate the some of my tasks.

I'm now in the process of writing a script that will rip episodes off of DVDs from TV shows.  Its easy enough to write a script that will rip specific titles, but now I want to have a script to rip all titles over, say, 20 minutes.  I have most of the difficult programming figured out, what is holding me up is finding away to get a list of titles and durations from the DVD and piping it or saving it to a file to be processed.

HandBrakeCLI has an option to print title information, which I have been using up until now.  I can capture HandBrake's output with this command during a regular terminal session:
```

$ `/home/jmap82/HandBrakeCLI -i /media/cdrom0/VIDEO_TS/ -t 0 2>&1`| tee titles.txt

```

However, this command does not work when run inside a script.  I assume that it has something to do with way HandBrakeCLI puts out the information, but I really don't know enough about how computers work to know for sure.

The Question and purpose of this thread is: 

Does anyone know of any other programs that can help me get title and duration information from a DVD in a way that can be capture when run inside of a script?

---

