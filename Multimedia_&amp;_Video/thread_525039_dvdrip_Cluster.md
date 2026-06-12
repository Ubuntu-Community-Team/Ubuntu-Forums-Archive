---
title: "dvd::rip Cluster"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by xur17 on 2007-08-13
I am trying to use dvd::rip in a cluster to backup my dvds to avi.

Whenever I try to run it, it gives me an error about 5 seconds after beginning.

I think it has something to do with this:
```
/mnt/files2/TV/.dvdrip-data/Breach/avi/001/audio-psu-00/Breach-001-audio-psu-00-00.avi -x null,vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -f 24,1 -b 128,0,0 -s 1.671 --a52_drc_off  --print_status 25 -S 00 -W
```

,but I am not sure (the part that starts \/mnt\/files2...)

Thank you very much.

The complete log file is included below.

```
Mon Aug 13 21:43:48 2007 [2] New log client connected
Mon Aug 13 21:43:48 2007 [1] Project file saved to '/home/tom/.dvdrip-master/projects/00000008-Breach.rip'
Mon Aug 13 21:43:48 2007 [1] Project with filename '/home/tom/.dvdrip-master/projects/00000008-Breach.rip' added
Mon Aug 13 21:43:50 2007 [1] Project file saved to '/home/tom/.dvdrip-master/projects/00000008-Breach.rip'
Mon Aug 13 21:43:58 2007 [1] Setting up job plan
Mon Aug 13 21:43:58 2007 [1] Project file saved to '/home/tom/.dvdrip-master/projects/00000008-Breach.rip'
Mon Aug 13 21:43:58 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #1'
Mon Aug 13 21:43:58 2007 [1] Start job 'Process all video chunks - title #1, PSU #0'
Mon Aug 13 21:43:58 2007 [1] Start job 'Process PSU #0'
Mon Aug 13 21:43:58 2007 [1] Start job 'Process all PSU's - title #1'
Mon Aug 13 21:43:58 2007 [1] Start job 'Project 'Breach' - title #1'
Mon Aug 13 21:43:58 2007 [1] Start job 'All running cluster projects'
Mon Aug 13 21:43:58 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 1, pass 1'
Mon Aug 13 21:43:58 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00000' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00000 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00000,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:43:59 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #2'
Mon Aug 13 21:43:59 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 2, pass 1'
Mon Aug 13 21:43:59 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00001' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00001 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00001,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 1, pass 1' finished
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 1, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00000' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00000 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00000,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:43:59 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #1: 50% done.
Mon Aug 13 21:43:59 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #3'
Mon Aug 13 21:43:59 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 3, pass 1'
Mon Aug 13 21:43:59 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00002' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00002 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00002,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 2, pass 1' finished
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 2, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00001' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00001 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00001,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:43:59 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #4'
Mon Aug 13 21:43:59 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 4, pass 1'
Mon Aug 13 21:43:59 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00003' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00003 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00003,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 3, pass 1' finished
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 3, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00002' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00002 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00002,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:43:59 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #2: 50% done.
Mon Aug 13 21:43:59 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #3: 50% done.
Mon Aug 13 21:43:59 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #5'
Mon Aug 13 21:43:59 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 5, pass 1'
Mon Aug 13 21:43:59 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00004' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00004 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00004,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 4, pass 1' finished
Mon Aug 13 21:43:59 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 4, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00003' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00003 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00003,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:00 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #6'
Mon Aug 13 21:44:00 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 6, pass 1'
Mon Aug 13 21:44:00 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00005' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00005 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00005,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 5, pass 1' finished
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 5, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00004' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00004 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00004,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:00 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #5: 50% done.
Mon Aug 13 21:44:00 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #4: 50% done.
Mon Aug 13 21:44:00 2007 [1] Process all video chunks - title #1, PSU #0: 10% done.
Mon Aug 13 21:44:00 2007 [1] Process PSU #0: 10% done.
Mon Aug 13 21:44:00 2007 [1] Process all PSU's - title #1: 10% done.
Mon Aug 13 21:44:00 2007 [1] Project 'Breach' - title #1: 10% done.
Mon Aug 13 21:44:00 2007 [1] All running cluster projects: 10% done.
Mon Aug 13 21:44:00 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #7'
Mon Aug 13 21:44:00 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 7, pass 1'
Mon Aug 13 21:44:00 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00006' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00006 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00006,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 6, pass 1' finished
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 6, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00005' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00005 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00005,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:00 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #8'
Mon Aug 13 21:44:00 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 8, pass 1'
Mon Aug 13 21:44:00 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00007' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00007 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00007,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 7, pass 1' finished
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 7, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00006' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00006 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00006,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:00 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #7: 50% done.
Mon Aug 13 21:44:00 2007 [1] Project 'Breach' - title #1: 20% done.
Mon Aug 13 21:44:00 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #6: 50% done.
Mon Aug 13 21:44:00 2007 [1] Process all video chunks - title #1, PSU #0: 20% done.
Mon Aug 13 21:44:00 2007 [1] Process PSU #0: 20% done.
Mon Aug 13 21:44:00 2007 [1] Process all PSU's - title #1: 20% done.
Mon Aug 13 21:44:00 2007 [1] All running cluster projects: 20% done.
Mon Aug 13 21:44:00 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #9'
Mon Aug 13 21:44:00 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 9, pass 1'
Mon Aug 13 21:44:00 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00008' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00008 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00008,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 8, pass 1' finished
Mon Aug 13 21:44:00 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 8, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00007' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00007 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00007,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:00 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #10'
Mon Aug 13 21:44:00 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 10, pass 1'
Mon Aug 13 21:44:01 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00009' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00009 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00009,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 9, pass 1' finished
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 9, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00008' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00008 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00008,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:01 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #8: 50% done.
Mon Aug 13 21:44:01 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #11'
Mon Aug 13 21:44:01 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 11, pass 1'
Mon Aug 13 21:44:01 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00010' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00010 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00010,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 10, pass 1' finished
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 10, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00009' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00009 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00009,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:01 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #9: 50% done.
Mon Aug 13 21:44:01 2007 [1] Process all video chunks - title #1, PSU #0: 30% done.
Mon Aug 13 21:44:01 2007 [1] Process PSU #0: 30% done.
Mon Aug 13 21:44:01 2007 [1] Process all PSU's - title #1: 30% done.
Mon Aug 13 21:44:01 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #10: 50% done.
Mon Aug 13 21:44:01 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #12'
Mon Aug 13 21:44:01 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 12, pass 1'
Mon Aug 13 21:44:01 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00011' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00011 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00011,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 11, pass 1' finished
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 11, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00010' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00010 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00010,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:01 2007 [1] Project 'Breach' - title #1: 30% done.
Mon Aug 13 21:44:01 2007 [1] All running cluster projects: 30% done.
Mon Aug 13 21:44:01 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #11: 50% done.
Mon Aug 13 21:44:01 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #13'
Mon Aug 13 21:44:01 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 13, pass 1'
Mon Aug 13 21:44:01 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00012' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00012 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00012,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 12, pass 1' finished
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 12, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00011' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00011 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00011,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:01 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #12: 50% done.
Mon Aug 13 21:44:01 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #14'
Mon Aug 13 21:44:01 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 14, pass 1'
Mon Aug 13 21:44:01 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00013' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00013 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00013,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 13, pass 1' finished
Mon Aug 13 21:44:01 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 13, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00012' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00012 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00012,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:02 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #13: 50% done.
Mon Aug 13 21:44:02 2007 [1] Process all video chunks - title #1, PSU #0: 40% done.
Mon Aug 13 21:44:02 2007 [1] Start job 'Multipass video transcoding - title #1, PSU #0, chunk #15'
Mon Aug 13 21:44:02 2007 [1] Start job 'Transcode video - title #1, PSU 0, chunk 15, pass 1'
Mon Aug 13 21:44:02 2007 [1] Executing command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00014' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00014 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00014,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 14, pass 1' finished
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 14, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00013' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00013 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00013,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:02 2007 [1] Project 'Breach' - title #1: 40% done.
Mon Aug 13 21:44:02 2007 [1] Start job 'Process all audio tracks - title #1, PSU #0'
Mon Aug 13 21:44:02 2007 [1] Start job 'Transcode audio - title #1, track #1'
Mon Aug 13 21:44:02 2007 [1] Executing command: umask 0002; mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/audio-psu-00 && execflow -n 19 transcode  -H 10 -g 0x0 -u 50 -a 1 -y raw -o /mnt/files2/TV/.dvdrip-data/Breach/avi/001/audio-psu-00/Breach-001-audio-psu-00-00.avi -x null,vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -f 24,1 -b 128,0,0 -s 1.671 --a52_drc_off  --print_status 25 -S 00 -W 15,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 15, pass 1' finished
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode video - title #1, PSU 0, chunk 15, pass 1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00' && mkdir -m 0775 -p '/mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00014' && cd /mnt/files2/TV/.dvdrip-data/Breach/cluster/001-00-00014 && mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/chunks-psu-00 && execflow -n 19 transcode -H 10 -x vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -w 1637,50 -f 24,1  -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid4,null -o /dev/null --print_status 25   -S 00 -W 00014,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"
Mon Aug 13 21:44:02 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #14: 50% done.
Mon Aug 13 21:44:02 2007 [1] Process PSU #0: 40% done.
Mon Aug 13 21:44:02 2007 [1] Process all PSU's - title #1: 40% done.
Mon Aug 13 21:44:02 2007 [1] All running cluster projects: 40% done.
Mon Aug 13 21:44:02 2007 [1] Multipass video transcoding - title #1, PSU #0, chunk #15: 50% done.
Mon Aug 13 21:44:02 2007 [1] Job 'All running cluster projects' finished
Mon Aug 13 21:44:02 2007 [1] Project file saved to '/home/tom/.dvdrip-master/projects/00000008-Breach.rip'
Mon Aug 13 21:44:02 2007 [1] Job 'Project 'Breach' - title #1' finished
Mon Aug 13 21:44:02 2007 [1] Job 'Process all audio tracks - title #1, PSU #0' finished
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode audio - title #1, track #1' finished
Mon Aug 13 21:44:02 2007 [1] Job 'Transcode audio - title #1, track #1' exited with error: Command exits with failure code:
Command: umask 0002; mkdir -p /mnt/files2/TV/.dvdrip-data/Breach/avi/001/audio-psu-00 && execflow -n 19 transcode  -H 10 -g 0x0 -u 50 -a 1 -y raw -o /mnt/files2/TV/.dvdrip-data/Breach/avi/001/audio-psu-00/Breach-001-audio-psu-00-00.avi -x null,vob -i \/mnt\/files2\/TV\/\.dvdrip\-data\/Breach\/vob\/001\/ -f 24,1 -b 128,0,0 -s 1.671 --a52_drc_off  --print_status 25 -S 00 -W 15,15,/mnt/files2/TV/.dvdrip-data/Breach/tmp/Breach-001-nav.log && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/mnt/files2/TV/.dvdrip-data/Breach/vob/001/"

```

---

### Post by Sam Lars on 2008-05-11
I'm having this same problem, has anyone figured it out?

---

