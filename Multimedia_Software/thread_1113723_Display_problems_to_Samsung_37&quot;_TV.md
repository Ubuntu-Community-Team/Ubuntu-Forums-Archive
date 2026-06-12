---
title: "Display problems to Samsung 37&quot; TV"
date: 2009-04-01
forum: Multimedia Software
---

### Post by vettman2001 on 2009-04-01
I am currently running Ubuntu 8.1 on a Sony Vaio VGN-FJ290.  I have a 37" Samsung LCD TV that will not recognize the input from the laptop, but Ubuntu recognizes the Monitor.  Sony released a download for XP that users report some success.  Is there any known Ubuntu fix for this?

---

### Post by wolfen69 on 2009-04-01
```
sudo apt-get install i810switch 
```

From the package manager:

Enables/disables video output to CRT/LCD on i810 video hardware

i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.

---

### Post by vettman2001 on 2009-04-01
Tried downloading and installing the package, and the TV still does not recognize a PC input.

---

### Post by Godly on 2009-04-01
> **vettman2001 said:**
> Tried downloading and installing the package, and the TV still does not recognize a PC input.

FN and F5. What type of out put to t.v. are you using?

---

### Post by vettman2001 on 2009-04-01
VGA to VGA

---

