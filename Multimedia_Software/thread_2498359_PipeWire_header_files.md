---
title: "PipeWire header files"
date: 2024-06-10
forum: Multimedia Software
---

### Post by lydloke on 2024-06-10
Where can I find the PipeWire header files?

---

### Post by #&amp;thj^% on 2024-06-10
I'm not sure what you mean by header files??? Are you referring to Modules?
They should be listed with:
```
ls -1 /usr/lib64/pipewire-0.3/libpipewire-module*

```
I'm not sure what your asking, could you be more specific?

---

### Post by lydloke on 2024-06-10
I am looking for the header files required in order to compile PipeWire client modules, i.e the .h files.

---

### Post by &amp;KyT$0P# on 2024-06-10
package [FONT=monospace]libpipewire-0.3-dev[/FONT] and/or [FONT=monospace]libspa-0.2-dev[/FONT] ?

---

### Post by #&amp;thj^% on 2024-06-10
Also have a look here: [https://docs.pipewire.org/page_modules.html](https://docs.pipewire.org/page_modules.html)

---

### Post by lydloke on 2024-06-11
Solved. The following works on Kubuntu 24.04:
sudo apt install libpipewire-0.3-dev
sudo apt install libspa-0.2-dev

---

