---
title: "Jitsi won't start"
date: 2015-01-25
forum: Multimedia Software
---

### Post by marc-defossez-c on 2015-01-25
Hi,

Installed Jitsi (amd64) on Ubuntu_14.04 64-bit.
starting it from the command line results in a long list of errors.
Type of errors:

 org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.swingui [85]: Unable to resolve 85.0: missing requirement [85.0] package; (package=javax.accessibility)
    at org.apache.felix.framework.Felix.resolveBundle(Felix.java:3564)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1797)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1192)
    at org.apache.felix.framework.StartLevelImpl.run(StartLevelImpl.java:266)
    at java.lang.Thread.run(Thread.java:745)

This is the java version installed:

<...>:~$ java -version
java version "1.8.0_31"
Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)

Anybody an idea how to solve this?

Many thanks in advance,

Marc

---

### Post by Rob Sayer on 2015-01-25
Seen this?

[http://askubuntu.com/questions/477375/install-jitsi-from-ppas](http://askubuntu.com/questions/477375/install-jitsi-from-ppas)

Don't know if that's 100% relevant but it's a start.

One thing about linux is that a minor problem can generate error messages that look like Armageddon.

---

