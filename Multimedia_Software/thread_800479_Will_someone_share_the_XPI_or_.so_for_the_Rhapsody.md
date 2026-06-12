---
title: "Will someone share the XPI or .so for the Rhapsody Player Engine?"
date: 2008-05-19
forum: Multimedia Software
---

### Post by rainwalker on 2008-05-19
It doesn't work correctly with FF3 (Hardy), but apparently can be fixed by manually copying the plugin into the folder. I don't have access to the file, so could someone post it as an attachment or something?
It should be "nprhapengine.so" in ~/.mozilla/plugins/ or /usr/lib/firefox-addons/plugins

---

### Post by bigredx24x on 2008-05-21
I was unable to get the Rhapsody plugin to work in the 64-bit Firefox.  I had to do this:

[http://ubuntuforums.org/showpost.php?p=5007491&postcount=10](http://ubuntuforums.org/showpost.php?p=5007491&postcount=10)

But, if you want to get the XPI, try to open the Rhapsody online player window (click a play button on the Rhapsody site)...then click Install Now.  A window will pop up asking if you want to install the plugin.  In that window will be the path to the XPI file.  Copy the path.  Then in a terminal run:

>> wget /path/to/***.xpi

Now, unzip that file

>> unzip ***.xpi

You will now have the *.so file

---

### Post by rainwalker on 2008-05-21
Ah! I totally forgot about wget!

---

### Post by hawkinsdale on 2008-10-09
I used this:

cd .mozilla/plugins/
wget [http://forms.real.com/real/player/download.html?f=unix/rhapxRhapsodyPlayerEngine_Inst_Linux.xpi&amp;install=rwih](http://forms.real.com/real/player/download.html?f=unix/rhapxRhapsodyPlayerEngine_Inst_Linux.xpi&amp;install=rwih)
unzip RhapsodyPlayerEngine_Inst_Linux.xpi

It got the .so file into the right place OK.  But Rhapsody still didn't work: it complained of a "technical error."  

I ended up having to install Firefox 2.  Ubuntu is OK with this, as far as I've been able to tell.  I just used Applications > Add/Remove, now I have both.

Rhapsody STILL didn't work until I cleared out the cookies from the previous attempts.  But now I'm in business.

More detail [here]("http://hawkinsdale.com/?p=136"), including the full text of the wget, which seems to be munged by the forum software.

---

### Post by rainwalker on 2008-10-09
> **hawkinsdale said:**
> I used this:

cd .mozilla/plugins/
wget [http://forms.real.com/real/player/download.html?f=unix/rhapxRhapsodyPlayerEngine_Inst_Linux.xpi&amp;install=rwih](http://forms.real.com/real/player/download.html?f=unix/rhapxRhapsodyPlayerEngine_Inst_Linux.xpi&amp;install=rwih)
unzip RhapsodyPlayerEngine_Inst_Linux.xpi

It got the .so file into the right place OK.  But Rhapsody still didn't work: it complained of a "technical error."  

I ended up having to install Firefox 2.  Ubuntu is OK with this, as far as I've been able to tell.  I just used Applications > Add/Remove, now I have both.

Rhapsody STILL didn't work until I cleared out the cookies from the previous attempts.  But now I'm in business.

More detail [here]("http://hawkinsdale.com/?p=136"), including the full text of the wget, which seems to be munged by the forum software.

I never followed up either; I think that's what I did. It worked fine for a little while, but now I'm getting the "Technical Error" too :(
I'd really rather not install Firefox2 just for this

---

