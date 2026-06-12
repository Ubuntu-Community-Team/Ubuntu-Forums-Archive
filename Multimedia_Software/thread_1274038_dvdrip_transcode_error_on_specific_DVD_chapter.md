---
title: "dvd::rip transcode error on specific DVD chapter"
date: 2009-09-24
forum: Multimedia Software
---

### Post by jbraswell on 2009-09-24
Anyone ever see this or have any guesses as to what the problem might be?  I'm converting an iso to avi with dvd::rip, and I get the following error only on one particular chapter.  I've seen one or two other threads that mention this kind of error, but with those, the solution was usually some kind of missing codec or something that affected the entire process, not just one chapter.  

(And before I hear any jokes, this is the Japanese version of "Shall We Dance."  That makes it a little better.)

```
Job 'Transcode video - title #1, chapter #17, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/jbraswell/dvdrip-data/ShallWeDance/tmp' && cd /home/jbraswell/dvdrip-data/ShallWeDance/tmp && mkdir -p /home/jbraswell/dvdrip-data/ShallWeDance/avi/001 && execflow -n 0 transcode -H 10 -a 0 -x vob -i \/home\/jbraswell\/dvdrip\-data\/ShallWeDance\/vob\/001\-C017\/ -w 9000,50 -b 224,0,2 -s 1.610 --a52_drc_off -f 24,1 -M 2 -Y 12,0,12,0 -B 15,10,8 -R 1 -y xvid,null -o /dev/null --print_status 25 -J extsub=0:0:0:0:0 && echo EXECFLOW_OK

Output: te: Broken pipe
syncinfo write error (0)
write: Broken pipe
syncinfo write error (0)
write: Broken pipe
```

---

