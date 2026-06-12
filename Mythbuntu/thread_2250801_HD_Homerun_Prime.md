---
title: "HD Homerun Prime"
date: 2014-10-31
forum: Mythbuntu
---

### Post by deanie44 on 2014-10-31
Hi everyone.  I am using Mythbuntu 14.04 with Mythtv 0.27+ fixes.  The tuners are listed as 1, 3, and 5.  Tuner 5 is not recording.  It says in the information that the tuner has an error.  How do I find the error?  I have looked through the backend logs, which I do not understand.  Any assistance will be appreciated.  deanie44

---

### Post by dannyboy79 on 2014-10-31
can you please use pastebinit or whatever method you want to get your mythtv-backend.log (look in /var/log/mythtv/) file put on pastebin and then share that link with us so we can see your log file. it will help us diagnose.

---

### Post by deanie44 on 2014-10-31
Thanks for answering my post.  Here is the link to the log; [http://pastebin.com/160vubzg](http://pastebin.com/160vubzg)

---

### Post by dannyboy79 on 2014-10-31
im at a loss here. i see the following several times
```
Oct 26 00:05:00 deanie56-Inspiron-560 mythbackend: mythbackend[1899]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[5]: HW Tuner: 5->5
Oct 26 00:05:00 deanie56-Inspiron-560 mythbackend: mythbackend[1899]: E TVRecEvent recorders/hdhrstreamhandler.cpp:429 (TunerSet) HDHRSH(192.168.2.4-3): DeviceSet(vchannel 1008): ERROR: unknown getset variable
Oct 26 00:05:00 deanie56-Inspiron-560 mythbackend: mythbackend[1899]: E TVRecEvent tv_rec.cpp:3792 (TuningFrequency) TVRec[5]: Failed to set channel to 1008. Reverting to kState_None
Oct 26 00:05:00 deanie56-Inspiron-560 mythbackend: mythbackend[1899]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[5]: Changing from RecordingOnly to None
Oct 26 00:05:00 deanie56-Inspiron-560 mythbackend: mythbackend[1899]: I CoreContext scheduler.cpp:704 (UpdateRecStatus) Updating status for Castle:"Like Father, Like Daughter" on cardid 5 (Will Record => Recorder Failed)
```
but i don't really know what that means. can you provide more info please, what tuners are they?  have you tried to remove all tuners from all hosts and then re-add them? if you do ensure that you reconnect each 1 to a source.

---

### Post by deanie44 on 2014-10-31
Hi.  I have removed and installed the tuners five times now.  Tuner 5 is giving me the trouble.  I reconnect it to the source, which is Comcast in Ct.  I only have fe/be machine.  Is there any way that I can use the terminal to see what is happening to the tuner? I tried dmesg, but I do 
not understand the jargon it put out.  thanks again,  deanie44

---

### Post by dannyboy79 on 2014-11-01
im not familiar with how to check anything with hdhomerun's from a command line sorry.

dmesg is a lot of information but if you scroll thru it you may be able to find where the error is.

---

