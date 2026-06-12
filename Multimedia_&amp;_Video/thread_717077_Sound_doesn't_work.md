---
title: "Sound doesn't work"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by tacosta on 2008-03-06
Hi,

I just installed Ubuntu on my laptop and everything works perfectly except the sound.

I'm using Ubuntu version 7.10

I searched this forum and i found numerous threads about this problem but with my limited linux knowledge all the commands i tried didn't solve it,

I'll post some info i think is relevant, feel free to ask me for more if you need it.

**lspci | grep -i**
aud00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

**lspci -v**
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Again, i apologize because i know that there are threads related to this issue, but i couldn't fix it :(

Thank you for your time, 

Tiago Costa

---

### Post by tacosta on 2008-03-06
After searching a little more about this i found this miraculous line of code that fixed the problem:

**sudo apt-get install linux-backports-modules-generic**

Thanks to Frank ;)

---

### Post by linuxNewb on 2008-03-06
That worked for me as well on a Dell Vostro 1500. Thanks for posting the solution!

---

### Post by msailg on 2008-03-11
Hi
I am new to linux, where do input this code?
Vostro 1500, linux 7.10 amd64 & intel

---

### Post by mrpixels0 on 2008-03-13
Hi there msailg :)

got to Applications->Accessories->terminal

A screen will come up that looks like a Windows Dos Box

type: sudo apt-get install linux-backports-modules-generic and press enter
enter your password and press enter again

when it installs it will as you some questions just hit  "y" at all of them 
wait for it to finish and close the terminal window

reboot the system and your good to go.

hope this helps you out.

MP0

---

### Post by 85fb on 2008-05-01
i have a vostro 1500 and i tried that code but it says the package linux backports whatnot doesnt exsist? als;khfj

---

