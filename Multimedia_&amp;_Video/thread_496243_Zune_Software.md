---
title: "Zune Software"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by nonmi9 on 2007-07-08
So, i need to set up my zune, for now i use Windows but only for my Zune, i so want to get rid of it, but can't seem to find something for linux...

---

### Post by Hork on 2007-07-10
Heh, I'm looking for this too.

---

### Post by hyrule_man on 2007-07-10
Well, you could try installing Zune software in Wine...... But at any rate, I have to ask? WTH did you buy a Zune if you have Linux? Lol. I woulda got a Zen Vision: M.

---

### Post by nonmi9 on 2007-07-10
i just got into linux, i really like it so i want to convert to just linux, so i bought the zune when i had windows...

---

### Post by nystud162 on 2007-07-23
ive read somewhere that you can use the zune software to run in vmware, but the tranfer rates are only usb 1.1 so its painstakingly slow...i have a zune and both my laptop and my pc are ubuntu im still looking for something better than usb 1.1. If you have a seperate windows pc lying around you can install the software and network the music from the ubuntu pc to the windows pc but besides that i dont think you can get anything faster than usb 1.1 as for now.

---

### Post by spartan777 on 2007-07-29
there is a open source library that would allow zune use cross platform, called libmtp, but it is only at the point where it can read the contents. who knows how long it will take for better support.

---

### Post by nonmi9 on 2007-09-09
so has anyone had any luck on  this?

---

### Post by zed41 on 2008-02-29
I don't know if any one has posted this yet, but I have been successfully using my Zune on linux with the USB 2.0. for several months now. I am using it under virtual box and had to manually change a file to activate the USB support. This has been posted somewhere on this message board, I can't find it at this moment,  after you have the USB support activated and Windows installed with the zune software it all depends on how you initiate virtual box to recognize the usb port the zune is attached to. plug the zune into your computer. You may notice that your media player recognizes it, close the media player. Now open virtualbox and start up Windows, after it has started open up the Zune software and you will notice that the main menu says attach? spelling? device. It is not recognizing a zune plugged in. From this point you can go to the bottom of the screen where the USB icon is, right click on it and it will bring up the USB devices that vitual box is detecting, and click on the one you wish to initiate, being the Zune player, and from this point it should now be recognized. 

Oh, the only way I could get the software to recognize my llibrary was having it on a fat32 partition and set up a samba shared folder, link that to the shared folder in windows XP and you should be good to go.

PS, being late I may have left out a step, but this does work.

---

