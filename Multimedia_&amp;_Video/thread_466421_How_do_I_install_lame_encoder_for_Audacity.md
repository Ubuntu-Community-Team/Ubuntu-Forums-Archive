---
title: "How do I install lame encoder for Audacity?"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by bcsco on 2007-06-06
I have installed Unbutu 7.04 and the application, Audacity. Audacity requires that lame encoder be installed, to export music files to the mp3 format. This encoder does not come with Audacity but must be installed separately. 

I have tried installing this encoder using Kunbutu (as a separately installed application on it's own drive), to no avail. Now, I'm trying it with Unbutu (on another drive) and am still having problems.

The lame encoder is NOT available through the Add/Revove Applications feature. So, it must be installed separately from the Internet. I downloaded "dbm" files while using Kunbutu, but could never get them installed.

How can I get this accomplished? This is the primary reason for installing Unbutu on this PC. I really have to have it functioning.

---

### Post by tux821 on 2007-06-06
Eh this looks nice for a start:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
[http://www.thanhsiang.org/faqing/node/56](http://www.thanhsiang.org/faqing/node/56)

---

### Post by trak87 on 2007-06-06
It's similar but different in Ubuntu. In Synaptic, enable the Multiverse repository. Press Reload. Look for and install "lame".

---

### Post by josesanders on 2007-06-06
Just do the following:

$ sudo apt-get install lame

When you try to export audio files as mp3 in Audacity, you have to locate the file "libmp3lame.so".  When audacity opens the directory where it expects the file to be, it only shows files with the name "libmp3lame.so", but for some reason, on my system it is called "libmp3lame.so.0".  It is the same thing, but for some reason the name is wrong.  In order to see it, you just have to change it to show all files.

---

### Post by tux821 on 2007-06-06
> **trak87 said:**
> It's similar but different in Ubuntu. In Synaptic, enable the Multiverse repository. Press Reload. Look for and install "lame".
ok, as my vmware was broken I had no change to check this, thanx (removed my old post)

---

### Post by bcsco on 2007-06-07
That did it! Thanks to you and everyone else who responded to my request. This is an older PC that I use strictly for copying LP's. I wanted to give Ubuntu a try but came up against this dilema. You really came through for me.

---

### Post by Bohlio on 2007-06-08
What is the difference between LAME and gstreamer0.8-lame?
By following the "enabling multimedia in Fiesty" thread, I installed a bunch of gstreamer stuff, So should i also install gstreamer-lame, or just lame? Do they both work for audacity?

---

### Post by steeleyuk on 2007-06-08
LAME is just the codec on its own. I presume that gstreamer0.8-lame includes the backend for allowing apps to use it. So for example, it would allow a program like Totem to access the MP3 codec using Gstreamer.

The LAME codec is now included in Bad or Ugly of Gstreamer version 0.10 so there shouldn't really be much use of 0.8 unless its an older application.

---

### Post by Bohlio on 2007-06-08
Thank you :-)

---

### Post by DrZeus on 2007-06-09
hi all.  I tried to export a wav file to mp3, and i selected the **libmp3lame.so.0.0.0 ** and audacity started the encoding, then crashed.  After that, i saw the **libmp3lame.so.0 ** and used that one, then audacity started doing the export, and crashed!

I opened audacity it from the console(to see the error msg), and it gave me a **Segmentation fault (core dumped)** message and crashed again.

Just dont know what happened.  I already installed lame, lame-extras, and it keeps happening.

Hope for opinions soon; God bless you fellas

---

### Post by kanguin on 2007-06-21
I am a new Linux user.

I am using Audacity to record for LibriVox.org which [inexplicably]("http://librivox.org/forum/viewtopic.php?t=879&sid=b0271513fdd8374d68a6309ea2e15f4c") uses mp3 for its free audiobooks instead of an open source format like Ogg Vorbis.

Therefore I needed to add the export mp3 function to Audacity. 

I carefully searched the forums for explanations I could understand. I learned that mp3 export is disabled because it uses software which is not, or may not be, free. 

Nevertheless, I needed to produce my audiobooks in mp3 format for this project.

Here are the steps I used. Please pardon the micro step-by-step approach if you are an expert, and if you are a beginner I apologize for any minor steps I may have missed.

130. In Ubuntu Feisty Fawn I used the automatic software installation method named "Synaptic" by clicking on the System menu at the top of the screen. 

132. Chose Administration and then Synaptic Package Manager.

140. Entered my Ubuntu password for my PC at the prompt

150. In the Synaptic window I chose Settings / Repositories 

160. In the Ubuntu Software tab I checked the Software restricted by legal or copyright issues (multiverse) box, and then the Close button

170. Back in the main Synaptic Window I clicked the search button and typed LAME and clicked search.

180. In the search results list I scrolled down and clicked the boxes for lame and liblame0 and chose "mark for installation" for each.

190. Clicked the green "apply" button, and okayed the Summary Screen warning.

200. After the software was automatically downloaded and installed, I closed the Synaptic window.

210. Opened Audacity and in the Edit / Preferences window clicked File Formats

220. In the mp3 export setup I clicked the Find Library button and then Yes when it asked to search for the libmp3lame.so (so means shared object) file.

230. Changed the file name by adding a dot zero to the end: libmp3lame.so.0

240. Clicked OK to the warning and then noted that mp3 encoding with 128 bit was now enabled.

250. Closed Audacity Preferences and was now able to export recordings in mp3

Complete credit to:
[http://ubuntuforums.org/showthread.php?t=268030&highlight=lame](http://ubuntuforums.org/showthread.php?t=268030&highlight=lame)

---

