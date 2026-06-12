---
title: "Intel Centrino Wireless 6150-N Not recognized"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by FiveNine on 2013-03-21
Long story short, I have a virtual machine on my ASUS. 
I currently run Windows 7 on my ASUS and on my virtual machine I have Ubuntu and Kali Linux and on one of my old ancient laptops I currently have Xubuntu freshly installed.

My old laptop does not recognize any wifi, so being curious I checked on my VM and noticed that Kali Linux and Ubuntu both believe they are 'wired' physically to the internet rather than through wifi.

On my ASUS I have an Intel Centrino Wireless 6150-N, I am just learning Ubuntu right now and wondering what do I need to do to get it to recognize my wireless card rather than think it is physically connected with a cable? 

I plan to eventually install Ubuntu onto my laptop directly so I have the dual boot option when I become more familiar and comfortable with it.

Thanks!

---

### Post by carl4926 on 2013-03-21
Lets just check and see
```
lspci -nnk | grep -iA2 net
```

---

### Post by FiveNine on 2013-03-21
Following is the response when the code is entered into the terminal

~# lspci -nnk | grep -ia2 net
    Subsystem: VMware Device [15ad:1976]
    Kernel driver in use: uhci_hcd
02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
    Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971 [1022:2000]
    Kernel driver in use: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128 [1274:1371]

---

### Post by chili555 on 2013-03-21
I hope I am not stepping on toes here, but my esteemed colleague carl4926 will point out that networking on a virtual machine is handled quite differently and PCI wireless is generally unavailable.

---

### Post by FiveNine on 2013-03-21
So would it be safe to say that I should not experience these issues if I do a direct installation onto the computer for a dual boot option instead?

---

### Post by Yellow Pasque on 2013-03-21
> **FiveNine said:**
> So would it be safe to say that I should not experience these issues if I do a direct installation onto the computer for a dual boot option instead?

Correct

---

### Post by carl4926 on 2013-03-22
> **chili555 said:**
> I hope I am not stepping on toes here, but my esteemed colleague carl4926 will point out that networking on a virtual machine is handled quite differently and PCI wireless is generally unavailable.

LOL
I missed the VM part. Skip reading...

@[COLOR=#000000]FiveNine
You should be good
It'll probably work from the live session[/COLOR]

---

### Post by FiveNine on 2013-03-22
I actually just did a live boot from my CD and I noticed that it was picking up my wireless card.

Now since I want to do a direct install I need to partition my C: drive... Shrink it first I suppose to make room. Shame I have to much stuff on this laptop to just simply save everything and wipe the slate clean and start fresh. :P

---

