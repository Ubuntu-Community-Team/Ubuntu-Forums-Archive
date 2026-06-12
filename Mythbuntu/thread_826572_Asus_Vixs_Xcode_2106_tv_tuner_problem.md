---
title: "Asus Vixs Xcode 2106 tv tuner problem"
date: 2008-06-12
forum: Mythbuntu
---

### Post by toastermm on 2008-06-12
Setting up my first front/back end mythbuntu 8.04 machine on an HP that came with a "preinstalled" tv tuner.  None of the documentation online or with the computer describe what card it is.  So upon inspection of the card, here is what I can determine:

"ASUS, ViXS, Xcode-2106"

I'm on an amdX64 as well.

I have no idea what to select under the capture card option.  Here is the "lspci output:"

```
me@me-desktop:~$lspci

....not important stuff here...

01:05.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e2 (rev a1)
04:00.0 Multimedia controller: ViXS Systems, Inc. Unknown device 2100

```

Any tips or pointers would be greatly appreciated.

---

### Post by toastermm on 2008-06-12
Still can't find a driver or how to capture the card.

Anyone else with this problem?

---

### Post by Arkold Thos on 2008-06-13
Here I have this one:

david@david-desktop:~$ lspci
...
02:00.0 Communication controller: Conexant Unknown device 2f80
07:00.0 Multimedia controller: ViXS Systems, Inc. Unknown device 2100
...

Using 64 bits Ubuntu on a Q6600. anyone? <.<

---

### Post by ian dobson on 2008-06-14
Hi,

Go have a look at [www.linuxtv.org](www.linuxtv.org) to see if it's supported, sounds as if it isn't.

Regards
Ian Dobson

---

