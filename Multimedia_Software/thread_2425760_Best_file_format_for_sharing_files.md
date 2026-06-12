---
title: "Best file format for sharing files?"
date: 2019-08-29
forum: Multimedia Software
---

### Post by jacatone on 2019-08-29
I'm using Ubuntu Mate 18.04 LTS. I can copy files from my Ubuntu HDD to a flash drive with NTFS OK, but when I try copying them to a Windows machine and playing them they're all messed up. Apparently, I can't use ext4 to copy to Windows. Anyone know an answer?

---

### Post by Autodave on 2019-08-29
I use NTFS on all my shared flash drives w/o a problem.  What do you mean when you say that they "are all messed up"?

---

### Post by vanadium on 2019-08-30
Indeed, the error is somewhere else. For years I am using an ntfs removable disk to play video files on a TV without any issues. File systems need to be in a healthy state. You should check your file systems from time to time and always be very careful in removing removable media from a computer or other device.

---

### Post by TheFu on 2019-08-30
I've never seen any issue with this as described.  Check the system log files for other problems.
Flash drives do wear out.  What are the file types involved? There are media types that Windows doesn't support without addon codecs.

How are you copying from ext4 to Windows?  Act like we are 5 yrs old and please provide the steps.

---

### Post by Morbius1 on 2019-08-30
> **Autodave said:**
> I use NTFS on all my shared flash drives w/o a problem.  What do you mean when you say that they "are all messed up"?
I agree. The meaning of "all messed up" would be quite helpful.

Can you give us an example - from Linux - of a file that gets messed up when you try to access it from Windows.

Linux has a wider set of allowed characters than windows when it mounts an NTFS partition. When Windows tries to read them it gets all discombobulated. THere's a parameter that prevents the saving of those files with those caracters during an ntfs mount in Linux:
[TABLE]
[TR]
[TD="colspan: 2, align: left"]**windows_names**[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]This option prevents files,  directories and extended attributes to be created with a name not  allowed by windows, either because it contains some not allowed  character (which are the nine characters ” * / : < > ? \ | and  those whose code is less than 0x20) or because the last character is a  space or a dot. Existing such files can still be read (and renamed).[/TD]
[/TR]
[/TABLE]

---

### Post by jacatone on 2019-08-30
I meant the video is stepping and the audio is out of sink. Seems mkv files work fine when played or copied in Windows. Other formats like avi and mpeg4 have problems. When I use a video converter program to change them to mkv, they play OK. Must be some kind of issue with codecs in Ubuntu.

---

### Post by TheFu on 2019-08-30
> **jacatone said:**
> I meant the video is stepping and the audio is out of sink. Seems mkv files work fine when played or copied in Windows. Other formats like avi and mpeg4 have problems. When I use a video converter program to change them to mkv, they play OK. Must be some kind of issue with codecs in Ubuntu.

avi, mkv, mp4 are all "containers", the video codec and audio codecs inside aren't fixed.  There is no need to transcode either avi or mp4 files to have them placed into an mkv container.
install the mkvtoolkit and either use the GUI program or **mkvmerge**:

```
mkvmerge -o file.mkv   file.avi
```
It is as fast as a file copy.
```
mkvmerge -o file.mkv   file.mp4
```

The root issues is most likely poor MSFT codecs for the specific vcodec and acodec inside the files and has nothing to do with the container used.  You'll see when you change a few files into the mkv container. It won't help with the playback issues.

Once the are in the mkv container, you can easily see the codecs used by using the **mkvinfo** program.  There are avi codecs that were substandard.  Lots.  Transcoding those files into h.264/aac will loose some quality, but can also drastically improve playback.

To transcode the video to h.264, something like:
```
 ffmpeg -i "$IN" -c:v libx264   -crf 19.5   -c:a libvorbis -q:a 6  "output.mkv"
```
is probably easiest.

---

### Post by SeijiSensei on 2019-08-31
The standard audio and video codecs for AVI files were mp3 and mpeg4.  What player are you using in Windows?  Try this: [https://www.smplayer.info/en/downloads](https://www.smplayer.info/en/downloads)

---

