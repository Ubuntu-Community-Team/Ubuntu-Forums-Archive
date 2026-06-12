---
title: "Extracting a file from megaupload"
date: 2009-04-03
forum: Multimedia Software
---

### Post by dawj on 2009-04-03
i downloaded a move file from megaupload but my system cannot recognise the format. i checked in the synaptic package manager and both rar and unrar have been properly installed.The format is as follows (for part 1):

/home/dawj/Desktop/LCN.10000.BC.2008.HDRip.x264.[300Mb].mkv.__a   

When i right click on it, there is no command for extracting it. How do i extract this file?

---

### Post by Jose Catre-Vandis on 2009-04-03
Try the file on the command line with this:
```
/usr/bin/unrar e -y /path/to/your/file.__a
```
If it _is_ a rar this should work

---

### Post by dawj on 2009-04-03
> **Jose Catre-Vandis said:**
> Try the file on the command line with this:
```
/usr/bin/unrar e -y /path/to/your/file.__a
```
If it _is_ a rar this should work

sorry it did not work.

i should have said this earlier, when i was downloading,it came up with the message "BIN file." i am a bit confused here as well because i have never encountered a bin file when downloading a movie from megaupload/rapidshare etc. when using windows ( i am very new to Linux)

---

### Post by SunnyRabbiera on 2009-04-03
.mkv is a matroska video, it should open with your default media player...
are you sure you are downloading it right?

---

### Post by dawj on 2009-04-03
> **SunnyRabbiera said:**
> .mkv is a matroska video, it should open with your default media player...
are you sure you are downloading it right?

i am unsure if there is a different procedure for Linux. i merely add the url  ([http://www.megaupload.com/?d=C6FLYEEY](http://www.megaupload.com/?d=C6FLYEEY) - part 3) to the web browser and it goes to the website and i download as a free user. Once the waiting period is over, it asks me if i want to download the file and it gives the message that this is a bin file. i am presently downloading part 3 of 4

---

### Post by Jose Catre-Vandis on 2009-04-04
You will need all the parts of the archive before you can start unarchiving :)

---

### Post by dawj on 2009-04-04
> **Jose Catre-Vandis said:**
> You will need all the parts of the archive before you can start unarchiving :)

Thanks, but still does not work. The files are all BIN format and i tried burning them using brasero but could not read them after having burned them on a dvd disk. Perhaps i need to join all the files first. Do u know of any File Splitter/Joiner programs?

---

