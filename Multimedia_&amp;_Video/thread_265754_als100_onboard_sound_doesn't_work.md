---
title: "als100 onboard sound doesn't work"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by almal on 2006-09-26
I have an older AMD-K6 based system with onboard sound (Avance als120 audio chip). Ubuntu 6.06 does not recognize any sound card.

I have followed the Comprehensive_Sound_Problems_Solutions_Guide and believe that I successfully compiled alsa-drivers from source.

I then went back to step 4 – input “sudo modprobe snd-”

The reply is --- FATAL: Module snd_ not found.

I tried “ sudo modprobe snd-als100” and I was able to access the alsa mixer and did get some audio but the application froze after a few seconds. After reboot I am right back to “no sound card found”.

Thanks for your help.

---

### Post by Kateikyoushi on 2006-09-26
You loaded the module manually but after a reboot have to load it again or
add it to etc/modules to autoload it.

```
sudo nano /etc/modules
```

add this to the end: snd-als100

This will load the module automatically.

---

### Post by almal on 2006-09-26
I tried to do what you suggested but can't figure out how to save the change to the file in the terminal. 

I tried to make the changes with the text editor but don't have permissions.

Thanks for your patience.

---

### Post by Kateikyoushi on 2006-09-26
You have to use the sudo command to have permissons to edit the file.
This is the case with most system files, its for your own protection.

For example:

```
sudo gedit /etc/modules
```

---

### Post by almal on 2006-10-23
I ended up buying a cheap sound card and it works fine now.

---

