---
title: "Save streaming video WMA 8?"
date: 2008-08-16
forum: Multimedia Software
---

### Post by WizMedic on 2008-08-16
Hello all,

I am somewhat new to Ubuntu. Been plying with it for about 4 months now and have a dual boot system on my Dell laptop.

My wife is taking an online nursing course and some of the classes are streaming video. There is no way to copy from the main page that I can see and my wife would like to keep each class video for a reference.

Is there a way with Ubuntu to copy the streaming video as it is playing? I am using Totem Movie Player 2.22.1 and the streaming format is WMA Version 8.

Any help would be grateful...

Rick

---

### Post by cor2y on 2008-08-16
Ok heres some options what you use.
 
1) Vlc, and mplayer can record video and audio streams.
Vlc via the gui or terminal and mplayer via the terminal.

2) Check the tmp folder in your System File Folder aka root (you can find it via nautilus) look there for all streaming video and audio and its a simple thing to copy it back to your home directory
Or
3) remove the totem mozilla webbrowser plugin and install the mplayer one, then simply save the stream (by right clicking by selecting save as) after it has all been streamed.
Or
4) Depending on how its streamed you can download it using wget or mimms, wget is a downloader amd mimms is downloader for asf.wma,wmv streams.
Wget is already installed by default in ubuntu mimms you will have to look for via synaptic, both are terminal based tools although there are several gui frontends for wget like gwget etc.

---

### Post by WizMedic on 2008-08-16
Hello and thanks for the reply...

I looked in the Tmp folder and did not find any files in there at all. Not sure if I am in the right folder. Dont know enough yet about getting into Root.

Will try and remove the totem mozilla webbrowser plugin and add the mplayer one. Still learning about installing program yet also.

Tried to copy the stream with Vista, but no luck. Think it might be encrypted or something......

Thanks again!
Rick

---

### Post by cor2y on 2008-08-16
sorry i wasn't clearer on the tmp video thing.
If its audio and video it will be in /tmp and it will probably have a funny name but if its vidoe or audio it will be visible by the icons that are used for video and audio files.

---

### Post by WizMedic on 2008-08-16
Thanks again...

That helped and found Tmp folder. The only file in there was /tmp/tmp.vFPFLh5717 and it has a big lock in the icon and wont play at all. Is that the encrypted file I found with Vista?

Rick

---

