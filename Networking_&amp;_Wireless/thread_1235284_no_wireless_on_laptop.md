---
title: "no wireless on laptop"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by muklinux on 2009-08-08
i am new i have 8.04 installed and i tried "sudo ndiswrapper -i wg511v2.inf" and it came back and said
 "couldn't open wg511v2.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

i am totally new to linux and need help. also my laptop does not have a cd drive

---

### Post by Vakman on 2009-08-08
It might be easier to do this one the graphical way. System > Administration > Windows Wireless Drivers. I am assuming you already have Ndiswrapper installed based on what you were trying to do. When you open this up just click "Install Driver" and locate the .inf file.

---

### Post by muklinux on 2009-08-08
ok the driver installed how do i set up access...never mind just got it

---

### Post by Katalog on 2009-08-08
1.  Download the Windows wireless driver you need for your card.

2.  Create a folder where you would like to keep the driver and unpack it there.

3.  Using Synaptic, install ndisgtk (puts a nice graphical interface on ndiswrapper) and the dependencies it picks for you.

4.  Open a terminal window and enter the command "sudo ndisgtk".  A Wireless Network Drivers window will appear.

5.  Click the Install New Driver button.

6. Navigate through the folders for the driver you downloaded . Select the file "wg511v2.inf" and then click Install. Ignore the error that comes up about not being able to detect the hardware.

7.  Close ndisgtk and then restart the computer.

You should then be able to connect to the network. 

Hope this helps

EDIT: Too late with my answer. Glad to see you got it sorted out.

---

### Post by Vakman on 2009-08-08
> **muklinux said:**
> ok the driver installed how do i set up access...never mind just got it
Great, so all working? Have fun :)

---

