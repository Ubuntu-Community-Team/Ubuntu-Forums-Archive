---
title: "Problems with lirc repeat"
date: 2010-09-05
forum: Mythbuntu
---

### Post by jammln on 2010-09-05
Hi There,

If I'm not mistaken setting the 'repeat' parameter in the lirc config file should allow me to hold down a key on my remote, say arrow down, and have it scroll until I release the key. Is that right?

In fact, what I am getting is that the cursor only moves when I let the key go, like it's reacting to keyup only.

I'm using a logitech remote which I've configured like the grey hauppauge remote.

I've tried:

repeat 1
repeat 3
repeat 100

although I have no idea what the different values should represent.

Any help appreciated!

TIA

---

### Post by ian dobson on 2010-09-05
Hi,

From the lirc documentation:-

repeat 
tells the program what shall happen if a key is repeated. A value of zero tells the program to ignore repeated keys. Any other positive value 'n' tells the program to pass the config string every 'n'-th time to the according application, when a key is repeated. The default for repeat is zero.

from [http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)

Regards
Ian Dobson

---

### Post by nickshanley on 2010-09-16
.

---

### Post by nickshanley on 2010-09-16
.

---

### Post by nickshanley on 2010-09-16
.

---

