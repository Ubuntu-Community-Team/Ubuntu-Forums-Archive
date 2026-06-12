---
title: "need inf file"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by JakeHinojosa on 2009-04-28
does anybody know where i can get the correct inf file for a WUSB54GC usb adapter so i can install it with ndiswrapper?

---

### Post by JakeHinojosa on 2009-04-28
is anybody sure they dont know?

---

### Post by JakeHinojosa on 2009-04-29
please?

---

### Post by m_duck on 2009-04-29
Which version of the adapter is it? [The Linksys site](http://www.linksysbycisco.com/UK/en/support/WUSB54GC) says there are three versions of it.

Also, are you running 32- or 64-bit Ubuntu?

---

### Post by JakeHinojosa on 2009-04-29
> **m_duck said:**
> Which version of the adapter is it? [The Linksys site](http://www.linksysbycisco.com/UK/en/support/WUSB54GC) says there are three versions of it.

Also, are you running 32- or 64-bit Ubuntu?

im running linux mint.

---

### Post by SuperSonic4 on 2009-04-29
> **JakeHinojosa said:**
> im running linux mint.

You can type ```
uname -m
``` into a terminal to see if you're using 32bit or 64bit

---

### Post by m_duck on 2009-04-29
Is the link in my previous post to the correct wireless dongle? If so, what version of the dongle is it? It should say somewhere on it: either version 1.0, version 2.0 or version 3.0.

Could you paste the following in terminal and post the output:```
uname -m
```

---

### Post by JakeHinojosa on 2009-04-29
> **m_duck said:**
> Is the link in my previous post to the correct wireless dongle? If so, what version of the dongle is it? It should say somewhere on it: either version 1.0, version 2.0 or version 3.0.

Could you paste the following in terminal and post the output:```
uname -m
```

i typed in uname -m and got i686 (whatever that is), and i am using the version 3 adapter.

---

### Post by m_duck on 2009-04-29
OK, then. i686 means you are running the 32-bit version of Ubuntu.

Go [here]("http://www.linksysbycisco.com/US/en/support/WUSB54GC/download") and select version 3 in the drop-down menu. Click the download link under the "Setup Wizard" title. Once that has downloaded, unzip the resulting .zip file and open the folder. Once in the folder, navigate to *setup/adapter/xp/x86*. The file that you probably want rt2870.inf. Load that in ndiswrapper (not sure how off the top of my head as I've not used it for ages) and your wireless should work nicely...

---

### Post by JakeHinojosa on 2009-04-29
> **m_duck said:**
> OK, then. i686 means you are running the 32-bit version of Ubuntu.

Go [here]("http://www.linksysbycisco.com/US/en/support/WUSB54GC/download") and select version 3 in the drop-down menu. Click the download link under the "Setup Wizard" title. Once that has downloaded, unzip the resulting .zip file and open the folder. Once in the folder, navigate to *setup/adapter/xp/x86*. The file that you probably want rt2870.inf. Load that in ndiswrapper (not sure how off the top of my head as I've not used it for ages) and your wireless should work nicely...


but will it work for LINUX MINT too?

---

### Post by SuperSonic4 on 2009-04-29
Almost certainly, linux mint is based off ubuntu anywayq

---

### Post by JakeHinojosa on 2009-04-29
> **m_duck said:**
> OK, then. i686 means you are running the 32-bit version of Ubuntu.

Go [here]("http://www.linksysbycisco.com/US/en/support/WUSB54GC/download") and select version 3 in the drop-down menu. Click the download link under the "Setup Wizard" title. Once that has downloaded, unzip the resulting .zip file and open the folder. Once in the folder, navigate to *setup/adapter/xp/x86*. The file that you probably want rt2870.inf. Load that in ndiswrapper (not sure how off the top of my head as I've not used it for ages) and your wireless should work nicely...

it didnt work. it said: invalid driver

---

### Post by m_duck on 2009-04-30
Did you move the .inf file out of the directory it was in within the zip file before you installed it? I'm not very familiar with ndiswrapper, as I said, but looking [thread=257639]here[/thread] it is necessary to have the .sys file in the same folder as the .inf whilst enabling the .inf file.

---

