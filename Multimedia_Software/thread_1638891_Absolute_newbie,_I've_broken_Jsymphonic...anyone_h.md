---
title: "Absolute newbie, I've broken Jsymphonic...anyone help?"
date: 2010-12-06
forum: Multimedia Software
---

### Post by mcorr on 2010-12-06
Argh!  If anyone can give any advice at all it would be so helpful!  I'm totally new to Linux, and have just had the newest version of Ubuntu installed.  I love it, my laptop runs so much better, I love the software, it's easy to use, etc...and I found a great wee program in the Software Centre that means I can still use my Sony mp3 player!  Or so I thought...

I've wrestled with trying to get JSymphonic to work with my mp3 player for a few days now, and hit all sorts of problems, and just when I think I'm there something else pops up.  I wont go into those problems now as I've apparently managed to block myself out of JSymphonic altogether, and so they're kind of irrelevant at this point.

As I was having trouble transferring music to my mp3 player, I thought I could try another way, by transferring the music to somewhere on my computer, and then copying them over to the mp3 player.  So I created a folder called 'mp3' in the home folder, and within that created 'OMGAUDIO' and 'esys' folders which Jsymphonic apparently needs to run.  So then in JSymphonic, I changed the device path from media/mp3 to home/mp3, and tried to copy music.  Needless to say it didn't work (I guess because the program is looking for a device which I've directed it away from).  And now I can't access JSymphonic at all.  When I try to open it through the terminal, this is what I get:

[B]06-Dec-2010 13:13:26 org.danizmax.jsymphonic.gui.SettingsHandler startDocument
INFO: Reading file /home/jilly/.jsymphonic.xml...!
06-Dec-2010 13:13:26 org.danizmax.jsymphonic.gui.SettingsHandler endDocument
INFO: Done reading file
06 Dec 2010 13:13:26 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : Initializing JSymphonic...
06 Dec 2010 13:13:28 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:mountDevice : Mounting the device "mp3"
06 Dec 2010 13:13:28 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
06 Dec 2010 13:13:28 [WARNING] org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : The device path /home/mp3/esys does not exist!
06 Dec 2010 13:13:28 [SEVERE]  org.naurd.media.jsymphonic.device.sony.nw.NWEsys:<init> : Invalid OMGAUDIO directory.
Exiting program[/B].

**Does anyone have any ideas how I can get back into JSymphonic to change the device path back to my mp3 player?**  I've tried uninstalling and reinstalling the program from the Software Centre, but the device path remains set to my home folder...bit of a chicken and egg situation, as without changing the device path I can't get into JSymphonic, yet I need to get into JSymphonic to change the path.  

As I know nothing about Linux, I don't know if maybe there's a behind-the-scenes way to sort this out?  

Sorry for the long-winded post, but thank you to anyone who's read it and can perhaps offer guidance or suggestions, would be very much appreciated!!

---

### Post by arubislander on 2010-12-06
Hi!

You mentioned you created an mp3 folder in your home folder. But your path to said folder is incorrect. It's ```
/home/mp3/esys
``` while it should be ```
/home/jilly/mp3/esys
```

The setting is probably in the hidden file .jsymphonic.xml in your home folder. Just open a terminal and type ```
$ gedit /home/jilly/.jsymphonic.xml
``` and search for /home/mp3/esys

---

### Post by mcorr on 2010-12-06
Thanks so much for your speedy reply Arubislander!  I followed what you said and it worked perfectly -  I've managed to get back into JSymphonic and have changed the path back to my mp3 player - a mini victory!  I'm now back where I started with my original problem though...which is that for some reason I can't transfer music to my mp3 player.  JSymphonic appears to work, and memory is taken up on my mp3 player, yet it (mp3 player) claims there's NO DATABASE.  I've seen posts by others that mention the same problem, yet I can't see a clear solution.  Here's what the terminal says when I transfer music files:

06 Dec 2010 17:13:07 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/MP3/ESYS
06 Dec 2010 17:13:07 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
**06 Dec 2010 17:13:07 [WARNING] org.naurd.media.jsymphonic.device.sony.nw.NWGeneric$1:run : [Ljava.lang.StackTraceElement;@5d391dnull**
06 Dec 2010 17:13:09 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
06 Dec 2010 17:13:09 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/MP3/ESYS
06 Dec 2010 17:13:09 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree

Any ideas what the warning's all about?  I assume that that's what the problem is.  If any one can walk me through how to fix that bit too, I will be forever grateful.  And thanks again Arubislander!

---

### Post by mcorr on 2010-12-06
It's all good!  Not sure how, but it's fixed and working and I can return to day-to-day life, phew!  If anyone's experiencing the same problem, I'm not sure exactly what I did, but I had a 'esys' folder alongside 'OMGAUDIO' which I thought was necessary.  I was fiddling about with things and deleted the 'esys' folder, and whether that's what did it or not, I don't know, but JSymphonic is now fully functional.  Yaldie!

---

### Post by tgalati4 on 2010-12-06
Anything to avoid that craptastic Sony SonicStage software.

---

