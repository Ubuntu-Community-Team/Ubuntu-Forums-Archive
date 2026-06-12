---
title: "nubie - using the 'make' &amp; 'make install' commands"
date: 2009-01-05
forum: Mythbuntu
---

### Post by Peter Martin on 2009-01-05
I'm installing Mythbuntu 8.10. Some stuff is working. I've moved past the video card problems, and the tunners, now I'd like to get the sound working. After much searching I've downloaded a driver from Creative that should work with my X-fi sound card. It's a xxx.tar.gz file. I've moved it into my user dir 'Peter'. That's as high as I can get in terminal (where I get when I do cd by it self). It is the only file in 'Peter'

The readme says to: - cd to source dir.
                    - Execute make command as root
                        make
                        make install

I can't figure out how to do this?? (the make and make install)

Help is much appreciated Peter, I've been searching and reading all day and more.

---

### Post by Wobblybob on 2009-01-05
> **Peter Martin said:**
> 

The readme says to: - cd to source dir.
                    - Execute make command as root
                        make
                        make install

I can't figure out how to do this?? (the make and make install)

Help is much appreciated Peter, I've been searching and reading all day and more.

Open a [Terminal] and type cd Peter to get into your Home dir, if you then type ls you should get a list of the files in home one being the file you have downloaded. Now type into the [Terminal] tar -zxvf xxx.tar.gz which should create a folder called xxx. Now cd into that folder with the command cd xxx and then type sudo make, and enter your password when asked, then sudo make install.

Good Luck!

---

### Post by UltramaticOrange on 2009-01-05
Yea. This was one of my hang-ups when i was first starting in Linux. They give you half the steps and assume you know all the details.

Decompress, cd to, and install the files:
user@linux ~/Peter$ tar -zxvf xxx.tar.gz
user@linux ~/Peter$ cd xxx
user@linux ~/Peter/xxx$ sudo make
Password:
user@linux ~/Peter/xxx$ sudo make install

You can find out in detail what the flags on the 'tar' command (zxvf) mean by issuing the command 'man tar', but here's a rough idea: z=we're working with a 'gzip' file. x=extract the contents of the file. v=verbose (display, in detail, what the tar program is doing), f=the file name follows.

---

### Post by Peter Martin on 2009-01-06
Thanks for the help. The step I'd missed completely was the need to decompress the downloaded file. The only deviation from the excelent directions was the fact that the 'make' command did not require 'sudo' in front of it.
 So now the driver is installed and the audio card is partially working. Once I've figured out what is going on I'll be back to the forum for assistance. 
Thanks again for the rescue.

Peter

---

