---
title: "Best way to scan and sort multiple storage devices for duplicates."
date: 2009-05-22
forum: Multimedia Software
---

### Post by pastalavista on 2009-05-22
My first question here for a while. All I'm using now is Rhythmbox to sort and file my 20,000 or so random mp3 files. They're on more than 50 CDs of mp3 rips and downloads, a couple of old but kicking hard drives and my commercial collection of a couple of hundred or so. I know I have way too many copies and duplicates and want to be able to filter them out to copy to a new 1TB hard drive. 

My question is obvious.. what's the best (easiest/least time consuming) method to accomplish this? A simple free minimal GUI is preferable.. or even a bash script I could copy. Is there anything like that in open source? Some of the duplicate mp3s have had their ID tags changed. Can anything compare actual mp3 files as well as their titles and tags?

I hope this is the right forum to ask all this... I've searched a little and everything I've found is so tedious and time consuming.. or expensive and made for Windows... or Mac

---

### Post by chriskin on 2009-05-22
you can install fdupes.
it works via the terminal , and all you have to write is a command and it identifies all your duplicate files within the given folder - in your case the music one.

you can also add a letter or two you will find in the manual (i think it is -d) and it will delete automatically all but one of the duplicates
it doesn't search by name , but by file size and checks within the file, so you will not get two versions of the same song to suffer

that's the one i use, i don't know if there is another around

---

### Post by PGScooter on 2009-05-29
See the following thread for a script that is being developed specifically for removing music files:

[http://ubuntuforums.org/showthread.php?t=1125737](http://ubuntuforums.org/showthread.php?t=1125737)

---

