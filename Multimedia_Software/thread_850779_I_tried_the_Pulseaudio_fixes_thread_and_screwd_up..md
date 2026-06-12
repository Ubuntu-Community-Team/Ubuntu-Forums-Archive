---
title: "I tried the Pulse/audio fixes thread and screwd up. How to fix?"
date: 2008-07-05
forum: Multimedia Software
---

### Post by sofasurfer on 2008-07-05
I tried to install the Pulse/audio fixes at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and screwed something up. I failed to end up with the equallizer and to top it off I don't have a volume control at the bottom of my desktop anymore. I don't know if anything else is screwed up up can you tell me how to get my volume control back?

---

### Post by kostkon on 2008-07-06
> **sofasurfer said:**
> I tried to install the Pulse/audio fixes at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and screwed something up. I failed to end up with the equallizer and to top it off I don't have a volume control at the bottom of my desktop anymore. I don't know if anything else is screwed up up can you tell me how to get my volume control back?
Could you be more specific? What problems do you have now that you didn't have before following the how-to?

If you see at the end of the how-to, it says how you can restore your original configuration. It's a matter of deleting some (hidden) files in your home folder, nothing special or difficult.

And the problem with your volume control does not seem to be serious. I assume it was removed for some reason. Try to add it back by right clicking on your panel, selecting *Add to Panel* and then adding the *Volume Control* Applet.

Afterwards, right click on this applet and select *Preferences* to define which sound device you want it to control.

If you get any errors please post back here.

---

### Post by sofasurfer on 2008-07-06
Ok, I will confess. I really did some dumb things. Those files that were loaded into my home directory were deleted. I panicked and tried fixing thing back the wau they were. I reloaded a backup I had of home and this deleted those files.
So I figured that I could retry the tutorial and then I would have the files back. But When I run the first command in the tutorial I get 'bash: $: command not found'.

I tried reloading the volume control applet to the panel and I get this message: The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

I tried reinstalling volume control from synaptic with no change in results.

EDIT::
I see that my trash can is gone also. Trying to put the applet back gives this error: The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

---

### Post by sofasurfer on 2008-07-06
It appears that I have fixed the problems that I see (so far). I ran "sudo apt-get install --reinstall gnome-applets" and then put the appletta back on the panel.
Thanks and sorry for the panic.

---

