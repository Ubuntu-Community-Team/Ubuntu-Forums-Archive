---
title: "Installing Java 1.5?"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by mikeaguilar1 on 2007-02-17
Alright i tried installing Frostwire but this is what i get when i go to terminal and type in "frostwire"

mike@mike-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
mike@mike-desktop:~$ 


So where can i get Java 1.5? and can i get the exact name i need.

---

### Post by maxamillion on 2007-02-17
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins)

---

### Post by mikeaguilar1 on 2007-02-18
> **maxamillion said:**
> [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins)

still dosent work I installed it but still nothing.

ughh i get the same error message. heeeelp.

---

### Post by phossal on 2007-02-18
Have you run this:
```
sudo update-alternatives --config java
```
If you're installing Java just to run Lime(*or Frost*)Wire, I would install both Java and FrostWire using the downloads available directly from each of them. I can walk you through it if the command I offered first doesn't work and you're willing to consider an alternative.

---

