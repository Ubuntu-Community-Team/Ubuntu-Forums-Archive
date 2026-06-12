---
title: "Music recording in Gutsy"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by eajohnson on 2008-03-16
Hello,

So as an aspiring musician, i would like to be able to record my music.  I am using an Edirol fa-66 firewire interface to record my music. Unfortunately, when i try to record in either Rosegarden or Audacity, no sound is recorded.  I have installed both ALSA and freebob separately and neither of these have given any positive results.  There are no problems with the JACK server for rosegarden, so i have to think that this is a problem most likely with firewire support in Ubuntu (gutsy 7.10).  Anyone have any ideas as to how to remedy this problem?  Just as a side note, i had no problems with any of this equipment in windows.......

thanks

---

### Post by xc3RnbFO8P on 2008-03-16
Try this:

> sudo gedit /etc/modules

Add this two lines in to the bottom of the page:
> dv1394
video1394
raw1394
ohci1394

Load the modules:
> 
sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394
 

Getting read and write access:
> sudo chmod a+rw /dev/*1394 

Reopen the program.

---

### Post by univac on 2008-03-29
> Add this two lines in to the bottom of the page:

What page? Also, there are four lines. Can someone please explain what this means?

---

