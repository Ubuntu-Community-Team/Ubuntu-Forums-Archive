---
title: "How to backup the wireless profiles of NetworkManager"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by v.wochnik on 2009-01-18
Hi!

I want to backup the wireless profiles from the NetworkManager in Ubuntu to restore them on another computer, so I don't have to enter each key again.

Thank you guyz.

---

### Post by jgoguen on 2009-01-18
Copy ${HOME}/.gconf/system/networking/connections/ over to the other system.  Shut down NetworkManager and the applet before doing it:
```
sudo /etc/init.d/NetworkManager stop
pkill nm-applet
```
and once the directory has been copied over restart them:
```
sudo /etc/init.d/NetworkManager start
```
Press Alt+F2 and enter **nm-applet --sm-disable** to start the applet.

---

### Post by cruzer45 on 2010-05-03
Thanks

---

### Post by Ajd on 2011-01-18
For 10.10, you should use: 

```
sudo service network-manager stop
```

(Not  a ghost thread, this question ranks on Google.)

---

### Post by Virus666 on 2011-05-02
Thanks, I was looking for this... :-)

---

### Post by avocador on 2011-06-22
hey, 
I was looking for such a solution...but its not working for my problem. I want copy my network profiles from one System (10.10) and hard drive to another 11.04. one. In both Im using network manager. 

(highly rang on google)

---

### Post by Jessimo on 2011-10-06
Hi there, also having a hard time finding any documentation on this. I run 10.04, and I used a combination of the advices here which hasn't worked for me so far.

I stopped network
sudo service network-manager stop

then tried to copy $/.gconf/system/networking/connections

and I get
Error copying "%gconf.xml"

There was an error copying the file into /media/SEALIFECAM/connections/46/802-11-wireless.

and 
Error opening file: Input/output error

a bunch of times, though within my newly copied folder are a bunch of %gconf.xml files.

Any advice on what is going wrong?  I can't find a how to specific to 10.04. 

Vancouver ubuntu LoCo rocks!

Jesse

---

