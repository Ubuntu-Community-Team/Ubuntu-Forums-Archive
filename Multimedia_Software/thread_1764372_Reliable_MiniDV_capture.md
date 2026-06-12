---
title: "Reliable MiniDV capture"
date: 2011-05-21
forum: Multimedia Software
---

### Post by NotConvincedYet on 2011-05-21
Just a quick question:
I have a shoebox full of MiniDV tapes dating as far  back as 2007. I want to transfer these to my external HDD,  I want to do it   once and I want it in the highest quality format possible  (file size is not an issue). I tried Kino but it freezes up    sometimes and   that is not good  for the capture process.  DVGrab looks fine but I have no idea how to   select the location  where my  files are saved and  I Would really  prefer something  with a     GUI interface.  Suggestions? Thanks.

---

### Post by marcia on 2011-05-21
I have done this many times,however, not for a long time. I would use dvgrab which is a command line package. There are a few things to download to work with this I believe and I just do not remember all of the packages needed.Permissions had to be correct with the device, too.  

I would suggest to search dvgrab in this forum and there should be some good help. I am sorry that I cannot be more specific, I have forgotten the details of how to do this.

Good Luck,

Marcia

---

### Post by marcia on 2011-05-21
It is too bad kino is not working correctly for you since that is usually a good gui for dvgrab. I have heard Lives can do it, Cinelerra, and maybe VLC? I have not used any of these for that.

I found dvgrab so easy to use at the command line that I preferred it to a gui program. $dvgrab --help or $man dvgrab could get you started.

I just found a sample in the forum for dvgrab.  	

desktop:~$ dvgrab --format raw --duration 2:10:00 /home/kris/capture

I hope you get this working.

Sincerely,

Marcia

---

