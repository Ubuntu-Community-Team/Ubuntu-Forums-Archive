---
title: "Program doesn't find mounted iso"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by Jonas_Henricsson on 2006-11-13
I'm trying to run a program, a chinese learning tool, which is made for Windows and Mac. I was able to install the program, however the program can't find the lessons which are located in an .iso file. I mounted this file using :

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

I can see the mounted .iso on my desktop. However the program still does not find the lessons. Any ideas what the problem might be?

Thanks in advance!

/Jonas

---

### Post by taurus on 2006-11-13
```
xine dvd://mnt/iso
```
Otherwise, what is the output of this command?

```
ls -la /mnt/iso
```

---

### Post by Jonas_Henricsson on 2006-11-13
> **taurus said:**
> ```
xine dvd://mnt/iso
```
Otherwise, what is the output of this command?

```
ls -la /mnt/iso
```


Hmm.. The second line gives the answer that there is no such file or catalogue. 

The first line starts a program and I get the error message "There is no input plugin available to handle 'dvd://mnt/iso'. Maybe MRL syntax or file/stream source does not exist."

Should I create such a folder?

---

### Post by taurus on 2006-11-13
What is the output of this command then?

```
df -h
```
Remember, you need to mount your ISO first before you can view or see it!!!

---

### Post by Jonas_Henricsson on 2006-11-17
> **taurus said:**
> What is the output of this command then?

```
df -h
```
Remember, you need to mount your ISO first before you can view or see it!!!


The output of that command is :

jonas@ubuntu:~$ df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/hda1              16G  9.7G  4.7G  68% /
varrun                252M  104K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdd              512M  512M     0 100% /media/cdrom-1
/media/cdrom-1/Rosetta Stone - Chinese I 01-08 v3.1.iso
                      386M  386M     0 100% /media/iso


So last in the list the CD is mounted. The commands I've used are in the first message of this thread. Are they not correct? 

I can see the iso-folder on my Desktop. Still, however, the program does not find the lessons.

Thanks for any help!

/Jonas

---

### Post by taurus on 2006-11-17
```
xine dvd://media/iso
```

---

### Post by Jonas_Henricsson on 2006-11-17
> **taurus said:**
> ```
xine dvd://media/iso
```



If I type that command, Xine starts running and I get the error message "There is no input plugin available to handle 'dvd://mnt/iso'. Maybe MRL syntax or file/stream source does not exist."

Hmm, I'm starting to feel really stupid here... What am I doing wrong?

/Jonas

---

### Post by taurus on 2006-11-17
> **Jonas_Henricsson said:**
> If I type that command, Xine starts running and I get the error message "There is no input plugin available to handle 'dvd://mnt/iso'. Maybe MRL syntax or file/stream source does not exist."

Hmm, I'm starting to feel really stupid here... What am I doing wrong?

/Jonas
Are you sure you typed "xine dvd://media/iso" not "xine dvd://mnt/iso"???

---

### Post by Jonas_Henricsson on 2006-11-19
Oh, sorry, yeah. I did actually. The error message in the last post I just copied from an earlier post in the thread, so it wasn't entirely correct. I tried xine dvd://media/iso, but I the same error message in the program and the following error message in the terminal window:

jonas@ubuntu:~$ xine dvd://media/iso
This is xine (X11 gui) - a free video player v0.99.4.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.

Got any other ideas? This should be able to work somehow...



> **taurus said:**
> Are you sure you typed "xine dvd://media/iso" not "xine dvd://mnt/iso"???

---

### Post by gubemton on 2007-11-09
I know I'm a little late, but I need some help with this issue, too.

I think i'm trying to use the same DVD mentioned above, It's a Rosetta Stone multi-language dvd.

It is _not_ just a DVD video, which is what one guy was trying to get at (with the xine thing).

It is a program that displays a set of pictures on the screen, and plays its own sound files (each file is a sentence spoken in some other language), and the user is supposed to click on the picture that corresponds to the sentence that was just spoken.

The problem is that, though WINE is capable of running the DVD's autorun.exe program, It does not find the necessary files to feed the program.

Does anybody know how we could possibly get the program to find the necessary files?

Help is greatly appreciated.

Thank you

---

