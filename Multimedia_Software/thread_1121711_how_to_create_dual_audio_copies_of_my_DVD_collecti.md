---
title: "how to create dual audio copies of my DVD collection?"
date: 2009-04-10
forum: Multimedia Software
---

### Post by jrz on 2009-04-10
I have a very large collection of DVD's, and would like to back them up digitally while they are in good condition. Our family is multi-lingual so I would like to retain 2 languages when available. I have seen some .avi copies of videos which had dual languages, but have not been able to find out how they were made.

Does anyone know what software is needed to make dual language copies of DVD's in a format that will play on a set top player? Most often we copy the videos we watch to a memory stick and watch them on the TV.

I'd also like something that would not be too complicated to use as I have nearly 200 DVD's.

Thanks for any help

---

### Post by Ares Drake on 2009-05-18
If space is available, you can just copy the DVD to a harddisk image file with the dd command.

Something like
```
dd if=/dev/dvdrom of=/path/to/your/colletion/dvdname.iso
```
should work, see
```
man dd 
```and
```
cat /etc/mtab
```
before you start.

If you want to convert it to say Xvid (which most set-top players with an DivX Logo will play) to save space I know only of one nice programm wit a graphic frontend: dvd2xvid [http://www.neoversum.org/](http://www.neoversum.org/)

Unfortunately the website is German and no ready-made Ubuntu packages are available, so you would have to compile. Maybe someone here can publish debs?

---

### Post by jrz on 2009-05-18
I have no problem making iso's, but would prefer to make avi copies with just 2 languages which would conserve disk space, and allow me to put several movies on a memory stick to watch on the TV. I've seen some dual audio avi's previously but haven't been able to find out how they were made, or if there is a Linux app capable of producing them.

---

### Post by Ares Drake on 2009-05-19
Dvd2xvid easily creates Dual-Language avi files in decent quality. Unfortunately I have no time right now to build ubuntu packages. I have tested it in suse linux though and there it works nicely.

---

### Post by jrz on 2009-05-20
I'll look into dvd2xvid. I hadn't heard of that program before. Thanks.

---

### Post by Ares Drake on 2009-05-22
I also found another nice program, which is a lot easier to install than dvd2xvid. It is called handbrake and you can download ready-made 32bit and 64bit ubuntu packages from here: [http://handbrake.fr/](http://handbrake.fr/)

The 8.10 packages work with 9.04 as well. Furthermore it does not only allow 2 languages in an xvid avi file, but also lets you use h264 in mkv-files as an option (though your set-top player probably wouldn't play the later).

---

### Post by jrz on 2009-05-22
I'm looking into that now. dvd2xvid appears to require visual basic run time and sounds like it must be made for Windows rather than linux. I prefer to avoid anything that requires something related to windows if at all possible.

Thanks much for your help as it seems you are turning up things I've not found at all, no matter how much I've searched.

---

### Post by jrz on 2009-05-23
I downloaded and installed Handbrake, and am now in the process of converting my 4th DVD. So far the copies made appear to fill my needs quite well, I have been able to reduce the size to around 700 MB, and include both Thai and English audio tracks. The video and audio quality remains quite good and the audio appears to remain in sync in each copy produced so far. 

Thanks very much, this is exactly what I was looking for and it appears to be made to order for Ubuntu.

---

