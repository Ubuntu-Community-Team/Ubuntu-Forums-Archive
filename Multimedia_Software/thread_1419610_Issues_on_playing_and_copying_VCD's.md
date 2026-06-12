---
title: "Issues on playing and copying VCD's"
date: 2010-03-02
forum: Multimedia Software
---

### Post by genothomas on 2010-03-02
Cannot able to playback VCD.
I cannot able to play VCD files directly from the 'MPEGAV' folder.
Before I can play VCDs from the Mplayer menu. But now, the player is also not working. I reinstalled it tried again, but no use. I then tried usin VLC, it was failure. I googled for this problem but I did not find any solution for this.

Again the problem with copying VCD files (AVSEQxx.dat).
I am unable to copy any vcd files to my system.I have tried many vcds and all of them are shiny new and not at all scratched. I got an input output error while copying them.
I also have a dual boot system with Windows XP SP2. I am however able to copy them on a windows operating system. And can then play the files by converting their extension from xx.dat to xx.mpg. I have read it at many places that this is a bug in all distro of linux, but I need to find a way on how to do this.

So please guide if possible,
Awaiting your answers.

Thanks and Regards.

---

### Post by genothomas on 2010-03-03
Will this issue solved in Ubuntu 10.04 (Lucid Lynx)..?

---

### Post by gordintoronto on 2010-03-10
> **genothomas said:**
> Before I can play VCDs from the Mplayer menu. But now, the player is also not working.


To get help, say, "I clicked on this, and then on that, and expected such and such to happen.  Instead, this other thing happened."

---

### Post by genothomas on 2010-03-14
> **gordintoronto said:**
> To get help, say, "I clicked on this, and then on that, and expected such and such to happen.  Instead, this other thing happened."

I have registered in Linux Mint forums, there i got a suitable answer for my thread.

The issue appears on Linux, but the problem is caused elsewhere
**This is the famous ongoing [COLOR=red]problem with vendor lock-in[/COLOR], that plagues the other OS's, like Linux or OS-X**
[http://www.linuxjournal.com/node/1000107](http://www.linuxjournal.com/node/1000107)

[LIST]Doesn't only affect media formats.. 
[/LIST]

[http://www.videohelp.com/play](http://www.videohelp.com/play)
[search.php?st=0&sk=t&sd=d&keywords=play+vcd+files]("http://forums.linuxmint.com/search.php?st=0&sk=t&sd=d&keywords=play+vcd+files")
**search on these forums..**

**VCD files Linux**
[http://linux.about.com/od/linux101/a/desktop06e.htm](http://linux.about.com/od/linux101/a/desktop06e.htm)
[http://codeidol.com/unix/linux-multimed ... Rip-a-VCD/]("http://codeidol.com/unix/linux-multimedia/Video/Rip-a-VCD/")

**Dat file extension..**
[http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html](http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html)

[LIST]About .DAT files.  **The ~600 MB file visible on the first track of the mounted VCD is not a real file! It is a so called ISO gateway, created to allow Windows to handle such tracks **(Windows does not allow raw device access to applications at all). Under Linux you cannot copy or play such files (they contain garbage). Under Windows it is possible as its iso9660 driver emulates the raw reading of tracks in this file. To play a .DAT file you need the kernel driver which can be..
[/LIST]

---

