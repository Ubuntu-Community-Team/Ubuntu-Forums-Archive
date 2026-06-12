---
title: "= of Giver"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by ssulaco on 2012-11-10
Can anyone suggest a simple,I mean simple file sharing program like Giver,that will work across Lubuntu 12.04 and Ubuntu 10.04.Giver is not in the 12.04 repo..Thanks in advance.

---

### Post by ajgreeny on 2012-11-10
Try **Transfer-on-lan** from [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list).  It is a simple java application, and not only cross *ubuntu family of OSs but also cross platform, ie Linux, Windows, Mac.

Download the tar.gz and extract the TransferOnLAN folder in the archive to somewhere in your home.  Now make a launcher to run the TransferOnLAN.jar file with the command ```
java -jar /full/path/to/TransferOnLAN.jar
```

If you're not sure how to make a launcher in Lubuntu simply open Leafpad and copy the text below into it. Save it as **transferonlan.desktop** file.  Use the full pathway to the java executable jar file, and make sure the .desktop file is executable as well.
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=TransferOnLAN
Comment=Transfer on LAN
Exec=java -jar */home/path/to/TransferOnLAN-0.4.5*/TransferOnLAN.jar
Icon=/path/to/chosen/icon
Terminal=false
Type=Application
# MimeType=text/plain
# Categories=GTK;Utility;Network;
```

I use this a lot between several machines in the household and find it extremely good.  It is not a real alternative to, for example, using ssh over the network, as files will only go in the the one direction, ie, away from the machine you're working on, but it is nevertheless a very useful utility and does exactly what it sets out to do.

---

### Post by ssulaco on 2012-11-10
Thanks ajgreeny,I will give that a whirl,also thanks for the code.

---

### Post by ssulaco on 2012-11-10
> **ajgreeny said:**
> 
Download the tar.gz and extract the TransferOnLAN folder in the archive to somewhere in your home.  Now make a launcher to run the TransferOnLAN.jar file with the command ```
java -jar /full/path/to/TransferOnLAN.jar
```

aj,I extracted the tar.gz to home,and ran the 1st command,and got this output:
```
john@john-OptiPlex-GX260:~$ java -jar /full/path/to/TransferOnLAN.jar
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
john@john-OptiPlex-GX260:~$ 
```
not sure where to go from here.

---

### Post by ajgreeny on 2012-11-11
It sounds as if you don't have java installed on your machine so try ```
sudo apt-get install openjdk-6-jre
``` if you are using 10.04, or openjdk-7-jre if on 12.04.  You can also use synaptic, of course.

It is also worth adding the icedtea plugin, so search for that and install it in synaptic as well.

---

### Post by Whoopie on 2012-11-11
I can recommend [nitroshare]("https://code.launchpad.net/nitroshare").

It's also available for Linux and Windows.

---

### Post by ssulaco on 2012-11-11
> **ajgreeny said:**
> It sounds as if you don't have java installed on your machine so try ```
sudo apt-get install openjdk-6-jre
``` if you are using 10.04, or openjdk-7-jre if on 12.04.  You can also use synaptic, of course.

It is also worth adding the icedtea plugin, so search for that and install it in synaptic as well.
Will do,Thanks

> **Whoopie said:**
> I can recommend [nitroshare]("https://code.launchpad.net/nitroshare").

It's also available for Linux and Windows.
Thanks Whoopie,yea,it would install fine in 12.04,but not 10.04,would get this:
[PHP]Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)[/PHP]

---

### Post by ssulaco on 2012-11-13
> **ajgreeny said:**
> Try **Transfer-on-lan** from [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list).  It is a simple java application, and not only cross *ubuntu family of OSs but also cross platform, ie Linux, Windows, Mac.

Download the tar.gz and extract the TransferOnLAN folder in the archive to somewhere in your home.  Now make a launcher to run the TransferOnLAN.jar file with the command ```
java -jar /full/path/to/TransferOnLAN.jar
```

If you're not sure how to make a launcher in Lubuntu simply open Leafpad and copy the text below into it. Save it as **transferonlan.desktop** file.  Use the full pathway to the java executable jar file, and make sure the .desktop file is executable as well.
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=TransferOnLAN
Comment=Transfer on LAN
Exec=java -jar */home/path/to/TransferOnLAN-0.4.5*/TransferOnLAN.jar
Icon=/path/to/chosen/icon
Terminal=false
Type=Application
# MimeType=text/plain
# Categories=GTK;Utility;Network;
```

I use this a lot between several machines in the household and find it extremely good.  It is not a real alternative to, for example, using ssh over the network, as files will only go in the the one direction, ie, away from the machine you're working on, but it is nevertheless a very useful utility and does exactly what it sets out to do.
I'm missing something in these steps....
after installing Java I run the first command and get this:
```
john@john-OptiPlex-GX260:~$ java -jar /full/path/to/TransferOnLAN.jar
Unable to access jarfile /full/path/to/TransferOnLAN.jar
john@john-OptiPlex-GX260:~$ 
```
I create the Launcher,and make it executable and try running the above command again,and/or try the Launcher,no effect,I try opening the TransferOnLAN.sh file,which gives me the option Execute,Execute in terminal,Open or Cancel,still cant get it to open,I might be missing this:> Use the full pathway to the java executable jar file, and make sure the .desktop file is executable as well.
I tried all the above with the Ubuntu 10.04 box,I can open it by clicking on the .sh file.

---

### Post by ajgreeny on 2012-11-13
```
john@john-OptiPlex-GX260:~$ java -jar /full/path/to/TransferOnLAN.jar
Unable to access jarfile /full/path/to/TransferOnLAN.jar
john@john-OptiPlex-GX260:~$
```I didn't mean you to copy the full pathway to the shell script like that; it was just a way to show you how to add the full path.

So if the ToL folder is in your Downloads folder in home use ```
java -jar /home/*your-username*/Downloads/TransferOnLAN-0.4.10/TransferOnLAN.jar
``` but again, enter your proper username, not "your-username" in the path as I show it here.

Double clicking on the .sh shell-script, and choosing Execute in terminal should also start the application, so I am not sure what is going wrong for you.

---

### Post by ssulaco on 2012-11-13
> **ajgreeny said:**
> I didn't mean you to copy the full pathway to the shell script like that; it was just a way to show you how to add the full path.
I understand,Im not proficient at cli and or shell scripts,it opens with this.
```
java -jar /home/john/TransferOnLAN-0.4.10/TransferOnLAN.jar
```
Oddly after running this,and Tol opens,I closed it and went in and tried opening it with the .sh shell script,click execute and it worked.
Thanks ajgreeny for your help.

---

