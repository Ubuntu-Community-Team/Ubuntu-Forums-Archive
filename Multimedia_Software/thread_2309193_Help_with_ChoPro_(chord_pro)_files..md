---
title: "Help with ChoPro (chord pro) files."
date: 2016-01-08
forum: Multimedia Software
---

### Post by blueb4sunrise on 2016-01-08
OK, so my freind has sent all our band songs as things called .chopro files which can be opened using gedit as a text file. After some googling I understand I need a program called 'chordii' to view them as sheet music. I read the instructions 3 or 4 times and have been fiddling about with the command prompt to try and make chordii work, but due to my lack of computing skills I simply can't make it work. Is there not a simple way of opening these files, a easy to use GUI or something? 

please help.

---

### Post by Bucky Ball on 2016-01-08
Please describe exactly what you are doing and where it is falling down. Are you attempting to use chordii to open the .chordpro files? What have you tried so far?

---

### Post by blueb4sunrise on 2016-01-08
If I open a .chopro file, it opens in gedit and looks like the attached screen shot. My understanding is if I want to view it as proper sheet music I have to use a program called 'chordii'. I installed it, but have found that it only works from a terminal. I read the instructions provided here> [https://ftp.fau.de/gentoo/distfiles/chordii-4.3-user_guide.pdf](https://ftp.fau.de/gentoo/distfiles/chordii-4.3-user_guide.pdf) ; I simply don't understand these instructions and can't make it work... i.e. what exactly does one type into the terminal to make the program come on? The instructions suggest that I type something like $ chordii -o name of file.sp name of file.chopro. It talks about arguments? what on earth does that mean? 

Is there a simpler program i can use to open chord pro files?

---

### Post by Bucky Ball on 2016-01-08
Try this. Navigate to the folder you have the .chopro file in, then:

```
chordii <filename>.ps <filename>.cho
```

Where <filename> is the name of your file, i.e. funkychoon.cho.

You could also try:

```
chordii <filename>.ps <filename>.chopro
```

Did you install chordii from the Ubuntu repositories?

---

### Post by howefield on 2016-01-08
Not that I know the program but reading the manual seems to say..

Assuming a chopro file in the Documents folder, use the following to produce a postscript file, (substitute the path and file name with your own)

```
chordii -o ~/Documents/house.ps ~/Documents/house.chopro
```

Then use ghostscript to open (or print to a capable printer) the newly created .ps file

```
ghostscript ~/Documents/house.ps
```

Edit : ninja'ed.

---

### Post by Bucky Ball on 2016-01-08
> **howefield said:**
> Edit : ninja'ed.

But you said it better. ;)

---

### Post by blueb4sunrise on 2016-01-08
Thanks for taking time to help me out. I know I could just ask for them in a different format but getting this to work on my pc has become a mission, lol. 

I tried as you suggest but I must be doing something wrong still, here is a screen shot. What is a ghost script?

---

### Post by howefield on 2016-01-08
> **blueb4sunrise said:**
> Thanks for taking time to help me out. I know I could just ask for them in a different format but getting this to work on my pc has become a mission, lol. 

I tried as you suggest but I must be doing something wrong still, here is a screen shot. What is a ghost script?

~/ at the start of the file path is a shortcut to /home/user/ so use one or the other, not both :)

~/Downloads is the same as /home/user/Downloads

Try navigating to the folder where your files are stored, might be easier for you as that way you will only need the file name in the chordii command.

Ghostscript will open the .ps file, it is in the Ubuntu repository, it was already installed on my system but I am not sure if it was installed with the default installation or as a dependency to a subsequently installed application. Either way, you'll find it in the Software Centre.

> GPL Ghostscript is used for PostScript/PDF preview and printing. Usually as a back-end to a program such as ghostview, it can display PostScript and PDF documents in an X11 environment.

Furthermore, it can render PostScript and PDF files as graphics to be printed on non-PostScript printers. Supported printers include common dot-matrix, inkjet and laser models.

---

### Post by blueb4sunrise on 2016-01-09
Ah OK, Thanks again. I understand a little more than I used to. 

I gave it another shot using "chordii -o ~/Downloads/Always Be The Same.ps ~/Always Be The Same.chopro". 

This was the output.



p.s. I Found an app for my phone that can open the files so the computer is no longer absolutely necessary, but it would be nice if I can get it to work.

---

### Post by howefield on 2016-01-09
Try this..

```
chordii -o '/home/neil/Downloads/Always Be The Same.ps' '/home/neil/Downloads/Always Be The Same.chopro'
```

Using the full path and escaping the spaces in the file name with single quotes. Does that create the ps file ?

---

