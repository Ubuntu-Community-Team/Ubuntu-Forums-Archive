---
title: "Dial-up Netzero"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by Kinetix7 on 2009-05-23
I've been trying to get internet (dial-up connection) working on Ubuntu 9.04 for a while now, and to no avail. Is there no way to get around the fact that Netzero has no software for Linux?

---

### Post by colorpurple21859 on 2009-05-23
have to have  sun-java jre runtime from sun-java and  netzero.deb installed. have to use  netzero's software to connect to the internet the default dialers won't work.

---

### Post by Kinetix7 on 2009-05-23
Where can I download the sun-java jre runtime from inside Windows so I can transfer it to Ubuntu?

---

### Post by colorpurple21859 on 2009-05-23
java.sun.com download  the java se runtime file jre-6u13-linux-i586.bin and copy to /usr then in a terminal
```
 [code] cd /usr 
sudo chmod a+x jre-6u13-linux-i586.bin
sudo ./jre-6u13-linux-i586.bin
sudo ln -sf /usr/jre1.6.0_13/bin/java /usr/bin/java
```to run netzero
```
 cd /opt/nzclient
sudo ./runclient.sh
```

---

### Post by Kinetix7 on 2009-05-25
It appears I botched something. When I entered the command "sudo ln -sf /usr/jre1.6.0_13/bin/java /usr/java", I didn't put a space between java and /usr/java. Now there is a defunct shortcut in the nzclient folder and it won't let me delete it because "permission denied". I don't have the knowledge to delete it via the terminal, either.

---

### Post by iiiears on 2009-05-25
sudo rm -f /path
[http://ubuntuforums.org/archive/index.php/t-423274.html](http://ubuntuforums.org/archive/index.php/t-423274.html)

Best Wishes.

---

### Post by colorpurple21859 on 2009-05-26
I'm sorry the java link should have been
```
sudo ln -sf /usr/jre1.6.0_13/bin/java /usr/bin/java
```
you will also need to make a link to your modem in the /etc/rc.local file
will look something like this
ln -sf /dev/yourmodemname /dev/modem
as an example my modem is on /dev/ttyS0 so my link is
ln -sf /dev/ttyS0 /dev/modem
yours is probably something different
will have to use the following to edit /etc/rc.local
sudo gedit /etc/rc.local

---

