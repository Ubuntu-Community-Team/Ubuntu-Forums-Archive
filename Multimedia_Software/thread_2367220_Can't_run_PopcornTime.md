---
title: "Can't run PopcornTime"
date: 2017-07-27
forum: Multimedia Software
---

### Post by Flame_Phoenix on 2017-07-27
**[SIZE=4]Backgroung[/SIZE]**

I have an old x86 machine that I am trying to use as a media center using [Lubuntu 17.04]("http://cdimage.ubuntu.com/lubuntu/releases/17.04/release").

For that effect, I downloded [Popcorn-time for x86]("https://popcorn-time.to/linux32.html") and unzipped it. 

When running *./Popcorn-time* a message showed saying:

   ```
 ./Popcorn-Time: error while loading shared libraries: libgconf-2.so.4: cannot open shared object file: No such file or directory
```

So, like a good soldier, I find out that electron (the framework where Popcorn is built upon) requires this lib, and I install it using *sudo apt-get install libgconf-2-4*.

That works and so when I try to run *./Popcorn-Time* again, I get a different error:

    ```
./Popcorn-Time: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory
```

Doing *sudo apt-get install libudev0:i386* didn't fix it, so I had to download it from a [3rd party website]("http://gamblisfx.com/how-to-solve-missing-libudev-so-0-library-on-ubuntu-16-04") and install it manually.

**[SIZE=4]Problem[/SIZE]**

After doing that I tried running *./Popcorn-Time*, but it immediately crashes for no reason.  

It also created a dump file in what I assume is binary, thus being totally useless to me ...

**[SIZE=4]Question[/SIZE]**

 - How can I install popcorn time in my x86 machine ?

---

### Post by oldos2er on 2017-07-27
Hello, as mentioned in the Code of Conduct we don't support file sharing or potential copyright infringement, which is illegal in some parts of the world.

"Messages containing violent, sexually oriented, or illegal content or  links to sites with this content will be saved in the Jail as evidence.  Messages with links to or suggesting illegal activity will also be saved  in the Jail. Posting or linking to any of these could result in a ban."

Closed.

---

