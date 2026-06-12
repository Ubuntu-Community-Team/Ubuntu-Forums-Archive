---
title: "Anyone got Scala running on ubuntu?"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by ssavelan on 2007-03-10
Hey, I've been working with Ubuntu sound and MIDI for a few months and enjoy it a lot.  I don't use any commercial software anymore.

I've really been into alternate tunings in the past, but rarely with MIDI (used Fractal Tune Smithy in the past under MSwin).

The program "Scala" looks really cool, but I have not been able to run it.  Does anyone know how?
[URL="http://www.xs4all.nl/~huygensf/scala/"]
http://www.xs4all.nl/~huygensf/scala/[/URL]

I am really a JACK partisan.  If anyone has thoughts, questions, concerns or answers about anything MIDI/JACK/ALSA/SOUND/

UBUNTUSTUDIO

This might be a good place to put them.

---

### Post by lhtown on 2007-03-10
What steps have you taken to get Scala to run? It looks like it should work.

---

### Post by ssavelan on 2007-03-10
biouser@biouser-laptop:~/Desktop/scala-22-pc-linux$ ./scala
./scala: error while loading shared libraries: libgnat-3.4.so.1: cannot open shared object file: No such file or directory

biouser@biouser-laptop:~/Desktop/scala-22-pc-linux$ ./scala
./scala: symbol lookup error: /usr/lib/libgnarl-3.4.so.1: undefined symbol: system__soft_links__set_machine_state_addr
biouser@biouser-laptop:~/Desktop/scala-22-pc-linux$

---

### Post by lhtown on 2007-03-11
OK, so I'm not too good at this kinds of stuff, but it appears to me that you have a dependency missing meaning that you need to install a package that your program needs.

I would suggest that you try installing libgnat through apt-get or synaptic and then try installing Scala again.

If that doesn't work, you might try creating a symbolic link called libgnat-3.4.so.1 to the version you installed or else try to find the older version and install it. (Perhaps you can find it in the Debian stable or testing repositories).

---

### Post by ssavelan on 2007-03-13
yes, I have gnat and gnarl 4.1 standard and I put 3.4 in the user lib as well.  Perhaps I should remove the older gnarl I put in from the scala website.

---

### Post by Kadrus on 2007-11-23
.

---

### Post by ssavelan on 2007-11-26
I don't see the great post that I got in my gmail, but thanks a lot, I will try again soon!

Any news of a fractal tune smithy type program in Ubuntu?

---

### Post by Smbrandes on 2007-12-24
~/Desktop/scala-22-pc-linux$ ./scala
./scala: error while loading shared libraries: libgnarl-4.1.so.1: cannot open shared object file: No such file or directory
 I managed to get that far. Not sure where to put the above dependency. The install instructions are somewhat vague. Placing the  libgtkada-2.8.so.0 in the /usr/local/lib was the first obstacle to be overcome. However, it mentions the libgnarl-4.1.so.1 and another dependency and something about setting the ldconfig. itrided placing the libgnat and libgnarl in the same spot as the libgtkada with no result? I am stumped. Still days away from mean tone.

---

### Post by Smbrandes on 2007-12-24
Well that was far easier than I thought. The trick was to simply list in the ld.so.conf file located in the etc folder in the file system this little bit of text "usr/lib" which basically tells the system where the shared libraries are. Then to make sure you get the cache renewed run ld config in the terminal. And then go and run ./scala again from inside the folder containing the application.

---

### Post by Smbrandes on 2008-01-03
Now the question is how on earth to get it to run with Jack ready applications?

---

