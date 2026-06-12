---
title: "Why i cant play a sound?"
date: 2008-09-10
forum: Multimedia Software
---

### Post by kyme on 2008-09-10
my mp3 will play but it has no sounds, and my sounds or
  volume controller is disable..
  Help me how to put my sound... :-(

---

### Post by starcannon on 2008-09-10
Please open a terminal:

Applications>Accessories>Terminal

and run:
```
lshw -C sound
```

Then Shift+Ctrl+C (copy from terminal)the text that pops up.

then Paste it here.

---

### Post by kyme on 2008-09-11
It appears on this after typing the code.
> 
WARNING: you should run this program as super-user.


---

### Post by starcannon on 2008-09-12
you can run it as sudo or not, either way you have to wait a minute, it does a scan of all your hardware lshw{list hardware), the -C is a flag that tells it that we only want to read about a particular class of hardware, in our case sound.

anyway feel free to run it as superuser(sudo) and post the message that tells us about your sound card please.

```
sudo lshw -C sound
```

...strange that it didn't tell you anything other than the Warning message though...

---

