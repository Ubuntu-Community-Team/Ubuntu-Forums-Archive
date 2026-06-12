---
title: "Issue with Gtkpod."
date: 2008-12-30
forum: Multimedia Software
---

### Post by Tom Waite on 2008-12-30
I am trying to put the music off my Ipod onto my hardrive because I just reformatted. I followed the instructions I found on google to install and use Gtkpod. It transfers some music but I get hundreds of errors saying the following:
> Template ('%o;%a - %t.mp3;%t.wav') does not match file type '/media/ASHLEY'S IP/iPod_Control/Music/F07/OEWC.m4a'
Failed to write 'Fall Out Boy-Honorable Mention'

Now that is one song, I have hundreds of these errors. I canceled the transfer until I can figure out what needs changing. Can anyone offer a hand?

---

### Post by pytheas22 on 2008-12-30
This is just a slightly educated guess, but do the music files that you're trying to copy have file-name extensions--in other words, is there a '.mp3' or similar appended to their names?  In the example you give, it doesn't look like there is, and I think this may be its problem.  I would try renaming one of the files and see if that helps.

If you have hundreds of files to rename, we could help you write a bash command to do it automatically.

---

### Post by Tom Waite on 2009-01-01
Yes. It says "OEWC.m4a". Which is the Apple code for Fall Out Boy-Honorable Mention lol. 

Renaming the file is going to be a tough one for me because I would need to go find OEWC.m4a within my Ipod's folders because GTkpod doesn't allow me to see file names or allow editing them.

Either way I don't think it is the file extension because .M4a is it.

---

### Post by Tom Waite on 2009-01-01
Okay I think I figured it out but don't know how to solve it. In the following menu:
[IMG]http://i197.photobucket.com/albums/aa217/Ipdking711/gtkpodScreenshot.jpg[/IMG]

Right now the "File Format" box is blank. When I typed in .m4a, it worked. I have multiple different file extensions(.m4a,.mp3, even some video formats) on my ipod. How do I all it to transfer all formats. I tried to type in ".m4a,.mp3,.wav" But it did not work.

---

### Post by pytheas22 on 2009-01-01
I'm not sure how to deal with the file-type issue, although perhaps googling would lead to a solution.

Before trying that, however, I wonder if you'd have better luck using Rhythmbox to manage the iPod.  You can launch it from Applications>Sound and Video>Rhythmbox.  Can you add music to the iPod that way?

---

### Post by Tom Waite on 2009-01-02
I can use rhythm box. But I want my music off my Ipod and onto my HD. I run dual boot XP-Linux and need to extract the music so I can listen, edit and enjoy in Windows. If I simply drag and drop the music, it copies it in the Apple code name files.

I appreciate the help:D

---

### Post by pytheas22 on 2009-01-02
Ohhh, sorry, I was thinking that you were having problems copying from your hard disk to your iPod.  I reread your original post (always a good idea) and see now that it's the other way around.

A quick workaround, although not a solution, would be to boot to Windows to copy the files, since you have a dual-boot.  You can [install drivers]("http://www.fs-driver.org/") so that Windows can access your Ubuntu partition, and you should already be able to access your Windows partition from Ubuntu (8.04 and up have read/write access for Windows file systems out-of-the-box) by selecting it from the Places menu.  So you can use iTunes in Windows to copy the music to wherever you want it to go, and still be able to access it from both operating systems.  Is this an acceptable solution?

If this doesn't solve the problem well enough for you, I can keep googling around to try to figure out a better fix, so please let me know either way.

---

