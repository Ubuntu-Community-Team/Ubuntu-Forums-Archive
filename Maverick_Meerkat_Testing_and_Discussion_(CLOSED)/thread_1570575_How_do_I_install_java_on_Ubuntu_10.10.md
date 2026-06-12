---
title: "How do I install java on Ubuntu 10.10?"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by BobPOW on 2010-09-08
Hi everybody.  I spend the entirety of August 2010 playing around with Ubuntu 10.04.

I'm now using the new Ubuntu 10.10.  I'd like to learn how to install Linux programs on it.  Right now I am mostly interested in [Java SDK]("http://www.oracle.com/technetwork/java/javase/downloads/index.html").

I can't use the software manager because my computer has no internet connection (long story, has nothing to do with Ubuntu).  Do I use the terminal to install programs?  How do I use the terminal?

Thanks for reading this.  I'm happy to see a freeware operating system being supported by hundreds of thousands of people.

---

### Post by sharathcshekhar on 2010-09-08
If you do not have internet, you will have to download binaries from a computer which has internet(.deb files) from here 
[http://packages.ubuntu.com/lucid/java/]("http://packages.ubuntu.com/lucid/java/"), take in a pen drive or cd and put it in your computer, use ubuntu installer to install it. 
To install from terminal,
```

dpkg -i name_of_package.deb

```

---

### Post by Achilles124 on 2010-09-08
No internetconnection? That means you cannot download additional software with synaptic or with Ubuntu softwarecenter.

Can you not download with a 56K connection?

---

### Post by BobPOW on 2010-09-08
> **sharathcshekhar said:**
> If you do not have internet, you will have to download binaries from a computer which has internet(.deb files) from here 
[http://packages.ubuntu.com/lucid/java/](http://packages.ubuntu.com/lucid/java/), take in a pen drive or cd and put it in your computer, use ubuntu installer to install it. 
To install from terminal,
```

dpkg -i name_of_package.deb

```

I don't see anything about Java SDK from that link, just a bunch of files.  The official Java SDK from Sun.com is a binary file.  How do I install that?

> **Achilles124 said:**
> No internetconnection? That means you cannot  download additional software with synaptic or with Ubuntu  softwarecenter.

Can you not download with a 56K connection?

My family got broadband internet access a couple a years ago when I was living across the country.  I am unable to connect my computer to their internet because of a lost password.

---

### Post by Elfy on 2010-09-08
If you have no internet connection then I would think that installing a development version that could in all likelihood get many updates available daily might cause to a problematic for a while.

Aside from that - moved to meerkat forum.

---

### Post by ratcheer on 2010-09-08
> **BobPOW said:**
> I don't see anything about Java SDK from that link, just a bunch of files.  The official Java SDK from Sun.com is a binary file.  How do I install that?



All you have to do is move or copy that file to a location where you want to install Java and execute the file. I do it in /opt, but it doesn't really matter where you put it. You may need to execute it under sudo.

At that point, Java is "installed" but your system doesn't know about it. For general use, just put a couple of environment variables in your profile. One is JAVA_HOME and the other is CLASSPATH. I will have to get back to you with the specifics, as this is my Maverick testing system and I have never installed Java on it, either.

The other task is to link one of the Java executables to your web browser. I will log on to Lucid and give you those specific instructions, too.

Tim

---

### Post by ratcheer on 2010-09-08
Here are the details I promised. Apparently, I executed the file in /usr/java the last time I installed, so here are the environment variables I set:

```

JAVA_HOME=/usr/java/jre1.6.0_20
CLASSPATH=$JAVA_HOME/lib

```

Now, to link it to the web browser (I use Firefox), cd to the plugins directory and create a symbolic link to the Java file libnpjp2.so. For example, on my system, in directory /usr/lib/firefox/plugins, run:

```

ln -s /usr/java/jre1.6.0_20/lib/i386/libnpjp2.so .

```

I hope I have not overlooked anything, but it has been some time since I set all this up.

Tim

---

### Post by ktp on 2010-09-08
if you need sun jvm, you can download the deb from the Partner repository:

[http://archive.canonical.com/pool/partner/s/sun-java6/](http://archive.canonical.com/pool/partner/s/sun-java6/)

---

### Post by ktp on 2010-09-08
> **BobPOW said:**
> I don't see anything about Java SDK from that link, just a bunch of files.  The official Java SDK from Sun.com is a binary file.  How do I install that?

I would use the deb from previous post, but this explains how to install the sun JDK Self-Extracting Binary:

[http://www.oracle.com/technetwork/java/javase/install-linux-self-extracting-138783.html](http://www.oracle.com/technetwork/java/javase/install-linux-self-extracting-138783.html)

> % chmod a+x jdk-6u <version>-linux-i586.bin
% ./jdk-6u <version>-linux-i586.bin

---

### Post by bredman on 2010-09-09
The official method to install without an internet connection can be found in chapter 5 of
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by bredman on 2010-09-09
Slightly off the java topic, you say that you cannot connect to your family's internet connection because of a lost password.

I assume you mean that you have lost the password to your ADSL or Cable modem. I suggest that you search the net for the user guide for the modem, and reset it to factory defaults. Then you can choose a new password.

---

### Post by ktp on 2010-09-09
technically that is not official...it is community document.  Just saying.

---

### Post by nilarimogard on 2010-09-12
> **BobPOW said:**
> Hi everybody.  I spend the entirety of August 2010 playing around with Ubuntu 10.04.

I'm now using the new Ubuntu 10.10.  I'd like to learn how to install Linux programs on it.  Right now I am mostly interested in [Java SDK]("http://www.oracle.com/technetwork/java/javase/downloads/index.html").

I can't use the software manager because my computer has no internet connection (long story, has nothing to do with Ubuntu).  Do I use the terminal to install programs?  How do I use the terminal?

Thanks for reading this.  I'm happy to see a freeware operating system being supported by hundreds of thousands of people.

You can install it by temporarily using the Lucid partner repository in Ubuntu 10.10. See [here]("http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html").

---

### Post by cjnkns on 2010-09-15
I have seen blogs that mention the sun-jdk being available in the 
add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

If I add this repo when I am using 10.10 .. how do I know it is ok to simply just remove it when it is available in the maverick repos?

Will sun-java be available in the maverick repos?

This article says it's going to be removed...

[http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010?utm_source=am6_feedtweet&utm_medium=twitter&utm_campaign=toya256ForRSS]("http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010?utm_source=am6_feedtweet&utm_medium=twitter&utm_campaign=toya256ForRSS")

---

### Post by rworloma on 2010-09-21
Read this post at [Liberian Geek]("http://www.liberiangeek.net/2010/09/install-sun-java-runtime-environment-jre-ubuntu-10-10-maverick-meerkat/").

---

### Post by ratcheer on 2010-09-22
> **rworloma said:**
> Read this post at [Liberian Geek]("http://www.liberiangeek.net/2010/09/install-sun-java-runtime-environment-jre-ubuntu-10-10-maverick-meerkat/").

Great post. Thank you.

Tim

---

### Post by kuvanito on 2010-09-23
rworloma,thanks for the link,that did it :P

---

