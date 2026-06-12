---
title: "Amarok ESD output"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by dasbooter on 2007-06-19
I dont seem to have an option for esd output in the prefs engine section of Amarok. This seems a bit weird as any reference on these boards or google seems to have it as an option. I require this output for use with freenx . If anybody knows what the problem might be  or how I can enable it pls let me know. I have the latest amarok from the medibuntu repos installed with the xine and other engine packages also installed. I can play just about every format so that is not a problem. I just cant get the remote sound to play when I am freenx'ing. System sounds seem to work fine with esd running as a service. Too bad there isnt a way to get all sounds enabled remotely with just one setting :) 0h well thanks for looking in.

---

### Post by dasbooter on 2007-07-02
bumporama

---

### Post by dasbooter on 2007-07-14
hellooo anybody out there

---

### Post by fiatguy85 on 2007-08-01
> **dasbooter said:**
> I dont seem to have an option for esd output in the prefs engine section of Amarok. This seems a bit weird as any reference on these boards or google seems to have it as an option. I require this output for use with freenx . If anybody knows what the problem might be  or how I can enable it pls let me know. I have the latest amarok from the medibuntu repos installed with the xine and other engine packages also installed. I can play just about every format so that is not a problem. I just cant get the remote sound to play when I am freenx'ing. System sounds seem to work fine with esd running as a service. Too bad there isnt a way to get all sounds enabled remotely with just one setting :) 0h well thanks for looking in.

I was working on trying to get this to work as well, and found the libxine1-gnome package, which says it includes the esd plugin.  So I would think you could output with xine into esd, however I cannot get this to work.

---

### Post by dasbooter on 2007-08-13
OMG somebody answered. Unfortunately I forgotten what the problem was ;) Seriously I think that amarok needs to be compiled with this option and the version on the repos wasnt ,oh well. Feel free to correct me but pls take aprox. 2 months at least to do so :)

---

### Post by dasbooter on 2007-09-10
Wow my sarcasm is offending myself but seriously bump how about even giving some input on where I can even begin to solve this problem.

---

### Post by fiatguy85 on 2007-09-11
Sorry, I kind of gave up on what I was trying to accomplish with this, never found a solution.  You say it can be compiled with the option?  Have you actually tried this?  I may look into it when I get some time.

---

### Post by dasbooter on 2007-09-24
I completely and utterly destroyed my system while trying to compile amarok with a script. I tried to install some dependencies for the compilation and a conflict had synaptic happily removing gnome in its entirety. I have been unable to restore things to there former glory I have a good install of suse sitting and may go back to it perhaps they have worked out there package man issue.

---

### Post by fiatguy85 on 2007-09-24
Sorry to hear that.

---

### Post by dasbooter on 2007-09-25
back up and running :)

I think esddsp may be used as a wrapper for amarok to output to esd but I cannot figure out how. Even the latest amarok from backports doesnt have esd support. 

fiatguy85: If you need esd output for sound xmms is a viable albeit old old alternative. 

Still wanting help here, oh well

---

