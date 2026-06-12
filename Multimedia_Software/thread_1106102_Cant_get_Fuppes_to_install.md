---
title: "Cant get Fuppes to install"
date: 2009-03-25
forum: Multimedia Software
---

### Post by bruceleeroy on 2009-03-25
I have a PS3 and I was using MediaTomb but it kept losing my directory's which in turn caused me to lose my mind a little.

I keep trying to install Fuppes but from the get go I get this output
after I type **sudo apt-get remove autoconf.**

```

chris@otacon:~$ sudo apt-get remove autoconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autoconf is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fuppes: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libmagick++10 but it is not going to be installed
          Depends: libsimage20 but it is not going to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not installable
[COLOR="Red"]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR]
```

I don't know what any of that means what am I doing wrong?

---

### Post by neu2buntu on 2009-03-25
looks like you have broken dependencies, do as your error says and run the command in terminal ```
sudo apt-get -f install
``` the -f options means fix broken ,then try and install your prog again

---

### Post by bruceleeroy on 2009-03-25
Ha that seems pretty obvious thanks man I am really new to this.

---

### Post by neu2buntu on 2009-03-25
post the output of any more errors as well as more info ie where you are installing from (source or whatever) and what distro you are running and what all you have done to this point. also include the instructions for the install if possible...ok

---

### Post by bruceleeroy on 2009-03-25
That worked perfectly thanks man!

One more question. 

In the instructions for install Fuppes he says this:

> The tricky part is getting a proper **fuppes.cfg** file in order. You can find a **fuppes.cfg** in the forums, but I modified mine so that I am NOT transcoding vids to my Xbox 360--again, no need to.

Here is my **fuppes.cfg** file. You will have to change to direct to your personal folders up top, and in network section set up to your ip addy and port. Just cut and paste my whole file over your whole file (after making a backup copy of yours in case it does not work), make changes in folder area and network area, and save it. Also, place this in your home/**your user name**/.fuppes directory (the hidden one again, Ctrl+h to toggle hidden folders). You will need admin rights to do this.

I cant find the fuppes.cfg anywhere I looked in my Home/etc and Home/ directories. Is there anyway I can open it from the terminal.

---

### Post by bruceleeroy on 2009-03-25
Ah man I dont know how you guys deal with this stuff. Everything is so difficult to fricken do its maddening.

---

### Post by neu2buntu on 2009-03-25
files starting with . eg .fuppes are hidden by default you can open it 2 ways 
1.use nautilus(your file browser) goto > places > home folder > click on "view" and tick "show hidden files" now you should be able to see it . open the file by right click and choose "open with text editor"
2. if the file is in your home directory you can view it by doing this command in terminal ```
gedit .thenameofyourfile
``` where .nameofyourfile is the file you want to edit ,make sure you save any changes eg the code you paste into it



i learn most of the stuff on this forum and reading linuxformat magazine and just generally asking "how to's" on the net:lolflag:

---

