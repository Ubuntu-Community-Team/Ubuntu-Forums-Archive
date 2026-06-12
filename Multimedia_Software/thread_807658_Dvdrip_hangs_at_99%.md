---
title: "Dvd::rip hangs at 99%"
date: 2008-05-26
forum: Multimedia Software
---

### Post by vdawg on 2008-05-26
Hey guys!

I'm trying to rip a dvd which has 4 episodes and I'm using dvd::rip to first copy the dvd on to the hdd which works great and then I set it up with all the settings, etc. but when I start the transcode process about 70% of the time the bloody thing hangs at the end of pass 1 (when it is about 99%)

Here's the logfile, as you can see I started the job the night before, and then when I rolled back in the next morning the process was hung at the point of "Sending signal 9 to PID(s) 20130, 20133"

Now I know that signal 9 is kill, but if I send the signal myself will it continue? I'm going to try doing it tomorrow morning anyways, I just started the stupid thing again but I would like to see if you guys have any feedback, thanks!

```
Sat May 24 19:41:16 2008	Start job 'Generate preview thumbnails - title #4'
Sat May 24 19:41:16 2008	Executing command: execflow dvdrip-thumb /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-orig.jpg /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-clip1.jpg 0 0 0 0 && execflow dvdrip-thumb /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-clip1.jpg /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-zoom.jpg 512 288 && execflow dvdrip-thumb /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-zoom.jpg /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-preview-clip2.jpg 6 8 10 8 && echo EXECFLOW_OK
Sat May 24 19:41:16 2008	Job 'Apply Clip & Zoom preset - title #4' finished
Sat May 24 19:41:17 2008	Generate preview thumbnails - title #4: 30% done.
Sat May 24 19:41:17 2008	Generate preview thumbnails - title #4: 60% done.
Sat May 24 19:41:17 2008	Generate preview thumbnails - title #4: 100% done.
Sat May 24 19:41:17 2008	Job 'Apply preset & make previews - title #4' finished
Sat May 24 19:41:17 2008	Job 'Generate preview thumbnails - title #4' finished
Sat May 24 19:41:21 2008	Project file saved to '/home/vic/dvdrip-data/sophie_paquin_s1d1.rip'
Sat May 24 19:41:30 2008	Project file saved to '/home/vic/dvdrip-data/sophie_paquin_s1d1.rip'
Sat May 24 19:41:31 2008	Start job 'Transcode multipass - title #4'
Sat May 24 19:41:31 2008	Start job 'Transcode video - title #4, pass 1'
Sat May 24 19:41:31 2008	Executing command: mkdir -m 0775 -p '/home/vic/dvdrip-data/sophie_paquin_s1d1/tmp' && cd /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp && mkdir -p /home/vic/dvdrip-data/sophie_paquin_s1d1/avi/004 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/vic\/dvdrip\-data\/sophie_paquin_s1d1\/vob\/004\/ -w 567,50 -b 128,0,2 -s 3.592 --a52_drc_off -I 3 -f 30,4 -M 2 -Y 6,8,10,8 -Z 512x288 -R 1 -y xvid,null --psu_mode --nav_seek /home/vic/dvdrip-data/sophie_paquin_s1d1/tmp/sophie_paquin_s1d1-004-nav.log --no_split  -o /dev/null --print_status 25 && echo EXECFLOW_OK
Sat May 24 19:55:17 2008	Transcode video - title #4, pass 1: 10% done.
Sat May 24 20:07:41 2008	Transcode video - title #4, pass 1: 20% done.
Sat May 24 20:20:10 2008	Transcode video - title #4, pass 1: 30% done.
Sat May 24 20:32:35 2008	Transcode video - title #4, pass 1: 40% done.
Sat May 24 20:45:04 2008	Transcode video - title #4, pass 1: 50% done.
Sat May 24 20:57:23 2008	Transcode video - title #4, pass 1: 60% done.
Sat May 24 21:09:55 2008	Transcode video - title #4, pass 1: 70% done.
Sat May 24 21:22:16 2008	Transcode video - title #4, pass 1: 80% done.
Sat May 24 21:34:47 2008	Transcode video - title #4, pass 1: 90% done.
Sun May 25 13:42:26 2008	Sending signal 9 to PID(s) 20130, 20133
Sun May 25 13:42:26 2008	Job 'Transcode multipass - title #4' cancelled
Sun May 25 13:42:26 2008	Job 'Transcode video - title #4, pass 1' cancelled

```

PS: I used acid rip and it did a decent job, but the thing is that dvd::rip gives me a much better quality and control over my videos!

---

### Post by vdawg on 2008-05-26
Ok so this morning the damn thing was hung at 99% on the second pass with 12 seconds to go!!!!

That was really annoying...

---

