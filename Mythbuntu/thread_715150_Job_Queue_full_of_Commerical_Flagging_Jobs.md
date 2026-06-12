---
title: "Job Queue full of Commerical Flagging Jobs??"
date: 2008-03-04
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-03-04
I am hoping someone can help me with this issue I am having with my MythTV backend server. I am running

/usr/bin/mythbackend --version
Library API version     : 0.20.20070821-1
Source code version     :
SVN Branch              : branches/release-0-20-fixes
Options compiled in     :
 linux debug using_xvmcw using_v4l using_oss using_alsa using_arts using_jack using_ivtv using_firewire using_dbox2 using_hdhr using_ip_rec using_freebox using_live using_lirc using_joystick_menu using_dvb using_x11 using_xv using_xrandr using_xvmc using_xvmc_vld using_opengl_vsync using_opengl using_frontend using_backend

I don't use the auto commercial skip so I don't need any of my recordings flagged. I went through Mythweb and changed all current Recording Schedules such that the Auto-Transcode and Flag Commercials check boxes were unchecked. i did this back around 2/20/08 (not a precise date as I forget) 

I now notice that my Job Queue is full of Flag Commercial jobs that haven't run all the way back to 2/20/08.

How can I clear the Job Queue? I don't need any of those jobs to run not to mention I don't know why they are there in Mythweb. Please help

---

### Post by rhpot1991 on 2008-03-05
You can disable commflagging in mythtv-setup, general section maybe 4 or 5 pages in.  Would be a heck of a lot cleaner than doing it on every recording.  I would do that and then restart your backend (sudo /etc/init.d/mythtv-backend restart) and see if your queue is still messed up.

---

### Post by dannyboy79 on 2008-03-05
thanks, that's what I did after all but my job queue is still full of stuff that's not running and I want to remove them from mythweb job queue. i don't know the mysql commands which is what I am guessing will resolve this.

---

### Post by dannyboy79 on 2008-03-19
I was able to finally figure out that I could remove these jobs from the Frontend. I never fire up the frontend because I use my xbox to watch recordings and I never watch livetv. I would have loved to solve this thru ssh but oh well. The frontend, job queue solved it. I clicked on the job, then hit enter, then it asked if I wanted to delete it. Gone.

---

