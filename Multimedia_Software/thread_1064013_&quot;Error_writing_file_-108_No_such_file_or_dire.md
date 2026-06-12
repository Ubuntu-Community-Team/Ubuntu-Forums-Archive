---
title: "&quot;Error writing file: -108: No such file or directory&quot; - Nokia"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Vanslashington on 2009-02-08
I'm trying to transfer music from my computer to my Nokia 5310 XpressMusic (cell phone obviously)

It was working before, but now I get an "Error writing file: -108: No such file or directory".
It's strange, because I can transfer things from phone to computer, but not the other way around.

All I'm doing is dragging and dropping.
It didn't used to do this. If it helps, it started after I transferred some music from my brother's laptop.
Also, the name of the phone's directory seems to have been changed. Before, it was called Nokia- something. But now, it is "gphoto2://[usb:001,003]/". The filesystem type of the phone is now "gphoto2", and I'm not sure if it always was. I think this is somehow because F-Spot image-file transferer seems to think I have digital photos on my phone, and I don't. I let it go ahead and transfer whatever it wanted, but it just copied all of my music and still thinks I have uncopied photos. I then went and deleted F-Spot, but the problem persists.
I also tried what it said in this ([http://ubuntuforums.org/showpost.php?p=6231205&postcount=24](http://ubuntuforums.org/showpost.php?p=6231205&postcount=24)) thread, but it's no good.

I googled this, and found nothing valuable.
So if anybody can help...

---

### Post by pooja on 2009-07-21
I'm having the same problem. I can't transfer mp3s to my Nokia 5310 Xpress Music mobile phone. 

As soon as I plug in the phone through Nokia's USB cable, Ubuntu recognizes it as a digital photo camera (indeed it does contain some photos), but when I try to copy/paste an mp3 into the phone's "Music" folder, an error:108 message pops up. 

Also, Nokia's music file format is *.m4a. I installed "Gnac" to try and convert mp3s to the m4a format but again, when I try to copy/paste the converted files into the mobile phone, the system displays the same error-108 message.

I'm attaching two pictures to this post. Hope it helps to unravel this problem.

---

### Post by pooja on 2009-07-22
Surprisingly enough, when this morning I connected the phone to the PC it recognized it as an iPod! I don't know how this happened but the problem may be solved. Perhaps, when prompted, one must choose to open the device with Rhythmbox instead of F-Spot Photo Manager from the drop down menu (see 2nd picture in my previous post).

I also converted an mp3 to a *.m4a file with "Gnac" and then transferred it to the phone via Rhythmbox. Rhythmbox sees the phone as an iPod and an iPod icon appears on the side panel too. To transfer the track, I first added it to the Music library of Rhythmbox and then just dragged and dropped it over the iPod icon of the side panel.

Hope this helps others too!

---

### Post by pooja on 2009-07-22
There's still a problem with the .m4a file. 

Even though the mp3 file was bigger (~6MB) it lasted 4 mins, instead the m4a file is only 21 sec long though it's half the mp3's size. 
When playing the track on Rhythmbox, it gave no problems but once it was transferred on the phone it became corrupt. Hence, the nokia phone couldn't play it. 
To fix the issue I kept the mp3 file both on my pc and on the phone.

---

