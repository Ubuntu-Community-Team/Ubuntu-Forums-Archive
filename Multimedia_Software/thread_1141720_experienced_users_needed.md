---
title: "experienced users needed"
date: 2009-04-28
forum: Multimedia Software
---

### Post by inobe on 2009-04-28
install xubuntu 9.04 last night "did updates"


i install the latest nvidia driver, did the restart and ended up in CLI.


tried to reconfiguring xserver-xorg !

well the output tells me xserver isn't installed :lol:

can anyone tell me what could have went wrong so that i can reverse the affects.


thanks :)

---

### Post by inobe on 2009-04-29
i still haven't touched anything, waiting to see if there is a good way to go about this.

:)

---

### Post by hansdown on 2009-04-29
Hi inobe.

Did you download the server edition?

Try ```
sudo /etc/init.d/gdm restart
```

---

### Post by inobe on 2009-04-29
it certainly looks like the server addition at the moment :lol:


no i didn't, it's xubuntu 9.04


:)

---

### Post by hansdown on 2009-04-29
Could you please try the command in my last post?

---

### Post by inobe on 2009-04-29
> **hansdown said:**
> 

Try ```
sudo /etc/init.d/gdm restart
```

it stopped gnome and restarted it in cli.

but no' no desktop.

edit: tried startx and get

```
/usr/bin/x11/x: not found
```

edit: bare with me, i am running from one computer to another :)

---

### Post by hansdown on 2009-04-29
Can you try ```
 sudo apt-get update
```

Then ```
sudo apt-get upgrade
```

---

### Post by inobe on 2009-04-29
it ran threw the mirrors on the first and the second said 0 upgraded and 0 to remove.

---

### Post by hansdown on 2009-04-29
Try resetting xorg.config.

```
sudo dexconf
```

---

### Post by inobe on 2009-04-29
i did a google for installing xubuntu desktop and did

```
sudo apt-get install xubuntu-desktop
```

then i got an error saying it couldn't continue, some errors about nvidia....

i figured if i removed a nvidia component i can try to install xubuntu, so i did

```
sudo apt-get remove nvidia-glx
```

that removed it, then did the first command again, it worked, that also installed xserver-xorg.


i appreciate the help and time hansdown :)


> Try resetting xorg.config.


yes at the start no matter what i did it said these things weren't installed.


ultimately when i installed the nvidia driver something uninstalled my desktop, i may never know why.

---

### Post by hansdown on 2009-04-29
Wow, that's good work inobe.

I was starting to sweat blood.

---

### Post by inobe on 2009-04-29
yeah' this was a weird situation, never experienced this.

---

