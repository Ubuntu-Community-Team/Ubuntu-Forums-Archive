---
title: "Is my GIMP broken or..."
date: 2007-09-29
forum: Multimedia Production
---

### Post by OsakaWilson on 2007-09-29
...am I just missing something.

I am attempting to use the Scissors Tool. I've followed several tutorials, but none of them work. All of the tutorials say to click on the Scissors tool icon, then click around the part of the image that you want selected. Finally click on the first dot which completes the perimeter.

This creates a solid line around the selected area. However if I click inside it, it disappears. I've spent a total of at least 8 hours trying every menu combination I can think of to convert this perimeter into a selection (the broken flashy line), but nothing I do works.

The tutorials at this point just say, "now select the area", or simply "convert the perimeter into a selection" which is not useful because they don't explain how to do this. 

I watched [this]("http://uk.youtube.com/watch?v=Rk-wqpzoi50") video which lists the final step as clicking on the first dot. At that point in the video everything outside the perimeter magically disappears and the selection has the flashy line around it. This does not happen for me, so I'm suspecting my GIMP is broken. 

Help?

Feel free to point out something that a monkey should have noticed, but I missed.

---

### Post by rsambuca on 2007-09-29
What version of gimp are you using?

---

### Post by OsakaWilson on 2007-09-30
I'm using 2.2.

---

### Post by OsakaWilson on 2007-09-30
Now I am sure that my GIMP is broken. Clearly on several tutorials, it describes clicking on the first dot, then clicking inside the perimeter to select. Mine does not do that. Instead the selected perimeter disappears.

I found other posts descibing the same problem I'm having. No solutions though. Anyone have a solution for this?

---

### Post by Steveway on 2007-09-30
How about upgrading to 2.4?
It's not finished but it works perfect here.

---

### Post by cubeist on 2007-10-01
It could be broken, but you may also just have the wrong mode selected.  After you have selected the scissor tool, go to Dialogues/Tool Options.  Under tool options, make sure the select mode is the one that looks like a full square (when you hover over it, it says "Replace the current selection").  That mode should work.

If that doesn't work you could try re-installing gimp from synaptic... although I doubt that will fix a "ghost problem"

---

### Post by OsakaWilson on 2007-10-04
Cubeist,

That did it!! You fixed my problem. Thank you very much.

---

### Post by eye208 on 2007-10-04
By the way, in order to reset a program to factory defaults, do not reinstall it. Just delete the associated settings folder from your home directory. In the case of GIMP it is the folder ~/.gimp-2.2. The same method works for other programs too. Each program will automatically recreate its settings folder and fill it with default settings upon the next run.

---

### Post by cubeist on 2007-10-04
> **OsakaWilson said:**
> Cubeist,

That did it!! You fixed my problem. Thank you very much.

Fantastic!  I keep the tool options dialogue open all the time.  It's a great way to learn all the different ways to use each tool.

---

