---
title: "New Sun Java from LffL PPA"
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-20
You can download the latest Sun Java for Lucid, Maverick and Natty from the LffL PPA.
The version is 6.24-1.
Here:
[https://launchpad.net/~ferramroberto/+archive/java/+packages](https://launchpad.net/~ferramroberto/+archive/java/+packages)

---

### Post by zika on 2011-02-20
> **Harry33 said:**
> You can download the latest Sun Java for Lucid, Maverick and Natty from the LffL PPA.
The version is 6.24-1.
Here:
[https://launchpad.net/~ferramroberto/+archive/java/+packages](https://launchpad.net/~ferramroberto/+archive/java/+packages)
64-bit plugin or...?

P.S. I guess it IS 64-bit...

(I'm using Sun7 preview...)

---

### Post by Harry33 on 2011-02-20
> **zika said:**
> 64-bit plugin or...?

P.S. I guess it IS 64-bit...

(I'm using Sun7 preview...)

Yes there are also the native 64-bit browser plugin included.
That has been around for quite some time.

---

### Post by recluce on 2011-02-20
> **zika said:**
> 64-bit plugin or...?

P.S. I guess it IS 64-bit...

(I'm using Sun7 preview...)

Why don't you just take a look at the PPA? 32 and 64bit....

---

### Post by ratcheer on 2011-02-20
I don't immediately discern the code to add the apt source. I tried:

deb [http://ppa.launchpad.net/ferramroberto/lffljava/ubuntu]("http://ppa.launchpad.net/ferramroberto/lffl/ubuntu") maverick main

but got "404 not found".

What exactly am I supposed to put?

Tim

---

### Post by zika on 2011-02-20
> **recluce said:**
> Why don't you just take a look at the PPA? 32 and 64bit....I did look... I asked afterwards...
Names of .deb's does not guarantee what I have asked about...

---

### Post by cariboo on 2011-02-20
@ratcheer

Have a look [here]("https://launchpad.net/~ferramroberto/+archive/java")

---

### Post by ratcheer on 2011-02-20
> **ratcheer said:**
> I don't immediately discern the code to add the apt source. I tried:

deb [http://ppa.launchpad.net/ferramroberto/lffljava/ubuntu]("http://ppa.launchpad.net/ferramroberto/lffl/ubuntu") maverick main

but got "404 not found".

What exactly am I supposed to put?

Tim

Never mind. I found it by going to his Overview. It is:

deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu]("http://ppa.launchpad.net/ferramroberto/lffl/ubuntu") maverick main

Tim

---

### Post by donniezazen on 2011-02-20
Are you suppose to remove iced tea browser plugin if you use sun java?

---

### Post by Harry33 on 2011-02-20
> **soham_1207 said:**
> Are you suppose to remove iced tea browser plugin if you use sun java?

Yes definitely.
Also you need to remove the whole open source java (open-jdk-6-*) before Sun Java too.

---

### Post by ratcheer on 2011-02-20
> **Harry33 said:**
> Yes definitely.
Also you need to remove the whole open source java (open-jdk-6-*) before Sun Java too.

Actually, you don't. If both Java's were installed with the package management system, you can use update-java-alternatives to select which one you want your system to use.

Tim

---

### Post by Harry33 on 2011-02-21
> **ratcheer said:**
> Actually, you don't. If both Java's were installed with the package management system, you can use update-java-alternatives to select which one you want your system to use.

Tim

I prefer to uninstall any package I am not using/don't need.
It is much easier to debug the system and trace bugs and irregularities when system is simple.
Natty is at a development stage and it I think this is a better way to isolate the possible problems.
Personally I need Sun Java beause my web bank does not accept authentication with openjdk.
Openjdk does not give me any advantage. If I later can use it, I'll install it then.

---

### Post by ratcheer on 2011-02-21
> **Harry33 said:**
> I prefer to uninstall any package I am not using/don't need.
It is much easier to debug the system and trace bugs and irregularities when system is simple.
Natty is at a development stage and it I think this is a better way to isolate the possible problems.
Personally I need Sun Java beause my web bank does not accept authentication with openjdk.
Openjdk does not give me any advantage. If I later can use it, I'll install it then.

I personally agree, but that is different from "you need to".

Tim

---

### Post by plun on 2011-02-21
Thanks Harry....

This is a massive security update which fixes a lot of issues.:-\"

Info:
[http://secunia.com/advisories/43262/](http://secunia.com/advisories/43262/)


Just to add **ppa:ferramroberto/java** to Software Sources

Test page
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)


...

---

### Post by zika on 2011-02-21
> **plun said:**
> Test page
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)
...
```
Oops! You don't have the recommended Java installed.
Your Java version is 1.7.0-ea. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

Download Free Java Software
Version 6 Update 24
```[img]http://images.mylot.com/userImages/images/postphotos/2148276.gif[/img]

(sorry for off-topic, I couldn't help myself, just a joke... This is actual output of that test Webpage... I do use it often...)

---

### Post by Harry33 on 2011-02-21
> **zika said:**
> ```
Oops! You don't have the recommended Java installed.
Your Java version is 1.7.0-ea. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

Download Free Java Software
Version 6 Update 24
```[img]http://images.mylot.com/userImages/images/postphotos/2148276.gif[/img]

(sorry for off-topic, I couldn't help myself, just a joke... This is actual output of that test Webpage... I do use it often...)

That may be due to the fact that v. 6 update 24 is the latest stable.
Whereas v. 1.7 is a development series.

Then again, it is a known issue, that some community arguments and to some extent also licence issues are preventing JCP (Java Community Process) executive committees not to approve new JSR.

---

### Post by zika on 2011-02-22
> **Harry33 said:**
> That may be due to the fact that v. 6 update 24 is the latest stable.
Whereas v. 1.7 is a development series.

Then again, it is a known issue, that some community arguments and to some extent also licence issues are preventing JCP (Java Community Process) executive committees not to approve new JSR.Again, You're totally right... I, again, admit, that this was (improper maybe) just a joke...

---

### Post by Harry33 on 2011-02-22
> **zika said:**
> Again, You're totally right... I, again, admit, that this was (improper maybe) just a joke...

No not at all improper, zika.
And a good point too.

---

### Post by Krause on 2011-02-22
> **zika said:**
> (I'm using Sun7 preview...)

You managed to get it working as a browser plugin? Was it 64 bit? I was never able to do that with Java 7, and there is practically no info out on it. Mind telling me how you did it?

Also there is a better java tester on Javas website, lists a bit more info and shows you a working java applet. It never seemed to care when I was using Java 7 on windows either :P

[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

---

### Post by zika on 2011-02-22
> **Krause said:**
> You managed to get it working as a browser plugin? Was it 64 bit? I was never able to do that with Java 7, and there is practically no info out on it. Mind telling me how you did it?

Also there is a better java tester on Javas website, lists a bit more info and shows you a working java applet. It never seemed to care when I was using Java 7 on windows either :P

[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)
Using that site several times a week...
```
Your Java configuration is as follows:  Vendor: Oracle Corporation Version: Java SE 7 Operating System: Linux 2.6.38-999-generic Architecture: amd64
``````
:~$ java -version
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b130)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b02, mixed mode)
```It works everywhere I tested it, even with serious math's stuff (I'm nutty mathematician...)

```
0. cd ~/ZIKA
1. wget [http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b129-linux-x64-10_feb_2011.bin](http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b129-linux-x64-10_feb_2011.bin)
2. un-pack (several ways to do that, be carefull, You need to be able to answer to the question in the script...) jdk-7-ea-bin-b129-linux-x64-10_feb_2011.bin
2.1 rm jdk-7-ea-bin-b129-linux-x64-10_feb_2011.bin 
3. rm -rf ~/ZIKA/JDK
3.1 mv ~/ZIKA/jdk ~/ZIKA/JDK
4. ln -s ~/.mozilla/plugins/libnpjp2.so ~/ZIKA/JDK/jre/lib/amd64/libnpjp2.so
5. sudo update-alternatives --install "java" "~/ZIKA/JDK/bin/java" 1
6. (optional)sudo ln -s /usr/lib/mozilla/plugins/libnpjp2.so ~/ZIKA/JDK/jre/lib/amd64/libnpjp2.so
(There are several purposeful syntactical ambiguities) 
```

---

