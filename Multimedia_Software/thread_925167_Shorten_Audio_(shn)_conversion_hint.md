---
title: "Shorten Audio (shn) conversion hint"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Piraja on 2008-09-20
For all of us who have spent hours trying to figure out how to convert **Shorten Audio (shn)** files into other formats (e.g. **wav**), I found an efficient solution by [Forrest at a weblog titled "Adventures in Switching"]("http://adventuresinswitching.blogspot.com/2008/04/convert-shn-shorten-to-mp3-or-flac-in.html").

Here's a brief summary of the steps to be taken in converting Shorten (shn) to Wave (wav), with a few clarifying additions for us newcomers:

1. Install the **shntool** package using Synaptic or the command line option:

```
$ sudo apt-get install shntool
```

2. When you're done, you can try the command 

```
$ shntool conv -h
``` 

to get some information on the conversion options. Navigate to the directory where you have the shn files to be converted (i.e. input files), such as the Music directory in your home folder:

```
$ cd ~/Music/*your-input-files-folder*
```

Obviously, you need to replace "your-input-files-folder" with the name of the folder where your **.shn** files reside. 

3. Now you can try this command line argument:

```
$ shntool conv -o wav *.shn
```

The following is more or less the response I got, just like Forrest did:

```
shntool [conv]: warning: failed to read data from input file using format: [shn]
shntool [conv]:          + you may not have permission to read file: [jlc2003-02-14d1t01.shn]
shntool [conv]:          + arguments may be incorrect for decoder: [shorten]
shntool [conv]:          + verify that the decoder is installed and in your PATH
shntool [conv]:          + this file may be unsupported, truncated or corrupt
```

4. This means that you need to download the **Shorten codec source tarball** (shorten-3.6.1.tar.gz). Here's a link for that: 

[http://etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz]("http://etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz")

Choose "Save file" and your home folder as the location where you want to store the tarball. You can extract the contents to a folder of your choice (I created a "codecs" folder in my home folder), for instance by right-clicking the tarball folder in Nautilus and choosing "Open with Archive manager" and the "Extract" in the toolbar.

5. Next you need to install a couple of tools: 

```
$ sudo apt-get install libc6-dev g++ gcc
```

6. Navigate to the folder where your new codecs are stored (the "codecs" folder was my choice, as I mentioned earlier):

```
$ cd ~/codecs/shorten-3.6.1/
```

7. Compile and install the codecs as follows (type commands one by one, omitting the dollar signs, of course):

```
$ ./configure
$ make
$ make check
$ sudo make install
```

8. Now you can easily convert your **shn** files to **wav** files. Since the **wav** file format is default, all you have to do in your input folder is

```
$ shntool conv *.shn

```

This is more or less what you should see next:

```
Converting [jlc2003-02-14d1t01.shn] (0:35.65) --> [jlc2003-02-14d1t01.wav] : 100% OK
Converting [jlc2003-02-14d1t02.shn] (5:18.22) --> [jlc2003-02-14d1t02.wav] : 100% OK
...
```

9. If you want to have mp3 output, you can follow Forrest's instructions. I used SoundConverter to convert the Wave files into Ogg Vorbis format. SoundConverter is a powerful tool, since you can convert several files or a whole directory at once. (In KDE, it's Sound**K**onverter, of course...)

There's lots of good stuff around in the old Shorten file format, so it's a pity it isn't so widely supported and you have to use a command line tool. But luckily shntool is pretty easy to use.

Enjoy!

---

### Post by motoperpetuo on 2008-10-27
thanks! this worked great!

---

### Post by 666porcondissaum on 2008-11-23
Converting [101.shn] (12:24.00) --> [101.wav] :   6% ERROR
shntool [conv]: warning: error while transferring 131241600-byte data chunk -- skipping.


Got trouble. Help me.

---

### Post by Piraja on 2008-11-27
I'm sorry, I'm just another non-tech user myself. But here's some information on shntool: [http://www.etree.org/shnutils/shntool/](http://www.etree.org/shnutils/shntool/)

As you might know, Etree is also the place where you can download legal concert recording torrents in the Shorten Audio file format (as well as FLAC). That's why they also have this info on shntool. I quote:

> Who do I contact if I have any questions/comments/suggestions/patches/bugs/flames?

Send it all to <shnutils at freeshell dot org>.

---

### Post by prvngrnd on 2009-02-16
Perfect! Thanks!

---

### Post by Sunflower1970 on 2009-05-10
Hey all I'm trying to convert some .shn files I have. I've installed shntool, then tried to install shorten, but I'm having some trouble. I've followed the instructions above, and when I get to 

./configure

I get this error: "configure: error: cannot find sources (src/main.c) in . or .."

So I have to be missing something for making/configuring packages, but I don't know what. I've got libc6-dev g++ gcc all installed.

Anyone ever run into this before?

Thx!

---

### Post by otriades on 2010-05-14
Thank very very much !!! Thank you a lot !!! Not a great post, a PERFECT post !!!
People like you make me love linux world !!!
:guitar:

---

### Post by otriades on 2010-05-19
Today I converted another album (David Gilmour's first solo album, 1984) and I can't don't say thanks again...

---

