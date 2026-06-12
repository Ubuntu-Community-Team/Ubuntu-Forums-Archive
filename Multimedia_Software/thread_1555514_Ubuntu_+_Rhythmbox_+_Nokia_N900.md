---
title: "Ubuntu + Rhythmbox + Nokia N900"
date: 2010-08-18
forum: Multimedia Software
---

### Post by nickpiggott on 2010-08-18
I'm using Rhythmbox on Ubuntu 10.04 (Lucid). I've got the N900 connected via USB in Mass Storage mode.

Initially, it failed to detect the N900 as a media player, but I've added a .is_audio_player file to the root, with a single entry of audio_folders=.sounds/

That's now finding the existing music on the N900. However, I can't transfer any music into the N900 - it's just doing nothing when I drag files over. (I'm trying to copy .mp3 and .wma over). If I copy the music using the File Manager on the desktop, it appears in the N900 Media Player and plays fine.

So it seems like it's a problem with the way Rhythmbox is seeing the N900.

The audio format description string for the N900 is extensive, and it looks like Rhythmbox can't parse it properly, as it's showing:

```
audio/3gpp,audio/3ga,audio/3gpp2,audio/amr,audio/x-ams,audio/mpa,audio/mp3,audio/x-mp3,audio/x-mpg,audio/mpeg,audio/mpeg3,audio/mpg3,audio/mpg,audio/mv4,audio/m4a,audio/aac,audio/x-aac,audio/mp4a-latm,audio/wave type
```

If I add a line to the .is_audio_player file that says

```
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg
```

then Rhythmbox shows the audio support as:

```
Ogg multimedia file
WIndows Media audio
MP3 audio
```

I can now drag files to the device, but it converts them to OGG, which the Media Player on the N900 doesn't support. 

If I remove the "application/ogg" from the formats, leaving just Windows Media and MP3, then it won't transfer again (even though it just needs to copy the files, not convert them).

So my questions are:

[LIST]
[*]How do I correct the audio formats supplied by the N900 / in udev so that Rhythmbox reads them correctly, removing the need to have an output_formats line in the .is_audio_player file
[*]What do I need to do to get Rhythmbox to just copy .wma and .mp3 files directly to the N900?
[/LIST]


Thanks.

---

### Post by nzjrs on 2010-09-07
Fixed here -

[https://bugs.launchpad.net/ubuntu/+source/media-player-info/+bug/632585](https://bugs.launchpad.net/ubuntu/+source/media-player-info/+bug/632585)

Please go and comment on the bug.

---

### Post by nickpiggott on 2010-10-01
I've been asked to do a HOWTO on how to fix this up, based on the bug fix above. This fixes the .mdi file for the Nokia N900, and I'm describing how to fix it on Ubuntu Lucid Lynx 10.04

1 - DOWNLOAD THE ZIP FILE CONTAINING THE FIXED MDI FILES
Click [here]("http://cgit.freedesktop.org/media-player-info/snapshot/media-player-info-660af20187ef6a76406c9de5de8f5d3c70cd2077.zip") to download it directly.

2 - OPEN UP THE ZIP FILE USING ARCHIVE MANAGER
Usually, if you've downloaded this in Firefox, it will offer to open it in Archive Manager directly. If not, save it to disk somewhere, then find it in the File Manager and double click it.

3 - FIND THE N900 MDI FILE
In the .zip file, double click on the folder **media-player-info-660af20187ef6a76406c9de5de8f5d3c70cd2077** then double click on the folder **media-players**
Find **nokia-n900.mpi **and right click it. Select "Extract...". Save the file to disk - it will usually save it into your home directory.

4 - MOVE THE FIXED N900 FILE TO THE RIGHT PLACE
On my install, the mdi files are at **/usr/share/media-player-info** .
You'll need to go into Terminal mode (from the desktop, click Menu -> Accessories -> Terminal)
```
cd ~
sudo rm /usr/share/media-player-info/nokia-n900.mpi
sudo mv nokia-n900.mpi /usr/share/media-player-info/

```If you get file not found errors, you might need to do
```
sudo find / -name nokia-n900.mpi
``` to find where its installed on your system, and correct the path above accordingly.

You should now have the fixed N900 file in the right location. and everything should work OK.

---

### Post by locknest95 on 2010-10-02
> **nickpiggott said:**
> 
```
sudo find / -name nokia-n900.mdi[/CODE

Is the above code supposed to look like this??? [CODE]sudo find / -name nokia-n900.mpi
```

---

### Post by nickpiggott on 2010-10-02
> **locknest95 said:**
> Is the above code supposed to look like this??? ```
sudo find / -name nokia-n900.mpi
```

Yep! I must stop writing things at 4am. I've corrected it, so well done for spotting that...

---

