---
title: "Spotify very slow"
date: 2011-04-05
forum: Multimedia Software
---

### Post by LakesideLoafer on 2011-04-05
Spotify Linux Preview has recently become extremely slow. It can take up to 30 seconds to commence playback and then pauses frequently. It is even taking a long time to perform searches and bring up album art which used to be pretty instantaneous.

I've tested the broadband connection which is fine. Spotify works fine on my Android phone and is much quicker when I run it through Testify rather than the native client. I don't particularly want to go back to installing via Wine if I can help it.

Is anyone else having this problem. Any ideas what could be causing it?

Running Ubuntu 10.10.

Thanks

---

### Post by LakesideLoafer on 2011-04-06
Think I might have managed to work out the problem. Figured that the problem might be with Java so changed the default Java runtime environment from JDK to Sun using the instructions here:

[http://www.randombugs.com/java/change-the-default-java-runtime-on-ubuntu.html]("http://www.randombugs.com/java/change-the-default-java-runtime-on-ubuntu.html")

Hope this helps anyone else with a similar problem.

---

### Post by LakesideLoafer on 2011-06-09
Just as an addendum, I have finally found out what the problem was. Nothing to do with the java engine, in the end. My Android phone had Spotify running as a service and the two were interfering with each other. Problem solved. Eventually. :D

---

