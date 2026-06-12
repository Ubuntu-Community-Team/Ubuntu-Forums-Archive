---
title: "bluetooth adapter"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by mirinamulhaq on 2010-02-13
i have windows 7 and ubuntu karmic dual boot system.i can easily transfer files via bluetooth in windows 7 but in ubuntu it shows a message bluetooth adapter not connected while as i dont use any such adapter while working in windows .can anybody help me resolve this problem.

---

### Post by byStanderone on 2010-02-13
...would surmise that your bluetooth device is integrated in your mobo, and that your present ubuntu install doesn't recognize it, for one or two reasons...you have not installed the right codecs needed by ubuntu for bluetooth operation,...or ubuntu have no support for that particular make of bluetooth hardware.(integral)

---

### Post by mirinamulhaq on 2010-02-13
in windows my bluetooth drivers are provided by broadcom.one more thing is that when i first installed ubuntu then the bluetooth was working in a nice way for the very first day because it was detect my mobile and import its folders but then i updated my ubuntu using command prompt by using sudo apt-get update. and then onwards the problem occured

---

### Post by byStanderone on 2010-02-13
...try booting in restore mode, if the situation remains the same, perhaps you need to install the restricted codecs, update your synaptic source.

---

### Post by mirinamulhaq on 2010-02-14
thanku ,it worked well.but i am able to tranafer only photographs between my mobile phone and laptop and nothing else. all the folders are in fact displayed in my laptop when i browse files but i am not able to import anything except photographs
thanks a lot for your kind help.

---

