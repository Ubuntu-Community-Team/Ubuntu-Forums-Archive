---
title: "Adding/Removing Applications (help!)"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by lost09 on 2008-02-23
I am attempting to add the supposedly necessary files in order to get Multimedia (mp3, avi, etc) functioning (specifically the GStreamer stuff). However,  when I attempt to select an application in the Add/Remove Applications window, I receive a message box titled "Confirm instillation of restricted software". Clicking "confirm" brings up a second window claiming that the list of application is unavailable. Clicking "refresh" here brings up two subsequent windows which flash out of view far too quickly for me to read (however I do know they had progress indication bars on them), and the cycle repeats. 

Any help would be most appreciated, as my computer is thus unable to handle either music or video of any kind.

---

### Post by wikityler on 2008-02-24
If it's the GStreamer ffmpeg video plugin you're looking for, you can do
*sudo apt-get install gstreamer0.10-ffmpeg*
in the terminal.

---

### Post by ryanhaigh on 2008-02-24
Perhaps you should try enabling the other software repositories. Just go to System > Administration > Software Sources and enable main, universe, restricted and multiverse. Click close and a new window will appear, press reload and then try installing the packages again.

As a side note I find it synaptic a much better tool for software installation, its in System > Admin > Synaptic Package Manager.

As a second side note there is an easier way to install all the codec/fonts etc that you will need. Again you will need to enable the extra software repositories as above, then you can open up System>Admin>Synaptic Package Manager, search for the package ubuntu-restricted-extras and install that (which will also install mp3 support, java, flash etc). Alternately after you have added the extra repositories you can click the link below.

[apt://ubuntu-restricted-extras]("apt://ubuntu-restricted-extras")

---

