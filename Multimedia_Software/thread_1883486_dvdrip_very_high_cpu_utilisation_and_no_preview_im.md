---
title: "dvdrip very high cpu utilisation and no preview images"
date: 2011-11-19
forum: Multimedia Software
---

### Post by Mayfair on 2011-11-19
Hello,

I'm using Mythbuntu 10.10 with all the updates.  Recently dvdrip (0.98.11) is maxing the cpu whenever I attempt to select a title from the 'Clip & Zoom' page and it is not producing any preview images at least they don't appear in the 'Clip & Zoom' page.  I've tried different DVDs and the results are the same. I can't get beyond the ripping stage and i have to kill the dvdrip process.

There is 74G of free space after the title has been ripped therefore I can't work out why this is happening.

Here's the log from start to ripping DVD titlle #1.  I hope someone can help me.

Sat Nov 19 10:02:58 2011 Start job 'Read TOC (lsdvd|tcprobe)'
Sat Nov 19 10:02:58 2011 Start job 'Read TOC (lsdvd)'
Sat Nov 19 10:02:58 2011 Executing command: execflow lsdvd -a -n -c -s -v -Op \/dev\/sr0 2>/dev/null && echo EXECFLOW_OK
Sat Nov 19 10:02:58 2011 Start job 'Read TOC (tcprobe)'
Sat Nov 19 10:02:58 2011 Successfully read DVD TOC
Sat Nov 19 10:02:58 2011 Copying IFO files from /media/IM_ALAN_PARTRIDGE to /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/ifo
Sat Nov 19 10:03:02 2011 Job 'Read TOC (lsdvd|tcprobe)' finished
Sat Nov 19 10:03:02 2011 Job 'Read TOC (tcprobe)' finished
Sat Nov 19 10:03:02 2011 Job 'Read TOC (lsdvd)' finished
Sat Nov 19 10:03:45 2011 Start job 'Rip selected title(s) / chapter(s)'
Sat Nov 19 10:03:45 2011 Start job 'Process title #1'
Sat Nov 19 10:03:45 2011 Start job 'Rip - title #1'
Sat Nov 19 10:03:45 2011 Executing command: rm -f /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/vob/001//I_AM_ALAN_PARTRIDGE_S01_D01-???.vob && execflow -n 19 tccat -t dvd -T 1,-1,1 -i \/dev\/sr0 | dvdrip-splitpipe -f /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-nav.log 1024 /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/vob/001//I_AM_ALAN_PARTRIDGE_S01_D01 vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Sat Nov 19 10:04:08 2011 Rip - title #1: 10% done.
Sat Nov 19 10:04:26 2011 Rip - title #1: 20% done.
Sat Nov 19 10:04:43 2011 Rip - title #1: 30% done.
Sat Nov 19 10:05:01 2011 Rip - title #1: 40% done.
Sat Nov 19 10:05:17 2011 Rip - title #1: 50% done.
Sat Nov 19 10:05:33 2011 Rip - title #1: 60% done.
Sat Nov 19 10:05:51 2011 Rip - title #1: 70% done.
Sat Nov 19 10:06:09 2011 Rip - title #1: 80% done.
Sat Nov 19 10:06:26 2011 Rip - title #1: 90% done.
Sat Nov 19 10:06:39 2011 Executing command: execflow tcprobe -H 25 -i /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/vob/001/ && echo EXECFLOW_OK
Sat Nov 19 10:06:39 2011 Program stream units calculated
Sat Nov 19 10:06:39 2011 Start job 'Process preview frame - title #1'
Sat Nov 19 10:06:39 2011 Start job 'Grab preview - title #1'
Sat Nov 19 10:06:39 2011 Executing command: mkdir -m 0775 /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/dvdrip7489.snap; cd /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/dvdrip7489.snap; execflow tccat -i \/var\/local\/dvdrip\/I_AM_ALAN_PARTRIDGE_S01_D01\/vob\/001\/  -t vob -S 285949 -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 0 -d 0 -P /dev/null | tcextract -t vob -a 0 -x mpeg2 -d 0 | ffmpeg -r 25.000 -i - -an -r 1 -ss '0.240' -vframes 1 snapshot%03d.png  && execflow convert -size 720x576 /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/dvdrip7489.snap/snapshot*.png /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-orig.jpg && execflow convert -size 720x576 /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/dvdrip7489.snap/snapshot*.png gray:/var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-orig.raw && rm -r /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/dvdrip7489.snap && echo EXECFLOW_OK
Sat Nov 19 10:06:39 2011 Job 'Rip - title #1' finished
Sat Nov 19 10:06:40 2011 Start job 'Apply preset & make previews - title #1'
Sat Nov 19 10:06:40 2011 Start job 'Apply Clip & Zoom preset - title #1'
Sat Nov 19 10:06:41 2011 Start job 'Generate preview thumbnails - title #1'
Sat Nov 19 10:06:41 2011 Executing command: execflow dvdrip-thumb /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-orig.jpg /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-clip1.jpg 0 0 0 0 && execflow dvdrip-thumb /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-clip1.jpg /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-zoom.jpg 656 492 && execflow dvdrip-thumb /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-zoom.jpg /var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/I_AM_ALAN_PARTRIDGE_S01_D01-001-preview-clip2.jpg 6 8 6 8 && echo EXECFLOW_OK
Sat Nov 19 10:06:41 2011 Job 'Apply Clip & Zoom preset - title #1' finished
Sat Nov 19 10:06:41 2011 Job 'Grab preview - title #1' finished
Sat Nov 19 10:06:41 2011 Generate preview thumbnails - title #1: 30% done.
Sat Nov 19 10:06:41 2011 Generate preview thumbnails - title #1: 60% done.
Sat Nov 19 10:06:41 2011 Generate preview thumbnails - title #1: 100% done.
Sat Nov 19 10:06:41 2011 Project file saved to '/var/local/dvdrip/I_AM_ALAN_PARTRIDGE_S01_D01/tmp/backup.rip'
Sat Nov 19 10:06:41 2011 Job 'Rip selected title(s) / chapter(s)' finished
Sat Nov 19 10:06:41 2011 Job 'Process title #1' finished
Sat Nov 19 10:06:41 2011 Job 'Process preview frame - title #1' finished
Sat Nov 19 10:06:41 2011 Job 'Apply preset & make previews - title #1' finished
Sat Nov 19 10:06:41 2011 Job 'Generate preview thumbnails - title #1' finished

---

