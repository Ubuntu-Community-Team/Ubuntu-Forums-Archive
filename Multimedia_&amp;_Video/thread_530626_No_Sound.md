---
title: "No Sound"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by mike6426 on 2007-08-20
I have recently installed Gutsy (Feisty did not work)  I have not gotten sound out of the speakers yet.  I have a dell inspiron 1420, so I have the sigmatel 9228 and should be using the hda-intel driver.  When I click the volume control, it states that "No volume control Gstreamer plugins and/or devices found."  I have tried using the comprehensive guide to sound problems...that did not work.  Any and all help is appreciated.

---

### Post by mike6426 on 2007-08-20
bump/update
I have gotten the vista sound to work, but ubuntu still has no sound (logical seeing as I un/reinstalled the drivers.)  No other updates.

---

### Post by sdim on 2007-08-21
If I understood your problem correctly:
Have you tried  opening Adept Manager (code:sudo adept_manager) and typing in the SEARCH box "gstreamer"? It will pop up some plugins and next to them the STATUS(i.e. if they are installed or not).Right-click there to change the status and download them.

---

### Post by mike6426 on 2007-08-21
I've downloaded all of the plugins: the good, the bad, and the ugly.  None of them worked.

---

### Post by mike6426 on 2007-08-21
bump

---

### Post by netron on 2007-08-22
i have similar problem

gateway laptop

sigmatel stac9200 
hda-intel

followed this guide to the letter
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and still no sound.

the maddening thing is that i can see the osciloscopes in Totem moving when i play an mp3 .. but i cant hear anything.

---

### Post by mike6426 on 2007-08-22
The problem fixed itself during the most recent gutsy update.

---

### Post by netron on 2007-08-22
> **mike6426 said:**
> The problem fixed itself during the most recent gutsy update.

any idea what that update was?
should i dist-upgrade to gutsy?

---

### Post by mike6426 on 2007-08-22
no, I have no clue what update it was.  you should upgrade, but just wait until tribe CD 5 is released(aug. 23)

---

