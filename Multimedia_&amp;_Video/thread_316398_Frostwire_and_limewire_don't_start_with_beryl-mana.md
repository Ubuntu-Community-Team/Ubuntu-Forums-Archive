---
title: "Frostwire and limewire don't start with beryl-manager up"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by waltervalderrama on 2006-12-10
I 've found a problem with frostwire/limewire. When I start kubuntu with beryl-manager, those java programs don't work. Example, I started frostwire and I only see an empty window with no menu or options. I tried a session without beryl-manager and It did work. How can I make frostwire work with beryl-manager???? any idea???????????:-k :-k :-k :-k :-k

---

### Post by HighD on 2006-12-10
Got the same exact problem....guess I'll just bump in :mrgreen: ...Anybody know a fix??:confused:

---

### Post by nrgtek on 2006-12-12
same here

---

### Post by mjpoetic on 2006-12-18
If you don't know by now...it has something to do with java and not lime/frostwire.  Anyway java based app you run will have the same problem.  I can't remember exactly where I read that but I was Googling the answer for a couple of days now.  Apparently they are trying to fix the problem.

---

### Post by s0Ma on 2006-12-19
hi,

this script works:

#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

save as whatever you want, chmod +x, and run.

---

### Post by foureight84 on 2006-12-23
is there a way to add 

export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost

to .bashrc or .bash_profile so that this will work with all java progs so you don't have to write a script for every single one of them?
that's what i found from this site [http://noiesmo.dnsalias.net/article.php?story=20061217105248161](http://noiesmo.dnsalias.net/article.php?story=20061217105248161)

btw, the script works flawlessly. i just wanna apply that globally.

---

### Post by Hairy_Palms on 2006-12-23
hmm i dont have this problem with azureus or jrisk and beryl , and they are java apps but im using java6 from the sun website maybe thats the key.

---

### Post by foureight84 on 2006-12-23
na, azureus doesn't have that problem. it's mostly java apps that uses swing.

---

### Post by reza81 on 2007-01-02
samething here with IDE Netbeans that runs on jvm and its made in java. it shows a white screen aften startup. the program starts only the interface (java swing, maybe awt to) doesnt work with beryl on my edgy desktop. LimeWire and FrostWire are also made with jave and use jvm to run. So they all dont work on edgy+beryl. how to fix this??? I dont know ... I am runing Linux just for 3 weeks now  (XP -> Ubuntu). newbie ... :D

---

### Post by foureight84 on 2007-01-03
there's a temp fix for now.

run terminal and type:
```

nano frostwire_fix

```

paste the following and save:
```

#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire #path to frostwire or limewire

```

make it executable:
```

sudo chmod +x frostwire_fix

```

---

### Post by pudland on 2007-01-17
here is the output after running the script:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading LimeWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Error: Couldn't find per display information

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

BTW... i'm running AIGLX/BERYL on Edgy

---

### Post by pudland on 2007-01-17
UPDATE.......

Doing the same for Frostwire worked perfectly.
Limewire Pro a no go.
Gonna do some more digging](*,) .

---

### Post by whistlerspa on 2007-01-21
Just tried this  - it didn't do anything - which folder should the frostwire_fix file be located in 
/usr/bin /home/**** or /home/*****/.frostwire?

---

### Post by Kratos on 2007-02-24
> **pudland said:**
> here is the output after running the script:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading LimeWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Error: Couldn't find per display information

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

BTW... i'm running AIGLX/BERYL on Edgy
I get the same error, only with Frostwire. Any further suggestions?

---

### Post by scorp001 on 2007-02-26
The script given early really works - THANKS - no problem there. For some reason after some time java starts hogging cpu - using edgy

any ideas guys

---

### Post by shoota13 on 2007-02-26
I tried the script but not only did it not work but i can't shut down frostwire unless i opened it with a terminal, which is annoying b/c I just want to open it with it's panel icon. How do i remove the script?

---

### Post by scorp001 on 2007-02-26
> **shoota13 said:**
> I tried the script but not only did it not work but i can't shut down frostwire unless i opened it with a terminal, which is annoying b/c I just want to open it with it's panel icon. How do i remove the script?

U cud perhaps make a "bin" folder in ur home folder where u can have all ur script files. Make this script executable and try it once from it's location, then u can use the Menu Layout in the system / preferences menu to get to the menu properties of Frostwire by right clicking on it - for the program location - browse to the bin folder and ur script file - it shud work from the menu now and if u use it as a panel icon - u can also right click on this and choose preferences and give the script as ur program. Now u shud have no probs in running the program via ur menu or the panel.

cheers

---

### Post by shoota13 on 2007-02-26
OK i tried that. Made a bin folder, moved frostwire_fix into it, and did the menu layout and pointed frostwire to the script but it didn't work. I right clicked on the script and it says that it is executable and i ran it from it's current location. I'm sure i'm missing something. Thx for the reply, really, but u failed to mention how i can just remove it if we can't figure it out... but i'm still willing to try!

Edit: OK wow i was starting it without beryl running, silly me, and it works. BUT when i click on the X to close it, it just minimizes.. any ideas? i can only 'xkill" it...

---

### Post by sancheztavo on 2007-02-27
The same problem here on Ubuntu Edgy and Beryl, the fix posted earlier didn't work, it just opens an empty gray window...

---

### Post by k_smolka on 2007-03-01
That script will only work if you are using java 1.5 because in Java 6 the Motif toolkit is not avaliable.

There is a fix avaliable but it did not work for me.
[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

The next java update should solve this problem as a bug report was reported to sun a while back. 

Karl

---

### Post by amaan on 2007-03-03
i'm having the same problem, when i run frostwire i get a blank grey, i tried the script still nothing

---

### Post by lcbl86 on 2007-03-04
I used the script it works perfectly, but you have to run it everytime you start frostwire, so I edited my menu and put the script in the frostwire command and everything is working fine. 

Now just one problem "anti-aliasing" the fonts look very bad, like in amsn before the amsn_fix

---

### Post by rko618 on 2007-03-05
> **k_smolka said:**
> That script will only work if you are using java 1.5 because in Java 6 the Motif toolkit is not avaliable.

There is a fix avaliable but it did not work for me.
[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

The next java update should solve this problem as a bug report was reported to sun a while back. 

Karl

Karl- I followed the directions and it worked for me.  I recommend trying again.  There is one really confusing part in the guide.  It doesn't tell you how to apply the patch.  The way I did it was:

- Save the patch text in a file, call it berylpatch.patch
- place the file in /tmp/java/src
- run "patch -p1 berylpatch.patch

that should apply the patch.  Good luck!

---

### Post by Kratos on 2007-03-05
> **rko618 said:**
> Karl- I followed the directions and it worked for me.  I recommend trying again.  There is one really confusing part in the guide.  It doesn't tell you how to apply the patch.  The way I did it was:

- Save the patch text in a file, call it berylpatch.patch
- place the file in /tmp/java/src
- run "patch -p1 berylpatch.patch

that should apply the patch.  Good luck!

I, too, am attempting this fix. But, when I try to extract the source .jar, I get this:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at javax.swing.RepaintManager.<clinit>(RepaintManager.java:178)
        at javax.swing.JComponent.repaint(JComponent.java:4714)
        at java.awt.Component.repaint(Component.java:2924)
        at javax.swing.JProgressBar.setModel(JProgressBar.java:769)
        at javax.swing.JProgressBar.<init>(JProgressBar.java:316)
        at javax.swing.JProgressBar.<init>(JProgressBar.java:284)
        at com.sun.tools.extractor.Installer.<init>(Installer.java:43)
        at com.sun.tools.extractor.Installer.main(Installer.java:51)
```

EDIT: Never mind, I was trying to unpack it as root. Using sudo worked, though.

---

### Post by skul3r on 2007-03-10
you can fix it going to the beryl's tray icon with right click then: select windows manager > Metacity. Then you can chage back to beryl...it will work ok..

---

### Post by rko618 on 2007-03-14
Just a reminded for those of you who this script is not working for. **The frostwire_fix script will only work if you are using Java5! ** If you have the Java6 installed you need a different fix which is given on page 2 of this thread.

---

### Post by foureight84 on 2007-03-16
could someone post their **fixed** rt.jar please?

---

### Post by SurR3AL on 2007-03-24
i dont have jdk installed....only jre....what can i do??

---

### Post by dspari1 on 2007-04-16
If you're using Java 6 instead of 5, use this script instead:

Note: If you're using kubuntu, use kate instead of gedit and remember that Konsole is the terminal used for kubuntu.

**Step 1:**
Open up a Terminal

**Step 2:**
gedit limewire_fix

**Step3:**
paste this script into gedit

> #!/bin/bash
cd /usr/lib/LimeWire/
export AWT_TOOLKIT=MToolkit && java -jar LimeWire.jar

**Step 4:**
save and close limewire_fix

**Step 5:**
sudo chmod +x limewire_fix

**Step 6:**
To run the script, type:
./limewire_fix

Make sure you go to tool->options->system tray and change it to shut down immediately since system tray doesn't work with this fix.  I haven't tried to do it in frostwire, but I believe that if you replace limewire with frostwire in all of these steps, it should also work.

I give credit to jaideep_jdof at [http://www.linuxmint.com/forum/viewtopic.php?p=12857](http://www.linuxmint.com/forum/viewtopic.php?p=12857) for posting the fix.

Good Luck.

---

### Post by spankymasterc on 2007-04-17
Well the last script helped me thx but the system tray dont wokr that sux anyways thanks in advance :D

---

### Post by dspari1 on 2007-04-17
> **spankymasterc said:**
> Well the last script helped me thx but the system tray dont wokr that sux anyways thanks in advance :D

No problem, but I agree with you that it sucks that the system tray doesn't work with this script. I turned this post into a wiki at our community docs at

[https://help.ubuntu.com/community/LimeWire]("https://help.ubuntu.com/community/LimeWire")

The problem has to do with Java apps that use AWT and Swing. I am hoping that the next update of Java will fix this issue.

---

### Post by Koba on 2007-04-19
I found a fix for this blank window on limewire and frostwire, for Java 6. Make a shell script containing this:
[COLOR="RoyalBlue"]Frostwire:[/COLOR]
```
#!/bin/bash
cd /usr/lib/frostwire/
export AWT_TOOLKIT=MToolkit && java -jar FrostWire.jar
```
[COLOR="Lime"]Limewire:[/COLOR]
```
#!/bin/bash
cd /usr/lib/LimeWire/
export AWT_TOOLKIT=MToolkit && java -jar LimeWire.jar
```
Then just modify your application starter to use that script instead of the "frostwire" or "limewire" command.

---

### Post by dspari1 on 2007-04-21
> **Koba said:**
> I found a fix for this blank window on limewire and frostwire, for Java 6. Make a shell script containing this:
[COLOR="RoyalBlue"]Frostwire:[/COLOR]
```
#!/bin/bash
cd /usr/lib/frostwire/
export AWT_TOOLKIT=MToolkit && java -jar FrostWire.jar
```
[COLOR="Lime"]Limewire:[/COLOR]
```
#!/bin/bash
cd /usr/lib/LimeWire/
export AWT_TOOLKIT=MToolkit && java -jar LimeWire.jar
```
Then just modify your application starter to use that script instead of the "frostwire" or "limewire" command. 


It's good to know that the fix also works with frostwire.
:guitar:

---

### Post by granite230 on 2007-04-22
I have Java 5 and Frostwire installed on Feisty. After that I added *alias frostwire='export AWT_TOOLKIT=MToolkit && frostwire'* to /home/username/.bashrc to avoid the blank screen.  If I enter 'frostwire' in my terminal Frostwire will run perfectly. 

**1.** So now I want to make a shortcut in my top-panel but when I tell the launcher to use the command 'frostwire' it starts Frostwire with a blank screen. Is there an easy fix for this?

**2.** I also have a small problem in my Applications > Internet menu. The Frostwire launcher is there but it launches Frostwire with a blank screen. If I click Add/Remove and search for the Frostwire launcher in the menu it won't give me any results... I can't remove the launcher.

Any suggestions?

---

### Post by LuisGMarine on 2007-04-24
I just tried the fix for frost wire using Ubuntu Fiesty, Java 6 and the latest frostwire from their website, and it works.

I just made the complete move to Linux, and I was amazed at how an open source thing like beryl can function so close to what proprietary companies come up with, in my opinion I think open source community does a better job.  

Anyhow I just wanted to say that this was one of the first problems that I encounter, I wasn't sure on how to go about solving this, and here I come and stumble on these forums, and wow did it save me!  So in essence I just wanted to say thanks to Kobe for posting the fix, and I wanted to confirm that it does work for another person, thanks a lot :) :KS 

-LuisGMarine

---

### Post by ruffneck on 2007-06-27
Thanks for the fixes...works a charm!

---

