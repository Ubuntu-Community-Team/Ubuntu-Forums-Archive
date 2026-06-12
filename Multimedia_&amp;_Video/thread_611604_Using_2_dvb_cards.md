---
title: "Using 2 dvb cards"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by lowebb on 2007-11-13
Guys,

I've been working on getting 2 freecom dvb usb stick card working on my ubuntu mythtv deployment (NOT mythbuntu).

Getting the first going was easy but there seems to be a conflict when I attach a second. At boot up, 1 comes up fine but the other refuses to initialize. (I'll post the errors later after work). I can bring the second card online by hotplugging it and as a result will work via xine. Has anyone seen this before and could help me fix this issue so both cards are initialised on start-up. 

furthermore, Mythtv does some initialization at start meaning it doesn't do what it requires to initialise the second dvb card during hotplug. Does anyone know what this initialization is and how I could produce a work-around script? 

Currently my workaround is to watch both cards on boot up and when 1 initializes (seen by light on card), I quickly hotplug the other one. If done correctly this seems to allow time for mythtv to initialize both cards and I can again use both cards within mythtv

---

### Post by lowebb on 2007-11-14
no ideas guys. When I 'dmesg' I see the error

usb 3-2: device descriptor read/64, error -71

someone must have seen this!!

---

### Post by lowebb on 2007-11-15
Nope, apparantly only those with problems post here :)

---

### Post by keyz on 2007-11-16
Lowebb,
I have the same problem and am using two PCI cards. One with the Conexant cx23880 chipset and the other with a philips chipset. I can get them going independently but not at the same time. Did you find a solution anywhere ?
Regards
Keyz

---

### Post by keyz on 2007-11-16
see my post at
[http://ubuntuforums.org/showthread.php?p=3781420#post3781420](http://ubuntuforums.org/showthread.php?p=3781420#post3781420)

---

### Post by lowebb on 2007-11-16
Nope, what output are you seeing from dmesg? anything in /var/log/messages?

I believe whats happening mine is, the first card is coming up, the second is coming up, sees the first one, kills it (somehow), and the first is staying down until I hotplug it. 

Its really tiresome trying to fix it as I have tried any number of configurations and have been trying to work out some sort of workaround via a startup script. I'll keep this thread informed but as things stand it isnt looking good

---

