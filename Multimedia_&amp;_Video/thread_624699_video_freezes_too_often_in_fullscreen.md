---
title: "video freezes too often in fullscreen"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by sourcemorph on 2007-11-27
hey i have all the latest gstreamer plugins... whenevr i play a video in totem or mplayer the playback freezes frequently (in mplayer this happens when i play fullscreen, totem it happens all the time)...

how do i get rid of this??

---

### Post by Yellow Pasque on 2007-11-27
What video card do you have and are you using a 2D-accelerated driver for it?

---

### Post by sourcemorph on 2007-11-27
i have the nvidia 6150 controller.. no i am using the nvidia-glx-new restricted driver... sitll i face the problem.

---

### Post by gninnes on 2007-11-27
I am having the exact same problem.

My video card is: GeForce 6100 nForce 430  
My video driver is: nvidia-glx

I was using Ubuntu Fiesty for a few months with no problems, but after the upgrade to Gutsy I have my full screen videos freeze seemingly randomly. Very frustrating.

When the video freezes, playback continues in the background, it is just the imagery that freezes along with mouse or keyboard input. Eventually the movie responds to my clicks, and allows me to get out of full screen.

If there is any other information I can give to help troubleshoot, please let me know. 

It looks like this guys is having the same problem:
> I'm having a very similar problem on a laptop. Video card is a Ati Mobility X300. I find that sometimes videos will full screen ok but usually I get the same operation that you do. If I disable compiz (by hitting Alt-F2 and typing "metacity --replace") then I can play videos just fine. Then when I'm done playing the video I hit Alt-F2 again and type "compiz".

So far thats my work around. I never have the problem when running metacity. 
- bthoward [(link)]("http://ubuntuforums.org/archive/index.php/t-581488.html")

I will try disabling compiz as well. Seems a bit drastic though. I wonder if the compiz guys are aware of this issue.

Many thanks for any help,

Gerard

---

### Post by gninnes on 2007-11-27
I found a work around for this problem.

[This guy]("http://ubuntuforums.org/showpost.php?p=3599301&postcount=2") had a similar issue, and solved it by adding a line to his xconf file. 

The work around only seems to be useful if you have only one monitor though.

Make sure you post here if this solves your issue.

---

### Post by sourcemorph on 2007-11-28
i tried the fix u told.. totem is freezing less now but its not completely gone...

---

### Post by gninnes on 2007-11-28
sourcemorph: Which of the above two workarounds did you try? 

There were two:
[LIST=1]
[*]Switching from compiz to metacity
[*]Adding a line to xorg.conf
[/LIST]

You probably already did, but did you restart your desktop environment (ctrl+alt+backspace) once you changed the line in your xorg.conf?

---

### Post by davec64 on 2007-11-28
Are running Compiz (Desktop effects) whilst trying to view video?
If you are it may be linked to that, try this it worked for me!

```
gstreamer-properties
```

and select the video tab, set the output to "X Windows System (No Xv)".

Hope it helps!
:)

---

### Post by gninnes on 2007-11-28
I am sad to report that the freezing is back again today. Which means that the xorg and gstreamer fixes don't work for me. Is there no end to this problem?

---

### Post by sourcemorph on 2007-11-29
yeah i tried the xorg.conf thing n i rebooted after editing the file.

---

### Post by sourcemorph on 2007-12-05
well i tried al things said here.. nothing seemed to work but i found the solution ratheru nexpectedly.. ;)

i downloaded smplayer (a front end for mplayer) and it works real smooth... fullscreen mode with no pauses... atleast none till now...

---

### Post by gninnes on 2007-12-05
I'll have to check that out.

I went to the effort of installing the latest version of the video drivers thanks to [envy ]("http://albertomilone.com/nvidia_scripts1.html"). 

So far I haven't had any issue either. Let me stress 'so far'.

---

