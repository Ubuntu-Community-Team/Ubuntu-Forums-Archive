---
title: "Gom player in Ubuntu"
date: 2009-03-20
forum: Multimedia Software
---

### Post by ayonkhan on 2009-03-20
Can I install Gom Player in Ubuntu using Wine? If it is possible then how to do it?

---

### Post by lovinglinux on 2009-03-20
I don't think it will work (I guess I have already tried that) but you can try.

First you will need to enable the "Universe"  repository under  "System >>> Administration >>> Software Sources" to install wine from the repositories. Then you can install wine using these methods:

Method 1 - Access the "Add/Remove" menu, then select "All available applications" in the "show" drop-down menu option and type "Wine" in the search field. Select "Wine Windows Emulator" in the application list and click the "Apply Changes" button.

Method 2 - Run the following command in the terminal

```
sudo apt-get install wine
```


Once wine is installed, download the GOM Player executable and double click it to install.

You might need to configure some wine options to make it work.

For more information visit [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by ayonkhan on 2009-03-23
It works. But I am not satisfied.

---

