---
title: "Crashes and lock ups with video in 7.10 (SIGSEGV)"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by eznet on 2008-01-02
Ok, so until today everything has been fine, but for some reason now when I play video the computer starts freaking out.  I watch a lot of videos on my computer.  I have a nVidia GeForce 5200 which I have hooked to my TV via s-video as well as hooked to my LCD monitor.

Beginning today, when I attempt to play a video the computer will either 
[LIST]
[*]a) lock up [*]b) the window/display manager will crash (Metacity and Compiz crash as has Emerald - so most anything that has to do with display) and return to a partially functioning state (ie windows will not move but alt-tab works) or [*]c) the video player will crash and close without error[/LIST]
I have loaded loaded videos in totem, gxine and vlc from terminal to attempt to learn more, but generally I will only get either a "floating point exception" or "segmentation fault (core dump)".  When I check the crash reports (/var/crash) the errors are SIGSEGV...

I am clueless of what the problem is and so obviously the solution escapes me as well.  Like I said, I use this constantly and until today everything has worked great.  No updates have been performed since last using the video nor has any system changes occurred...

I am in x86 7.10 with all updates through Dec 312007....

Any info?  Thanks in advance!

---

### Post by eznet on 2008-01-04
For anyone reading this, here is an update....

I am still clueless.

I have reinstalled Gutsy and am continuing to have the problem.  I have now realized that the problem is not confined to video, but also pretty much every application I am running.  I have had everything from the system log viewer to totem crash, all with SIGSEGV...

I have attempted xorg changes, bios changes and pretty much everything I can find a shred of an article that suggests a change...  It seems that there is some sort of problem in the c environment...  it just seems odd that everything is crashing with SIGSEGV...

Looking at the apport crash report for log viewer I can see that gnome-system-log crashed with SIGSEGV in gtk_main_do_event() but that pretty much means squat tio me....  Before reinstall I also got some SIGILL errors which seem, from my limited understanding, to be similar to the SIGSEGV - but I don't really know...

When I load an app to crash via the terminal I get various outputs, but usually they are "Illegal instruction (core dumped)" or "Segmentation fault (core dumped)"...


Anyone?

---

