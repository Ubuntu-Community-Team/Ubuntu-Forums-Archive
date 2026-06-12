---
title: "Mythtv - Move recorded tv to another location"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-05-04
How would i add a button to the context screen in the recorded tv to rename and move recorded movies to my movies folder?? 

Or could this be done by creating a new job / task like transcoding?

---

### Post by Titus A Duxass on 2007-05-04
You can add "buttons" by editing the .xml files that are part of the mythtv installation.

Take a look at this guy's site for a good amount of relevant info:

[http://www.myhdbox.com/mythtips/](http://www.myhdbox.com/mythtips/)

---

### Post by Dubstar_04 on 2007-05-05
That information says that you can't run shell commands from menu items. Is it possible to make a script  to run or add a job to the job list?

---

### Post by Dubstar_04 on 2007-05-10
I've had a little progress with this. I now have mythrename set to rename all recordings when the recording is finished and i have been looking into writing a perl script to move the file from one location to another, however this is a problem as i have no idea what i am doing.

After some googling i have managed to bodge together this

```
 #!/usr/bin/perl
use File::Copy; 

$oldlocation = "/media/sdb1/Recorded TV";
$newlocation = "/media/sdb2/Movies";
move($oldlocation, $newlocation); 
```

However it seems to be wrong as the job completes and the file is still in the same location!! 

If you could assist in producing the correct script please could you help me??

Thankyou.

---

### Post by Dubstar_04 on 2007-05-12
Someone must know perl???

---

### Post by Dubstar_04 on 2007-05-12
I have found another option: myth_archive_job.pl (See attached)

The problem is i don't know how to configure it to suit my needs. 

any suggestions?

---

### Post by Dubstar_04 on 2007-05-18
anyone?

---

### Post by dannyboy79 on 2007-06-13
Well I have it create symlinks instead of rename the actual files. It's using the --link option with the  mythrename.pl perl script if you just want a more readable filename, that will just create readable filenames and make a symlink with the new name and point to the whereever your original recordings are. All you need to do is put mythrename.pl in /usr/local/bin/, make it executable, then add this to your root crontab:
0,30 * * * * /usr/local/bin/mythrename.pl --link /media/400gb/mythtv/readable-recordings/
and it will create symlinks for me within the /media/400gb/mythtv/readable-recordins/ folder every 30 minutes. So my original recordings folder looks like this:
1015_20070602220000.mpg      1029_20070608013000.mpg.png  1029_20070613010000.mpg      1051_20070531205900.mpg.png
1015_20070602220000.mpg.png  1029_20070609010000.mpg      1029_20070613010000.mpg.png  1051_20070607205900.mpg

as an example and then the readable-recordings folder looks like this:
Arli$$ - 2007-06-08, 1-00 AM - Crossing the Line.mpg             BodogFight - 2007-06-05, 10-00 PM.mpg
Arli$$ - 2007-06-08, 1-30 AM - Colors of the Rainbow.mpg         BodogFight - 2007-06-12, 10-00 PM.mpg

If you wanted it to just rename your original recordings then don't use the --link option. I don't know what happens as far as autoexpire, and other awesome mythtv stuff which is why I chose to use the --link option.

And you can change how the new symlink name looks, I need to remove the time from it as I don't like that but I just got it working last night with a little help from superm1, the developer of mythbuntu. 

As far as I can tell you don't have to edit the myth_archive perl script thing at all, you would copy it to wherever you want like say, /usr/local/bin, make it executable, then you would just add a command to cron or crontab with something like this:
myth_archive_job.pl -d %DIR% -f %FILE% -a /video/groups/ 
and that's per this link I found: [http://www.gossamer-threads.com/lists/mythtv/dev/103879?search_string=myth_archive_job.pl;#103879](http://www.gossamer-threads.com/lists/mythtv/dev/103879?search_string=myth_archive_job.pl;#103879)
Within that link, he even talks about having it work for different recording groups, so you could have shows archived to a folder for your wife and a different folder for you I guess. I don't use the recording groups ( i don't think, he he) I am still very new to this awesome program!!!!! Good luck

---

