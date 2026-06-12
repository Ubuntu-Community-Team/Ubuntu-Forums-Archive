---
title: "Nvidia Xserver, changing resolution each time I boot."
date: 2009-07-06
forum: Multimedia Software
---

### Post by gasto on 2009-07-06
Hi there,

I start with the wrong resolution (Full HD I think), but I need it to be 1024x768

[[IMG]http://img41.imageshack.us/img41/4561/screenshotnvidiaxserver.th.png[/IMG]](http://img41.imageshack.us/i/screenshotnvidiaxserver.png/)

I am able to change it but in order to be permanent(each time I boot will have that resolution), the xconfig file must be updated but I can't:

[[IMG]http://img41.imageshack.us/img41/2412/screenshotsavexconfigur.th.png[/IMG]](http://img41.imageshack.us/i/screenshotsavexconfigur.png/)


[[IMG]http://img190.imageshack.us/img190/4624/93623237.th.png[/IMG]](http://img190.imageshack.us/i/93623237.png/)


Any help really appreciated.

---

### Post by overdrank on 2009-07-06
Hi and are you using ```
gksu nvidia-settings
```

---

### Post by gasto on 2009-07-07
This is what I get from the terminal when executing

```
gksu nvidia-settings
```

And clicking on 'Save to X configuration file':



WARNING:  No Layout specified, constructing implicit layout section using screen "Default Screen".



WARNING:  Unable to find CorePointer in X configuration; attempting to add new CorePointer section.


WARNING:  The CorePointer device was not specified explicitly in the layout; using the first mouse device.



WARNING:  Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.


WARNING:  The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

But when I click on 'Save' no error message is thrown. Hmmm... will reboot and see what happens...

---

### Post by gasto on 2009-07-07
Wow,thanks that worked, now the question is how did that work?

---

### Post by overdrank on 2009-07-07
> **gasto said:**
> Wow,thanks that worked, now the question is how did that work?

You just opened nvidia settings as root and it allowed you to save the settings :)

---

### Post by gasto on 2009-07-08
Thanks again.

---

