---
title: "Presetup Questions"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by Rush_898 on 2006-10-09
Contemplating the jump to Ubuntu as my DAW OS, linux newb to intermediate.  My setup is primarily PreSonus Firepod +AMD XP Processor +MIDI devices.  I have effects, hardware, etc, but it all runs through the Firepod, so that's priority 1 for me.  I've been reading through information online but all the pieces don't seem to be fitting for me so I'm hoping to lay out my thoughts and maybe someone can fill in the lines/correct me.

FreeBob is a program that acts as a collection of drivers for various audio input devices.  So it would be the key to getting the Firepod to work.  But unclear how exactly to go about installing it even after it's wiki.  Would I use the instructions, [here?]("http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux#Building_Debian_Source_Packages_From_Apt_Repository").  Is the apt-get applicable for Ubuntu?

Jack

Soft Patch panel basically.  Needed to route signals from card to devices, an device to device. Is there an apt-get for this?



So summary of what I'm going to do:

Step 1:

Fresh Install of Ubuntu, any special install instructions off the bat?

Step 2:

[http://ubuntustudio.com/wiki/index.php/Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Studio_Preparation)

subtask questions:  what does  Real-Time Support actually do for me?  Is the kernal recompile for lower latency a 90% used option or is it truly the exception?  



Step 3:

Freebob (make sure audio interface works) Easist install route?


Step 4:

Jack & QjackCtl


Step 5:

Install software and test.  [Ardour]("http://ardour.org/")




Other Q's:

Where does [LASH]("http://www.nongnu.org/lash/") fit into these steps?



Last but not least, I've been reading several places that Edgy will have a lot of this battle taken care of, or some of it, is it wise to simply wait for those smarter than I?


Sorry some questions are probably obvious I'm just trying to lay my cards on the table to prevent an 'oh sh*t' moment upon install.  Also, I'm hoping to do this in a step by step fashion with screenshots that may help others.

---

### Post by dolson on 2006-10-10
With regards to realtime access, by default you do not have the ability to run applications with realtime priority access. So you need to enable the ability to run applications that can request realtime access priority scheduling (aka SCHED_FIFO). It has nothing to do with preemption, and is something totally separate. Think of it as a privilege that you need to allow yourself to have, and therefore the applications you launch.

---

