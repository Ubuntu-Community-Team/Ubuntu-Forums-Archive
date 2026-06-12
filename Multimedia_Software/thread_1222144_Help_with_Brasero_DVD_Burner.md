---
title: "Help with Brasero DVD Burner"
date: 2009-07-24
forum: Multimedia Software
---

### Post by greymaus on 2009-07-24
I'm running 8.04 32-bit Ubuntu, with Brasero DVD burner installed and operating properly. I want to be able to use the DVD drive (/media/DVD+-RW) as if it is another hard drive; IOW, I want to put in a disk, enter/delete files at will, add to files already on the disk, or delete any part, or all, of the disk at any time.

Unfortunately, when I give the command to write to the disk, Brasero insists on "finishing" the disk and thus making it impossible to enter more data on it, or alter the disk in any way.  Is there a way that I'm overlooking to do what I described above?

---

### Post by ohzopants on 2009-07-24
The only way to permanently solve all Brasero problems is to run this command:
[code]
sudo apt-get install k3b
[\code]

I'm only slightly joking, of course.  I try to use native gnome apps as much as possible but Brasero is quite simply a terrible program, the KDE equivalent (k3b) is so much better.

CD/DVD-RWs have never, ever worked properly for me so I really don't have much experience with them.

On a more serious note, this thread explains how to setup DVD-RAM drives in ubuntu which sort of sounds like what you want to do:
http://ubuntuforums.org/showthread.php?t=11513

---

### Post by greymaus on 2009-07-24
Tried to reply earlier, forgot to log into the forum!  [[ggg]]

Thanks for your quick response. You've solved a major problem for me. I downloaded k3b and tried it out on a few short text files. Found that it allows adding new files to the disk in separate sessions, but doesn't allow adding new data to an existing file. There's probably a solution to that too, that I just haven't come across with only a half-hour's acquaintance with the program.

---

