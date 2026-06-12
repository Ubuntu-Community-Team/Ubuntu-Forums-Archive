---
title: "Mapping help"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by t43m4n on 2009-07-21
I have a problem on opening a file on a network.

Here is my situation, I have oracle forms installed and running on WINE. My linux machine is on a windows domain which I authenticate myself through Likewise. I've successfully mapped the folder that I want to get the form file(.fmx) which i will be using for oracle forms with and it's already accessible on the desktop. My problem is, I can't just copy the sbis.fmx file to the desktop because it is dependent on other files in that same folder. I tried making a  link but it wont allow me saying "target doesn't support symbolic links". My only option is to open the mapped drive inside WINE but the drive isnt there when I run oracle forms under wine.

On windows, map the drive, create a shortcut to the sbis.fmx file to my desktop. I then right click the file and change the target to C:\orant\bin\ifrun32.exe Y:\sbis\sbis.fmx (where the 1st one is the oracle forms executable and the latter is the location of the form on the mapped drive)

I need help. If I dont get this to work, I might push through with our linux migration here in the office.

---

### Post by t43m4n on 2009-07-21
If you cant picture it out, here's a screenshot of my desktop. Not sure how it can help you tho

[IMG]http://img24.imageshack.us/img24/1672/screenshotyzd.png[/IMG]

---

