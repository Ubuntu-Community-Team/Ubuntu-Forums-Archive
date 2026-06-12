---
title: "Compiz worries......"
date: 2009-03-08
forum: Multimedia Software
---

### Post by Euanbuntu on 2009-03-08
I'm fairly new to ubuntu: I think it's the best thing since sliced apples, and have intrpid installed on a fujitsu-seimens Amilo A1667G. It has a ATI Mobility Radeon X700 video card and seems to be working ok, despite some technical worries to begin with, everything is ok now.

So, I'm trying to get compiz to work, but everytime i run compiz...this happens (see down there) then nothing, it just seems to freeze, and i never get back to the command line :(

euan@euan:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I'm not quite sure if it's the 'not present' items i need to be focussing on ... any ideas out there please?

---

### Post by Euanbuntu on 2009-03-08
ok, I've got as far as downloading and installing and running CCSM, but i still have no idea why none of the options i enable within CCSM work...probably something to do with my initial post above.

---

### Post by Fenris_rising on 2009-03-08
Hi there

You have done the following?

Right click desktop>Change desktop background>Visual effects

Select 

Extra's

Have you installed the Fusion icon? This will give you access to a couple of other options such as choosing windows manager- Compiz or Metacity and
the window decorator- GTK Window decorator or Emerald

Also check you have installed the restricted drivers for your graphic card?

regards

Fenris

---

### Post by Euanbuntu on 2009-03-08
Hi fenris_r, thank you for that!

 for some inexplicable reason the extras were turned off!!!!! I thought I'd done that, but it looks like I hadn't....yes, all the drivers are updated etc etc, and I have the fusion icon, although I have absolutely no idea how this is used. I can see the options, but they are all quite foreign to me at the mo.

I can now rotate between 2 desktops...! Hooray

...is there an easy to read noob-guide for compiz I wonder...if I anyone else does find one, may I suggest posting back here to try to get the word out?

Again, thank you Fenris.

---

### Post by Fenris_rising on 2009-03-08
Hi there

Usually if restricted drivers are needed then a an Icon pops up in the top right (looks like a graphic card) with a notice saying that they are needed.

Go to- System>Admin>Hardware drivers and see if the 'Enabled' box is ticked if not, tick it :)

The Compiz or Or Metacity option is to have either of the 2 control how your GUI works. Compiz will have all the bells and whistles Metacity is far simpler (no cube or other Compiz type effects)

The decorators decorate your window frames Emerald has more 'Swish' looking style but you may need to go Download some .emerald themes as the default is empty. (You have installed Emerald via synaptic?) The GTK decorator has more pedestrian styles.

I'm fairly new to this too so hopefully someone else will pickup from me as I am out of ideas :) Do search the forums as well though.

regards

Fenris

---

### Post by Euanbuntu on 2009-03-08
Great stuff Fen,

no, i got emerald through the terminal, but i have it anyhow.

and once you get used to the compiz settings and stuff, it's very easy to understand...you just need to be able to play a bit and find out what's what!

I installed a module for emerald...something about what is necessary to build engines in emarald, not that I'm pretending to have a clue what that really means, but I'm wondering...if emerald gives you fancy control over the look of your desktop, then how do you use it? I have emerald installed and can see it's presenced under applications>system tools>compiz fusion icon ... yet i have no idea of its functionality in any sense! I will look for this in the forums!

Another question is how to get the animations in CCMS going....dunno what I'm doing wrong there, but i select the options (for example the airplane option) and then come out and open some windows, but no effects :(

---

### Post by Therion on 2009-03-08
> **Euanbuntu said:**
> I can now rotate between 2 desktops...! Hooray
You need to increase your number of virtual desktops if you want the Cube effect:

You'll need to install CCSM. Search on it using Add/Remove.

Go to System/Preferences/Advanced Desktop Settings

Click on the "General" section, double-click on "General Options".

Click on "Desktop Size" tab and increase the "Horizontal Virtual Size" from the default of "2" to "4".

Click on the "Back" button.

Enable the the "Desktop Cube" and "Rotate Cube" plugins.

To activate the Cube, press Ctrl+Alt+Left Mouse Button



**Some basic documentation on using Compiz can be found here:**

Brief explanation of the main plugins:  [http://wiki.opencompositing.org/PluginsMain](http://wiki.opencompositing.org/PluginsMain)

Examples of what the Animations do:  [http://wiki.opencompositing.org/Plugins/Animation](http://wiki.opencompositing.org/Plugins/Animation)

CompizFusion Users Forum:  [http://forum.compiz-fusion.org/index.php](http://forum.compiz-fusion.org/index.php)

---

### Post by Euanbuntu on 2009-03-08
Cheers Therion,

I've just edited the original post to include  stuff about animations, but i'll read your guides before going any further. Thanks :)

ok for anyone else who gets here, I'm off to the compiz users forum. All thanks to Therion for that link...check up a post to see it.

See you in the compiz forums

Euanbuntu

---

