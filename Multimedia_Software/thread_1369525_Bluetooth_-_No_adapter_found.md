---
title: "Bluetooth - No adapter found"
date: 2010-01-01
forum: Multimedia Software
---

### Post by anjohnso on 2010-01-01
I'm at my wits end here.  I finally got a bluetooth usb adapter and headphones and was all excited. Until I plugged in the adapter and got nothing.  Tried installing blueman. Still nothing.  Ubuntu won't recognize my adapter?  

I've been searching all over the web, and ended up more confused I guess.  Why oh why can't it just be plug and play? :(  If anyone can get me some help, hopefully without 900 lines of code and a bash script I'd love you forever.

---

### Post by xc3RnbFO8P on 2010-01-01
Start in system> preferences> Bluetooth Manager and then plugin the bluetooth adapter.

---

### Post by anjohnso on 2010-01-03
Ok, I've got it working. Problem is, whether I plug the adapter in before or after I open blueman, I have to enter ```
sudo hciconfig hci0 reset
```

This is kinda annoying...  Otherwise everything works great!  

Oh, and I guess I should specify, I'm running Jaunty.  Using Blueman and Pulse Audio Device Chooser.

---

### Post by anjohnso on 2010-01-04
bump?  I've searched all over and can't seem to find a solution.  Tons of thanks to the other threads here that got me this far!

---

