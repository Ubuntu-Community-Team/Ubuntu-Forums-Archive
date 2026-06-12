---
title: "Do I need more memory?"
date: 2010-03-02
forum: Mythbuntu
---

### Post by TheMiz on 2010-03-02
I have only 1 GB of memory on my Frontend and my FE/BE and I notice that I have audio sync issues when I play .mpg files or .iso files.  I also have some skipping and jumping when I play DVDs.

Do you think it is a memory issue, or maybe a problem with the file or the DVD drive?

---

### Post by Ghost|BTFH on 2010-03-02
> **TheMiz said:**
> I have only 1 GB of memory on my Frontend and my FE/BE and I notice that I have audio sync issues when I play .mpg files or .iso files.  I also have some skipping and jumping when I play DVDs.

Do you think it is a memory issue, or maybe a problem with the file or the DVD drive?

More RAM = Better - always

That being said, I've run Ubuntu on a 512mb RAM lappy w/o a single playback issue.

I would look to other solutions - it might be the files, it might be the libraries you're using (are you using restricted extras?) it could be the drive your using, it could be additional programs open in the background causing the stutter.

More details.

Cheers,
Ghost|BTFH

---

### Post by nickrout on 2010-03-02
No you probably don't need more memory. What you do need to do is look at your frontend logs and proceed to diagnose from there.

---

### Post by delectate on 2010-03-02
1g is big enouth to play dvd
maybe you don't choose the right videopot device?
or you need to install video decodes?

---

### Post by lyall on 2010-03-02
use **System Monitor**
from the System > Administrator

it will show you are Memory usage 

good luck and have fun learning

---

### Post by ian dobson on 2010-03-02
Hi,

Could please provide abit more information on your hardware specs (CPU,Graphic card).


How are the frontend/backend connected (Wireless,Wired 10Mbit).

Regards
Ian Dobson

---

### Post by azmyth on 2010-03-03
I'm using 1GB of memory and dvd etc works well. Buying a nvidia card with a GPU, definitely made a big difference on other areas of myth though.

---

### Post by TheMiz on 2010-03-03
I can't seem to find "System Monitor", as lyall suggested.

I looked through my logs, but I'm not sure I am interpreting them correctly.

My remote front end is an Acer Revo with an NVIDIA ION LE Motherboard, an Intel Atom Processor 230 1.6GHZ and a 160GB HDD.

It is connected over a wired 100Mbit network to my FE/BE which has a NVIDIA ION MB, an Intel 330 Atom 1.6GHz and a 250GB HDD.  The DVD drive is an LG SATA DVD Drive which claims a 16x DVD read speed.  I have a lot of sync issue when I'm trying to watch certain DVDs (I've cleaned them and made sure they are pristine).

They both have 1GB of RAM.

The audio goes out of sync particularly when I am changing chapters in an .iso image.

I use the restricted libdvdcss drivers.  

Thanks for the tips so far.

---

