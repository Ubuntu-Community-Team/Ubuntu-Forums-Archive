---
title: "Anyone have any experiance with AtomicParsley?"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by jeeves on 2008-01-01
[[COLOR="Blue"]AtomicParsley[/COLOR]]("http://atomicparsley.sourceforge.net/") is a command line program for reading and setting tags in .mp4 files. 

The program is supposed to be able to run on linux but there is no documentation on how to install it on *nix systems.  **Does anyone know how to compile this from source?** Here is a list of the files you get when you untar the source file:

```
APar_sha1.cpp 
AP_iconv.cpp            
build
APar_sha1.h           
AP_iconv.h               
COPYING
APar_uuid.cpp         
AP_NSFile_utils.h         
getopt1.c
APar_uuid.h           
AP_NSFile_utils.mm       
getopt.c
AP_AtomDefinitions.h  
AP_NSImage.h              
getopt.h
AP_AtomExtracts.cpp   
AP_NSImage.mm             
main.cpp
AP_AtomExtracts.h     
AtomicParsley.cpp         
Ubuild
AP buglist.txt       
AtomicParsley_genres.cpp  
Using AtomicParsley.rtf
AP_commons.cpp        
AtomicParsley_genres.h
AP_commons.h         
AtomicParsley.h

```
[I]
Not even a "configure" script to run. How do you get started?[/I]

---

### Post by jeeves on 2008-01-02
I'm going to answer my own post since I finally did manage to get this working. To compile AtomicParsely:

1. download the latest source from svn:

```
 svn co https://atomicparsley.svn.sourceforge.net/svnroot/atomicparsley atomicparsley 
```

2. Drill  into the "atomicparsely" director inside the "trunk"

```
cd  atomicparsley/trunk/atomicparsley
```

3. Create the configure script:
```
  autoconf && autoheader
```

 4. Run the configure script:
```
   ./configure
```

 4. Build the program
```
   make
```

Now you can test executable you made by running the following command while still in the "atomicparsley" directory:
```

./AtomicParsley --help
```

you can get more detailed help by running 

```
./AtomicParsley --longhelp
```

To actually read the tags on mp4 you can run

```
 ./AtomicParsley  /path/to/my.mp4 -t
```
[I]
note the commands above assume you are running them from the same directory that "AtomicParsley" is in.[/I]

When changing the tags AtomicParsley leaves your original alone and writes the changes to a "temp" file.  You can override this behavior with the --overWrite option.

---

### Post by jeeves on 2008-03-19
I [found an even easier method of getting AtomicParsely]("http://ubuntuforums.org/showpost.php?p=4343107&postcount=15"). Here are the steps

1. Download the Debian version of AtomicParsley at Sourcefordge [http://sourceforge.net/projects/atomicparsley/](http://sourceforge.net/projects/atomicparsley/)

unzip it
```
unzip AtomicParsley-debian-0.9.0.zip
```

move into the new AtomicParsley-debian directory
```

cd AtomicParsley-debian-*
```

copy the AtomicParsley binary to your /usr/bin/ directory
```

 sudo cp AtomicParsley /usr/bin/
```

You can test it by simply running ```
 AtomicParsley --help
```

---

