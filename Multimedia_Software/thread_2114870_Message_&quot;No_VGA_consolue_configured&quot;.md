---
title: "Message &quot;No VGA consolue configured&quot; ?"
date: 2013-02-11
forum: Multimedia Software
---

### Post by HolgerB on 2013-02-11
Hi all,

just yesterday I upgraded my Xubuntu 11.04  x64 to Xubuntu 12.04 x64.
Everything went fine so far. Since I wanted to try out Steam under Xubuntu I upgraded my Graphic driver to the latest "offcial" NVidia driver (304.64).

In my messages I found a strange part about something saying that my VGA console is not configured:
```

[   31.832976] NVRM: Your system is not currently configured to drive a VGA console
[   31.832985] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   31.832990] NVRM: requires the use of a text-mode VGA console. Use of other console
[   31.832995] NVRM: drivers including, but not limited to, vesafb, may result in
[   31.832999] NVRM: corruption and stability problems, and is not supported.

```

Must I be concerned about this message ? Switching to the text consoles (F1 - F6) works fine.

TIA,
Holger

---

### Post by matt_symes on 2013-02-11
Hi
 
Try adding these lines to the kernel command line.
 
```
 
video=vesa:off vga=normal

```
 
Kind regards

---

