---
title: "Reading a DVD-RW Disk"
date: 2013-02-03
forum: Multimedia Software
---

### Post by MorrisMonkey on 2013-02-03
Apologies if this has been answered somewhere else.

I am steadily switching from windows to Linux and have 2 laptops with Ubuntu 11.10 and 12.04, and one with Linux Mint 14. they all have the same problem.

I save video recordings off  radio channels on my Panasonic dvd recorder, they are saved as videos but I only want the audio channel.

Under Windows:
I used to transfer them to a RAM disk and then edit the .vro file to split the audio from the video and then use Audacity to make a mp3

I started using Avidemux, the windows version, but it could only read the first recording in a .vro file, I think the .vro file does not have an end point recorded so Avidemux read to the first break in the file and stopped.

I switched to making my recordings on DVD-RW disks and Avidemux (Windows version) could read them perfectly and the process worked well.
Now I have switched to Linux, I  use the Avidemux (Linux version), I practised editing .vob files copied to the hard drive, again no problems.

So this morning I hopefully said goodbye to Windows, I copied some recordings off the Panasonic onto a DVD-RW disk, finalised it put it into the Ubuntu 11.10 laptop, cannot read the disk, tried other dvd drives, different Linux laptops, none of them could read the disk. The disk is OK in that it can be read in Windows.

I searched the internet to see if LInux could read DVD-RW disks but had no success, so I hope someone here can help me. Is there a way to make it work?

---

### Post by TheFu on 2013-02-03
A few questions:

Are any of the PCs that can read the disk under Windows also running Linux?  We need to remove hardware compatility from the list of issues.  Not all DVD readers handle +/-RW DVDs. Some only do -R, +R, -RW, or +RW disks. You'll need to know the specifics of your hardware.

Which file system is the DVD burned using?  You may need to specifically tell Linux to mount using THAT file system.  Check what Panasonic says in the Owners Manual.  Hopefully, it isn't some MS-only UDF file system.

You realize that 11.10 is not supported anymore, correct?

You know that grabbing the audio from most video files is really easy using mplayer, correct?  **man mplayer** will explain how. It is much quicker than point-n-click through a GUI.

Are there any warnings or errors in the system log files after you insert the DVD under Linux?  You can find them with:
$ **sudo egrep -i 'error|warning' /var/log/*log**

Please copy/paste any relevant errors.

---

### Post by MorrisMonkey on 2013-02-03
Thanks for the prompt reply and apologies for my slow one.

None of my computers are dual booting, they are either running Windows XP or some flavour of Linux.

I have 3 laptops running Linux:
one with Ubuntu 11.10 and Unity 2D, this computer is very slow and crashed when I installed 12.04, hence I rolled it back and I use it for testing new software packages.

The other 2 laptops are both dual core processors with 1 gb or more Ram and with reasonably big hard disks.
One runs Ubuntu 12.04 with Unity and the other runs Linux Mint 14 32bit with Cinnamon.

I have 2 external DVD writers that I can plug into any of the laptops or the two desktops  (still running XP)

My project is to convert to Linux and be able to do all my tasks without resorting to Windows, I am nearly there.

Video editing is the last big stumbling block.

I am only using DVD-RW disks as a means of transferring video material from the hard disk on my Panasonic DVD recorder to the hard disk on a computer, preferably running Linux.

Ram disks did not work, so I tried DVD-RW, the Panasonic also can copy to DVD+RW, but I have not tried that yet .

There is no information about the file system used by the Panasonic, but I have to format the disk on the Panasonic machine before being able to use it. If I look in properties in Windows and Linux for the finalised DVD-RW disk they both say "UDF"

All three laptops running Linux behave in the same way, the path opens, says DVD_Video_Recorder and shows the folder "Video_TS" it is greyed out, and if I try to open the folder Linux says ""could not display.........This file is of unknown type."

Thanks for the information about mplayer, I am new to video editing in Linux and any help and guidance is much appreciated.

Being able to use DVD-RW disks is not vital what is important is finding a way to move files from the Panasonic hard drive onto a Linux computer.
Thank you again for your help.

---

### Post by TheFu on 2013-02-03
The only things that I still do on Windows are 
* recording TV (Win7 MC)
* video editing

I've searched and searched for comparable Linux tools that accept comskip cut files, but none seem to support that. I am unwilling to give up on pre-marked commercial blocks in my editing.

I have not looked extensively, but you need to find a compatible UDF file system reader, then mount the optical drive using it.  [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD) has something about UDF inside it. Seems it requires drivers that are probably illegal to load where I live.

**$ man mount**

will explain how to mount UDF.  UDF is not on my 12.04 systems, but I've never tried to mount them recently either.

---

### Post by ortermagic on 2013-02-03
You could try Kdenlive, I can drag video files into the dropzone and easily rip the audio out. 
Perhaps i'm missing the point of the question tho?

---

### Post by MorrisMonkey on 2013-02-03
I do not know what this means...

The following has been tried only on the laptop with Mint 14 and Cinnamon.

I typed in mount -t udf

-this put an icon of a DVD onto the desktop,
-I left clicked on the DVD icon, the file manager opened with "Video_TS" greyed out
-I right clicked and amongst the options were "open as root"

I did not know what it meant, but tried it, it asked for my password and then the DVD folder opened with all the files eg vobs,ifo etc

I highlighted all the vobs and used the copy to option and copied them to the desktop. All the files were copied, and I closed the file manager.

But there were no files on the desktop.

There seems to be 2 desktops, Home>Kevin>Desktop with no vob files and Root>Desktop which does contain the files.

I could open the files into Avidemux, so I split off video and saved the audio to the desktop. The file was there with a padlock on it, if I then copied the file to Kevin>Music, the file no longer had the padlock.

I do not understand this, is it something to do with permissions?

I can get the files off the DVD but it is a long process, can you tell me what I am doing?

Thanks
I tried the man mount and man mplayer, I did not know about these commands, so thanks once again.

---

### Post by TheFu on 2013-02-03
**man** is the manual reader for UNIX and Linux systems. It is similar to Windows Help, but actually extremely useful.  If you've ever seen an RTFM - that is someone telling someone else to read the man page - what they are asking is inside it.

**man mount** - is the command to display the manual/help for the **mount** command.  You need to read and understand it to use it.  **mount -t udf **is not enough. There are many other options and you must have the UDF file system support loaded on your box.  Loading that support is illegal where I live, so I will not do that and cannot explain how to do it.

These are all terminal commands. You need to open a terminal FIRST.

It is very doubtful that there are permission issues, but you might want to understand permissions on Linux/UNIX now. This should explain: [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

Some DVDs are encrypted, so we cannot directly copy the files from them, but we can view and listen to them on common DVD players. It is odd for a home-created DVD to be encrypted, but we have no way of knowing what Panasonic does when they burn DVDs for you.

Copying an entire DVD should take 15-45 minutes, depending on your DVD drive speed and the speed at which the Panasonic device writes the data.

Sorry, but I don't use the GUI in Ubuntu very much, so I've never seen a padlock on any files and don't know what that means.

---

### Post by MorrisMonkey on 2013-02-04
My question should have been titled "how to read a disk with UDF format"

With Ubuntu 12.10 and Cinnammon I can get access to the root by right clicking on the computer icon on the desktop and I can then open the finalised -RW disk. I have to have elevated privileges to be able to open and view the contents of the -RW disk.

I cannot do this with Ubuntu 11.10 and 12.04 both with Unity as the options to open as root do not seem to exist. Perhaps I have to do it with a sudo command.
Can anyone help with this?

I did a search for UDF and Linux and the messages coming back seemed to indicate that the latest Linux kernel should support UDF, but there are many different versions of UDF so perhaps Panasonic use an unusual version?

---

### Post by TheFu on 2013-02-04
> **MorrisMonkey said:**
> My question should have been titled "how to read a disk with UDF format"

With Ubuntu 12.10 and Cinnammon I can get access to the root by right clicking on the computer icon on the desktop and I can then open the finalised -RW disk. I have to have elevated privileges to be able to open and view the contents of the -RW disk.

I cannot do this with Ubuntu 11.10 and 12.04 both with Unity as the options to open as root do not seem to exist. Perhaps I have to do it with a sudo command.
Can anyone help with this?

I did a search for UDF and Linux and the messages coming back seemed to indicate that the latest Linux kernel should support UDF, but there are many different versions of UDF so perhaps Panasonic use an unusual version?

If you need to use sudo to run any non-administrative program, then something is not setup correctly.  For devices, it usually means that your userid was not added to the correct group.  THAT is easy to change. I have no idea how to do it through a GUI or even which group it should be on your specific installs, but if you figure out which device is used to access the DVD, discover which group it has, then make certain that you are a member of that group, AND the group for the device has "rw" permissions, then everything WILL work.

As an example, on my 10.04 system, here are the permissions for the DVD/CDROM device:
```
brw-rw----+ 1 root cdrom 11, 0 2013-02-03 16:43 /dev/sr0
```
The **cdrom** group has **rw** permissions, so if I want to read or write to anything inside the DVD or CDROM, then I need to be a member of that group.

**man group** will explain how to add yourself to a group, if you have sudo rights.  You can check which groups to which you belong with the** id** or **groups **commands.

Sorry, I cannot help with the UDF side of this.

---

### Post by MorrisMonkey on 2013-02-05
How do I do this?

"When you find the solution, **please** come back to this thread, explain the solution, and mark it **SOLVED** to help the next guy. 			"

For me the solution is simple:

do not use -RW disk with my Panasonic recorder but instead use a +RW disk which can be read by Ubunbtu 12.10 with Unity and Linux Mint 14 with Cinnammon.

Can someone help with how to mark the thread  solved please.

---

### Post by MorrisMonkey on 2013-02-05
My wife said why don't you try the "Tools menu", thread is now solved, thanks for the help and the advice on man commands and mplayer.

---

