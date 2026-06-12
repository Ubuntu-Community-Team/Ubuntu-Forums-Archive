---
title: "switching to NVIDIA driver"
date: 2013-03-10
forum: Multimedia Software
---

### Post by KylePhys on 2013-03-10
I have black screen after resuming from suspend. Just found a thread stating that the new NVIDIA driver fixes it, I installed it but it says that "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

Anybody can give me a hint what to do?

---

### Post by ManamiVixen on 2013-03-10
What graphics card do you have and what version of ubuntu?

---

### Post by KylePhys on 2013-03-10
ubuntu 12.04, how do i check the graphic  card?

---

### Post by ManamiVixen on 2013-03-10
Put into terminal and the paste/type the output here.
lspci | grep VGA

---

### Post by ManamiVixen on 2013-03-10
Also, which of the drivers did you install?

---

### Post by KylePhys on 2013-03-10
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647

I just installed nvidia-current

---

### Post by KylePhys on 2013-03-10
i just have two problems: suspend and brightness adjustment, both don't work.

---

### Post by ManamiVixen on 2013-03-10
You need to install the ATI driver... Thats not Nvidia.
First remove the nvidia driver -- sudo apt-get remove --purge nvidia-current
then install for ATI -- sudo apt-get install fglrx-installer

---

### Post by Bucky Ball on 2013-03-10
*Thread moved to **Multimedia & Video***

---

### Post by KylePhys on 2013-03-10
it's a toshiba satelite laptop

---

### Post by QIII on 2013-03-10
@KylePhys

Please stop for a moment.  How old is your laptop?

---

### Post by ManamiVixen on 2013-03-10
But still... The fglrx driver is what you need. ;)

---

### Post by QIII on 2013-03-10
Not if it is, indeed, a 9600.  That card has been moved to legacy support by AMD/ATI and needs a legacy driver.  The driver in the Precise repo will NOT work.

---

### Post by ManamiVixen on 2013-03-10
I was looking online and it turns out the 9647 was a codename for Radeon HD 6XXXm cards.

---

### Post by QIII on 2013-03-10
If it is an APU, and the device is [1002:9647], then it is an HD 6xxxM series.

If it is an older model and not an APU, then we need to know that.  Which is why I asked how old the machine is.

---

### Post by QIII on 2013-03-10
@KylePhys --

I may need to hobble off to bed soon. 

If you determine that your machine is running an APU and we can assume that the graphics are HD 6xxx, there is one more question to be answered:

Does it also have an Intel GPU?  That is, is it an Intel/ATI hybrid?  If it is, then the answer is not so simple as just installing the ATI driver.

---

