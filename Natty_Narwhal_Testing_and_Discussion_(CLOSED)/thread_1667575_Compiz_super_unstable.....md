---
title: "Compiz super unstable...."
date: 2011-01-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Anduu on 2011-01-15
As of today's updates Compiz is no fun at all.I pretty much only have to give her a dirty look and she crashes.Trying to maximize windows pretty much guarantees a crash...

I have also noticed desktop widgets(ie Screenlets,Cairo Dock etc...)are showing a white triangle...almost looks like it is meant to be a resize handle...on the bottom right corner of each widget.Also they will flicker when moused over.

If I run "compiz --replace" from a terminal I can't get any output from the crash.It just seems to hang up and Ctrl+C is needed to get back to a shell prompt.

Anyone else having any issues?

**Note**:I didn't notice anything wrong immediately after the update but have restarted since and that is when things got a little western around here.
**Note 2**:I am running classic desktop not unity.

---

### Post by Anduu on 2011-01-15
Did a little more poking around.Here is what i have found so far...

It seems Compiz isn't completely crashing.If I open ccsm and disable/reenable the Window Decoration plugin things come back but it will still crash at the drop of a hat.

Also from a terminal I get *some* output:
```
Setting Update "active_plugins"
Starting unity-window-decorator
Floating point exception
```

---

### Post by ikt on 2011-01-15
> **Anduu said:**
> Anyone else having any issues?


[http://ubuntuforums.org/showthread.php?t=1666697](http://ubuntuforums.org/showthread.php?t=1666697)

---

### Post by JRV on 2011-01-15
Running the classic desktop I get the resize handles on the bottom right corner of both panels, and they don't work.

---

### Post by dino99 on 2011-01-15
no troubles since i've removed it :)

---

### Post by shafin on 2011-04-04
> **Anduu said:**
> 
I have also noticed desktop widgets(ie Screenlets,Cairo Dock etc...)are showing a white triangle...almost looks like it is meant to be a resize handle...on the bottom right corner of each widget.Also they will flicker when moused over.


Have you found any solution to this? 
I am also bugged by this. I am quite sure this is caused by the addition of resize handlers to all windows.

---

### Post by jerrylamos on 2011-04-04
> **Anduu said:**
> As of today's updates Compiz is no fun at all.I pretty much only have to give her a dirty look and she crashes.Trying to maximize windows pretty much guarantees a crash...

Anyone else having any issues?

Oh, yes, Compiz has even crashed on me doing "shadows" when I was running full screen applications and nothing Compiz was doing was even on the screen.  And even all up to date with hardware that meets all requirements Compiz freezes and crashes randomly.

That's been going on for me starting with Intrepid.

If you don't want Compiz crashes, then log in with Classic "no effects" or else reload Synaptic and install Unity 2D.  Unity 2D doesn't use Compiz, looks and acts much like Unity, and doesn't crash since it doesn't use Compiz.

Jerry

---

### Post by beew on 2011-04-04
> **jerrylamos said:**
> 
That's been going on for me starting with Intrepid.

If you don't want Compiz crashes, then log in with Classic "no effects" or else reload Synaptic and install Unity 2D.  Unity 2D doesn't use Compiz, looks and acts much like Unity, and doesn't crash since it doesn't use Compiz.



So that means it is not a Compiz issue or a Natty issue. I think it is your hardware. Compiz has been extremely stable for me on Lucid and Maverick (tried on different machines with different specs and age) With Natty it is a bit flaky but not nearly as bad as OP reported since the early alpha3(maybe today's update breaks something? That I wouldn't know since I haven't updated today yet)

I would never use a desktop without Compiz now that I am so used to it. But if it doesn't work for you you may try Gnome Shell (a big reason why i won't use it is that it doesn't work with Compiz, I am shallow. :))

---

### Post by Anduu on 2011-04-05
> **beew said:**
> With Natty it is a bit flaky but not nearly as bad as OP reported since the early alpha3(maybe today's update breaks something? That I wouldn't know since I haven't updated today yet)



Yeah that was way back when....

Compiz is still a tad flakey like you say but no where near as bad as it was then

---

