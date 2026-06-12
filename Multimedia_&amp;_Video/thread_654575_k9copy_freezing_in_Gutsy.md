---
title: "k9copy freezing in Gutsy"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by gewitty on 2007-12-31
I have been using K9copy successfully for some time now, but ever since upgrading to Gutsy the application is causing problems.

Whenever I run K9 I can get as far as listing the contents of a DVD, but whenever I try to create an ISO or make a copy to a blank disk the program freezes. When this happens, there is a lot of hard drive activity and my processor usage goes up to 100% and stays there even after I quit K9. I have checked System Monitor and this shows that K9 is still running as a process. Even after I force it to quit though, the processor is still at 100%, although System Monitor shows nothing demanding this level of usage. The only way to restore normality is by rebooting.

As an experiment, I tried running DVD Rip and got a similar result. No other apps are misbehaving, so I'm baffled about what is causing the problem. Any ideas would be welcome.

---

### Post by Steve1961 on 2007-12-31
Same thing happened here with k9copy in Gutsy.

---

### Post by foolsh on 2007-12-31
I think the title menu on newer dvds cause this try any older dvd to confirm this.

---

### Post by cotcot on 2007-12-31
I used K9 yesterday and today without problems. (fresh install of K9 on gutsy freshly installed a couple of weeks ago). I guess you already tried a complete remove and reinstall of K9 ?

---

### Post by gewitty on 2007-12-31
> **Steve1961 said:**
> Same thing happened here with k9copy in Gutsy.

I tried an older DVD, but got the same problem. The fact that this also affects DVD Rip would seem to suggest that the fault is caused by something in Gutsy, rather than the individual apps.

---

### Post by gewitty on 2007-12-31
I just tried DVD Rip again as it outputs a log file which may be useful. The fault is similar to the problem with K9 Copy, but DVD Rip is not causing the same 100% processor usage. It appears to work OK when retrieving the DVD TOC, but when I click the Rip button there is a brief burst of activity from the DVD reader and also the hard drive, then everything stops. The log file shows that the program thinks it has finished the job, whilst in reality, nothing has happened at all.

Mon Dec 31 16:03:50 2007 Detected transcode version: 10002
Mon Dec 31 16:04:04 2007 Project file saved to '/home/dave/dvdrip-data/test.rip'
Mon Dec 31 16:04:04 2007 Project {name} created
Mon Dec 31 16:04:25 2007 Start job 'Read TOC (lsdvd|tcprobe)'
Mon Dec 31 16:04:25 2007 Start job 'Read TOC (lsdvd)'
Mon Dec 31 16:04:25 2007 Executing command: execflow lsdvd -a -n -c -s -v -Op \/dev\/hdc 2>/dev/null && echo EXECFLOW_OK
Mon Dec 31 16:04:25 2007 Start job 'Read TOC (tcprobe)'
Mon Dec 31 16:04:25 2007 Successfully read DVD TOC
Mon Dec 31 16:04:25 2007 Copying IFO files from /media/cdrom1 to /home/dave/dvdrip-data/test/tmp/ifo
Mon Dec 31 16:04:25 2007 Job 'Read TOC (lsdvd|tcprobe)' finished
Mon Dec 31 16:04:26 2007 Job 'Read TOC (tcprobe)' finished
Mon Dec 31 16:04:26 2007 Job 'Read TOC (lsdvd)' finished
Mon Dec 31 16:04:55 2007 Start job 'Rip selected title(s) / chapter(s)'
Mon Dec 31 16:04:55 2007 Start job 'Process title #1'
Mon Dec 31 16:04:55 2007 Start job 'Rip - title #1'
Mon Dec 31 16:04:55 2007 Executing command: rm -f /home/dave/dvdrip-data/test/vob/001//test-???.vob && execflow -n 19 tccat -t dvd -T 1,-1,1 -i \/dev\/hdc | dvdrip-splitpipe -f /home/dave/dvdrip-data/test/tmp/test-001-nav.log 1024 /home/dave/dvdrip-data/test/vob/001//test vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Mon Dec 31 16:05:01 2007 Executing command: execflow tcprobe  -i /home/dave/dvdrip-data/test/vob/001/ && echo EXECFLOW_OK
Mon Dec 31 16:05:01 2007 Job 'Rip - title #1' finished

---

