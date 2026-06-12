---
title: "bluetooth headset"
date: 2009-11-09
forum: Multimedia Software
---

### Post by timmson on 2009-11-09
Hello!
Try to use bluetooth headset on ubuntu 9.10. 
1. I use Blueman manager
2. I find my headset, connect headset service - success
But device doesnt appear here:
```
timmson@timmson-pc:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8240000 irq 21

```

---

### Post by walmis on 2009-11-09
It shouldn't appear there. Check pavucontrol. The new sink and source should be available there if everything connected successfuly.

---

### Post by timmson on 2009-11-09
Thanks.
I have checked pavucontrol, but sink didnot appear.

---

### Post by suyog on 2009-11-09
I was able to stream audio to my BT stereo headphones Nokia BH-501.

Please check in synaptic if you have pulseaudio-module-bluetooth.

This required. install it, then try again.

let me know how it goes?

---

### Post by timmson on 2009-11-09
big thx!
its works.

---

### Post by RedRat on 2009-11-09
is the "pulseaudio-module-bluetooth" module peculiar to 9.10 or is it available for other distros of Ubuntu, e.g., 8.04?? What repo is it in?

---

### Post by suyog on 2009-11-10
Its in main repo of karmic , I dont think its in earlier versions.
As you can see in following link.
[https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio)

---

### Post by suyog on 2009-11-10
Guys , anyone has tried to stream music from Phone to PC?
I tried , PC gets listed as Headphone,music plays but no sound from PC.
I see that in latest blueman, there are local services listed.
Advanced Audio Receiver - Experimental
Headset Emulation - Very Experimental

So I assume that these services are not stable now, may not work.

But anyone of you had any luck? Please let me know as I need this.

@Walmis, being developer of Blueman, can you suggest solution?

---

