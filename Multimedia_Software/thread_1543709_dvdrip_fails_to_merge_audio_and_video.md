---
title: "dvd:rip fails to merge audio and video"
date: 2010-08-01
forum: Multimedia Software
---

### Post by roman5x3 on 2010-08-01
I am attempting to rip a DVD to ogm format with dvd::rip. It has failed twice with the same results. It creates a ogm file with the video and another with the audio. I am new to kubuntu but not new to linux. (I have a gentoo background.) 

Here is the log. I am not sure what is useful and what is not so I am posting the whole thing.

```

Fri Jul 30 22:26:33 2010 Detected transcode version: 10105
Fri Jul 30 22:26:56 2010 Project file saved to '/home/damon/dvdrip-data/The.Quiet.rip'
Fri Jul 30 22:26:56 2010 Project temporary dir '/home/damon/dvdrip-data/The.Quiet/tmp' created
Fri Jul 30 22:26:56 2010 Project The.Quiet created
Fri Jul 30 22:27:00 2010 Start job 'Read TOC (lsdvd|tcprobe)'
Fri Jul 30 22:27:00 2010 Start job 'Read TOC (lsdvd)'
Fri Jul 30 22:27:00 2010 Executing command: execflow lsdvd -a -n -c -s -v -Op \/dev\/sr0 2>/dev/null && echo EXECFLOW_OK
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:27:06 2010 Start job 'Read TOC (tcprobe)'
Fri Jul 30 22:27:06 2010 Successfully read DVD TOC
Fri Jul 30 22:27:06 2010 Mounting DVD at {mount_point}
Fri Jul 30 22:27:06 2010 WARNING: no IFO files found - vobsub feature disabled.
Fri Jul 30 22:27:06 2010 Copying IFO files from {src_dir} to /home/damon/dvdrip-data/The.Quiet/tmp/ifo
Fri Jul 30 22:27:06 2010 Umount {mount_point}: Usage: umount -h | -V
       umount -a [-d] [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-d] [-f] [-r] [-n] [-v] special | node...
Fri Jul 30 22:27:06 2010 Job 'Read TOC (lsdvd|tcprobe)' finished
Fri Jul 30 22:27:07 2010 Job 'Read TOC (tcprobe)' finished
Fri Jul 30 22:27:07 2010 Job 'Read TOC (lsdvd)' finished
Fri Jul 30 22:27:12 2010 Start job 'Rip selected title(s) / chapter(s)'
Fri Jul 30 22:27:12 2010 Start job 'Process title #1'
Fri Jul 30 22:27:12 2010 Start job 'Rip - title #1'
Fri Jul 30 22:27:12 2010 Executing command: rm -rf /home/damon/dvdrip-data/The.Quiet/tmp/subtitles/001/00; mkdir -p /home/damon/dvdrip-data/The.Quiet/tmp/subtitles/001/00; touch /home/damon/dvdrip-data/The.Quiet/tmp/subtitles/001/00/.ripped; rm -f /home/damon/dvdrip-data/The.Quiet/vob/001//The.Quiet-???.vob && execflow -n 19 tccat -t dvd -T 1,-1,1 -i \/dev\/sr0  | dvdrip-multitee 1 'tcextract -x ps1 -t vob -a 0x20 | subtitle2pgm -P -C 0 -o /home/damon/dvdrip-data/The.Quiet/tmp/subtitles/001/00/pic -e 00:00:00,50000 2>&1 | dvdrip-subpng' | dvdrip-splitpipe -f /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-nav.log 1024 /home/damon/dvdrip-data/The.Quiet/vob/001//The.Quiet vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Fri Jul 30 22:30:02 2010 Rip - title #1: 10% done.
Fri Jul 30 22:32:35 2010 Rip - title #1: 20% done.
Fri Jul 30 22:34:57 2010 Rip - title #1: 30% done.
Fri Jul 30 22:36:50 2010 Rip - title #1: 40% done.
Fri Jul 30 22:38:47 2010 Rip - title #1: 50% done.
Fri Jul 30 22:40:58 2010 Rip - title #1: 60% done.
Fri Jul 30 22:43:34 2010 Rip - title #1: 70% done.
Fri Jul 30 22:44:57 2010 Executing command: execflow tcprobe -H 25 -i /home/damon/dvdrip-data/The.Quiet/vob/001/ && echo EXECFLOW_OK
Fri Jul 30 22:45:00 2010 Program stream units calculated
Fri Jul 30 22:45:00 2010 Not enabling PSU core, because this movie has only one PSU.
Fri Jul 30 22:45:01 2010 Start job 'Process preview frame - title #1'
Fri Jul 30 22:45:01 2010 Start job 'Grab preview - title #1'
Fri Jul 30 22:45:01 2010 Executing command: mkdir -m 0775 /home/damon/dvdrip-data/The.Quiet/tmp/dvdrip4026.snap; cd /home/damon/dvdrip-data/The.Quiet/tmp/dvdrip4026.snap; execflow tccat -i \/home\/damon\/dvdrip\-data\/The\.Quiet\/vob\/001\/  -t vob -S 1256755 -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 0 -d 0 -P /dev/null | tcextract -t vob -a 0 -x mpeg2 -d 0 | ffmpeg -r 29.970 -i - -an -r 1 -ss '0.067' -vframes 1 snapshot%03d.png  && execflow convert -size 720x480 /home/damon/dvdrip-data/The.Quiet/tmp/dvdrip4026.snap/snapshot*.png /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-orig.jpg && execflow convert -size 720x480 /home/damon/dvdrip-data/The.Quiet/tmp/dvdrip4026.snap/snapshot*.png gray:/home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-orig.raw && rm -r /home/damon/dvdrip-data/The.Quiet/tmp/dvdrip4026.snap && echo EXECFLOW_OK
Fri Jul 30 22:45:01 2010 Job 'Rip - title #1' finished
Fri Jul 30 22:45:01 2010 Job 'Rip - title #1' warning: It seems that transcode ripping stopped short.
The movie has 172992 frames, but only 137465
were ripped. This is most likely a problem with your
transcode/libdvdread installation, resp. a problem with
this specific DVD.
Fri Jul 30 22:45:04 2010 Start job 'Apply preset & make previews - title #1'
Fri Jul 30 22:45:04 2010 Start job 'Apply Clip & Zoom preset - title #1'
Fri Jul 30 22:45:04 2010 Start job 'Generate preview thumbnails - title #1'
Fri Jul 30 22:45:04 2010 Executing command: execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-orig.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip1.jpg 0 0 0 0 && execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip1.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-zoom.jpg 640 360 && execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-zoom.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip2.jpg 44 0 44 0 && echo EXECFLOW_OK
Fri Jul 30 22:45:04 2010 Job 'Apply Clip & Zoom preset - title #1' finished
Fri Jul 30 22:45:04 2010 Job 'Grab preview - title #1' finished
Fri Jul 30 22:45:04 2010 Generate preview thumbnails - title #1: 30% done.
Fri Jul 30 22:45:05 2010 Generate preview thumbnails - title #1: 60% done.
Fri Jul 30 22:45:05 2010 Generate preview thumbnails - title #1: 100% done.
Fri Jul 30 22:45:05 2010 Project file saved to '/home/damon/dvdrip-data/The.Quiet/tmp/backup.rip'
Fri Jul 30 22:45:06 2010 Job 'Rip selected title(s) / chapter(s)' finished
Fri Jul 30 22:45:06 2010 Job 'Process title #1' finished
Fri Jul 30 22:45:06 2010 Job 'Process preview frame - title #1' finished
Fri Jul 30 22:45:06 2010 Job 'Apply preset & make previews - title #1' finished
Fri Jul 30 22:45:06 2010 Job 'Generate preview thumbnails - title #1' finished
Fri Jul 30 23:13:49 2010 Start job 'Apply preset & make previews - title #1'
Fri Jul 30 23:13:49 2010 Start job 'Apply Clip & Zoom preset - title #1'
Fri Jul 30 23:13:50 2010 Start job 'Generate preview thumbnails - title #1'
Fri Jul 30 23:13:50 2010 Executing command: execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-orig.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip1.jpg 0 0 0 0 && execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip1.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-zoom.jpg 768 432 && execflow dvdrip-thumb /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-zoom.jpg /home/damon/dvdrip-data/The.Quiet/tmp/The.Quiet-001-preview-clip2.jpg 56 0 56 0 && echo EXECFLOW_OK
Fri Jul 30 23:13:50 2010 Job 'Apply Clip & Zoom preset - title #1' finished
Fri Jul 30 23:13:50 2010 Generate preview thumbnails - title #1: 30% done.
Fri Jul 30 23:13:51 2010 Generate preview thumbnails - title #1: 60% done.
Fri Jul 30 23:13:53 2010 Generate preview thumbnails - title #1: 100% done.
Fri Jul 30 23:13:54 2010 Job 'Apply preset & make previews - title #1' finished
Fri Jul 30 23:13:54 2010 Job 'Generate preview thumbnails - title #1' finished
Fri Jul 30 23:24:02 2010 Start job 'Transcode with VBR audio - title #1'
Fri Jul 30 23:24:02 2010 Start job 'Transcode with VBR audio, first pass - title #1'
Fri Jul 30 23:24:02 2010 Start job 'Transcode video - title #1, pass 1'
Fri Jul 30 23:24:02 2010 Executing command: mkdir -m 0775 -p '/home/damon/dvdrip-data/The.Quiet/tmp' && cd /home/damon/dvdrip-data/The.Quiet/tmp && mkdir -p /home/damon/dvdrip-data/The.Quiet/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/damon\/dvdrip\-data\/The\.Quiet\/vob\/001\/ -w 3794,50 -b 384 -s 1.952 --a52_drc_off -f 30,4 -M 2 -Y 56,0,56,0 -Z 768x432 -R 1 -y xvid4,ogg -m /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK
Fri Jul 30 23:35:49 2010 Transcode video - title #1, pass 1: 10% done.
Fri Jul 30 23:46:43 2010 Transcode video - title #1, pass 1: 20% done.
Fri Jul 30 23:57:24 2010 Transcode video - title #1, pass 1: 30% done.
Sat Jul 31 00:07:42 2010 Transcode video - title #1, pass 1: 40% done.
Sat Jul 31 00:18:21 2010 Transcode video - title #1, pass 1: 50% done.
Sat Jul 31 00:28:56 2010 Transcode video - title #1, pass 1: 60% done.
Sat Jul 31 00:39:41 2010 Transcode video - title #1, pass 1: 70% done.
Sat Jul 31 00:50:24 2010 Transcode video - title #1, pass 1: 80% done.
Sat Jul 31 01:01:08 2010 Transcode video - title #1, pass 1: 90% done.
Sat Jul 31 01:11:52 2010 Transcode video - title #1, pass 1: 100% done.
Sat Jul 31 01:22:47 2010 Transcode video - title #1, pass 1: 110% done.
Sat Jul 31 01:32:58 2010 Transcode video - title #1, pass 1: 120% done.
Sat Jul 31 01:35:46 2010 Start job 'Calculate video bitrate  - title #1'
Sat Jul 31 01:35:49 2010 Adjusted video bitrate to 3794 after vbr audio transcoding
Sat Jul 31 01:35:50 2010 Start job 'Transcode with VBR audio, second pass - title #1'
Sat Jul 31 01:35:50 2010 Start job 'Transcode video - title #1, pass 2'
Sat Jul 31 01:35:52 2010 Executing command: mkdir -m 0775 -p '/home/damon/dvdrip-data/The.Quiet/tmp' && cd /home/damon/dvdrip-data/The.Quiet/tmp && mkdir -p /home/damon/dvdrip-data/The.Quiet/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob,null -i \/home\/damon\/dvdrip\-data\/The\.Quiet\/vob\/001\/ -w 3794,50 -b 384 -s 1.952 --a52_drc_off -f 30,4 -M 2 -Y 56,0,56,0 -Z 768x432 -R 2 -y xvid4,null -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK
Sat Jul 31 01:35:52 2010 Job 'Calculate video bitrate  - title #1' finished
Sat Jul 31 01:35:52 2010 Job 'Transcode with VBR audio, first pass - title #1' finished
Sat Jul 31 01:35:52 2010 Job 'Transcode video - title #1, pass 1' finished
Sat Jul 31 01:50:48 2010 Transcode video - title #1, pass 2: 10% done.
Sat Jul 31 02:04:22 2010 Transcode video - title #1, pass 2: 20% done.
Sat Jul 31 02:17:44 2010 Transcode video - title #1, pass 2: 30% done.
Sat Jul 31 02:30:32 2010 Transcode video - title #1, pass 2: 40% done.
Sat Jul 31 02:44:19 2010 Transcode video - title #1, pass 2: 50% done.
Sat Jul 31 02:57:47 2010 Transcode video - title #1, pass 2: 60% done.
Sat Jul 31 03:12:15 2010 Transcode video - title #1, pass 2: 70% done.
Sat Jul 31 03:26:06 2010 Transcode video - title #1, pass 2: 80% done.
Sat Jul 31 03:40:05 2010 Transcode video - title #1, pass 2: 90% done.
Sat Jul 31 03:53:40 2010 Transcode video - title #1, pass 2: 100% done.
Sat Jul 31 04:08:21 2010 Transcode video - title #1, pass 2: 110% done.
Sat Jul 31 04:21:33 2010 Transcode video - title #1, pass 2: 120% done.
Sat Jul 31 04:26:15 2010 Start job 'Merge audio - title #1, audio track #0'
Sat Jul 31 04:26:15 2010 Executing command: execflow -n 19 ogmmerge -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged  /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && mv /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm && rm -f /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && echo EXECFLOW_OK
Sat Jul 31 04:26:15 2010 Job 'Transcode video - title #1, pass 2' finished
Sat Jul 31 04:26:16 2010 Merge audio - title #1, audio track #0: 430% done.
Sat Jul 31 04:26:16 2010 Job 'Transcode with VBR audio - title #1' exited with error: Job 'Transcode with VBR audio, second pass - title #1' failed with error message:
Job 'Merge audio - title #1, audio track #0' failed with error message:
Command exits with failure code:
Command: execflow -n 19 ogmmerge -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged  /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && mv /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm && rm -f /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && echo EXECFLOW_OK

Output: Using AVI demultiplexer for /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm. Opening file. This may take some time depending on the file's size.
+-> Using video output module for video stream.
Using OGG/OGM demultiplexer for /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm.
*** glibc detected *** ogmmerge: free(): invalid pointer: 0x00000000016ff000 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f79ed7a35b6]
/usr/lib/libvorbis.so.0(vorbis_comment_clear+0x5d)[0x7f79ee648dcd]
ogmmerge[0x410a20]
ogmmerge[0x410366]
ogmmerge[0x405f05]
ogmmerge[0x40519f]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f79ed74ac4d]
ogmmerge[0x402b49]
======= Memory map: ========
00400000-0042f000 r-xp 00000000 08:01 4074410                            /usr/bin/ogmmerge
0062e000-0062f000 r--p 0002e000 08:01 4074410                            /usr/bin/ogmmerge
0062f000-00630000 rw-p 0002f000 08:01 4074410                            /usr/bin/ogmmerge
00630000-00631000 rw-p 00000000 00:00 0 
016c7000-0171e000 rw-p 00000000 00:00 0                                  [heap]
7f79ed090000-7f79ed72c000 rw-p 00000000 00:00 0 
7f79ed72c000-7f79ed8a6000 r-xp 00000000 08:01 3670313                    /lib/libc-2.11.1.so
7f79ed8a6000-7f79edaa5000 ---p 0017a000 08:01 3670313                    /lib/libc-2.11.1.so
7f79edaa5000-7f79edaa9000 r--p 00179000 08:01 3670313                    /lib/libc-2.11.1.so
7f79edaa9000-7f79edaaa000 rw-p 0017d000 08:01 3670313                    /lib/libc-2.11.1.so
7f79edaaa000-7f79edaaf000 rw-p 00000000 00:00 0 
7f79edaaf000-7f79edac5000 r-xp 00000000 08:01 3670095                    /lib/libgcc_s.so.1
7f79edac5000-7f79edcc4000 ---p 00016000 08:01 3670095                    /lib/libgcc_s.so.1
7f79edcc4000-7f79edcc5000 r--p 00015000 08:01 3670095                    /lib/libgcc_s.so.1
7f79edcc5000-7f79edcc6000 rw-p 00016000 08:01 3670095                    /lib/libgcc_s.so.1
7f79edcc6000-7f79edd48000 r-xp 00000000 08:01 3670317                    /lib/libm-2.11.1.so
7f79edd48000-7f79edf47000 ---p 00082000 08:01 3670317                    /lib/libm-2.11.1.so
7f79edf47000-7f79edf48000 r--p 00081000 08:01 3670317                    /lib/libm-2.11.1.so
7f79edf48000-7f79edf49000 rw-p 00082000 08:01 3670317                    /lib/libm-2.11.1.so
7f79edf49000-7f79ee03f000 r-xp 00000000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7f79ee03f000-7f79ee23f000 ---p 000f6000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7f79ee23f000-7f79ee246000 r--p 000f6000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7f79ee246000-7f79ee248000 rw-p 000fd000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7f79ee248000-7f79ee25d000 rw-p 00000000 00:00 0 
7f79ee25d000-7f79ee420000 r-xp 00000000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7f79ee420000-7f79ee620000 ---p 001c3000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7f79ee620000-7f79ee637000 r--p 001c3000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7f79ee637000-7f79ee638000 rw-p 001da000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7f79ee638000-7f79ee664000 r-xp 00000000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7f79ee664000-7f79ee863000 ---p 0002c000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7f79ee863000-7f79ee864000 r--p 0002b000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7f79ee864000-7f79ee865000 rw-p 0002c000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7f79ee865000-7f79ee86b000 r-xp 00000000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7f79ee86b000-7f79eea6a000 ---p 00006000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7f79eea6a000-7f79eea6b000 r--p 00005000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7f79eea6b000-7f79eea6c000 rw-p 00006000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7f79eea6c000-7f79eea8c000 r-xp 00000000 08:01 3670037                    /lib/ld-2.11.1.so
7f79eec6a000-7f79eec6f000 rw-p 00000000 00:00 0 
7f79eec86000-7f79eec8c000 rw-p 00000000 00:00 0 
7f79eec8c000-7f79eec8d000 r--p 00020000 08:01 3670037                    /lib/ld-2.11.1.so
7f79eec8d000-7f79eec8e000 rw-p 00021000 08:01 3670037                    /lib/ld-2.11.1.so
7f79eec8e000-7f79eec8f000 rw-p 00000000 00:00 0 
7fff28c7a000-7fff28c8f000 rw-p 00000000 00:00 0                          [stack]
7fff28d76000-7fff28d77000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
+-> Using Vorbis audio output module for stream 1.
Aborted

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
Sat Jul 31 04:26:23 2010 Job 'Transcode with VBR audio - title #1' cancelled
Sat Jul 31 04:26:31 2010 Job 'Transcode with VBR audio, second pass - title #1' finished
Sat Jul 31 04:26:32 2010 Job 'Merge audio - title #1, audio track #0' finished
Sat Jul 31 23:07:22 2010 Project file saved to '/home/damon/dvdrip-data/The.Quiet.rip'
Sat Jul 31 23:09:44 2010 Start job 'Transcode with VBR audio - title #1'
Sat Jul 31 23:09:44 2010 Start job 'Transcode with VBR audio, first pass - title #1'
Sat Jul 31 23:09:44 2010 Start job 'Transcode video - title #1, pass 1'
Sat Jul 31 23:09:44 2010 Executing command: mkdir -m 0775 -p '/home/damon/dvdrip-data/The.Quiet/tmp' && cd /home/damon/dvdrip-data/The.Quiet/tmp && mkdir -p /home/damon/dvdrip-data/The.Quiet/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/damon\/dvdrip\-data\/The\.Quiet\/vob\/001\/ -w 3794,50 -b 384 -s 1.952 --a52_drc_off -f 30,4 -M 2 -Y 56,0,56,0 -Z 768x432 -R 1 -y xvid4,ogg -m /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK
Sat Jul 31 23:21:29 2010 Transcode video - title #1, pass 1: 10% done.
Sat Jul 31 23:32:34 2010 Transcode video - title #1, pass 1: 20% done.
Sat Jul 31 23:43:41 2010 Transcode video - title #1, pass 1: 30% done.
Sat Jul 31 23:54:26 2010 Transcode video - title #1, pass 1: 40% done.
Sun Aug  1 00:05:30 2010 Transcode video - title #1, pass 1: 50% done.
Sun Aug  1 00:16:33 2010 Transcode video - title #1, pass 1: 60% done.
Sun Aug  1 00:27:48 2010 Transcode video - title #1, pass 1: 70% done.
Sun Aug  1 00:38:58 2010 Transcode video - title #1, pass 1: 80% done.
Sun Aug  1 00:50:08 2010 Transcode video - title #1, pass 1: 90% done.
Sun Aug  1 01:01:15 2010 Transcode video - title #1, pass 1: 100% done.
Sun Aug  1 01:12:33 2010 Transcode video - title #1, pass 1: 110% done.
Sun Aug  1 01:23:04 2010 Transcode video - title #1, pass 1: 120% done.
Sun Aug  1 01:25:57 2010 Start job 'Calculate video bitrate  - title #1'
Sun Aug  1 01:26:00 2010 Adjusted video bitrate to 3794 after vbr audio transcoding
Sun Aug  1 01:26:01 2010 Start job 'Transcode with VBR audio, second pass - title #1'
Sun Aug  1 01:26:01 2010 Start job 'Transcode video - title #1, pass 2'
Sun Aug  1 01:26:03 2010 Executing command: mkdir -m 0775 -p '/home/damon/dvdrip-data/The.Quiet/tmp' && cd /home/damon/dvdrip-data/The.Quiet/tmp && mkdir -p /home/damon/dvdrip-data/The.Quiet/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob,null -i \/home\/damon\/dvdrip\-data\/The\.Quiet\/vob\/001\/ -w 3794,50 -b 384 -s 1.952 --a52_drc_off -f 30,4 -M 2 -Y 56,0,56,0 -Z 768x432 -R 2 -y xvid4,null -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK
Sun Aug  1 01:26:03 2010 Job 'Calculate video bitrate  - title #1' finished
Sun Aug  1 01:26:03 2010 Job 'Transcode with VBR audio, first pass - title #1' finished
Sun Aug  1 01:26:03 2010 Job 'Transcode video - title #1, pass 1' finished
Sun Aug  1 01:41:31 2010 Transcode video - title #1, pass 2: 10% done.
Sun Aug  1 01:55:34 2010 Transcode video - title #1, pass 2: 20% done.
Sun Aug  1 02:09:24 2010 Transcode video - title #1, pass 2: 30% done.
Sun Aug  1 02:22:32 2010 Transcode video - title #1, pass 2: 40% done.
Sun Aug  1 02:36:43 2010 Transcode video - title #1, pass 2: 50% done.
Sun Aug  1 02:50:30 2010 Transcode video - title #1, pass 2: 60% done.
Sun Aug  1 03:05:16 2010 Transcode video - title #1, pass 2: 70% done.
Sun Aug  1 03:19:19 2010 Transcode video - title #1, pass 2: 80% done.
Sun Aug  1 03:33:31 2010 Transcode video - title #1, pass 2: 90% done.
Sun Aug  1 03:47:13 2010 Transcode video - title #1, pass 2: 100% done.
Sun Aug  1 04:02:04 2010 Transcode video - title #1, pass 2: 110% done.
Sun Aug  1 04:15:24 2010 Transcode video - title #1, pass 2: 120% done.
Sun Aug  1 04:20:08 2010 Start job 'Merge audio - title #1, audio track #0'
Sun Aug  1 04:20:08 2010 Executing command: execflow -n 19 ogmmerge -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged  /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && mv /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm && rm -f /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && echo EXECFLOW_OK
Sun Aug  1 04:20:08 2010 Job 'Transcode video - title #1, pass 2' finished
Sun Aug  1 04:20:09 2010 Job 'Transcode with VBR audio - title #1' exited with error: Job 'Transcode with VBR audio, second pass - title #1' failed with error message:
Job 'Merge audio - title #1, audio track #0' failed with error message:
Command exits with failure code:
Command: execflow -n 19 ogmmerge -o /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged  /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && mv /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm.merged /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm && rm -f /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm && echo EXECFLOW_OK

Output: Using AVI demultiplexer for /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001.ogm. Opening file. This may take some time depending on the file's size.
+-> Using video output module for video stream.
Using OGG/OGM demultiplexer for /home/damon/dvdrip-data/The.Quiet/avi/001/The.Quiet-001-00.ogm.
*** glibc detected *** ogmmerge: free(): invalid pointer: 0x0000000000ed4000 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7ff1ca94c5b6]
/usr/lib/libvorbis.so.0(vorbis_comment_clear+0x5d)[0x7ff1cb7f1dcd]
ogmmerge[0x410a20]
ogmmerge[0x410366]
ogmmerge[0x405f05]
ogmmerge[0x40519f]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7ff1ca8f3c4d]
ogmmerge[0x402b49]
======= Memory map: ========
00400000-0042f000 r-xp 00000000 08:01 4074410                            /usr/bin/ogmmerge
0062e000-0062f000 r--p 0002e000 08:01 4074410                            /usr/bin/ogmmerge
0062f000-00630000 rw-p 0002f000 08:01 4074410                            /usr/bin/ogmmerge
00630000-00631000 rw-p 00000000 00:00 0 
00e9c000-00ef3000 rw-p 00000000 00:00 0                                  [heap]
7ff1ca239000-7ff1ca8d5000 rw-p 00000000 00:00 0 
7ff1ca8d5000-7ff1caa4f000 r-xp 00000000 08:01 3670313                    /lib/libc-2.11.1.so
7ff1caa4f000-7ff1cac4e000 ---p 0017a000 08:01 3670313                    /lib/libc-2.11.1.so
7ff1cac4e000-7ff1cac52000 r--p 00179000 08:01 3670313                    /lib/libc-2.11.1.so
7ff1cac52000-7ff1cac53000 rw-p 0017d000 08:01 3670313                    /lib/libc-2.11.1.so
7ff1cac53000-7ff1cac58000 rw-p 00000000 00:00 0 
7ff1cac58000-7ff1cac6e000 r-xp 00000000 08:01 3670095                    /lib/libgcc_s.so.1
7ff1cac6e000-7ff1cae6d000 ---p 00016000 08:01 3670095                    /lib/libgcc_s.so.1
7ff1cae6d000-7ff1cae6e000 r--p 00015000 08:01 3670095                    /lib/libgcc_s.so.1
7ff1cae6e000-7ff1cae6f000 rw-p 00016000 08:01 3670095                    /lib/libgcc_s.so.1
7ff1cae6f000-7ff1caef1000 r-xp 00000000 08:01 3670317                    /lib/libm-2.11.1.so
7ff1caef1000-7ff1cb0f0000 ---p 00082000 08:01 3670317                    /lib/libm-2.11.1.so
7ff1cb0f0000-7ff1cb0f1000 r--p 00081000 08:01 3670317                    /lib/libm-2.11.1.so
7ff1cb0f1000-7ff1cb0f2000 rw-p 00082000 08:01 3670317                    /lib/libm-2.11.1.so
7ff1cb0f2000-7ff1cb1e8000 r-xp 00000000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7ff1cb1e8000-7ff1cb3e8000 ---p 000f6000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7ff1cb3e8000-7ff1cb3ef000 r--p 000f6000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7ff1cb3ef000-7ff1cb3f1000 rw-p 000fd000 08:01 4065807                    /usr/lib/libstdc++.so.6.0.13
7ff1cb3f1000-7ff1cb406000 rw-p 00000000 00:00 0 
7ff1cb406000-7ff1cb5c9000 r-xp 00000000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7ff1cb5c9000-7ff1cb7c9000 ---p 001c3000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7ff1cb7c9000-7ff1cb7e0000 r--p 001c3000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7ff1cb7e0000-7ff1cb7e1000 rw-p 001da000 08:01 4065861                    /usr/lib/libvorbisenc.so.2.0.6
7ff1cb7e1000-7ff1cb80d000 r-xp 00000000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7ff1cb80d000-7ff1cba0c000 ---p 0002c000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7ff1cba0c000-7ff1cba0d000 r--p 0002b000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7ff1cba0d000-7ff1cba0e000 rw-p 0002c000 08:01 4065859                    /usr/lib/libvorbis.so.0.4.3
7ff1cba0e000-7ff1cba14000 r-xp 00000000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7ff1cba14000-7ff1cbc13000 ---p 00006000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7ff1cbc13000-7ff1cbc14000 r--p 00005000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7ff1cbc14000-7ff1cbc15000 rw-p 00006000 08:01 4065640                    /usr/lib/libogg.so.0.6.0
7ff1cbc15000-7ff1cbc35000 r-xp 00000000 08:01 3670037                    /lib/ld-2.11.1.so
7ff1cbe13000-7ff1cbe18000 rw-p 00000000 00:00 0 
7ff1cbe2f000-7ff1cbe35000 rw-p 00000000 00:00 0 
7ff1cbe35000-7ff1cbe36000 r--p 00020000 08:01 3670037                    /lib/ld-2.11.1.so
7ff1cbe36000-7ff1cbe37000 rw-p 00021000 08:01 3670037                    /lib/ld-2.11.1.so
7ff1cbe37000-7ff1cbe38000 rw-p 00000000 00:00 0 
7fffe9b2e000-7fffe9b43000 rw-p 00000000 00:00 0                          [stack]
7fffe9bf8000-7fffe9bf9000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
+-> Using Vorbis audio output module for stream 1.
Aborted

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
Sun Aug  1 04:20:14 2010 Job 'Transcode with VBR audio - title #1' cancelled
Sun Aug  1 04:20:26 2010 Job 'Transcode with VBR audio, second pass - title #1' finished
Sun Aug  1 04:20:26 2010 Job 'Merge audio - title #1, audio track #0' finished

```
Thanx in advance for the help,
Roman

---

