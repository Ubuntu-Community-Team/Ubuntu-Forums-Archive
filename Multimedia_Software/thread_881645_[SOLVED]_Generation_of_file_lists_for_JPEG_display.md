---
title: "[SOLVED] Generation of file lists for JPEG display on TV (XML or Command Line solutio"
date: 2008-08-06
forum: Multimedia Software
---

### Post by Roelski on 2008-08-06
Hi all,

I’m revering to the Ubuntu community with a specific question regarding listing and exporting directory contents and the order of files in a directory.

**The Problem:**
I bought a nice Philips FlatTV a couple of months ago that can display pictures from a USB-stick.  Excellent, but the main problem is that the files on the USB-stick are read based on directory entry.  My € 1.000 television does not have the ability to sort the files automatically, I was told by customer support.

After a phonecall of almost an hour, they came up with the following.  It’s possible to determine the order of the pics if a “album-file” (.alb extension) is created.  This is based on standard XML as below:

```

<?xml version="1.0" encoding="ISO-885h9-1" ?> 
<philips-slideshow version="1.0" > 
  <title>Title of the slideshow</title>
<audio>audio_url</audio>
<slide-duration>30</slide-dura¬tion> 
  <slides> 
    <slide>pic_1.jpg</slide> 
    <slide>pic_2.jpg</slide> 
    <slide>pic_3.jpg</slide> 
    ... 
    <slide>slide_N_url</slide> 
  </slides>
</philips-slideshow>

```

Pic_1.jpg and so on being the jpgs in the same folder as where the .alb-file will be located.

**My First Question:**
Is there a convenient and easy way to generate such a file automatically?  E.g. via a series of commands in a terminal or via a script?  

Please bear in mind that I’ve no programming experience nor skills and Philips are not offering more help than the above. (Their argument was: it's not in the specs so we cannot help you any furhter...)

**My Second Question:**
After doing some research, I came to the conclusion that the jpg’s are shown in the same order as their directory entry / order.  Kai12 at LinuxForums seemed to have a similar issue with his MP3-player.  See here: [http://www.linuxforums.org/forum/linux-newbie/111044-change-order-files-directory.html]("http://www.linuxforums.org/forum/linux-newbie/111044-change-order-files-directory.html")

Would there be a similar solution for jpgs?

Any thought would be helpful to prevent me from throwing my brandnew tellie through the shop window of the first next Philips store… :)

Best regs,

Roelski
PS to moderators: feel free to move this post to a more convenient section if not posted properly

---

### Post by Roelski on 2008-08-08
All,

Problem solved thanks to the info I found on the following page: [http://www.murraymoffatt.com/software-problem-0010.html]("http://www.murraymoffatt.com/software-problem-0010.html")

Apparently, the order of the directory entries of the files is used rather than an alphabetical / numerical order.

The good part: there's a linux command line tool called "fatsort" that helps you to order the directory entries. See here: [http://packages.ubuntu.com/en/hardy/fatsort]("http://packages.ubuntu.com/en/hardy/fatsort")

Probably the better part: Windows users (yes, we support those too !) can do the trick with a tool called DriveSort: [http://www.anerty.net/software/file/DriveSort.php]("http://www.anerty.net/software/file/DriveSort.php"). 



Many thanks to both developers !

Regs,


Roelski,
Antwerp

---

