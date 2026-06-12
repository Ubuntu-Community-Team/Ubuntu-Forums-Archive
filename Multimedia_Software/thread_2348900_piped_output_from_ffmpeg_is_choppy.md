---
title: "piped output from ffmpeg is choppy"
date: 2017-01-08
forum: Multimedia Software
---

### Post by two4two on 2017-01-08
It is the official ffmpeg.  I entered the following command:  "ffmpeg -f mpegts -i /dev/video1 -c copy /media/LinWork2/VidRecord-6.mp4 -f mpegts -c copy - | ffplay -f mpegts -s 1920x1080 -"  It works -- sort of.  Video1 is a Hauppage HDPVR 1212.  My system has AMD Phenom II X6 1100T with 16GB DDR3.  Yes, my Ubuntu 11.04 is old.  But it works.  The ffmpeg is a very current static build.  It played the live video on my monitor fairly nicely while it recorded a file simultaneously.  But when I'm finished recording and try to play the file, the file plays back very choppy with any player EXCEPT ffplay.  As the play clock ticks away correctly it displays static scenes for a while, then skips to another static scene, etc.  EXCEPT FFPLAY.  The recorded file plays beautifully with ffplay.  I tried a smaller scale for ffplay in the command -- maybe for better efficiency.  And I tried rawvideo (which displays only green lines.)  I haven't tried another player in the command line -- maybe a more efficient one (if there is one.) Anyway, to sum up, the command does record a file while simultaneously displaying the live video on my monitor, but ffplay is the only player that plays the recorded file nicely.  Can anyone suggest improvements?  Thanks.

---

### Post by mörgæs on 2017-01-09
> **two4two said:**
> Yes, my Ubuntu 11.04 is old.  But it works.

With support ending in january 2012 you have five years worth of security breaches accumulated. This does not qualify as 'works' in the systems that I administrate. 

I suggest that you begin with a fresh install of 16.04.1. Post again if you still have the problem here.

---

### Post by ajgreeny on 2017-01-09
Yes, I'm afraid there is nothing that can be done here to help you as the repositories for 11.04 were closed early in 2012, so it will be a non-starter to administer and keep updated.

Install 14.04 or 16.04 if either of those will work with your hardware, and then come back again if you still have problems.

---

### Post by two4two on 2017-01-09
> **ajgreeny said:**
> Yes, I'm afraid there is nothing that can be done here to help you as the repositories for 11.04 were closed early in 2012, so it will be a non-starter to administer and keep updated.

Install 14.04 or 16.04 if either of those will work with your hardware, and then come back again if you still have problems.

Yes, I have a 16.04.1 partition.  I absolutely hate the desktop that comes with it.  I use the 11.04 because I have compiled a lot of software in there and don't wish to upgrade it because it ruins my compiled stuff, and I don't wish to re-do all of that in a new partition.  I "administrate" this 16.04.1 partition and have virtualbox there with a few VMs, but my OS of choice is the 11.04.  But I'll install this ffmpeg static build in the 16.04.1 and try this command there.  If it has the same problem (which I'm pretty sure it will because it's more a command and ffmpeg issue than release-oriented issue, and I'm not the best with terminal commands) I'll be back.  Thanks for reading and for responding.

---

### Post by ajgreeny on 2017-01-09
If you "absolutely hate the desktop" of 16.04 why did you install it; you could have used Ubuntu-mate, Xubuntu, Lubuntu or any other DE version that you prefer to unity of Ubuntu.

Like you, I don't like unity either, which is why I use Xubuntu, though I run Ubuntu 16.04 as a VM in VBox and I do agree that it has improved since it was first released.  Still not for me though.
Xubuntu is a very easily configurable desktop that can be made to look almost exactly as you want it to, like unity if you want, with a left hand launchbar panel, which is useful on a widescreen, but which still works in a more standard way in comparison with unity.

---

### Post by two4two on 2017-01-09
> **ajgreeny said:**
> If you "absolutely hate the desktop" of 16.04 why did you install it; you could have used Ubuntu-mate, Xubuntu, Lubuntu or any other DE version that you prefer to unity of Ubuntu.

Like you, I don't like unity either, which is why I use Xubuntu, though I run Ubuntu 16.04 as a VM in VBox and I do agree that it has improved since it was first released.  Still not for me though.
Xubuntu is a very easily configurable desktop that can be made to look almost exactly as you want it to, like unity if you want, with a left hand launchbar panel, which is useful on a widescreen, but which still works in a more standard way in comparison with unity.

I tried out all of the derivatives.  The only one that I liked was "Ubuntu Gnome".  But none are as user friendly as my 11.04 Ubuntu Studio.  In any event I will try my command on 16.04 with current genuine ffmpeg static build.  BTW, I also posted on ffmpeg forum, but no reply yet.

---

### Post by two4two on 2017-01-09
BTW, I recode the recorded file with this command:  ./ffmpeg -r 30 -deinterlace -i /media/LinWork2/VidRecord-6.mp4 -q:v 2 -c:v mpeg4 -c:a copy -y /media/LinWork2/VidRecord-6a.mp4
 and it comes out beautiful.  I thought the HDPVR could only do max of 1080i, but my recorded files have always shown 60 frames.  I don't know why.  I've always used -c copy to record from the unit.  So I don't know if this is an HDPVR or an ffnpeg thing.  I prefer to use ffmpeg to record.  VLC doesn't do a good job and I didn't try any others.  The recoded file shows 30 frames.  My whole objective was to be able to view what ffmpeg was recording and this approach seems to give me what I want.  There is an app called HDPVR-Capture (got it from SourceForge) that was developed on FLTK (Fluid) but it does not compile.  It has compile errors.  When I fix the compile errors it gets link errors.  I'd like to see that app fixed so I wouldn't have to mess with it.  It was last touched by the developer in 2011.

---

### Post by mörgæs on 2017-01-10
Good. If you consider the problem solved please mark the thread so.

---

