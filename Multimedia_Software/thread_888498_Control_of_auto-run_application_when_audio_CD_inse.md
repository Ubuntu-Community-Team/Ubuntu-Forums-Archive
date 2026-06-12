---
title: "Control of auto-run application when audio CD inserted"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Peter Bell on 2008-08-13
I installed Rubyripper some time ago and after installation it automatically started up whenever I inserted an audio CD.

&#65279;Now, when I insert an audio CD I get soundjuicer starting - perhaps this happened on the update to Hardy?

How can I get back to a state where Rubyripper automatically starts?

---

### Post by Peter Bell on 2008-08-14
Sorry, is this a difficult problem?

Is there no way to set which application runs when an audio disc is detected in the drive?

---

### Post by kpkeerthi on 2008-08-14
You can change that under System -> Preferences -> Removable Drives and Media

---

### Post by Peter Bell on 2008-08-14
> **kpkeerthi said:**
> You can change that under System -> Preferences -> Removable Drives and Media

Thanks for the reply, but I'm obviously being stupid ... all I see in the Removable Drives and Media Preferences are the following tabs : Cameras, PDAs, Printers & Scanners, Input Devices.  None of these tabs appears to have anything relating to a CD drive or Audio Disc.


Can you give any further guidance?

---

### Post by Peter Bell on 2008-08-16
Perhaps I need to treat this like a Windows system and just re-install in the hope that behaviour returns to that which I was happy with.

---

### Post by |Porsche on 2008-09-01
> **Peter Bell said:**
> Perhaps I need to treat this like a Windows system and just re-install in the hope that behaviour returns to that which I was happy with.

I hope it is not too late. To select the application which will launch upon Audio CD insertion just do the following:
1. Open Nautilus and go to your Home Folder.
2. Go to Edit -> Preferences
3. Select the Media Tab.
4. Select the type of media and the type of action you want Ubuntu to perform.
5. Enjoy 

Let me know how it goes.:guitar:

---

### Post by mc4man on 2008-09-01
Rubripper won't be available there, but it should be easy to set from various available methods.

The easiest may be to simply change the launch command of cd audio extractor to whatever the launch command of rubyripper is. (**must only be changed** in edit menus - sound & video -> properties of cd audio extractor.

Tried with grip - works fine (changed the cd audio ext... launch command to "grip"  (no quotes

For all methods I've found to modify behavior of default media insertion see here

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by Peter Bell on 2008-09-02
Many, many thanks mc4man.  I followed your method in the other post - a rubyripper.desktop was already present, as was the mimeapps.list.  I simply had to add 'rubyripper.desktop;' into the line for 'x-content/audio-cdda' and RubyRipper is, once again, selectable as the default app for audio cds.

This really does make life so much easier - the main use of this particular machine is as a media server hosting SqueezeCenter for my SlimBoxes and it lives in the audio cabinet in the lounge.  Every time I come home with a new CD, the first thing I do is load it in the machine and rip it to flac.

So, thanks once again!

---

### Post by mc4man on 2008-09-05
Depending on your usage you could try > rrip_cli -a as a launch command. That would create a 'insert the cd and walk away' method which would be fine if your using the same config most times and doing the complete disk.


Edit; just tried it, works very well running silently in the background. Set rr up to r&e  hq flac's and lower quality mp3's for a mobile, popped in the disk and it took care of all of it.

Note;  I'm using Audio cd extractor's autorun place for the comm. That leaves rr's default launch alone for accessing the gui when needed.
If you change rr's default then just make a desktop launcher w/  rrip_gui as comm. for setup or changes to config or just run the gui from the terminal.

---

