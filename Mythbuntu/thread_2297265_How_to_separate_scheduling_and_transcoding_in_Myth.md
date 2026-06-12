---
title: "How to separate scheduling and transcoding in MythTV"
date: 2015-10-02
forum: Mythbuntu
---

### Post by tristan-dawson on 2015-10-02
Hi all, I've currently got an all in one MythTV Frontend/Backend running the latest MythBuntu setup (how awesome is mythbuntu!), using a dual HDHomeRun as my tuner. All working pretty well - it starts up when a show is scheduled to record, records, then transcodes the show, and shuts down when it's done. Great. However, I need to make some changes to how my MythTV setup works for various reasons.


What I'd really like is a low powered computer, setup to just run something like MythWeb, so my users can browse to it from any device, and schedule a recording at any time - this will be an 'always on' PC. The 'MythWeb' computer would then need to be capable of switching on my current higher-powered backend to do the recording/transcoding and shut it down when said recording/transcoding is finished.


Is this possible? Can anyone tell me how to configure such a thing? Or perhaps point me to a guide on the internet somewhere that'll show me how??


I've got all the hardware, just need to get the software setup in the right configuration to support what I'm trying to accomplish :)


Thanks for your time.


If the above isn't possible, can I setup a frontend/backend on the low powered device, and have a secondary backend setup that's only used for transcoding? The Mythweb frontend PC sounds simpler to me though..


Thanks!

---

### Post by vidtek on 2015-10-07
T-D,

The requirements you state are well catered for in the normal myth setup.  You need to check out the WOL and ACPI wakeup wikis which give detailed instructions.

They can be quite confusing, especially if you use epoch time which is the best option. 

These are the steps you need to do:

1) setup WOL in your bios on the recording machine

2) ensure it actually works.  You should be able to send a packet from any device on your network and the machine will wake up.  Your router needs to be configured to allow these packets through as well.

3 set up your backend to shut down when not in use.

It sounds easy, but I hope you have lots of spare time to do it-you are going to need it!!  Be especially careful of the WAF!!!

Best of luck, Tony

---

