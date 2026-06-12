---
title: "unity launcher missing using external monitor"
date: 2012-05-14
forum: Multimedia Software
---

### Post by gmoore777 on 2012-05-14
Hardware: Gateway mt3705 laptop with a broken display but
with an external monitor attached to vga port.

I installed 12.04 PrecisePangolin 32-bit twice on a Gateway mt3705 laptop
and incurred the same exact problem.

The Unity Launcher thing (the vertical stack of icons on the left side of display) was missing.
(I did have the top menu bar)

Or in some reboot instances, it was just all black, and if I hovered over
it, i would see the tool tips, and could launch the application.

But mostly it was always missing. 

`unity --reset` did not help (and never really finished). 
`sudo service lightdm restart` didn't help.

I tried a few solutions:

Hitting <ALT><F2> to get the Dash search application, and found and
launched the "Displays" application.
It did show that I had 2 monitors and that they were being mirrored.

I unmirrored the 2 displays by un-checking the check box next to 
"Mirror Displays".
But this caused the Unity launcher to show up, but when I launched most
applications, they were running but "dissapeared". They were, I think, 
showing up on the broken laptop display. 
To interact with the launched application, I would have to click the 
"Workspace Switcher" and drag the application from the window on the
right side (that represented my broken laptop display) to the left side. 
I didn't like that mode of operation.
(if the laptop display was working, then I guess I would have 2 displays
to work with)

So then I went back into the "Displays" application, and clicked
the display that represented the broken laptop display and turned it
"off".
This worked fine, but then I was worried that if and when I fix the
laptop display, that when I boot it, without an external display
that the newly fixed laptop display may be black, cause I had turned it
off.

So then I went back into the Displays application, and clicked "Mirror displays", but then also un-clicked "Sticky Edges".
This also fixed the original problem;
I now see the Unity launcher and am hopefully positioned correctly for the
future for when i fix the laptop display and no longer have an external
monitor hooked up.


(small aside: somewhere in all my thrashing, Firefox was not starting and
gave me an error of: "your firefox profile cannot be loaded". To fix this:
I removed my .mozilla directory. `rm -rf ~/.mozilla` and relaunched Firefox.)

---

### Post by d.atanasov on 2012-05-14
Also in Displays there is one "tip menu" to show launcher in both monitors external and laptop. Did you tried that ?

To correct myself it is a drop down menu. It says where to place Launcher ?

---

### Post by gmoore777 on 2012-05-14
The "Launcher placement" is grayed out and set to "All displays"
when "Mirror displays" is checked/on.

Thus one can not change the "Launcher placement" option.

Which makes sense, cause if one wants all the displays to be mirrored,
(showing the same thing), then one wouldn't want to tell Ubuntu, show
me a launcher in monitor #1, but don't show it in monitor #2, but
make everything else identical.

---

### Post by gmoore777 on 2012-05-14
I may add that the solution that I presented above in the first comment
does not make sense from a technical standpoint. Fiddling with the Sticky edges has nothing to do on whether the launcher should appear or not, but
that is what worked for me and wanted to document it via this forum.

Also, I just booted the liveCD and chose "Try Ubuntu"
to ensure that the LiveCD also exemplifies the same problemm as
a real installation. 
It does. There is no Unity launcher present on the left hand side
and if I start the the Displays application, I see the the same exact
settings as I saw after having done an installation.
It is set to mirrored with Sticky edges to ON.

---

