---
title: "nvidia 6200"
date: 2010-12-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-12-16
So I've been testing for several releases now, and i've decided to up the notch a little bit by trying to test on nvidia graphics on my desktop.  I have nvidia 6200.  On 10.04 live cd i need to select the nomodeset option for it to even work, but on 10.10 i don't need to do anything for it to work.

Now i have installed it a few times and have tried nvidia current and nvidia 173 only to have it stop working.  I've been using my laptop with intel graphics so i'm new to the nvidia side of things.

I have tried to use the left shift button to bring up grub menu for setting nomodeset to the boot string, but the left shift button doesn't bring up the grub menu.

any suggestions would be greatly appreciated.

---

### Post by cariboo on 2010-12-16
Holding the shift key at the right time, can be tricky, I had to do it on one of my systems, it took 3 tries before I saw the grub menu, on that system I have the cdrom set as first boot device, As soon as I see boot from cdrom on screen I hold the shift key down.

I have a couple of systems with on board 6000 series nvidia cards, I've used nvidia-current with no problems, except I have to use nomodeset in order to boot the first time, once the correct driver is installed you don't need it any more.

---

### Post by seeker5528 on 2010-12-16
> **cariboo907 said:**
> Holding the shift key at the right time, can be tricky

One advantage of the shift key is that you *can* hold it down without having to worry about filling up the keyboard buffer, so I just press it right away and hold it until I get the grub menu.

There may be some systems that don't like you touching the keyboard too early and as a result report a keyboard error or stuck key, but generally speaking it shouldn't be an issue.

Later, Seeker

---

