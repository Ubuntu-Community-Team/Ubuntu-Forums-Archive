---
title: "ripping and burning cds"
date: 2014-06-21
forum: Multimedia Software
---

### Post by merlinus on 2014-06-21
Unfortunately my trusty Marantz CD Recorder has gone south, so I am wondering what I need to be able to get cd tracks onto my computer and then burn them to a playable cd, and exactly how to do this.  

I have looked at various software but frankly am at a loss, so am seeking assistance.

---

### Post by papibe on 2014-06-21
Hi merlinus.

You can create a copy from a CD using either the preinstalled 'Brasero', or install 'GnomeBaker'. You insert the source CD in your computer, then create an image on your hard disk. Once that is done you can remove the CD, insert the blank one, and burn that image into the new CD.

If you keep that image in your computer, you will be able to listen the content. You can use a player the can read images, like VLC, or mount the image and use any player of your choosing.

Although that may work, it'd use a LOT of space. Another approach would be to rip the source CD into individual tracks using 'Asunder CD Ripper' or 'RipOff'. To save space you can rip to mp3s, but if you want keep 100% the original quality I'd recommend flacc.

Does that help? Let us know how it goes.
Regards.

---

### Post by merlinus on 2014-06-21
Many thanks for your response!  I do not need to keep any of the "ripped" files on my hdd, but want to rip individual tracks so I can re-order the ones from the original cd, or delete some entirely, and then make a new playable cd.   I do not think creating an .iso will allow me to do that.

 I do know that Brasero can create and then burn audio projects.  I would still need individual files, and will the burned cd automatically play on my system?  Also, it seems as though the music cds have .wav files, so the ripper would need to use that format rather than flac.  I am not at all interested in lossy compression such as .mp3.

I d/l-ed asunder, but could not get it to install.  I extracted the files to a local directory, but the sudo make install command did not work.  It seemed to need other perameters that I did not understand.

---

### Post by Dennis N on 2014-06-21
> I d/l-ed asunder, but could not get it to install. I extracted the files to a local directory, but the sudo make install command did not work.

Asunder is in the Ubuntu Software Center. I would install it from there.

---

### Post by Dennis N on 2014-06-21
Since you don't want mp3s or other lossy format, use Asunder to rip the cd tracks into .wav files (lossless) on your computer. You can then pick and choose which to burn to your blank cd media with Brasero (or other burner).

---

### Post by merlinus on 2014-06-21
Thanks very much, Dennis -- I have installed Asunder via synaptic.  The interface (menu), however, does not seem to allow me to select a source.  I inserted a cd, but nothing comes up.

 Also, can I then specify the order in which the tracks will be burned in Brasero?

---

### Post by papibe on 2014-06-21
> **Dennis N said:**
> Since you don't want mp3s or other lossy format, use Asunder to rip the cd tracks into .wav files (lossless) on your computer. You can then pick and choose which to burn to your blank cd media with Brasero (or other burner).
+1

---

### Post by merlinus on 2014-06-21
I see in preferences it wants the location of my cd-rom drive.  There is nothing in /dev/cdrom, however, only a cdrom directory in filesystem. 

  How would this translate to something Asunder can find and read, since it clearly is not finding the inserted disc?  Changing the location to /cdrom did not do anything.

---

### Post by Dennis N on 2014-06-21
> **merlinus said:**
> Thanks very much, Dennis -- I have installed Asunder via synaptic.  The interface (menu), however, does not seem to allow me to select a source.  I inserted a cd, but nothing comes up.

 Also, can I then specify the order in which the tracks will be burned in Brasero?

Insert the cd into the computer's cd/dvd drive first. If the default cd player autostarts, close it. Then start Asunder. When it starts, it should scan for a cd, read the tracks and display them in its window. You can then select all or some to rip to computer files. Somewhere in the options, you should be able to select .wav as the format for saving those files before starting the ripping process. 

Yes, you can pick and choose which tracks to burn with Brasero - the order you select them is the order they will appear, and even after that, you can also rearrange them by dragging the entries.

---

### Post by merlinus on 2014-06-21
Thanks, but Asunder is not finding the disc.  Perhaps I have missed a setting in Preferences?

---

### Post by Dennis N on 2014-06-21
> **merlinus said:**
> Thanks, but Asunder is not finding the disc.  Perhaps I have missed a setting in Preferences?

Hmmm...I just switched computers to one that had Asunder installed. It has Ubuntu 12.04. I put in an audio cd, a window popped up asking what I wanted to do. I just closed it. Then I started Asunder from the Dash. On starting, it displayed the cd contents. I selected two tracks to rip, checked .wav in the preferences > encode tab, then back on the main window clicked the rip button. It ripped them to wav and all worked, so that is the correct process. 

Now, in the preferences the specification of the CD-ROM is in the general tab.  Mine is set to **/dev/cdrom** and that works on this machine. The tooltip suggests you might try **/dev/sr0** in there.

---

### Post by merlinus on 2014-06-21
/dev/sr0 did the trick!  Thanks!!!

---

### Post by Dennis N on 2014-06-21
> **merlinus said:**
> /dev/sr0 did the trick!  Thanks!!!

Well, glad to hear that. I hope the rest goes well.

---

