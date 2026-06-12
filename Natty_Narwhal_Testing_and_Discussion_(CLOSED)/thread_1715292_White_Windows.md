---
title: "White Windows"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pt123 on 2011-03-26
I upgraded a test maverick installation to Natty. As usual the upgrade was messed up with nvidia drivers had to remove it under root terminal, then I could log in using gdm and then reinstall it using Admin ->Additional drivers. 

But the problem I am facing now is white windows when applications have started. They remain white for most of the time, occasionally the content will be displayed. 
Firefox remains white.

---

### Post by Yumi on 2011-04-15
Did you find a solution? I have this and cured it for now by removing the NVIDIA accelerated driver.

Michael

---

### Post by pt123 on 2011-04-16
No I have not, yours is not much of a solution. 
What nvidia chip are you using?

---

### Post by r-senior on 2011-04-16
The workaround using the free Nouveau driver isn't actually that bad and gives a passable Unity experience, if a little off the pace in terms of 3D.

I have a bug report open on it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)

---

### Post by yorkie on 2011-04-16
I changed  from using nvidia driver to nouveau driver but the problem still exist did you change anything else?

---

### Post by r-senior on 2011-04-16
Lots of things - in an attempt to get it working without changing the driver ;) But I have since done a "unity --reset" and the Nouveau driver still seems to cure the white windows problem.

---

### Post by yorkie on 2011-04-16
I rechecked in synaptic and found I still had nvidia current installed I removed it  and its working o`k now 
thanks for the info R-senior

---

