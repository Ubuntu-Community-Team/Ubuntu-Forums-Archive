---
title: "[SOLVED] Ibex: Cannot find Java Control Panel"
date: 2008-10-31
forum: Multimedia Software
---

### Post by TheJimtasticOne on 2008-10-31
I need to access the java control panel. The sun website says it's in %jdkdir%/jre/bin or %jdkdir%/bin, as a file called ControlPanel. But it's not there.
Running "jconsole" in the terminal starts a program called java monitoring and management console, which isn't what I want, and jcontrol results in the following message: "The program 'jcontrol' is currently not installed.  You can install it by typing:
sudo apt-get install julius
bash: jcontrol: command not found"

java -version gives:
"java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)"

Has anyone got any ideas as to how I can get this?

---

### Post by TheJimtasticOne on 2008-11-01
Bump. :(

---

### Post by gandaran on 2008-11-01
are you running a 64-bits ubuntu version? if so then you provably have open java installed, I believe  only sun-java has a control panel

---

### Post by TheJimtasticOne on 2008-11-01
Thanks for your reply. I am running AMD64, but I've tried both sun java and openjdk and neither have a file called ControlPanel in any of the bin directories :(.

---

### Post by gandaran on 2008-11-01
I have sun-java installed in my 32-bits system and I do have a control panel launcher in system » preferences, you only get this if the sun-java plugin is installed, the sun-java plugin is not available for 64-bits systems

---

### Post by TheJimtasticOne on 2008-11-01
Ah, I see... thanks anyway.

---

