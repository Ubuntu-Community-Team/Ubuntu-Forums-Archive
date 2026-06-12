---
title: "Record My Desktop"
date: 2010-04-19
forum: Multimedia Software
---

### Post by truckbytes on 2010-04-19
Can anyone help with recordmydesktop? I get the following error each time I attempt to use it.

Recording is finished.
recordmydesktop has exited with status: 256
Description: Error while parsing the arguments.

---

### Post by 2hot6ft2 on 2010-04-19
Found this on it, and this is where I found it: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=785868](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=785868)
> **Rytron said:**
> I came across this:

start the Jack server. Either from terminal:

```
jackd -R -d alsa
```

or with the gui:

```
sudo apt-get install qjackctl
```
If you decide you want better quality check this guide out
[HOWTO: Proper Screencasting on Linux]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by truckbytes on 2010-04-19
Hmmm... still have the same results. I did install jack but it crashes too.

---

