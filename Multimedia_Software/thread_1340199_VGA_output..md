---
title: "VGA output."
date: 2009-11-28
forum: Multimedia Software
---

### Post by lover_of_sc on 2009-11-28
Hi guys,

Does anyone know if there is a way to activate the VGA output in ubuntu 9.10 without rebooting?

I currently have to have the VGA cable connected when booting up to get it to work? Thx.

---

### Post by hirnwurscht on 2009-11-28
Hello lover_of_sc,

what graphic card do you have?
       
For nvidia cards, a simple

```
Option          "ConnectedMonitor" "CRT-0"
```

in /etc/X11/xorg.conf Screen section and rebooting (with or without cable attached) will do.

---

### Post by lover_of_sc on 2009-11-29
I there, I have a Sony Vaio W Series netbook, so sadly no N-vidia card. It's a Intel GMA 950 128 MB card...

---

