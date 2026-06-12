---
title: "K3B Doesn't Work After Installing An Unsupported App"
date: 2008-05-27
forum: Multimedia Software
---

### Post by TheDemonHell on 2008-05-27
I installed Wine, thanks to a guide on Softpedia, and decided to try and install Fairstars CD Ripper for Windows. Currently, it's unsupported under Wine, but I wanted to see if it would work. I tried it, it didn't work so I removed it.

Then, I find one of my CDs is scratched beyond repair, so I try loading K3B up to burn it again (Already backed it up thanks to RipperX) and it freezes at the splash screen, giving me no error numbers or anything. I rebooted (used to it because of Windows) and tried running it again, now K3B doesn't want to work at all.

If you need any more information, I can give as much as I can, but I'm also green. I'm willing to do Terminal commands because I did install Wine and XMMS via terminal. Any help would be very nice, thank you.

---

### Post by xc3RnbFO8P on 2008-05-27
In terminal:
> k3b   <return>
show the output

---

### Post by TheDemonHell on 2008-05-27
it's not giving me any output after two minutes...

---

### Post by TheDemonHell on 2008-05-27
odd, I just tried again, and Bash gave me Command not found... sounds like it's not on my system!

---

### Post by xc3RnbFO8P on 2008-05-27
Try to reinstall K3B in Synaptic Package Manager:

libmad0
libmad0-dev
k3b
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

---

### Post by TheDemonHell on 2008-05-27
OKay, I've done that, and I'm trying to run the command again in Terminal, but again, it's not giving me a responce.

---

### Post by xc3RnbFO8P on 2008-05-27
Then try to reinstall:
kdebase-bin
kdebase-bin-kde3

---

### Post by TheDemonHell on 2008-05-27
And it's still failing me. :(

---

### Post by xc3RnbFO8P on 2008-05-27
Then reinstall Hardy (backup if needed)
if you dual boot dont forget to
defrag Windows and check disk.
I use Gpart to delete ubuntu part
and format to fat32.
How much space are you giving Ubuntu
on hard disk ?

---

### Post by TheDemonHell on 2008-05-27
Never mind, I just did another reboot after reinstalling and it works now.

it has the full disk, I'm not running Windows at all.

---

### Post by xc3RnbFO8P on 2008-05-27
Then its solved?

---

