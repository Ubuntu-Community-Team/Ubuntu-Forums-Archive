---
title: "Huge delay when booting"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MeltyBlood on 2011-03-06
Hey guys I'm a total linux noob, installed natty because drivers for dwa-131 wireless don't work too good on maverick kernel.

So my problem is when natty starts to boot usb devices are turning off and on again and there is a huge delay before they turn on, then booting continues. I did not have this problem on 10.10 and I have no idea what is causing this.

Here's the bootchart _**[link]("http://img269.imageshack.us/img269/5325/epicnatty201103071.png")**_ (res is too huge to attach).

---

### Post by cariboo on 2011-03-06
We need details to be able to help, how many and what type of usb devices? Will your system boot without them?

---

### Post by ghostborg on 2011-03-06
I had the same problem and for me it turned out to be my Rosewill media card reader. I unplugged it from the motherboard and everything else started working. I would experience longer boot times and about 3-5 mins before my wireless mouse was recognized.
Jobs sent to the printer were even affected.
I didn't notice the problem until Ubuntu 10.10 64bit . I did not notice this problem in version 10.04 64 bit. Maybe my card reader went bad or maybe a driver issue.
I picked up on this from another topic in the Ubuntuforums with other people having this mysterious issue with various card readers.
If you don't have a card reader maybe another device is possibly the cause.
Hope my experience points you in the right direction.

---

### Post by MeltyBlood on 2011-03-07
Thanks for replies!

Started messing with usb ports, well I did disconnect all usb devices before, didn't help, but I completely forgot I have card reader that connects somewhere inside case lol, thanks again for pointing me out. 
After finally disconnecting everything system booted just like 10.10 (maybe [_**a bit slower**_]("http://img17.imageshack.us/img17/1706/epicnatty201103077.png"), but definitely not in 3 min). 
Well, assuming it was reader I just connected keyboard and booted again only to run into that problem again :( 
It seems something is wrong with the way usb controller work in natty. Here is my [_**motherboard specs**_]("http://www.asus.com/product.aspx?P_ID=GieCoWs1Eigeef6i"), tho i do have usb 3.0 controller i don't use it at all (it isn't even connected), just usb 2.0 one. 

Just before posting results of my struggle I tried bios usb option "usb legacy: disabled" It worked! 
System boots as before with all usb devices attached. Great :) Tho maybe not so?
What exactly does this option do? And why 10.10 boots just fine in legacy enabled state and natty not? :confused:

---

