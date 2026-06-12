---
title: "kernel 2.6.17 and x"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by gaillard on 2006-08-07
hi. i was wondering if anyoe could help.  i have compiled and installed a vanilla kernel by using this guide. [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel+2.6.17](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel+2.6.17)
and follows tselliots guide for method 2 of the nvidia drivers and now x won't start

it says it failed to loead the glx module (a required submodule could not be leaded)

and that it failed to load module "nvidia" (module does not exist)

fatal server error: no screens found

now i followed the guides correctly and this is on a brand new installation (this is the first thing i did after installing the updates was compile the kernel.)

any ideas anyone??

thanks so much

---

### Post by tseliot on 2006-08-07
I don't know how you compiled your kernel but I can suggest you to try my Envy script which should work just fine (or follow VERY carefully method 2)

---

### Post by gaillard on 2006-08-07
nm

---

### Post by gaillard on 2006-08-07
ok i ran your script and it did everything with no errors and still i get the same thing.

---

### Post by gaillard on 2006-08-07
well i rebooted into the old default kernel and then ran the script and it work for that kernel.  then i booted back to my 2.6.17.7 kernel and ran it and this time it worked.

but it would not before then.  is that normal?

at any rate thanks tselliot

---

### Post by tseliot on 2006-08-08
> **gaillard said:**
> well i rebooted into the old default kernel and then ran the script and it work for that kernel.  then i booted back to my 2.6.17.7 kernel and ran it and this time it worked.

but it would not before then.  is that normal?

at any rate thats tselliot

I really don't know what happened.

I hope the next version of my script is more "reliable"

---

### Post by gaillard on 2006-08-08
i didn't mean it in anyway like that.  If it wasn't for your script i'd still be looking at a blinking cursor... =D

my brain is the unreliable one here...

---

