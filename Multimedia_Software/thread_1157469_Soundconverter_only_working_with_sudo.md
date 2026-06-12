---
title: "Soundconverter only working with sudo"
date: 2009-05-12
forum: Multimedia Software
---

### Post by Glendon on 2009-05-12
Since upgrading to Jaunty, Soundconverter has not worked. I can add a file to convert but then when I hit convert the Soundconverter window goes grey. I have to do a force quit. I ran it from the command line with the debug option but nothing appears when I hit convert. 

However, it does work when I run it with sudo. This means it's a permissions issue somewhere. 

My question is where would it have trouble writing? I've tried multiple output directories without success. I've tried multiple file formats without success.

Any ideas?

---

### Post by logos34 on 2009-05-12
> **Glendon said:**
> 
Any ideas?

did you try try reinstalling:

sudo apt-get remove --purge soundconverter

sudo apt-get install soundconverter

?

---

### Post by Glendon on 2009-05-12
Thanks for replying.

Yes, I reinstalled.

Initially I thought it was a gstreamer issue. I reinstalled soundconverter and all the gstreamer plugins. 

I also tried Soundconverter 1.4.3 (I'm on 1.4.1). No good.

---

### Post by logos34 on 2009-05-12
> **Glendon said:**
> However, it does work when I run it with sudo. This means it's a permissions issue somewhere.

My question is where would it have trouble writing? I've tried multiple output directories without success.

But do you have user write permission to (and ownership of) those output directories?  How and where is the partition mounting?

cat /etc/fstab

ls -l /dir/containing/music

---

### Post by Ericyzfr1 on 2009-05-12
Where is your output directory located at?

---

### Post by Glendon on 2009-05-13
Sorry for the slow responses. This is one of those do-it-when-i-can things.

Thank you very much for the help with this. 

When Soundconverter was working, I was writing back out to the original directory of the file being converted. Typically this was a directory in my home directory.

/home/me/music

When Soundconverter stopped working with my user I tried other directories to test whether or not the write permission had gotten borked. I tried my secondary internal drive without success. I also specified a directory in a temp directory in my home directory as well. I double checked the permisions and ownership of all the directories I tried. I also did a triple check by creating a new file in each target directory as well. Everything I tried tells me that I can write to my target directories. 

I'm wondering if there's a log file it's trying to write somewhere and can't?

---

### Post by Glendon on 2009-05-13
I'm using a work-around for now.

I just setup a custom launcher in AWN using gksudo as part of the command. 

It works.

---

