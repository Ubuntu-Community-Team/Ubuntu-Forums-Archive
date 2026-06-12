---
title: "DVD player"
date: 2010-01-05
forum: Multimedia Software
---

### Post by rodwatsoninalbany on 2010-01-05
Hello , I am new to Linux.
Downloaded restricted packages and search says I have libdvdread4 intalled
but when i do sudo /usr/share/doc/libdvdread4/install-css.sh  it says file does not exist.
can anyone help me here ?

---

### Post by jimmers on 2010-01-06
Check in Synaptic whether it is installed or not, you could also try,
sudo apt-get install w32codecs libdvdcss2

---

### Post by HappyFeet on 2010-01-06
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```

---

