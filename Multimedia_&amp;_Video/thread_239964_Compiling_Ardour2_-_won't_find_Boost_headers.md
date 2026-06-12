---
title: "Compiling Ardour2 - won't find Boost headers"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by flowbot on 2006-08-20
hi

i've just installed Ubuntu Dapper, and am glad to see theirs an audio sub-project. i've come over from Fedora Core 5, and i'm trying to install Ardour2 from svn, which i'd been using on FC5 for a few months now.

however, the scons build doesn't get very far at all - this is all it does:

```
flowbot@machine:~/dev/svn/ardour2$ scons -j2 PREFIX=/usr
scons: Reading SConscript files ...
Checking for usb_interrupt_write() in C library usb... yes
Checking for FLAC__stream_decoder_new() in C++ library FLAC... no
Checking for C++ header file boost/shared_ptr.hpp... no
Boost header files do not appear to be installed.
flowbot@machine:~/dev/svn/ardour2$

```

i have bcp installed (which pulls in all the seperated boost packages i think) as well as the related dev packages.

```
flowbot@machine:~/dev/svn/ardour2$ ls /usr/include/boost | grep shared_ptr
shared_ptr.hpp

```
so, i don't know what's going on here  .... i've never used debian based system, so maybe there's something i'm missing?

](*,) 

shayne

---

### Post by snowbum on 2006-08-20
Hi, I don't usually post. Since I'm a n00b. But I like Ardour. So here's my 2c.

```

Checking for FLAC__stream_decoder_new() in C++ library FLAC... no
Checking for C++ header file boost/shared_ptr.hpp... no
```


You probably need to have the boost library installed. For Ardour to compile, you proabably need the headers. I'm not sure if you need both. Boost is a real useful c++ library. Check it out here: [http://www.boost.org/](http://www.boost.org/)

You may also want to get the flac library if you want to be able to play different formats. I think that is what it is for.

---

### Post by floogy on 2006-08-20
I think for compilation he will need the headers of  libboost-dev.
apt-cache search boost dev

---

### Post by flowbot on 2006-08-20
thanx guys, but i already have the boost libraries installed - including libboost-devel.

if you look at the scons output, you will see that ardour2 checks for:

```
Checking for C++ header file **boost/shared_ptr.hpp**... no
Boost header files do not appear to be installed.
```

yet, the very file that it is looking for actually is on my system, as you can see from this:
```

flowbot@machine:~/dev/svn/ardour2$ ls /usr/include/boost | grep shared_ptr
shared_ptr.hpp
```

now, if you go and look at this thread (from the ardour mailing list) [http://www.nabble.com/error-bulding-ardour2-713-t2014924.html](http://www.nabble.com/error-bulding-ardour2-713-t2014924.html), you'll see that there seems to be problems with boost building, but they seem to be unresolved. while the poster in that thread manages to fix stuff by moving his boost libraries to the proper location, mine are already in the proper location ...

---

### Post by floogy on 2006-08-20
You might solve that by giving the path to the header files. See ./configure --help . On ubuntu you would probably set the prefix to /usr too: ```
./configure --prefix=/usr
```

EDIT: ok you want to  compile it with scons, and have already set your prefix to /usr . I don't have any clue how to do that with scons..., sorry.

---

### Post by luneo on 2006-11-28
If someone needs Ardour2, Audacity 1.3.2, and some... just go to my site, i have made edgy packages... [http://luneo.zendurl.com]("http://luneo.zendurl.com")

---

### Post by abacate on 2007-11-05
I ran into similar problems while trying to build ultrastar-ng. Had to track the missing pieces down one by one from the repos, but got them all in the end. Just search for "boost" and select the relevant dev-packages.

---

