---
title: "No Sound, Asus P5Q Deluxe"
date: 2011-03-24
forum: Multimedia Software
---

### Post by Vektor67 on 2011-03-24
:confused:No Sound at all yet.Until this I'd been so impressed with how far Ubuntu has come, I'm still blown away at how, umm... Gui it is.  and user friendly, intuitive I thought I'd finally reached the moment in time where my new build (sandy clockbox, maybe tomorow) would never see windows, oh well. Hopefully my system specs showed up in my SIG.I performed all of the instructions given by lidex in this thread;[http://ubuntuforums.org/showthread.php?p=10594476#post10594476]("http://ubuntuforums.org/showthread.php?p=10594476#post10594476") They all completed successfully but to no avail. My sound come out through my motherboards spdif via fibre opotics to an Onkyo TX-SR503 Reciever. Asus does have a set of audio files/drivers for linux but they are from 2009 and I belive are now built into the 
kernal aany help very much apprciated.  thanks, Mike

---

### Post by lidex on 2011-03-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Vektor67 on 2011-03-25
Sorry it took so long to reply, I'd given up for a while. My alsa info has been uploaded to this link;
[http://www.alsa-project.org/db/?f=b474e4a3d87bd644fe62fe545046aef7b9175c50]("http://www.alsa-project.org/db/?f=b474e4a3d87bd644fe62fe545046aef7b9175c50")

I sure hope you can  help me, I'm finding Ubuntu to be so usable that I can actually see light at the end of the M$ tunnel

I'm in awe of all of this console work you guys do. Thats a whole lot of information I hope it holds the key to my troubles.

---

### Post by Vektor67 on 2011-03-25
Oh and not to double up on you but as long as we are interacting. One of the main reasons I tried out Ubuntu was the bevy of 3rd party programs to use to manage my new ipod touch. This is my first(almost certainly last) ipod I hate Itunes enough to install an entire operating system to get around it. Rhythmbox does not acknowledge my Ipods existance. Although just now I directed Rythmbox to scan removable media and the ipod chirped, that was it however.

---

### Post by Vektor67 on 2011-03-30
I still have no sound, could you direct me to a site that specializes in troubleshooting these issues? I'd sure like to get this running. Thanks, Mike

---

### Post by lidex on 2011-03-31
```
control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 39'
		comment.dbmin -5850
		comment.dbmax 0
		iface MIXER
		name 'IEC958 Playback Volume'
		value.0 0
		value.1 0
```

The 'IEC958' term refers to digital. The values here are set at zero. Try changing that via a mixer - I'd suggest gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

