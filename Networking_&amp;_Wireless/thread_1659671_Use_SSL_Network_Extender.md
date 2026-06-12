---
title: "Use SSL Network Extender"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by AlanAbbott on 2011-01-04
I've done all I found in this forum with no success. I upgraded to 10.10 (64bit) then  got a 32bit machine. I still can not connect to  my clients net with enithing but Windows. I get:

This software requires Sun Java to be installed and enabled.If you are prompted to confirm the use of Java, make sure that you select 'Always' in the Confirmation message.

You might need to restart your browser before attempting to connect again.

When SNX/extender (SSL Network Extender) in invoked
it tries to run snx_install.sh and I get "The following plug-in has crashed: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

The JAVA i'm using is:
alan@AlanA1ubu:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu2)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

And Ubuntu is 10.10 on a 32bit machine, I tried to no avail on a 64bit machine with Ubuntu 10.04 and now 10.10

---

### Post by gmargo on 2011-01-04
If you enable the Canonical "partners" repository, you will be able to install the Sun (now Oracle) version of Java.

You'll be looking for the **sun-java6-jre** package, and perhaps the jdk.  Here's all of them:

```

$ apt-cache search sun-java6
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)

```

---

### Post by AlanAbbott on 2011-01-06
Now I get a return in Status of "Pending user reconnection" from SSL Network Extender. Something has changed, but I still can not loggin.

What should I do next?

Alan

---

### Post by AlanAbbott on 2011-01-12
I contacted Check Point Software Technologies Ltd and they informend me that their product dose not work with UBUNTU but that it did work under RED HAT.
Do I have to abandon UBUNTU and change to RED HAT if I want to continue with linux as I need to connect to where my bread and butter comes from.

---

### Post by gmargo on 2011-01-12
I wish I could help but I have no access to the software or any way to test it.  However I could download their release notes.  They claim to support Linux 32-bit: Fedora 8, Ubuntu 7, Linux RHEL 3.0, Linux Suse 9 and up, Red Had Linux 7.3.  All of which are quite old. Although the Suse says "and up".  You could try to load one or more into a virtual machine and try it from within.

---

### Post by jose.goncalves on 2012-01-03
It works in Ubuntu. 32bit or 64bit.

Just execute it first with root permissions:

1. Alt-F2
2. gksudo firefox
3. Login to VPN

After these steps you dont need root anymore, just execute in a normal browser.

---

### Post by rschmidt13 on 2012-02-21
The Firefox Java Plug-in has to be installed manually under Linux. Click Tools->Add-ons to find out if it is already installed. To install the Java Plugin you have to manually set a symbolic link within the Mozilla Plugin folder. Try something like this:

cd /usr/lib/mozilla/plugins
sudo ln -s /opt/java/jre/lib/i386/libnpjp2.so

or read: 

[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

---

### Post by gioradix on 2012-07-23
My Ubuntu is 12.04 64 Bit:
I installed snx network extender via script 
sudo ./installsnx.sh

snx -h
shows a problem with libpam.so, the problem is that I have the 64bit installed, i just downloaded 32 bit version and reinstalled.

then I installed ia32-libs packages to have all 32 Bit linked library.

For me I can't use Firefox and java plugin but I can connect via snx using command line and passing the necessary parameters for my connection.

I don't know which version of network extender (snx) I'm using because I downloaded from the web login page of my working company.

I can connect to remote desktop of my Windows Servers via Ubuntu !!

I hope it could by useful.

Gio

---

### Post by alcarraz on 2012-08-20
Hello gioradix I tried what you said but still with the ia32-lib installed have the libpam.so.0 problem, there is some step I might forgotten after installin ia32-lib package?

Thanks in advance

> **gioradix said:**
> My Ubuntu is 12.04 64 Bit:
I installed snx network extender via script 
sudo ./installsnx.sh

snx -h
shows a problem with libpam.so, the problem is that I have the 64bit installed, i just downloaded 32 bit version and reinstalled.

then I installed ia32-libs packages to have all 32 Bit linked library.

For me I can't use Firefox and java plugin but I can connect via snx using command line and passing the necessary parameters for my connection.

I don't know which version of network extender (snx) I'm using because I downloaded from the web login page of my working company.

I can connect to remote desktop of my Windows Servers via Ubuntu !!

I hope it could by useful.

Gio

---

### Post by lafouine29 on 2012-10-21
Did anyone face the problem of being connected (after an apparent successful installation) and not being able to do anything ?
I can connect through the web interface and everything seems alright. But I can't do anything (can't reach anything, no ping...).
(icedtea-plugin with both up-to-date ubuntu and kubuntu -tried on two different machines and installations, with firefox or chrome... behind personal WiFi connection if that could matter)... I don't understand. Maybe I miss sthg obvious (never had to use that before).
Thnak you very much for any hint you might have.
Complementary tests :
- no success either with sun-java6...
- tunnel is set (as shown by the connection pop-up window and ifconfig)
- ping only works with the "Office Mode IP" provided by the applet
... DNS resolving issue ?

---

