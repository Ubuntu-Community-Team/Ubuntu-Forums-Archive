---
title: "Best program to rip high quality mp3?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by curiousnoob on 2009-04-26
I am sure this is not a new question but unfortunately a search produces too many results from too long ago for me to find the answers I am looking for.  Basically I have two questions: 
1. What is the bitrate for modern .mp3 files comes closest to CD quality and is there such a thing as lossless .mp3 
2. What is the best program for Linux to rip .mp3 and will different programs give different quality .mp3's using the same bitrate? 

I realize there are better file formats that take up less space but I am trying to stay with .mp3 to keep maximum versitility.

---

### Post by vässlan on 2009-04-26
1. i guess anything above 192kbps sounds good enough. 
2. dunno which one is the best but anything that uses Lame to encode, get lame from the medibuntu repos

---

### Post by tom56 on 2009-04-26
Sound Juicer is installed by default and does the job excellently. Due to legal issues, MP3 support is not installed by default, but check the help files for information on how to add it.

---

### Post by logos34 on 2009-04-26
1. VBR -V2 setting in LAME (~192kbps) or higher is the standard.  Check out the lame/mp3 page over at Hydrogenaudio.  .mp3 is a lossy format.  Lossless = flac, wav, ape, wavpack, .alac (apple lossless), etc.

2. The ripping and encoding process are separate.  Two different rippers may call the same .mp3 encoder.  Exact Audio Copy (wine) is considered the best ripper (secure, verified rips.).  Rubyripper (native linux app) is probably next best.  Fast but good rips (using cdparanoia): abcde, grip, k3b.  

I think Sound Juicer is a p.o.s but that's just my opinion

---

### Post by yoasif on 2009-04-26
eac + lame is the current standard.

---

### Post by Arup on 2009-04-26
I tried all but settled for Ripper X which does the job as good as the programs I used on Win.

---

### Post by curiousnoob on 2009-04-26
It looks like eac and lame will do what I need but I don't know which version of lame is the latest and most stable.  Where can I find this?

---

### Post by Electron on 2009-04-26
GnomeBaker and Sound Converter :)

---

### Post by logos34 on 2009-04-26
> **curiousnoob said:**
> which version of lame is the latest and most stable.  Where can I find this?

[v. 3.98.2]("http://lame.sourceforge.net/")


the lame pkg in Intrepid and Jaunty uses 3.98

---

### Post by curiousnoob on 2009-04-27
> **logos34 said:**
> [v. 3.98.2]("http://lame.sourceforge.net/")


the lame pkg in Intrepid and Jaunty uses 3.98

If I am using Intrepid Ibex does that mean that I already have it?  How do I import it into EAC?

---

### Post by logos34 on 2009-04-27
if you're going to use it with EAC, you need the windows .exe file.  

Here:

[http://www.free-codecs.com/download/Lame_Encoder.htm](http://www.free-codecs.com/download/Lame_Encoder.htm)

Unzip and stick it in ~/.wine/drive_c/Program Files/

then [point EAC to it ]("http://wiki.hydrogenaudio.org/index.php?title=EAC_and_Lame")(-->external compression path)

---

### Post by curiousnoob on 2009-04-27
I have the latest version of EAC and WINE but am having trouble getting lame into EAC.
Whenever I start EAC it walks me through a quick wizard to for the settings until I get to this point:
[http://img2.imageshack.us/img2/4029/69193578.png](http://img2.imageshack.us/img2/4029/69193578.png)

It hangs there and even if I press cancel nothing happens. Has anyone else had this issue or is there a way to manually install lame so that I can skip this step?

---

### Post by logos34 on 2009-04-27
when the Configuration Wizard box pops up, can't you cancel it?  Then manually configure 

Menu bar>EAC
>EAC options
>Drive options
>Compression options

---

### Post by curiousnoob on 2009-04-27
> **logos34 said:**
> when the Configuration Wizard box pops up, can't you cancel it?  Then manually configure 

Menu bar>EAC
>EAC options
>Drive options
>Compression options

You da man.  I'm going to play around with this for a while but if anyone has any tips or tricks please let me know :)

---

### Post by stefcep on 2009-07-29
> **Arup said:**
> I tried all but settled for Ripper X which does the job as good as the programs I used on Win.

Thank you!!

I installed grip, sound-juicer, mp3c.  All I wanted was a GUI that let me select which tracks I wanted to rip, set the encoding parameters from a GUI and select the destination where I wanted the encoded files saved from a GUI.  And no I shouldn't have to install a second GUI system ie KDE in order to use such a program nor should have I have to install Windows compatibility layer to run Windows software to do this.  Hell I had this on my Amiga in 1995!!!!  You'd think it wouldn't be much to ask?  Ripperx was the only one to offer this.  Brilliant!!.

---

