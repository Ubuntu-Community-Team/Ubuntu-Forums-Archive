---
title: "DVD::RIP transcoding multiple titles problem"
date: 2010-09-21
forum: Multimedia Software
---

### Post by jasonjob on 2010-09-21
Can't find anything quite like this having been asked already :)

I have just bought all of Babylon 5, and want to put it on my hdd instead of using the discs.

dvd::rip works fine for me.  I can rip and then transcode titles to AVI manually.

What I want is to rip a disc or two, and then have dvd::rip transcode them overnight (takes about 50 minutes per episode on my machine).

I tried this on the command line:

dvdrip -f transcode -t 2 b5s1d1.rip

which, after briefly loading the GUI,  just gets this error:

Can't locate object method "error_dialog" via package "Video::DVDRip::GUI::Main" at /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 173.

Gave up and found dvd::ripqueue, which is a gui utility that automates what I would have put into a script, but it doesn't work properly - dvd::rip launches, but only performs the first pass and produces no output.  My projects were set up and saved correctly (as I said, all this works if I start it manually from the dvd::rip GUI).

So, how do I do it?

Thanks,

Jason

---

### Post by Ghost|BTFH on 2010-09-23
I'd say there's an issue in dvd::rip...
> /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 173.
That is the most logical source of the issue.

That being said, there is information about transcoding multiple files...and this makes me wonder (as I'm no expert on transcode nor on dvd rips) if it would be possible to simply point transcode to the vob files you want transcoded and use a proper batch file and transcode, as shown in the transcode wiki [http://wiki.videolan.org/Transcode]("http://wiki.videolan.org/Transcode")

Hope this helps, on a personal note, DVD::Rip has been acting up on me as of recent, and I gave up on dealing with it and switched over to DVD95 Converter, which does the job very well.

Cheers,
Ghost|BTFH

---

### Post by jasonjob on 2010-09-24
Dug into the perl module referred to in the error message, it's just a standard exception catch.  What triggered it was a missing target file.  Hmmm...

Went back to playing with my script - this time saving it in and running it from the dvdrip-data folder instead of specifying the path in the parameters.  Worked perfectly.

I'd say that's a design flaw in dvdrip - it should be able to be called from anywhere if I give the exact path to the project file (which I did).

Anyway, I now know how to get the thing going overnight :)

---

