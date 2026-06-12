---
title: "firefox live streaming"
date: 2010-01-09
forum: Multimedia Software
---

### Post by jackel7 on 2010-01-09
There is a live internet streaming cast that runs on Friday's. I can't watch it using firefox. so I have to reboot into windows, use ie to view it. I want to be able to view it while using firefox via ubuntu. How can make this happen:confused: 

Thanks

---

### Post by ron999 on 2010-01-09
Hi
It could be because you haven't got the multimedia plugins for Firefox.

You can check this by typing

[SIZE="4"]```
about:plugins
```[/SIZE] 
in the URL window.

It should show a whole list of the formats that Firefox can handle.

To install the plugins use this command in a monitor:-
```
sudo apt-get install mozilla-plugin-vlc
```

;)

---

### Post by jackel7 on 2010-01-09
> **ron999 said:**
> Hi
It could be because you haven't got the multimedia plugins for Firefox.

You can check this by typing

[SIZE="4"]```
about:plugins
```[/SIZE] 
in the URL window.

It should show a whole list of the formats that Firefox can handle.

To install the plugins use this command in a monitor:-
```
sudo apt-get install mozilla-plugin-vlc
```

;)

it gives me the following message E: Invalid operation instoll

---

### Post by ron999 on 2010-01-09
> **jackel7 said:**
> instoll

You've spelled it wrong.
It's an **a** in install, not an o.

---

### Post by jackel7 on 2010-01-09
I've done this. now will this insure live streaming in real time?

---

### Post by ron999 on 2010-01-09
> **jackel7 said:**
> I've done this. now will this insure live streaming in real time?
Keep your fingers crossed. :D

---

### Post by jackel7 on 2010-01-09
it is showing this media player which is the same one that was there before

Totem Browser Plugin 2.28.2,  Browser Plugin using GStreamer 0.10.25

I don't know if that did it and i wont be able to find out until next week.

that's why I want to fix it now

---

### Post by chaanakya_chiraag on 2010-01-09
you may have to uninstall the totem plugin if you have installed the vlc plugin in order to make sure firefox uses the vlc plugin.

---

### Post by jackel7 on 2010-01-09
i'm still kinda new to ubuntu how would I do this uninstallation

---

### Post by chaanakya_chiraag on 2010-01-09
Yeah...try running the following command:
```
sudo aptitude purge totem-mozilla
```
and see if that helps.

---

### Post by chaanakya_chiraag on 2010-01-09
You will also have to restart your browser after you run that command.

---

### Post by jackel7 on 2010-01-09
I've done this and I can't see the last post you left. the words are gone

---

### Post by jackel7 on 2010-01-09
ok i restart the browser it is all normal

---

### Post by lovinglinux on 2010-01-09
[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by chaanakya_chiraag on 2010-01-10
Is it playing now?

---

