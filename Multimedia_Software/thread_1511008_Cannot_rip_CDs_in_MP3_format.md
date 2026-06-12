---
title: "Cannot rip CDs in MP3 format"
date: 2010-06-16
forum: Multimedia Software
---

### Post by osx on 2010-06-16
After installing Ubuntu 10.04, 64-bit, I can no longer rip CDs to MP3 format. I can play MP3 files on the computer just fine. And this isn't limited to a single application.

I normally use Sound Juicer to rip my CDs. Under Edit >> Preferences >> Format, the drop down menu no longer lists MP3 as an output option; however, if I click on the "Edit Profiles" button, there is a "CD Quality, MP3" option and it is set to active.

I'm having the same problem with Rhythmbox. Under Edit >> Preferences >> Music, the "Preferred format" box is empty, the dropdown menu is grayed out, and clicking the "Edit" box only shows the same sound profiles as Sound Juicer with no way to make one enabled (yet they are marked as active).

Anybody have an idea as to what is wrong and how to enable MP3 as an output format?

Thanks.

---

### Post by oldos2er on 2010-06-16
Do you have **lame** installed?

---

### Post by osx on 2010-06-16
> **oldos2er said:**
> Do you have **lame** installed?

Yes, I do, and I've confirmed this issue on a second box.

lame was installed on its own, not done by installing the Ubuntu restricted extras.

Thanks.

---

### Post by oldos2er on 2010-06-16
You may still need a couple of the gstreamer packages. Try ```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-lame gstreamer0.10-plugins-really-bad
``` then see if sound-juicer works.

---

### Post by osx on 2010-06-16
> **oldos2er said:**
> You may still need a couple of the gstreamer packages. Try ```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-lame gstreamer0.10-plugins-really-bad
``` then see if sound-juicer works.

I wanted to see which one would add the feature so I first installed gstreamer0.10-plugins-ugly and that didn't work. Then I installed gstreamer0.10-lame and the MP3 output option was now available in Sound Juicer and it successfully ripped a CD.

Thanks for your help.

---

### Post by oldos2er on 2010-06-16
You're welcome. Enjoy Ubuntu!

---

### Post by pembo02 on 2010-07-26
Hi i was able to rip cd's then out of the blue i'm having the same problem no mp3 tab to select but i can go do >edit and access the mp3 options. tryed the install command and got 

nick@dalaran:~$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-lame gstreamer0.10-plugins-really-bad
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
Package gstreamer0.10-plugins-really-bad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
E: Package gstreamer0.10-plugins-really-bad has no installation candidate


no idea where i can source it from  tryed looking in synaptic but no luck any help would be great!
nick

---

