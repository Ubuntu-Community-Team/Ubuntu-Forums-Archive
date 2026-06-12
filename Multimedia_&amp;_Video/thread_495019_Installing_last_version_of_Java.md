---
title: "Installing last version of Java"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by Dyegov on 2007-07-07
Hi. I have installed all the property software I needed (Such as mp3, slash, Java, windows fonts, etc), but my Java seems not to be the latest version, and Runescape works slowly. How can I manage to update it?

---

### Post by family on 2007-07-07
Open Terminal:

[COLOR="Magenta"]family@U7:~$ java -showversion
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
[/COLOR]
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image

So that's what you should see, then check Sun's website for the latest out there. If not, dload it. Sorry if that's not what you want, soy noob. :popcorn:

---

### Post by Dyegov on 2007-07-07
Yes, that's exactly what it shows, I have navigated their site, but I don't seem to know exactly what I have to download. Could someone please link me to it?

---

### Post by Dyegov on 2007-07-07
Sorry for the double post, but I did all it said in **[This Page]("http://www.java.com/en/download/help/5000010500.xml")** and it didn't work. Can someone guide me please?

---

### Post by southernman on 2007-07-07
You can get sun java in synaptic. Both sun-java6-bin and sun-java-jre are there along with the dev packages.

Alternatively you can use the community wiki page found below:

[https://help.ubuntu.com/community/Java#head-74381102f8474db76ee74352a7562cadebbff11b]("https://help.ubuntu.com/community/Java#head-74381102f8474db76ee74352a7562cadebbff11b")

---

### Post by Dyegov on 2007-07-07
This has been fixed. I didn't need to update java to play runescape, I needed to disable compiz, since it takes a lot of ram, and runescape does too. Thanks for your help :)

---

### Post by mig5 on 2007-07-13
> **Dyegov said:**
> This has been fixed. I didn't need to update java to play runescape, I needed to disable compiz, since it takes a lot of ram, and runescape does too. Thanks for your help :)

I take it that you are using firefox?  Firefox seems to have issues with java and when it's using java it takes up a lot more memory than it should.  You could try Epiphany, which is a browser designed especially for gnome (i.e: Ubuntu's desktop interface), I've heard that it handles java better.  Or even Opera might give you better performance.

---

