---
title: "VCR Tape Digitizing -- How?"
date: 2007-07-05
forum: Multimedia Production
---

### Post by dabl on 2007-07-05
Has anyone used a Ubuntu system to capture the output from a VCR?  What tools did you use, what are the obstacles, where are sources of information?

Thank you very much!  :)

---

### Post by lisati on 2007-07-05
You'll need some kind of video capture card, one end plugged into your VCR, the other into your computer.

I'll be watching this discussion with interest, since I have a "cardbus" device that I have the Windoze drivers for but haven't managed to get working properly with Ubuntu yet....

---

### Post by juniorsonny on 2007-07-05
Yeah, I've done alot of converting in windows but I can't find anything either for linux.  I've ditched windows all together.  I love Ubuntu but, just wish I could find something to convert my tapes over to dvd.

---

### Post by dabl on 2007-07-05
I take it that one needs a card such as these, for the interface to the VCR:

[http://www.hauppauge.com/pages/prods_pvr.html](http://www.hauppauge.com/pages/prods_pvr.html)

They all look very Windows-centric -- are Linux/open source drivers available?

---

### Post by srt4play on 2007-07-05
> **dabl said:**
> I take it that one needs a card such as these, for the interface to the VCR:

[http://www.hauppauge.com/pages/prods_pvr.html](http://www.hauppauge.com/pages/prods_pvr.html)

They all look very Windows-centric -- are Linux/open source drivers available?

Yes there are built-in drivers for the pvr-150, pvr-250, and pvr-350 not sure about the USB model.

I've personally used both the 150 and 250 with mythtv, and was also able to capture from a VCR.  I'm sure there's a simpler program to do it though since installing mythtv would be overkill for this purpose.

---

### Post by newlinux on 2007-07-05
if you get one of the hardware encoding cards like the pvr-x50 I'm pretty sure you could simply hook it up, press play on your VCR, type in at the terminal

```

cat /dev/video0 > filename.mpg

```

assuming video0 is the device of the capture card. and hit CTRL-C when you are done. You could us the "at" command to schedule the start and end of the recording.

```

at 10:00pm
at> killall cat

```
or something similar

---

### Post by dabl on 2007-07-06
> **srt4play said:**
>  installing mythtv would be overkill for this purpose.
I've got lots of CPU, RAM, and disk space -- overkill is not my concern, just ignorance. ;)

@newlinux, assuming the card is recognized on the PCI bus and responds correctly, the simplicity of your approach is awesome -- thanks!

:D

---

### Post by dad311 on 2007-08-14
I bought a firewire card from ebay for $5.00

I use one of these captureboxes
[http://www.canopus.com/products/ADVC110/index.php](http://www.canopus.com/products/ADVC110/index.php)

I use kino to capture the DV

I use kino or cinelerra to edit the DV

I use kino or cinelerra to render the video to an mpeg or vob file.

I use glabels to create custom DVD labels.

All works well.

---

### Post by dabl on 2007-08-14
> **dad311 said:**
> 

I use kino or cinelerra to render the video to an mpeg or vob file.



These DVDs will "play" on a computer -- I have got that far, recently.  But, how about making an ISO image for a DVD to play on a household DVD player, connected to the TV?

---

### Post by dad311 on 2007-08-14
After creating  mpeg files, you will need to use a program like qdvdautor, ManDVD or kmediafactory.  These types of programs will author a DVD that will be readable on "most" DVD players.

My favorite DVD authoring program is qdvdautor found [HERE]("http://qdvdauthor.sourceforge.net/") with a demo video.

To install qdvdauthor in Ubuntu, type "sudo apt-get install qdvdautor"

---

### Post by dabl on 2007-08-14
Interesting -- thanks, I'm putting that on my list of things to try.  :)

---

