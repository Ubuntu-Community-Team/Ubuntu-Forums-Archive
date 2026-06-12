---
title: "mythtv episode and series numbers"
date: 2009-04-17
forum: Mythbuntu
---

### Post by yee379 on 2009-04-17
so i use xbmc and/or boxee to view my recorded shows from my mythbackend system. of course, the filenames are meaningless without using something like mythrename.pl (great script btw).

so i looked around a bit and found i could use a --format options like

```

%T/%T %- S%isE%ie %- %S %- (%Y-%m-%d @ %H%i)

```

to provide me something that i could actually get xbmc to parse and for me to be able to read.

(i got the %is and $ie from [http://www.mythtv.org/wiki/Talk:Mythrename.pl](http://www.mythtv.org/wiki/Talk:Mythrename.pl))

however, i am not convinced that (1) mythtv's program table even has directly useable series and episode numbers, and (2) the above format line works.

can anyone shed some light on whether it is possible to use mythtv as is to store and retrieve the series and episode numbers?

i was thinking that the only way may be to use use either the seriesid, programid and maybe the syndicatedepisodenumber and query an external service to get that info.

---

### Post by managementboy on 2009-04-17
I have not seen any series information in MythTV, at least something you would need. I have seen it being developed currently for the plugin mythvideo. I have the series information in the Subtilte (Tilte=Mythbusters Subtitle=S07E02)

---

### Post by menny on 2009-04-17
Guys,
There is a perl script I'm developing, which scans all the files in the mythvideo folders, parses the files (to check whether it is a tv show or a movie) and get tv show information/movies information from the internet (thetvdb.com or imdb.com).

If you want to test it, you can download the latest version from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl").

Just download the script, set it as executable (chmod +x fill_mythvideo_metadata.pl) and run it.

I use it in crontab (once a day, and it runs and looks for new files).

Usually the default values are OK. You can set special things (like title type, etc) by using the command line arguments. "fill_mythvideo_metadata.pl -h" for details about that.

There is a thread in the forum which follows this script: [http://ubuntuforums.org/showthread.php?t=1061733&page=15](http://ubuntuforums.org/showthread.php?t=1061733&page=15)

I hope it solves your problem.

---

### Post by yee379 on 2009-04-17
> **managementboy said:**
> I have the series information in the Subtilte (Tilte=Mythbusters Subtitle=S07E02)

how do you collect the information? do you run an external script to add the sNNeNN to the subtitle field?

thanks,

---

### Post by yee379 on 2009-04-17
> **menny said:**
> [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl").


thanks - i was following the thread but was not sure if your script actually is able to update locally recorded tv shows and movies - there was a lot of mention of mythvideo - but i do not use myth video; only off the air recordings.

so... does it? ;) i'm guessing some lookup to compare either the subtitle (episode name) and or the original air date would be required.

---

### Post by menny on 2009-04-17
> **yee379 said:**
> thanks - i was following the thread but was not sure if your script actually is able to update locally recorded tv shows and movies - there was a lot of mention of mythvideo - but i do not use myth video; only off the air recordings.

so... does it? ;) i'm guessing some lookup to compare either the subtitle (episode name) and or the original air date would be required.
Ho, I have misunderstood your request.

The script is only after the mythvideo videos.

Too bad :)

---

### Post by narghile on 2009-05-27
Bump! we really need syndicatedepisodenumber from the database added to mythrename.pl PLEASE ANY PERL CODERS!!! I looked at the source but don't see where / how to query the db. HELP! We need this for XBMC to work correctly... :evil:

---

### Post by ReddogOne on 2009-05-29
> **managementboy said:**
> I have the series information in the Subtilte (Tilte=Mythbusters Subtitle=S07E02)

Is this for all programs or for just something a specific channel has done? I believe that for UK Freeview this information is in the stream... well at least it identifies which programs are in the same series!

---

### Post by theophile on 2009-05-30
I patched together a script that does this very thing. It's used in the context of transcoding recordings made by the HD-PVR. It would be extremely easy though to configure it to just rename files or create symlinks.

The script is here: [http://monopedilos.com/dokuwiki/doku.php?id=hdpvrcutter.pl](http://monopedilos.com/dokuwiki/doku.php?id=hdpvrcutter.pl)

---

