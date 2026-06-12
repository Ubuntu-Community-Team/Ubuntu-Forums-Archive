---
title: "Java Ubuntu 11.04"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sadf on 2010-12-17
Hi, I'm new in Linux. I was able to install Ubuntu 11.04. Now, I'm trying to install Java SDK, Eclipse and all Java stuff so I can start programming with Java. How do you do it? Where do I start. Your help is very much appreciated. Thanks.

Sadf

---

### Post by Elfy on 2010-12-17
If you are not sure hwo to do those fairly basic tasks then I wonder whether you should be running the dev version which is extremely likely to crash and not boot or any other myriad issues before it reaches even Beta.

In the meantime moved to the dev forum


[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by uRock on 2010-12-17
You may want to install a stable version of Ubuntu, such as 10.04 or 10.10.

---

### Post by Com_2_Reset on 2010-12-17
Hello..

If u are using Ubuntu 10.10 :
1- System>Administration> Synaptic Package Manager>Settings>Repositories
2- Select **Other Software** then Mark the **Canonical Partners** (first line) then press **Close**
3- You have to reload the [B]Synaptic Package Manager
[/B]4- In the** Quick Search** box, write  **[COLOR=Red]sun-java6-jdk[/COLOR]**
5- Now you can see  **[COLOR=Red]sun-java6-jdk [COLOR=Black]and [/COLOR][/COLOR]** **[COLOR=Red]sun-java6-jre[/COLOR]**. Both of them Version 6.22
6- Right click the first one  **[COLOR=Red]sun-java6-jdk[COLOR=Black] ([/COLOR][/COLOR]**[COLOR=Red][COLOR=Black]which is for developer to use Netbeans or other[/COLOR][/COLOR]**[COLOR=Red][COLOR=Black])[/COLOR][/COLOR]**[COLOR=Red][COLOR=Black] Select[/COLOR][/COLOR]**[COLOR=Red][COLOR=Black] Mark for Installation [/COLOR][/COLOR]**
7- Do the same thing with  [B][COLOR=Red]sun-java6-jre [COLOR=Black](Java Run Time)[/COLOR]
[/COLOR][/B]

---

### Post by gamecraziness on 2011-02-06
Sorry for bumping, but the instructions here are not quite accurate. Java is not yet in the natty repositories, so you have to do the following:

1. Open Synaptic
2. Go to Settings>Repositories>Other Software
3. Click Add...
4. Type "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner" in the box
5. Press the reload button
6. Now install sun-java6-jre and sun-java6-jdk

---

### Post by jocko on 2011-02-06
If you're new to linux, **don't use a development version**. 11.04 is still in the alpha stage of development, which means it is constantly being changed and it is very likely that an update will break your OS soon.
Either wait until it's released (11.04 will be released in the end of April) or use a stable version (the newest stable version is 10.10, released in October 2010...).

Edit: Apparently this was an old thread... The op probably already gave up on natty...

---

### Post by YesWeCan on 2011-02-06
> **sadf said:**
> Hi, I'm new in Linux. I was able to install Ubuntu 11.04. Now, I'm trying to install Java SDK, Eclipse and all Java stuff so I can start programming with Java. How do you do it? Where do I start. Your help is very much appreciated. Thanks.

Sadf

You just visit the Oracle site and download it. :-|

---

### Post by zika on 2011-02-06
I'm using:
[http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b128-linux-x64-03_feb_2011.bin](http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b128-linux-x64-03_feb_2011.bin)
(386):[http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b128-linux-i586-03_feb_2011.bin](http://www.java.net/download/jdk7/binaries/jdk-7-ea-bin-b128-linux-i586-03_feb_2011.bin)

---

### Post by Yellow Pasque on 2011-02-06
Download the java (6u23) maverick debs from: [https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)
OR use the aforementioned canonical repo if you do not mind a slightly outdated version (6u22).

> You just visit the Oracle site and download it.
Better to find a .deb package..

---

### Post by Zlatan on 2011-02-06
sumerising:

- get a stable ubuntu- 10.04LTS or 10.10 (ubuntu.com -> Get ubuntu)
ubuntu 11.04 is a version to be released in 2011 april
ubuntu 10.04LTS is a long time support version  released in 2010 april to be supported for 3yrs desktop and 5yrs derver
10.10 is a regular latest stable verion to be supported for usual 18months
ubuntu is released every 6 months

- enable partner repository (check software sources 2nd tab), you need that because sun java is not foss anymore, click reload
by default only foss (check wikipedia for that) software repositories are enabled by default in ubuntu
but you can enable partner repositories anyway to install flash, java, mp3, fonts and codecs

- look for your required software in ubuntu software center or synaptic package manager and install it
only look for required for software in ubuntu software center or synaptic package manager because all software will be safe and prepackaged for your ubuntu. never go to any kind of websites for any kind of software if you aware of your system safety and stability

- post again if any questions/probems

---

### Post by pferraro on 2011-02-06
The answer to the ops question is far simpler than the above responses - install the "default-jdk" package.  This is a meta package that depends on ubuntu's default/supported java development kit, i.e. openjdk.

---

### Post by YesWeCan on 2011-02-06
I have had bad experiences with openJDK. it is not the same as the bona fide Oracle/Sun Java. I use 10.04 64-bit and I always install directly from the Java site and/or Netbeans site and it always works perfectly for me. Sun Java is proper software of very high standard.

---

### Post by sammiev on 2011-02-06
> **YesWeCan said:**
> I have had bad experiences with openJDK. it is not the same as the bona fide Oracle/Sun Java. I use 10.04 64-bit and I always install directly from the Java site and/or Netbeans site and it always works perfectly for me. Sun Java is proper software of very high standard.

+1 My kids like pogo and other sites which openJDK just do not work. GL :)

---

### Post by lykeion on 2011-02-07
@YesWeCan & sammiev
OP asked how to install Java SDK & Eclipse to start programming in Java. Not playing games that need the Sun/Oracle Java browser plugin. The discussion whether Sun/Oracle Java is proper/bona fide as opposed to OpenJDK seems out of place.

---

### Post by sammiev on 2011-02-07
> **lykeion said:**
> @YesWeCan & sammiev
OP asked how to install Java SDK & Eclipse to start programming in Java. Not playing games that need the Sun/Oracle Java browser plugin. The discussion whether Sun/Oracle Java is proper/bona fide as opposed to OpenJDK seems out of place.

Try [this]("http://sites.google.com/site/easylinuxtipsproject/java#TOC"). Worked great for me and is good for 32 or 64 bit OS. GL :)

---

### Post by lykeion on 2011-02-07
Sorry if I repeat myself but that guide^^ is to install Sun Java JRE not the JDK. The question was how to install JDK to start programming in Java.

---

### Post by cariboo on 2011-02-07
I don't use eclipse, but if you mark eclipse for installation in synaptic, it seems to pull in all the needed dependencies and recommends, did the op try that?

---

