---
title: "Audio-recorder on Saucy 13.10."
date: 2013-08-05
forum: Multimedia Software
---

### Post by osmoma on 2013-08-05
Audio-recorder is ready for Ubuntu 13.10.
Get source code and packages from: [https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

Obrigado e bem-vindo!

// moma
  Portugal

---

### Post by osmoma on 2013-08-08
Re-hi,

$ wget [www.futuredesktop.org/getstats.sh]("http://www.futuredesktop.org/getstats.sh") 
$ chmod +x ./getstats.sh 

$ ./getstats.sh 
Counting 32bit downloads for saucy: audio-recorder 1.2~saucy:   1
Counting 64bit downloads for saucy: audio-recorder 1.2~saucy: 6

Already 7 downloads.  Go more! ;-)

---

### Post by QkpW4xf on 2013-08-08
thanks,nice app and works very well ! 
ubuntu Saucy 13.10 :-)
obrigado amigo !

---

### Post by grahammechanical on 2013-08-13
I lost the ability to record audio with Raring Ringtail. Neither Gnome Recorder or any other application would record. Now, thanks to Audio-recorder I can record again. The instructions in the Install text file are very good. I installed the libraries that were not installed by default and I ran the commands listed and everything worked. I do not usually install from source code. I am not very confident about doing that. But I had no problem thanks to your instructions. The make install command came up with an error. I needed intltool installed. It was easy to fix and run make install again.

I can now record from Rhythmnbox playing an audio file or the web browser playing a radio program.

Thank you.

---

### Post by osmoma on 2013-08-14
Hello grahammechanical,
You compiled it from source. Very well done! 

You may also use the "build-dep" command to _install all dependencies __(and dev libraries) __automatically_. But it needs to access the source-code repository of the actual package. 
Do this:
0) Start software-properties-gtk
$ **software-properties-gtk**

1) And activate the package's Source Code repository. 
See this picture:
[[IMG]http://bildr.no/thumb/WjUxRnZk.jpeg[/IMG]]("http://bildr.no/view/WjUxRnZk")

2) Then update the package index and install all dependencies with apt-get build-dep. 
$ **sudo apt-get update **
$ [B]sudo apt-get build-dep audio-recorder 
[/B]
3) You can also download the source code with (run this without _sudo_ so you can edit the files as normal you).
$ [B]apt-get source audio-recorder

[/B]Notice: This will give you a source-snapshot of the package at compile time. Use "bzr" to download the most recent code files.


// moma

---

### Post by osmoma on 2013-11-25
[COLOR=#000000]The download numbers are just awesome.

$ wget [/COLOR][www.futuredesktop.org/getstats.sh]("http://www.futuredesktop.org/getstats.sh")
[COLOR=#000000]$ chmod +x ./getstats.sh 
[/COLOR]
$ lsb_release -sc
saucy

$ ./getstats.sh 
Counting 32bit downloads for saucy: audio-recorder 1.4-1~saucy 2350
Counting 64bit downloads for saucy: audio-recorder 1.4-1~saucy 2957
Total downloads: **5307**

$ ./getstats.sh raring
Counting 32bit downloads for raring: audio-recorder 1.1.2~raring 2315
Counting 64bit downloads for raring: audio-recorder 1.1.2~raring 3052
Total downloads: **5367**

$ ./getstats.sh quantal
Counting 32bit downloads for quantal: audio-recorder 0.9.8~quantal 6785
Counting 64bit downloads for quantal: audio-recorder 0.9.8~quantal 7992
Total downloads: **14777**

Thanks for using A.r. Go even more! 
The code is probably not tampered by NSA ;-)  
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

---

### Post by cariboo on 2013-11-25
Moved to Multimedia & Video as we are now in the Trusty development cycle.

---

