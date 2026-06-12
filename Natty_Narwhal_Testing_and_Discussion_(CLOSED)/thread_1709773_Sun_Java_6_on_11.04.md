---
title: "Sun Java 6 on 11.04?"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Cam! on 2011-03-18
Minecraft's a bit slow, so I figured I could switch to Sun Java. How do I install it on 11.04? (Alpha 3, 32bit)

---

### Post by galacticaboy on 2011-03-18
Try finding it in Synaptic, if you don't have synaptic, sudo apt-get install synaptic. If that does not work, have you tried installing java through the terminal?

---

### Post by cariboo on 2011-03-18
Sun Java is in the partner repositories, although there isn't a version for Natty yet, you could probably get away with using the maverick version. You should be able to get it from [packages.ubuntu.com]("http://packages.ubuntu.com/").

---

### Post by zika on 2011-03-19
Did You try Java 7?
If You would like to give it a try:
1. use [http://download.java.net/jdk7/](http://download.java.net/jdk7/) to DL... I use JRE...
2. extract archive in some folder (let us call it zika)
3. rename jre... to JRE (just for sake of simplicity and to have the same name after upgrade)
3. **sudo update-alternatives --install "/usr/bin/java" "java" "/zika/JRE/bin/java" 1**
4. go to ~/.mozilla/plugins and do: **ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
5. go to /usr/lib/mozilla/plugins/libnpjp2.so and do: **sudo ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
6. Enjoy!

---

### Post by Harry33 on 2011-03-19
There is also a PPA for Sun Java (6.24-1) for Natty.
Here:
[https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java)

---

### Post by dino99 on 2011-03-19
> **zika said:**
> Did You try Java 7?
If You would like to give it a try:
1. use [http://download.java.net/jdk7/](http://download.java.net/jdk7/) to DL... I use JRE...
2. extract archive in some folder (let us call it zika)
3. rename jre... to JRE (just for sake of simplicity and to have the same name after upgrade)
3. **sudo update-alternatives --install "/usr/bin/java" "java" "/zika/JRE/bin/java" 1**
4. go to ~/.mozilla/plugins and do: **ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
5. go to /usr/lib/mozilla/plugins/libnpjp2.so and do: **sudo ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
6. Enjoy!

Be aware: Latest release is Version 6 Update 24 

Version 7 will be available not before end of Jul 2011

---

### Post by zika on 2011-03-19
> **dino99 said:**
> Be aware: Latest release is Version 6 Update 24 

Version 7 will be available not before end of Jul 2011Yes, I thought I wrote, but, obviously, I did not, it is a prelease... Sorry...
Nevertheless, recipe given above works for most of Java (jre and jdk) packages on Oracle and similar sites...

---

### Post by cariboo on 2011-03-19
> **Harry33 said:**
> There is also a PPA for Sun Java (6.24-1) for Natty.
Here:
[https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java)

Thanks Harry33, I forgot about the ppa.

---

### Post by TTT_Dutch on 2011-03-20
> **zika said:**
> Did You try Java 7?
If You would like to give it a try:
1. use [http://download.java.net/jdk7/](http://download.java.net/jdk7/) to DL... I use JRE...
2. extract archive in some folder (let us call it zika)
3. rename jre... to JRE (just for sake of simplicity and to have the same name after upgrade)
3. **sudo update-alternatives --install "/usr/bin/java" "java" "/zika/JRE/bin/java" 1**
4. go to ~/.mozilla/plugins and do: **ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
5. go to /usr/lib/mozilla/plugins/libnpjp2.so and do: **sudo ln -s /zika/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
6. Enjoy!

Hello,
I am new here and I was trying to update to Java 7 and I think I screwed a few things up. I have uninstalled anything java now. Then I tried this tut to see if I could run minecraft and I couldn't. This tut worked but when I try to run 'java -jar minecraft' I get: java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

Can you help me out? Becaue I heard that Java 7 runs miecraft much better.

---

### Post by Harry33 on 2011-03-20
> **TTT_Dutch said:**
> Hello,
I am new here and I was trying to update to Java 7 and I think I screwed a few things up. I have uninstalled anything java now. Then I tried this tut to see if I could run minecraft and I couldn't. This tut worked but when I try to run 'java -jar minecraft' I get: java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

Can you help me out? Becaue I heard that Java 7 runs miecraft much better.

The best advice is to use a released stable version only.
You can find them from Maverick partner repository of from here:
[https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java)

If you install from a website directly, always be sure to read the uninstall process first.
Ubuntu is not a Micro.... system. It is not a good practise to install anything from a weg page. Repositories should be used.

---

### Post by zika on 2011-03-20
> **TTT_Dutch said:**
> Hello,
I am new here and I was trying to update to Java 7 and I think I screwed a few things up. I have uninstalled anything java now. Then I tried this tut to see if I could run minecraft and I couldn't. This tut worked but when I try to run 'java -jar minecraft' I get: java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

Can you help me out? Becaue I heard that Java 7 runs miecraft much better.What do you get from the following?```
java -version
```In my case I get```
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b134)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b04, mixed mode)
```Library that You're mentionng should be in /zika/JRE/lib/amd64/jli/libjli.so, whatever You've used instead of &#8222;zika&#8220;...
> **Harry33 said:**
> The best advice is to use a released stable version only.
You can find them from Maverick partner repository of from here:
[https://launchpad.net/~ferramroberto/+archive/java]("https://launchpad.net/%7Eferramroberto/+archive/java")

If you install from a website directly, always be sure to read the uninstall process first.
Ubuntu is not a Micro.... system. It is not a good practise to install  anything from a web page. Repositories should be used.As much as I can see Your point, even though I do not see where Micro... gets in the picture, I think that the way of introducing Java as I wrote in my post is as much reversible as any .deb in any ppa, if not, even more reversible. By going through &#8222;my&#8220; recipe backwards You can clean everything and get system in just the same state before applying it, which is, simply, not the case with all .deb... 
So, I will stop here and, just, let You go with repositories...

---

### Post by Harry33 on 2011-03-20
> **zika said:**
> What do you get from the following?```
java -version
```In my case I get```
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b134)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b04, mixed mode)
```Library that You're mentionng should be in /zika/JRE/lib/amd64/jli/libjli.so, whatever You've used instead of „zika“...
As much as I can see Your point, even though I do not see where Micro... gets in the picture, I think that the way of introducing Java as I wrote in my post is as much reversible as any .deb in any ppa, if not, even more reversible. By going through „my“ recipe backwards You can clean everything and get system in just the same state before applying it, which is, simply, not the case with all .deb... 
So, I will stop here and, just, let You go with repositories...

Zika, I know you are not a noob.
I am sure you can handle this kind of installations.
It is just that beginners keep asking quite a lot of help these days here, in a similar situations.
It  would be better to learn Linux basics first and then install directly from a website (be it amd.com, nvidia.com or whatever). ):P

---

### Post by zika on 2011-03-20
> **Harry33 said:**
> Zika, I know you are not a noob.
I am sure you can handle this kind of installations.
It is just that beginners keep asking quite a lot of help these days here, in a similar situations.
It  would be better to learn Linux basics first and then install directly from a website (be it amd.com, nvidia.com or whatever). ):POh, but I am a noob, I'll be a noob until I die and I'll die as a noob... :)
I'm here if I could help in any way, I will try, that's for sure... ):P

---

### Post by Harry33 on 2011-03-20
> **zika said:**
> Oh, but I am a noob, I'll be a noob until I die and I'll die as a noob... :)
I'm here if I could help in any way, I will try, that's for sure... ):P

:) A man who says he is a noob, really is not one.

---

### Post by TTT_Dutch on 2011-03-20
> **zika said:**
> What do you get from the following?```
java -version
```In my case I get```
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b134)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b04, mixed mode)
```Library that You're mentionng should be in /zika/JRE/lib/amd64/jli/libjli.so, whatever You've used instead of &#8222;zika&#8220;...
As much as I can see Your point, even though I do not see where Micro... gets in the picture, I think that the way of introducing Java as I wrote in my post is as much reversible as any .deb in any ppa, if not, even more reversible. By going through &#8222;my&#8220; recipe backwards You can clean everything and get system in just the same state before applying it, which is, simply, not the case with all .deb... 
So, I will stop here and, just, let You go with repositories...

When I run java -version I get:
> java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directoryAlso I have seen the lib and I have the folder with the lib to usr/local/lib and just the lib to that folder. I am not sure what I am doing wrong... BTW I chose my location of java with sudo upated-alternative --config java. Here is what I get when I do type that in:
> There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                 Priority   Status
------------------------------------------------------------
* 0            /tools/JDK/bin/java   1         auto mode
  1            /tools/JDK/bin/java   1         manual mode
  2            /tools/JRE/bin/java   1         manual mode

Press enter to keep the current choice
[*], or type selection number: 


---

### Post by zika on 2011-03-21
> **TTT_Dutch said:**
> When I run java -version I get:
Also I have seen the lib and I have the folder with the lib to usr/local/lib and just the lib to that folder. I am not sure what I am doing wrong... BTW I chose my location of java with sudo upated-alternative --config java. Here is what I get when I do type that in:
What do You get when You do:```
sudo updatedb
locate libjli.so
```...?
I get ```
:~$ sudo update-alternatives --config java
There is only one alternative in link group java: /...zika.../JRE/bin/java
Nothing to configure.
```Did You ```
sudo update-alternatives --install "/usr/bin/java" "java" "/zika/JRE/bin/java" 1
```with attention to what &#8222;zika&#8220; is really in Your system...? Where did You extract archive...? Did You rename archive to JRE...?
Re-check all the steps I gave... I suspect there is a minor error that prevents everything. Also, remove these java alternatives in /tools/... if You did get them from attempting...

Revised pecipe (with given name of folder instead of one with variable &#8222;zika&#8220;):

1. use [http://download.java.net/jdk7/](http://download.java.net/jdk7/) to DL JRE...
2. extract archive in ~/Java/
3. rename jre... to JRE (just for sake of simplicity and to have the same name after upgrade)
3. **sudo update-alternatives --install "/usr/bin/java" "java" "~/Java/JRE/bin/java" 1**
4. go to ~/.mozilla/plugins and do: **ln -s ~/Java/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
4.1. If You've already made link but for different folder rename it (or remove) before doing 4.
5. go to /usr/lib/mozilla/plugins/libnpjp2.so and do: **sudo ln -s ~/Java/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
5.1. If You've already made link but for different folder rename it (or remove) before doing 5.
6. Enjoy!

---

### Post by TTT_Dutch on 2011-03-21
> **zika said:**
> What do You get when You do:```
sudo updatedb
locate libjli.so
```...?
I get ```
:~$ sudo update-alternatives --config java
There is only one alternative in link group java: /...zika.../JRE/bin/java
Nothing to configure.
```Did You ```
sudo update-alternatives --install "/usr/bin/java" "java" "/zika/JRE/bin/java" 1
```with attention to what „zika“ is really in Your system...? Where did You extract archive...? Did You rename archive to JRE...?
Re-check all the steps I gave... I suspect there is a minor error that prevents everything. Also, remove these java alternatives in /tools/... if You did get them from attempting...

Revised pecipe (with given name of folder instead of one with variable „zika“):

1. use [http://download.java.net/jdk7/](http://download.java.net/jdk7/) to DL JRE...
2. extract archive in ~/Java/
3. rename jre... to JRE (just for sake of simplicity and to have the same name after upgrade)
3. **sudo update-alternatives --install "/usr/bin/java" "java" "~/Java/JRE/bin/java" 1**
4. go to ~/.mozilla/plugins and do: **ln -s ~/Java/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
4.1. If You've already made link but for different folder rename it (or remove) before doing 4.
5. go to /usr/lib/mozilla/plugins/libnpjp2.so and do: **sudo ln -s ~/Java/JRE/lib/amd64/libnpjp2.so libnpjp2.so**
5.1. If You've already made link but for different folder rename it (or remove) before doing 5.
6. Enjoy!

I followed that tut exactly and I get:
```
 brent@brent:~$ java -jar minecraft.jar 
Error: could not find libjava.so
Error: Could not find Java SE Runtime Environment.
```

And when I update the db and run this:
```
brent@brent:~$ locate libjli.so
/home/brent/Java/JRE/lib/amd64/jli/libjli.so
/usr/local/lib/libjli.so
/usr/local/lib/jli/libjli.so

```

I also get the same thing you got when I run the update-alternatives thing.

---

### Post by zika on 2011-03-22
> **TTT_Dutch said:**
> I followed that tut exactly and I get:
```
 brent@brent:~$ java -jar minecraft.jar 
Error: could not find libjava.so
Error: Could not find Java SE Runtime Environment.
```And when I update the db and run this:
```
brent@brent:~$ locate libjli.so
/home/brent/Java/JRE/lib/amd64/jli/libjli.so
/usr/local/lib/libjli.so
/usr/local/lib/jli/libjli.so

```I also get the same thing you got when I run the update-alternatives thing.
You have some java (other than 7) installed also... I guess... Or You have some remnants of previous install...
Did You make 7 as default in update-alternatives?

---

### Post by TTT_Dutch on 2011-03-22
> **zika said:**
> You have some java (other than 7) installed also... I guess... Or You have some remnants of previous install...
Did You make 7 as default in update-alternatives?

I did try and move java executables and libs directly into the local folder. I will remove those now.

EDIT: Hey! I got it to work! I had to install to my usr/local/bin too. Now it is fixed! Java still runs slow though.. At least I can use it though! Thanks again!

---

### Post by zika on 2011-03-23
> **TTT_Dutch said:**
> I did try and move java executables and libs directly into the local folder. I will remove those now.

EDIT: Hey! I got it to work! I had to install to my usr/local/bin too. Now it is fixed! Java still runs slow though.. At least I can use it though! Thanks again!I'm glad... Enjoy!

---

### Post by TTT_Dutch on 2011-03-24
> **zika said:**
> I'm glad... Enjoy!

Hey I have another question if you dont mind.

I am running Ubuntu and it is running slower than windows, which is very embarrassing. SO I heard that formatting your drive to ext3 would speed up ubuntu. (I also cleared out all un-needed files btw) So I was wondering, can I format with out really losing anything? Or do you have any suggestions to speed things up? I mean my computer should be pretty fast as its specs are good.

---

### Post by cariboo on 2011-03-24
I'd suggest you either open a terminal and run top, or open the system monitor and check  to see if there is anything using excess cpu cycles. Ext4 has been proven faster than ext3 in every test I've seen so far.

---

### Post by TTT_Dutch on 2011-03-24
> **cariboo907 said:**
> I'd suggest you either open a terminal and run top, or open the system monitor and check  to see if there is anything using excess cpu cycles. Ext4 has been proven faster than ext3 in every test I've seen so far.

Well nothing gets over 10% right now. SO I don't think its anything in there. Maybe its my grahics card? Anyway, what do you suggest that I use to speed up ubuntu? I am on natty.

EDIT: I feel kinda dumb but I just figured out that I am on ext4. SO what else can I do to speed up ubuntu? I use bleachbit btw. But I mean like optimizing it because my hdd cant transer over a mb/s which is very odd.

EDIT 2: I have found that whenever I use cairo-dock it sucks up 50% of my cpu. Anyway to fix this?

---

### Post by cariboo on 2011-03-24
What does the load average look like in top? this is what mine looks like:

```
 top - 23:17:14 up  2:36,  2 users,  load average: 0.05, 0.05, 0.10
Tasks: 161 total,   1 running, 159 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.8%us,  4.6%sy,  0.5%ni, 85.7%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2056476k total,  1772076k used,   284400k free,    53660k buffers
Swap:  1952764k total,      120k used,  1952644k free,   585392k cached
        

```

The above is with chromium, vbox, qbitorrent and a terminal open.

I've even got a zombie :)

---

### Post by TTT_Dutch on 2011-03-24
> **cariboo907 said:**
> What does the load average look like in top? this is what mine looks like:

```
 top - 23:17:14 up  2:36,  2 users,  load average: 0.05, 0.05, 0.10
Tasks: 161 total,   1 running, 159 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.8%us,  4.6%sy,  0.5%ni, 85.7%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2056476k total,  1772076k used,   284400k free,    53660k buffers
Swap:  1952764k total,      120k used,  1952644k free,   585392k cached
        

```

The above is with chromium, vbox, qbitorrent and a terminal open.

I've even got a zombie :)

Hey I got my hdd speed up with hdparm and when I run top I get:
> 
top - 23:34:10 up  1:04,  3 users,  load average: 2.18, 2.20, 2.20
Tasks: 183 total,   1 running, 181 sleeping,   0 stopped,   1 zombie
Cpu(s): 28.8%us, 12.1%sy,  0.0%ni, 27.1%id, 30.7%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:   5866064k total,  1582564k used,  4283500k free,     2704k buffers
Swap:  7191548k total,        0k used,  7191548k free,   611344k cached



---

### Post by cariboo on 2011-03-24
Your load averages are pretty high, and cpu usage seems pretty high to me too. Are you running a cpu intensive app of some sort?

---

### Post by TTT_Dutch on 2011-03-24
> **cariboo907 said:**
> Your load averages are pretty high, and cpu usage seems pretty high to me too. Are you running a cpu intensive app of some sort?

Well I have cairo dock running, but now I have a big problem. I cant click on apps most of the time. I can click on strait ubuntu but any apps only selectivly accepts my clicks. LIke I can click on one thing but then it wont repond to anything else. Anyway help with this because this is a really bad problemas I can't do anything useful right now.

I think its a problem with x-server or compiz since sometimes the title bar doesnt even respond.

Also I tried another mouse and nothing...

EDIT: I restarted compiz and everything worked for this session. IDK if it will work when I reboot though. I will check next time I do.

---

### Post by TTT_Dutch on 2011-03-27
Hey I still have speed problems with java so is there anyway to improve speed? Also what are the best things to do to speed up my graphics driver? BTW is there an xwindow alternative because it a bit slow.

---

### Post by Harry33 on 2011-03-28
> **TTT_Dutch said:**
> Hey I still have speed problems with java so is there anyway to improve speed? Also what are the best things to do to speed up my graphics driver? BTW is there an xwindow alternative because it a bit slow.

I do not think xserver brings any speed issues, version 1.10 works well.
However, Compiz is not very stable right now. Also graphics drivers have usually speed issues with Compiz.
So please try to open Ubuntu Classic session w/o Compiz and check the speed issue there.

---

### Post by TTT_Dutch on 2011-03-28
> **Harry33 said:**
> I do not think xserver brings any speed issues, version 1.10 works well.
However, Compiz is not very stable right now. Also graphics drivers have usually speed issues with Compiz.
So please try to open Ubuntu Classic session w/o Compiz and check the speed issue there.

How do I not use compiz? Should I change from compiz if I am using ring switcher regularly and I like wobbly windows and I have macbuntu installed? BTW I am always in Ubuntu CLassic session as I don't like Unity. :)

---

### Post by Harry33 on 2011-03-28
> **TTT_Dutch said:**
> How do I not use compiz? Should I change from compiz if I am using ring switcher regularly and I like wobbly windows and I have macbuntu installed? BTW I am always in Ubuntu CLassic session as I don't like Unity. :)

You wanted to know the best things to do to speed up the graphics driver.
My answer is (concerning Natty) to remove the unstable Compiz and then see what happens.
The other possibilities would be to buy a better graphics card (preferable NVidia because of the fine proprietary drivers) and to buy a fast SSD.

---

### Post by TTT_Dutch on 2011-03-28
> **Harry33 said:**
> You wanted to know the best things to do to speed up the graphics driver.
My answer is (concerning Natty) to remove the unstable Compiz and then see what happens.
The other possibilities would be to buy a better graphics card (preferable NVidia because of the fine proprietary drivers) and to buy a fast SSD.

Well I don't think I want to disable compiz but what could I disable within it that would speed things up? Also my graphics driver works great on windows for gaming so I don't think I want to go out and buy a new one...

---

### Post by Harry33 on 2011-03-28
> **TTT_Dutch said:**
> Well I don't think I want to disable compiz but what could I disable within it that would speed things up? Also my graphics driver works great on windows for gaming so I don't think I want to go out and buy a new one...

You may already have a goog graphics card, what is it?

---

### Post by TTT_Dutch on 2011-03-28
> **Harry33 said:**
> You may already have a goog graphics card, what is it?

ATI Radeon HD 4200, should I consider over clocking anything?

---

### Post by Harry33 on 2011-03-29
> **TTT_Dutch said:**
> ATI Radeon HD 4200, should I consider over clocking anything?

Overclocking shortens your hardware life and may only be helpful on intense gaming.
From the product numbering of your ATI card, you have the 4 series (4***) low-end (*200) card. Perhaps a (*850 - *890) would be better for gaming.

But in general desktop work, you would not notice the difference.

---

### Post by TTT_Dutch on 2011-03-29
> **Harry33 said:**
> Overclocking shortens your hardware life and may only be helpful on intense gaming.
From the product numbering of your ATI card, you have the 4 series (4***) low-end (*200) card. Perhaps a (*850 - *890) would be better for gaming.

But in general desktop work, you would not notice the difference.

Ok well I am just trying to run ubuntu smoothly otherwise everything else is ok to good fast. Can you help me speed up minecraft? Its not my ram as I have tried allocating a fourth of the 6gb to minecraft and it doesnt improve the lag...

---

### Post by Harry33 on 2011-03-29
> **TTT_Dutch said:**
> Ok well I am just trying to run ubuntu smoothly otherwise everything else is ok to good fast. Can you help me speed up minecraft? Its not my ram as I have tried allocating a fourth of the 6gb to minecraft and it doesnt improve the lag...

Sorry no, I cannot.
In general I think your speed issues are due to the problems of the ATI graphics card/drivers with unstable Compiz.

---

