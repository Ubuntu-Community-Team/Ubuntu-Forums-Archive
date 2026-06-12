---
title: "Graphics Card Driver"
date: 2009-06-30
forum: Multimedia Software
---

### Post by John Private on 2009-06-30
I really need to download a Driver for me to use 3 D Smoothly and I really need it but when ever it comes up like when I want to apply Visual Effects and I try to Download it. It freezes the first time it actually messed up my Ubuntu Linux then I just ran like the Repair Packages and everything worked again luckily but is there Terminal Code that will download this 3D Driver thing for me.

---

### Post by John Private on 2009-06-30
I really need to download a Driver for me to use 3 D Smoothly and I really need it but when ever it comes up like when I want to apply Visual Effects and I try to Download it. It freezes the first time it actually messed up my Ubuntu Linux then I just ran like the Repair Packages and everything worked again luckily but is there Terminal Code that will download this 3D Driver thing for me.

---

### Post by John Private on 2009-06-30
I really need to download a Driver for me to use 3 D Smoothly and I really need it but when ever it comes up like when I want to apply Visual Effects and I try to Download it. It freezes the first time it actually messed up my Ubuntu Linux then I just ran like the Repair Packages and everything worked again luckily but is there Terminal Code that will download this 3D Driver thing for me.

---

### Post by credobyte on 2009-06-30
Don't mind in telling us, what video card do you have ?

---

### Post by John Private on 2009-06-30
I really need to download a Driver for me to use 3 D Smoothly and I really need it but when ever it comes up like when I want to apply Visual Effects and I try to Download it. It freezes the first time it actually messed up my Ubuntu Linux then I just ran like the Repair Packages and everything worked again luckily but is there Terminal Code that will download this 3D Driver thing for me.

---John

---

### Post by 3rdalbum on 2009-06-30
What graphics card do you have?

If it's ATI or Nvidia, both those graphics card vendors make proprietary drivers for Linux, and the absolute latest versions of these can be downloaded from the ATI or Nvidia website. The Hardware Drivers program in Ubuntu is the preferred way to install those graphics drivers, but it will install older versions than what are currently available from the vendor.

If you get stuck installing the driver manually, there are HOWTOs in the "Tutorials and Tips" section of the forum.

---

### Post by overdrank on 2009-06-30
Please do not make multiple threads on the same issue. Threads merged

---

### Post by John Private on 2009-06-30
> **credobyte said:**
> Don't mind in telling us, what video card do you have ?I have Nvidia.

---

### Post by John Private on 2009-06-30
> **3rdalbum said:**
> What graphics card do you have?

If it's ATI or Nvidia, both those graphics card vendors make proprietary drivers for Linux, and the absolute latest versions of these can be downloaded from the ATI or Nvidia website. The Hardware Drivers program in Ubuntu is the preferred way to install those graphics drivers, but it will install older versions than what are currently available from the vendor.

If you get stuck installing the driver manually, there are HOWTOs in the "Tutorials and Tips" section of the forum.Thanks I will try to look for some Tutorials.

---

### Post by overdrank on 2009-07-01
> **John Private said:**
> I have Nvidia.

Hi and what version of Ubuntu are you using? If using Jaunty 9.04, have you tried the drivers under system, administration, hardware drivers?
What is the model of the nvidia graphics?
You may use this command in the terminal to identify the graphics
```
lspci | grep VGA

```

---

### Post by John Private on 2009-07-01
> **overdrank said:**
> Hi and what version of Ubuntu are you using? If using Jaunty 9.04, have you tried the drivers under system, administration, hardware drivers?
What is the model of the nvidia graphics?
You may use this command in the terminal to identify the graphics
```
lspci | grep VGA

```All I had to do was look at the Hardware Driver Section and Install 1 of the Graphics Accelerators there. Once again the Ubuntu Forums has helped me again :D

---

### Post by John Private on 2009-07-02
Solved Thanks Again Everyone.

---

