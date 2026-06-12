---
title: "Installing Java"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-05-06
Apparently I don't have the latest JRE installed (though I'm almost positive I did), and I'm lost as to how to install the latest version from [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

If it's any help (or if it explains anything), I think I might have downgraded my JRE or something like that when I followed the guide at [http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire) to install FrostWire.

All suggestions welcome  :)

---

### Post by silkstone on 2007-05-06
1) In the terminal, enter:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2) Once it downloads the packages and begins the installation, you&#8217;ll get a screen that contains the Sun Operating System Distributor Licence for Java. Hit Enter to continue. You&#8217;ll see a dialog that asks you if you agree with the DLJ licence terms. Select Yes, and hit Enter (may need to use arrow keys to get to the Yes box!). JRE will finish installing.

Check that the JRE is properly installed by running the following command from a terminal.

```
java -version
```

You should get something like...

```
java version &#8220;1.6.0&#8243;
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

You may need to...

```
sudo update-alternatives --config java
```

... to select the latest version, if it isn't already.

Making sure java works on Firefox:

Open Firefox and type...

```
about:plugins
```

.. in the address bar and check for java plugin.

---

### Post by rainwalker on 2007-05-06
I DO have Java 6 installed, according to "java -version", but not the Firefox plugin.
```
sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
          3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/Java6/bin/java
 +        5    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number: 
```

And just FYI, in your post you said to do "sudo update-alternative --config java" but it should be "sudo update-alternative**s** --config java

---

### Post by silkstone on 2007-05-06
Thanks for the correction - I'll amend the original.

---

### Post by rainwalker on 2007-05-06
Still, I don't understand why the Firefox plugin isn't there...

---

### Post by silkstone on 2007-05-06
I don't think the plugin comes automatically with the rest of JRE. You may have to..

```
 sudo apt-get install sun-java6-plugin sun-java6-fonts
```

I'm not sure if the fonts are essential, but I read somewhere that it was a good idea to have them as well.

---

### Post by rainwalker on 2007-05-06
```
E: Couldn't find package sun-java6-plugin
```

---

### Post by silkstone on 2007-05-06
Oops! Now that could because of a glitch at the repo, or it could be because when I did that it was on Feisty not Edgy, so perhaps there isn't a java6 plugin in the Edgy repos??? However, I've just checked and I do have the Java 1.6 plugin installed in Firefox on this machine which runs Edgy, so I must have done it somehow.

I may have used Automatix. ???

Does this help...?

[http://ubuntuforums.org/showthread.php?t=431116](http://ubuntuforums.org/showthread.php?t=431116)

---

