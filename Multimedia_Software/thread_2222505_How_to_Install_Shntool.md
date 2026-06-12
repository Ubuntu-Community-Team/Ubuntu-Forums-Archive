---
title: "How to Install Shntool"
date: 2014-05-06
forum: Multimedia Software
---

### Post by cicada2 on 2014-05-06
I am new to all this command line stuff. I grabbed shntool (3.0.8) to help with music (flac & shn conversion)... now in the "Downloads" folder. But, just cannot figure out what to do next. Something to do with 
% ./configure
% make
% su -c "make install"
 
I have lots of flac files that I want to convert to CD... eventually will burn to CD. 

Hopefully, I will be able to use my existing burner (LG with Nero software). 

I have just installed Lubuntu for the first time. Thanks in advance for your patience!

---

### Post by Christopher_Clark on 2014-05-06
Hello, you can actually install shntool from the software center, or from a terminal window with the following command:

sudo apt-get install shntool

If you have any more questions just ask.

---

### Post by cicada2 on 2014-05-07
I did the install from the terminal window. Thank you!! I feel pretty helpless. How do I convert Flac to WAV? For example, I have a folder containing flac files along with checksums and info.txt...

---

### Post by Christopher_Clark on 2014-05-07
I'm not familiar with shntool but you can view the manual page for it in a terminal by typing:

man shntool

If you're new to linux it would probably be easier to use something like Sound Converter

sudo apt-get install soundconverter

it is a GUI tool for converting audio files.

---

### Post by Yellow Pasque on 2014-05-07
flac -d will automatically check md5sums:
```
sudo apt-get install flac
flac -d file.flac
```

sox and avconv are also good utilities.
I think the only thing I've used shntool for is splitting flac's from a cue sheet, and I now use a program called flacon for that since it's easier and supports more formats.

---

### Post by cicada2 on 2014-05-17
[SIZE=2]Thanks to Christopher_Clark & Temujin ^^

I have success using the terminal window to navigate to the drive where all my audio files are located. I got to the folder containing about 14 FLAC files that i want to convert to WAV. After reading the shntool manual, I am lost. What's next?
[/SIZE]

---

### Post by Yellow Pasque on 2014-05-17
I'm not sure why you insist on using shntool. The flac decoder/encoder makes it easy (and checks for errors). Navigate to the correct directory and run:
```
sudo apt-get install flac
flac -d *.flac
```

You will now have 14 .wav files...

---

### Post by cicada2 on 2014-05-17
Thank you.The Flac decoder works perfectly.

Is there an easy way verify the checksums - ffp, md5 & st5 are the ones I use all the time. It looks like I might have to generate new ones and then compare them to the checksums sent with the audio files (manually). Is the anything that will do this automatically?

---

### Post by Yellow Pasque on 2014-05-17
Let's say you have a file named sums.txt in this format: [http://releases.ubuntu.com/14.04/MD5SUMS](http://releases.ubuntu.com/14.04/MD5SUMS)
Then:
```
md5sum -c sums.txt
```

---

