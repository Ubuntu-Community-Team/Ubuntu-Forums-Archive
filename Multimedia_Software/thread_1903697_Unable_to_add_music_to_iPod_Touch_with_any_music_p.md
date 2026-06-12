---
title: "Unable to add music to iPod Touch with any music player. Tried everything I've seen."
date: 2012-01-03
forum: Multimedia Software
---

### Post by StormageddonDarkLordOfAll on 2012-01-03
I've been completely unable to add any new music to my iPod Touch since  switching to Ubuntu, and I've looked all over for an answer, but I'm  still clueless. I've tried Banshee, gtkpod, Rhythmbox, (most  recently, after some advice I read on the forums tonight) Clementine, and maybe some other players, and nothing works. I've tried everything I've seen here, and no luck. It  seems that there's a problem with the iPod mounting (it doesn't appear on my desktop, and some of the music players sometimes give an error message about mounting,) so I tried  installing libimobiledevice as reccomended  [here]("http://ubuntuforums.org/showthread.php?t=1770199"), but it doesn't seem to have helped.

I am using a rather old iPod - this is one of the first iPod Touches (that's somehow still working.) Could that be the source of the problem?

I have no idea why this isn't working. Honestly, I know I have a lot to learn and I'm probably not giving much information to work with, but if there's something you need me to do so you can help, please let me know.

---

### Post by I_can_see_the_light on 2012-01-03
Some devices let you change the way they announce themselves to the system. Is it possible to do that from within your iPod? I'm guessing it's in 'MTP' mode - try changing it to 'mass storage device' or something like that.


**Edit **
It should work ootb: [https://help.ubuntu.com/11.10/ubuntu-help/media.html#music]("https://help.ubuntu.com/11.10/ubuntu-help/media.html#music")

This is old documentation but might work anyway: [https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by neu5eeCh on 2012-01-03
What have you switched from Ubuntu *from*? Was it Windows or a different distro?

Anyway, I was just fiddling around with PlayonLinux - a Wine variant like Codeweavers. They offer Itunes 7 and Itunes 10, I think. Haven't tried it, but can't hurt to give it a spin.

---

### Post by wolfen69 on 2012-01-03
Ipods can be hit or miss in linux. You could always install windows in virtualbox, or just get a used android phone on craigslist (they make great portable media players)

I bought a used Samsung Galaxy S for $25, and it does everything my ipod touch did and more, and does drag and drop in linux. I don't even use it as a phone. Well worth it. My .02

---

### Post by StormageddonDarkLordOfAll on 2012-01-03
So I have the problem solved. Kind of. See here: [http://www.reddit.com/r/linux4noobs/comments/o0xvt/unable_to_add_music_to_ipod_touch_with_any_media/](http://www.reddit.com/r/linux4noobs/comments/o0xvt/unable_to_add_music_to_ipod_touch_with_any_media/)

Basically, I got it working with Amarok, but at some point, everything else on my iPod was deleted. Going to have to move all of my music over from my Windows partition/maybe wipe Windows, have to wait until I can borrow an external hard drive or USB adapter to do that. Going to have a tiny music collection on my iPod until then.

---

### Post by I_can_see_the_light on 2012-01-04
If you feel the problem has been solved then please change the status of this thread as solved. 

Just out of curiosity, did you have to do anything besides installing Amarok?

---

### Post by StormageddonDarkLordOfAll on 2012-01-04
I thought the problem was solved, but now it's officially unsolved. Amarok freezes up whenever I connect my iPod. It works fine for listening to music on the computer, but I can't use it at all with the iPod plugged in. Since Amarok was the only thing that worked for adding music, I'm effectively back where I started.

I'm not entirely sure what made it work, honestly. I had to play around with a few things to get the iPod to even mount. I think it was a combination of Amarok + getting the computer to recognize the iPod properly.

---

### Post by OGpmpdog on 2012-01-04
Hi!

Not sure you wanna hear this...but you are spending a LOT of time to try and move music on your TheirPOD.

Why not just save some time and pickup this player?

[http://www.amazon.com/SanDisk-SDMX22-004G-A57K-Sansa-Clip-Black/dp/B005FVNGRS/ref=dp_ob_title_ce](http://www.amazon.com/SanDisk-SDMX22-004G-A57K-Sansa-Clip-Black/dp/B005FVNGRS/ref=dp_ob_title_ce)

Ubuntu simplifies music management...All you have to do is plug the above player in, and proceed to drag-n-drop...I still cant understand why the apple world finds it cool to go to a website to move music.

Welcome to Ubuntu and Happy New Year.

---

### Post by StormageddonDarkLordOfAll on 2012-01-04
1) I've had this thing for years - a long time before I switched to Ubuntu - and, except for the compatibility problems, it's still working perfectly. I don't really want to spend the money to replace a functioning device. Besides, it's not like I'm giving Apple any *more *money by continuing to use something that was paid for a long time ago. ;)

2) I want to learn more about Ubuntu and be able to fix things on my own. This is pretty frustrating, yes, but it's a learning experience.

I'll keep other players in mind when I eventually need a new one, though.

---

### Post by I_can_see_the_light on 2012-01-05
You could try installing **ifuse** from the Ubuntu software center. It says that its in an experimental stage but it could be worth a shot.

---

