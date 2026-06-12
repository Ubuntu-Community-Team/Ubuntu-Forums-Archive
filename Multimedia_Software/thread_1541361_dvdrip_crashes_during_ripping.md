---
title: "dvdrip crashes during ripping"
date: 2010-07-29
forum: Multimedia Software
---

### Post by bth73 on 2010-07-29
Since 10.04, dvdrip will not finish ripping without crashing on multi episode disk.
Reopened dvdrip to copy log files (below) and only part of log remains, but now transcode is available where before it was not. This dvd has 22 chaptors and it crashed at the end of 21. 22 came up on the progress bar but just stalled there.

[truncated 692 lines]
this specific DVD.
Wed Jul 28 23:22:30 2010 Start job 'Apply preset & make previews - title #21'
Wed Jul 28 23:22:30 2010 Start job 'Apply Clip & Zoom preset - title #21'
Wed Jul 28 23:22:30 2010 Start job 'Generate preview thumbnails - title #21'
Wed Jul 28 23:22:30 2010 Executing command: execflow dvdrip-thumb /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-orig.jpg /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-clip1.jpg 0 0 0 0 && execflow dvdrip-thumb /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-clip1.jpg /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-zoom.jpg 632 472 && execflow dvdrip-thumb /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-zoom.jpg /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-021-preview-clip2.jpg 4 4 4 4 && echo EXECFLOW_OK
Wed Jul 28 23:22:30 2010 Job 'Apply Clip & Zoom preset - title #21' finished
Wed Jul 28 23:22:30 2010 Job 'Grab preview - title #21' finished
Wed Jul 28 23:22:30 2010 Generate preview thumbnails - title #21: 30% done.
Wed Jul 28 23:22:30 2010 Generate preview thumbnails - title #21: 60% done.
Wed Jul 28 23:22:30 2010 Generate preview thumbnails - title #21: 100% done.
Wed Jul 28 23:22:30 2010 Start job 'Process title #22'
Wed Jul 28 23:22:30 2010 Start job 'Rip - title #22'
Wed Jul 28 23:22:30 2010 Executing command: rm -f /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/vob/022//BEAVIS_BUTTHEAD_VOL1_D2-???.vob && execflow -n 19 tccat -t dvd -T 22,-1,1 -i \/dev\/sr0 | dvdrip-splitpipe -f /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/tmp/BEAVIS_BUTTHEAD_VOL1_D2-022-nav.log 1024 /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/vob/022//BEAVIS_BUTTHEAD_VOL1_D2 vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Wed Jul 28 23:22:30 2010 Job 'Process title #21' finished
Wed Jul 28 23:22:30 2010 Job 'Process preview frame - title #21' finished
Wed Jul 28 23:22:30 2010 Job 'Apply preset & make previews - title #21' finished
Wed Jul 28 23:22:30 2010 Job 'Generate preview thumbnails - title #21' finished
Wed Jul 28 23:22:30 2010 Executing command: execflow tcprobe  -i /home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2/vob/022/ && echo EXECFLOW_OK
Wed Jul 28 23:22:30 2010 Job 'Rip - title #22' finished
Wed Jul 28 23:30:39 2010 Project file saved to '/home/bt/dvdrip-data/BEAVIS_BUTTHEAD_VOL1_D2.rip'

---

### Post by slooksterpsv on 2010-07-29
I can't say for sure why it's crashing, but here's a few suggestions:

1. Go to: Debug -> Check Dependencies, and make sure they're met, if RAR is a newer version, don't worry.

2. Make sure the CD isn't scratched on the bottom.

3. Make sure you have the libdvdread instealled and libdvdcss installed (don't remember the numbers, but there's a guide for it).

---

### Post by bth73 on 2010-07-29
all that is ok. does it on every disk I've tried so far. Rar is newer but optional.

---

