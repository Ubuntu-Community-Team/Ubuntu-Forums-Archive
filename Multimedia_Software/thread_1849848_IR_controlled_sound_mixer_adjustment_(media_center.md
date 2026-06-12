---
title: "IR controlled sound mixer adjustment (media center style), suggestions?"
date: 2011-09-25
forum: Multimedia Software
---

### Post by ponga on 2011-09-25
Grettings! I am hoping that someone can offer a suggestion here:

I am setting up a media center of sorts using Natty. Basically, I want an IR remote control to turn the gnome / alsa /pulse mixer volume up or down, etc.

I've been down this road before with MANY hours put in to getting the IR device (I'm using USB-UIRT) working, LIRC to talk with that device, getting the codes from the remote, making a script within LIRC to do stuff from a shell, etc... MANY hours in getting that going.

Now with this new box a couple years latter since I've last messed with IR+Linux, I'm hoping someone would know of a more sensible (and time saving) way to getting this going...

TIA,
--ponga

---

### Post by Bradburts on 2011-10-05
Me too! 
The review of this looks promising, he says he got it working on Ubuntu in minutes, should only take me 3 days then.
[http://www.amazon.co.uk/HDE-Wireless-Remote-Control-Mouse/dp/B001M56DI0/ref=pd_cp_ce_3](http://www.amazon.co.uk/HDE-Wireless-Remote-Control-Mouse/dp/B001M56DI0/ref=pd_cp_ce_3)
 
Post what you used in the end.
 
EDIT:
Not a great choice. irw does not detect anything from this remote or any other remote using the receiver.

---

### Post by Bradburts on 2011-10-12
Tried another USB port and the device works.
 
irw picks up alpha characters, mouse etc. 
The IR receiver does not work with any of my other remotes however.
Also I cannot see anything on irw when I use volume up. Volume down shows control codes.

---

