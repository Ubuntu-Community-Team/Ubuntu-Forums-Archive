---
title: "Bumblebee error &quot;NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0. Please&quot;"
date: 2013-02-20
forum: Multimedia Software
---

### Post by Maou on 2013-02-20
Hello, 
I am attempting to use bumblebee on my Lenovo Y570 ideapad running Mint. When using optirun I get an error message. So I checked the log, and the output of
```
grep -Fn '(EE' /var/log/Xorg.8.log
```is
```

15:     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
114:[    41.370] (EE) Failed to load module "kbd" (module does not exist, 0)
146:[    41.385] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
147:[    41.385] (EE) NVIDIA(0):     check your system's kernel log for additional error
148:[    41.385] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
149:[    41.385] (EE) NVIDIA(0):     README for additional information.
150:[    41.385] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
151:[    41.385] (EE) NVIDIA(0): Failing initialization of X screen 0
155:[    41.385] (EE) Screen(s) found, but none have a usable configuration.
159:[    41.385] (EE)
163:[    41.385] (EE) Please also check the log file at "/var/log/Xorg.8.log" for additional information.
164:[    41.385] (EE)

```I have gone through the troubleshooting portion of the bumblebee website, and it has helped some, as this was not my original problem. [http://linux-hybrid-graphics.blogspot.com/2011/12/bumblee-on-lenovo-ideapad-y570.html](http://linux-hybrid-graphics.blogspot.com/2011/12/bumblee-on-lenovo-ideapad-y570.html) states that the laptop is supported, but I can not find a fix for these errors.
Let me know if I need to provide additional information, any help at all would be appreciated. Steam for linux just came out and I want to play TF2 on my Laptop!

---

