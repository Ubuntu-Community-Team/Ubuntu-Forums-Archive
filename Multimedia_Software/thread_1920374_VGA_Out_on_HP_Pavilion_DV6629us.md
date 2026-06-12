---
title: "VGA Out on HP Pavilion DV6629us"
date: 2012-02-04
forum: Multimedia Software
---

### Post by joelstitch on 2012-02-04
I am trying to connect a second TV to my computer so I can use it as a second monitor but for some reason its not detecting the VGA. I am able to connect it using S-Video just fine using NVIDIA X Server Settings. I read something about adding some coding to the xconf file or something like that. Can someone please help me out with this issue! 

P.S. My laptop has a NVIDIA GeForce 7500M

---

### Post by sudodus on 2012-02-04
> **joelstitch said:**
> I am trying to connect a second TV to my computer so I can use it as a second monitor but for some reason its not detecting the VGA. I am able to connect it using S-Video just fine using NVIDIA X Server Settings. I read something about adding some coding to the xconf file or something like that. Can someone please help me out with this issue! 

P.S. My laptop has a NVIDIA GeForce 7500M
Which version and flavour of Ubuntu are you running?

What graphics driver are you using? If it is a proprietary driver, you need ***nvidia-settings*** to manage the graphics (to see the two screens etc). It won't work with the standard GUI tool for screen settings.

Have you checked that the hardware is detected by Ubuntu? For example with
```
gksudo lshw | less
``` or the GUI program ***hardinfo***?

Have you checked that the TV is listening to the VGA port?

---

### Post by joelstitch on 2012-02-04
> **sudodus said:**
> Which version and flavour of Ubuntu are you running?

What graphics driver are you using? If it is a proprietary driver, you need ***nvidia-settings*** to manage the graphics (to see the two screens etc). It won't work with the standard GUI tool for screen settings.

Have you checked that the hardware is detected by Ubuntu? For example with
```
gksudo lshw | less
``` or the GUI program ***hardinfo***?

Have you checked that the TV is listening to the VGA port?

I have **Ubuntu 12.04 32bit**. My graphic driver is **NVIDIA accelerted graphic driver (version current)**. I have been using the **NVIDIA X Server Settings** to do dual screen using S-Video and it did the job but the problem is that my computer is not detecting the VGA.

---

### Post by sudodus on 2012-02-05
> **joelstitch said:**
> I have **Ubuntu 12.04 32bit**. My graphic driver is **NVIDIA accelerted graphic driver (version current)**. I have been using the **NVIDIA X Server Settings** to do dual screen using S-Video and it did the job but the problem is that my computer is not detecting the VGA.
I think you know the tools well enough :-) Have you tried to attach a monitor to the VGA port, just to make sure if it can find a regular monitor? In that case, maybe there is something fishy with the TV's VGA port.
[I]
Edit: I got some second thoughts because you run 12.04. It is not stable yet, so try a released version (11.10 or older) live from a CD or USB drive! Maybe your computer finds the TV with that operating system.
[/I]

---

