---
title: "Ongoing Nvidia issues"
date: 2011-02-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-02-13
I have read a few threads on here recently about Nvidia users having trouble getting their systems to boot and getting scrambled displays. I wish I was having that much luck, ever since the X updates and nvidia driver issues I can't boot at all! My system gets as far as 'checking battery state' and then just hangs. It does however boot into safe graphics mode.

So I was wondering is my system broken somehow or are these people doing something I'm not? And does anyone know when these problems will be solved yet? It's been ages since I've seen unity and I'm beginning to forget what it looks like!

---

### Post by rburkartjo on 2011-02-13
mac i am sure they are working on it. i also have the nvidia drivers. dont forget the is only alpha2

---

### Post by macroshaft on 2011-02-13
Oh I'm not complaining, I was just making sure i hadn't missed anything. I hate the idea of assuming I should wait only to find out in 2 months my system was actually broken all along!

---

### Post by buzzmandt on 2011-02-13
[http://ubuntuforums.org/showthread.php?t=1675614](http://ubuntuforums.org/showthread.php?t=1675614)

---

### Post by VMC on 2011-02-13
> **macroshaft said:**
> Oh I'm not complaining, I was just making sure i hadn't missed anything. I hate the idea of assuming I should wait only to find out in 2 months my system was actually broken all along!

Try adding "nomodeset" to boot string to see if that enables you to boot up.

---

### Post by macroshaft on 2011-02-13
> **VMC said:**
> Try adding "nomodeset" to boot string to see if that enables you to boot up.

I'm not 100% sure of where to put this to be honest. I had a play and couldn't get any life out of it.

---

### Post by Quackers on 2011-02-13
During boot hold down the shift key to get the grub menu to show (if you only have one OS installed). Then, with Natty highlighted in the menu, press the "e" key. On the next screen, using the arrow keys, navigate to the end of the line that ends with "quiet splash". With the backspace key, delete those two words then type in nomdoeset and press ctrl + X (I think it is) to reboot.

---

### Post by macroshaft on 2011-02-13
> **Quackers said:**
> During boot hold down the shift key to get the grub menu to show (if you only have one OS installed). Then, with Natty highlighted in the menu, press the "e" key. On the next screen, using the arrow keys, navigate to the end of the line that ends with "quiet splash". With the backspace key, delete those two words then type in nomdoeset and press ctrl + X (I think it is) to reboot.

Aah, delete quiet splash. I didn't do that. This is one of those areas I know about but have to ask about or research every time I need it. I don't seem to soak up new information like I used to.

---

### Post by Quackers on 2011-02-13
I'm not even sure that deleting quiet splash is necessary. It's just that it seems to be done that way :-)
As for taking in new information - I know what you mean :wink:

---

### Post by macroshaft on 2011-02-13
> **Quackers said:**
> During boot hold down the shift key to get the grub menu to show (if you only have one OS installed). Then, with Natty highlighted in the menu, press the "e" key. On the next screen, using the arrow keys, navigate to the end of the line that ends with "quiet splash". With the backspace key, delete those two words then type in nomdoeset and press ctrl + X (I think it is) to reboot.

Well i tried it and got the error
> 
Booting a command list
alloc magic is broken at 0x7b8be7do
Aborted. Press any key to exit.

Thoughts anyone?

---

### Post by Quackers on 2011-02-13
That's new to me!
Have you tried more than once?

---

### Post by macroshaft on 2011-02-13
> **Quackers said:**
> That's new to me!
Have you tried more than once?

I have now, same result!

---

### Post by macroshaft on 2011-02-13
According to searches on google it's a grub issue, strange that I can boot into recovery then.

---

### Post by t1497f35 on 2011-02-13
I also have Nvidia, but I'm not installing the proprietary drivers cause I know they're too messy for now.
Do a clean install of a daily build and don't instal the proprietary Nvidia drivers until you see on this forum people reporting this issue is solved. Of course this way you can't use the 3D Unity but at least you can test/look at other stuff.

---

### Post by macroshaft on 2011-02-13
> **t1497f35 said:**
> I also have Nvidia, but I'm not installing the proprietary drivers cause I know they're too messy for now.
Do a clean install of a daily build and don't instal the proprietary Nvidia drivers until you see on this forum people reporting this issue is solved. Of course this way you can't use the 3D Unity but at least you can test/look at other stuff.

I'm not using the propriety drivers either and it would seem my issue is related to grub and not video drivers.

---

### Post by DukeBoxer on 2011-03-25
I was having the same problem, is there something that says "vt***=7" (stars stand for something I can't remember at the moment) after "quiet splash" in the grub boot menu? I deleted that and it boots fine. I have grub booting into text mode because I was having a lot of issues before with freezes, lockups and kernel panics (which might have gone away but I'm not sure) so that I could at least get to a command line so that I could try to fix something and I think that "vt" deal means virtual terminal 7, which would be the desktop, so it was getting stuck at the "check battery state" because it was being told to boot to text and also desktop at the same time (I'm not really sure this is the case, but it's what I invented in my mind...) Try that. I have an ASUS P7P55D-E Pro board, Intel Core i5 760 and an nVidia GTX460 card, which by the way I can't get more than 1024x768 resolution with natty (normal would be 1360x768 on a 32" Samsung 720p HDTV) which is the reason I found this thread in the first place. Good Luck!!

---

