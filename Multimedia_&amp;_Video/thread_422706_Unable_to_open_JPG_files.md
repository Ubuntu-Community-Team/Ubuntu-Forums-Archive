---
title: "Unable to open JPG files"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by gewitty on 2007-04-25
I have a large collection of JPG photos which I have transferred from a Windows XP machine onto my Ubuntu system. The problem is that although they seem to be OK as files, none of my Linux apps will open them. The most informative error message I get is from the GIMP. This gives me two error messages:

**JPEG image Message**

Not a JPEG file: starts with 0x50 0x4b
[B]
GIMP Message
[/B]
Opening '/media/disk/Photos/My Pictures/DDS/Three Towers 1230900.JPG' failed:

Plug-in could not open image


Other apps, such as Image Viewer, just throw up an error message saying 'Unrecognised image format'.

More recent photos that have been downloaded from a camera directly onto my Linux system work OK.

Anybody got any ideas as to what the problem might be?

---

### Post by Metacarpal on 2007-04-25
I did some quick googling and turned up info that "0x50 0x4b" is actually the header for a .zip file...

---

### Post by gewitty on 2007-04-26
You're right. They do appear to be zipped files. The odd thing is that they appear in the folder with ,jpg extensions. Each one is also a discrete zipped file, i.e. they are not all contained in a single archive which can be unzipped as a whole. This means that each file has to be individually unzipped, which is going to take hours as there are hundreds of them. I've had a look around to see if I can find a ZIP app that can handle bulk files, but so far haven't found anything.

---

### Post by Metacarpal on 2007-04-28
Use the command line.  (Pardon if you know how to do this, I'm assuming you've never used the terminal before, in case you haven't.  Don't want to tell you to do something without telling how!)  

First, move your zipped pictures to a directory by themselves (no other files present).  Open a terminal (Applications Menu > Accessories > terminal)
and move to the directory where you have the files.  For instance, if you copied the files to your "Pictures" folder in your home directory, enter this:
```
cd ~/Pictures
```
(~ is a shortcut for /home/*username*)
If you put them in a subdirectory under Pictures (let's call it "zipped" for the sake of this guide), make that:
```
cd ~/Pictures/zipped
```

Then, just type:
```
unzip *
```

That should do them all at one go.
It's a little strange that all of your image files are really zipped.  But since you're on linux now, you don't have much to worry about in terms of viruses or malware.

Best of luck to you!

---

### Post by gewitty on 2007-04-28
Thanks for the idea. Unfortunately, it doesn't work. There is something very strange about the files I'm trying to unzip. They were originally backed up from a Windows hard drive onto DVD. I have now transferred them back onto a USB hard drive running under Linux. Although they appear on this drive as individual files with the .jpg extension, when I unzip each of them individualy (the only way that works so far), I find that the unzipped version appears in a new nested set of folders which replicates the folder structure of the original Windows machine. This is hard to describe, but what happens is this: I start with a My Pictures folder on the USB drive. Opening this in Ubuntu shows me a set of apparently individual jpg files. When I unzip one of these files, e.g. disk-1/My Pictures/dog.jpg, I then get the unzipped version in a new folder structure like, disk-1/My Pictures/H/Photos/Dogs/dog.jpg. The H/Photos/Dogs folders which appear are a replica of the original Windows drive letter and folder structure. This is obviously why a batch unzip process will not work, because although the files each appear in Linux as individual jpg's, there is somehow a 'memory' of the old Windows drive structure attached to them. Weird.

---

### Post by Metacarpal on 2007-04-29
Ah, I'm starting to understand - did you use a backup utility to store the files to DVD?  If so, it probably saved the entire directory structure with each file, to ensure that it went back to the exact original location during a restore.  This allows for the restoration of individual files if they are lost, rather than having to restore the entire partition at once.

Unfortunately, yes, that's going to make unzipping them a massive pain in the butt.

EDIT:
Try this: if you have room to mass-unzip them all on the USB drive itself, you can copy only the jpgs themselves to your Pictures directory, again using command line.

(Note: after unzipping them, delete the zipped files, or those will be copied too.)

```
for PIC in `find /media/*usbdrivename*/`;do cp $PIC ~/Pictures; done
```

---

### Post by sappman2 on 2007-05-07
I was having the same problem downloading them directly from my camera.. I was attempting to download too many photos at once. IMy camera was shutting down half-way through the download from inactivity.  Taking the downloads from your camera in pieces of about 30 photos or less might help if anyone is having this issue.

---

### Post by gewitty on 2007-05-08
I'm pretty sure that Metacarpal has put his finger on the problem (sorry about that!). The files must have been backed up using something like Nero and have still got their original file structure data attached. I'lI give the bulk unzip idea a try,but I have a feeling I'm going to have to do this the hard way.

Thanks for all the help anyway.

---

