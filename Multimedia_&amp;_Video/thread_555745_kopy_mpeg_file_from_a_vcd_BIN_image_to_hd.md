---
title: "kopy mpeg file from a vcd BIN image to hd"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by TangoLima on 2007-09-20
hello,
can anyone help me to copy the mpeg file from a (s)vcd BIN image (with CUE file) to my HD. bchunk was no help for me, because the BIN file is split in two tracks. 

thanks for any help

greetz tim

---

### Post by mtn on 2007-12-07
I just had some luck extracting an mpeg movie file from a cue / bin VCD file stored on the hard drive i.e. there where no actual cd / dvd involved with this. The cue and bin are the VCD image files!

**Software used**

**Ubuntu Gutsy 7.10** (new-ish install)
**WINE  0.9.46** (was the most recent in repos)
**IsoBuster 2.2**: [http://www.smart-projects.net/](http://www.smart-projects.net/)

**1)** Install WINE with Synaptic. System>Synaptic Package Manager and then search for WINE, select and hit the "Apply" button.

**2)** Download and install ISO Buste - [http://www.smart-projects.net/r](http://www.smart-projects.net/r). This meant right clicking on it and choosing to open the .exe with WINE. It installed and then gave the option to launch automatically, which I chose.

**3)** Extract the movie from the bin file (this is the file that holds all the data). I used the instructions from here: [http://forum.videohelp.com/topic141726.html#svcdbin](http://forum.videohelp.com/topic141726.html#svcdbin)

> - Select File-> - Open Image File and open the CUE file.

- Click on the MPEG2 folder (in my case, as it was a VCD, the folder I selected was **MPEGAV**)

- Select all mpg files and right click and select Extract but filter only M2F2 Mpg frames in (again, due to this being a VCD I selected the **.dat** file).

- Save the new file as filename.mpg.

This worked great for me and I could play the new movie file in MPlayer and Ubuntu's default movie player. Not tried on my Neuros OSD yet! 

To convert between codec and encode for DVD etc I found this Windows app worked flawlessly, again with WINE- TMPGEnc (I used the most current version TMPGEnc-2.524.63.181-Free.exe with )  :[http://www.tmpgenc.net/](http://www.tmpgenc.net/)

I hope this helps a little.

---

