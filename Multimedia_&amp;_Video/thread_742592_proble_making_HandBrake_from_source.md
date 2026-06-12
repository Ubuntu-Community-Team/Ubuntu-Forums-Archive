---
title: "proble making HandBrake from source"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by jacob01 on 2008-04-01
i keep getting this error
 ```
make[1]: *** [../HandBrakeCLI] Error 1
make: *** [HandBrakeCLI] Error 2

```

i am trying to install HandBrake from source and i got this far after installing bjam and started to make the file.

---

### Post by rockstar on 2008-04-02
Did you download the 

Follow these instructions

[http://trac.handbrake.fr/wiki/CompileGuide](http://trac.handbrake.fr/wiki/CompileGuide)

When it talks about "Download Subversion" - you can find this in the synaptic package manager

---

### Post by jacob01 on 2008-04-02
ok cool i downloaded the svn and then made that file and i finally got the thing compiled or or made, so i then i tried to get the gui working but hit another snag i dont know if i really can fix it or weather i should wait until the gui comes out.

```
qhandbrake.cpp: In member function ‘void QHandBrake::encode()’:
qhandbrake.cpp:116: error: ‘struct hb_job_s’ has no member named ‘acodec’
qhandbrake.cpp:117: error: ‘struct hb_job_s’ has no member named ‘audios’
make: *** [qhandbrake.o] Error 1

```

thats the error i got help if you know what the problem is but dont worry about it if its a complicated fix.  thanks for the help and your time :)

---

### Post by ron999 on 2008-04-02
Hi
There is a GUI in a deb package.
From here:- [http://rippedwire.sourceforge.net/downloads.html]("http://rippedwire.sourceforge.net/downloads.html")

---

### Post by jacob01 on 2008-04-02
thanks:)

---

