---
title: "Video Drivers for Dell 700m"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Robotuner on 2007-02-08
Hey all, I made a mess of my system trying to get the resolution to 1280x800, so I looked around first at the Dell site and saw that the video driver is an Intel Extreme Graphicx 855GM.  Then I googled it and ended up at the intel site:

[http://www.intel.com/support/graphics/intel852gm/](http://www.intel.com/support/graphics/intel852gm/)

That appears to indicate that the 855GM is the same as the 82855 GM video controller.  The site also says that there are drivers available.  So, I'm new to linux, can someone with a dell 700m who knows more than me tell me where to find and how to download the precomipled binaries and then how to get edgy to use them?

Thanks.

---

### Post by veloce on 2007-02-10
I believe the you need is the i810, and it is probably already running.  Check in Synaptic Package manager - search for i810 - the notes will tell you if it supports your card.

To get the higher graphics modes you may need the program 915resolution, but not sure if it works for the intel 8xx series.

 Good luck.

---

### Post by Robotuner on 2007-02-11
HI:

I wanted to try getting higher resolution by first obtaining thei915, then installing it in the proper location on machine, then re-running the 

dpkg-reconfigure -phigh xserver-xorg

script.  Unfortunately, other that running that scrip, I don't know how to do the first two steps.

---

### Post by veloce on 2007-02-14
Sorry for the late post, I forgot to add this to my bookmarked threads.  You may have already sorted it, but if not, the instructions I wrote for myself are attached:

Using Synaptic Package Manager search for "915" and you should see 915resolution. Install this.
Easiest thing to do next is just to reboot. If you are more adventurous (and know to use Ctrl + Alt+F1 to get a command prompt to reboot out of difficulty):

[LIST]
[*]Use Alt+F2 to bring up the run command window. 
[*]Run the command: sudo /etc/sbin/915resolution
[*]Close everything that you want to save 
[*]restart X windows "Ctrl + Alt + Bksp"
[/LIST]

The default setting will probably work.  If not, then the card has not managed to interrogate the screen correctly.  You need to edit the file /etc/default/915resolution. Instructions are in the file.  Leave: mode=auto but set the resolution parameters for the resolution you are after.

---

### Post by Robotuner on 2007-02-16
Thanks very much.  Works like a charm and does exactly what I wanted it to do, without all the steps that 815resolution seemed to make everyone go through.  What I don't understand is why it worked and replaced on reboot.  I expected that I would need to obtain the 915resolution driver, copy it on the machine somewhere, then have to somehow tell the machine to use it instead of the currently installed video driver.

Thanks again

---

### Post by veloce on 2007-02-16
915resolution isn't a video driver, it's just a hack that forces a check on your monitor and stores the result in the video bios memory so that it's available to the i810 driver.

---

