---
title: "ffmpeg video copy increased bit rate - Why?"
date: 2008-09-05
forum: Multimedia Software
---

### Post by RDV on 2008-09-05
I wanted to change container type from mpg to ts to use a specific video editor and I found ffmpeg changed the video bit rate and subsequently the files size. Here is my command line:
ffmpeg -i "hdpvr.mpg" -vcodec copy -acodec copy "hdpvr.ts"
The bit rate changed from: (mpg) 3,645 Kbps to  (ts) 4,676 Kbps
File size changes from (mpg) 779.2Mg to (ts) 999.6Mg

Does anyone know why ffmpeg made the change on a copy? Is there anyway to prevent the increase in file size and bitrate?

In case anyone is interested I am trying to edit mpg files recorded from a Hauppauge HD-PVR. The mpg files was created in Hardy with svn MythTV and the alpha HD-PVR driver. So far the only video editor that will produce lossless edits of these recording is the windows app "H264 TS Cutter v1.11". I run it in a Win-XP Virtualbox session. 

Unfortunately I must transcode the mpg file to a ts container before editing. The increased size is definitely not what I was looking for. As a note none of the mythtv utilities will cut commercials so I need to rely on a windows app. 

I have tried both svn versions of MythTV and Avidemux but the native mpg files cannot be edited with those tools. 

The HD-PVR mpg files contain x264 encoded video and AAC audio. There are no issues with ffmpeg audio copying process from one of these mpg files.

---

### Post by xzero1 on 2008-09-26
I have just purchased the hd-pvr and the current driver creates the captured file in its native .ts format. If you capture directly to a .ts file you should not have the issue. In addition, I would try re-taging your original captured files. The captured stream is format is .ts.

---

