---
title: "What My Graphics card make?"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by RedSingularity on 2009-03-04
What is a good command for the terminal to find my graphics card make and model?

---

### Post by Therion on 2009-03-04
My suggestion:

Synaptic, Search for and install **gnome-device-manager**

Go to Applications, System Tools, Device Manager.

For additional information overload go to "View" and check the box for "Device Properties" then head over to...

You guessed it, the new "Properties" tab.

Go nuts.

---

### Post by RedSingularity on 2009-03-04
Very nice......a GUI as well.  Can this detect and name Network controllers even if the drivers are not installed?

---

### Post by yther on 2009-03-04
> **Shadow121 said:**
> What is a good command for the terminal to find my graphics card make and model?

In a terminal?  **lspci**

It will output something like this, along with a bunch of other stuff:

```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
```

There's also **lshw**, which will tell you the same thing like this, if you run "lshw -short":

```
/0/100/1/0                     display     GeForce 8600M GT
```

---

