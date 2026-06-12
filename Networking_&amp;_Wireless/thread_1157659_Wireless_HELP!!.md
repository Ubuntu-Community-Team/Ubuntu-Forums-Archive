---
title: "Wireless HELP!!"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by cacollins08 on 2009-05-12
Ok so i have a HP Pavilion Entertainment PC (its about 4 months old) and i am currently dual booting windows vista and ubuntu. There is a little touch button on my keyboard that turns the wireless lan on and off but ubuntu doesnt seem to recognize this button becase it doesnt do anything when i press it. 

So the the wireless internet in my house is found by the lan in my computer but only when i'm in vista...so i think what the problem is is that i dont know how to turn the wireless lan thing on in ubuntu so it can 'find the internet.' (for lack of better words) 

If anyone can explain how to do this or what you think my problem is that would be very helpful (also i am not that computer savy so you may have to dumb it down a bit) THANKS!!

---

### Post by wabbalee on 2009-05-12
you would probably need to enable your wireless functionality.
check 'system' -> 'hardware drivers' with a network cable plugged in.
if nothing shows up there then update your system first and after reboot check there again with the network cable still plugged in. It will probably (after enabling) want to download/install drivers for your hardware.

---

### Post by cacollins08 on 2009-05-12
how does one go about 'updating their system'? (just wondering i haven't tried either way yet)

---

### Post by Peter09 on 2009-05-13
Can you post the output of

```
ifconfig
```

and

```
lshw -C network
```

and

```
route
```

---

### Post by wabbalee on 2009-05-13
If you have Ubuntu then you can update using synaptic (system -> synaptic).

while you are in synaptic you may aswell enable all repositories (if you haven't already done so), you can find that in synaptic's menu: 'settings -> repositories'. place a tick in the all the boxes in the first three tabs (Ubuntu Software (not the source code one), Third-Party Software (not the cdrom one), and Updates) then hit 'close'.

then back in its main screen you click on 'reload' (let it do its thing), then on 'mark all updates', and then on 'apply' (and once more) and off it goes updating.

---

### Post by cacollins08 on 2009-05-17
thank's a lot wabbale that wokred!

---

### Post by wabbalee on 2009-05-18
Glad I could assist.

---

