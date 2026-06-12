---
title: "GNURadio install missing libgnuradio-pmt-3.7.6git.so?"
date: 2017-08-21
forum: Multimedia Software
---

### Post by machs on 2017-08-21
I've been having a fight with installing gnuradio. I'm running ubuntu 16.04 and I'm using the  myriadrf repos as suggested by [gqrx install page]("http://gqrx.dk/download/install-ubuntu") to install gqrx and gnuradio.   apt-get successfully completes install of gnuradio version 3.7.10 and  all of the dependencies.  When I run gnuradio-companion it complains that  libgnuradio-pmt-3.7.6git.so is missing.  

There error message has the following text: 

  ```
[INDENT] Cannot import gnuradio. Is the model path environment variable set correctly? 

All OS: PYTHONPATH Is the library path environment variable set correctly?
Linux: LD_LIBRARY_PATH  
Windows: PATH 
MacOSX: DYLD_LIBRARY_PATH

  (libgnuradio-pmt-3.7.6git.so.0.0.0: cannot open shared object file: No such file or directory)

 [/INDENT]

``` 

 

I have a libgnuradio-pmt file installed however it is  version 3.7.10.  I do not have a libgnuradio-pmt-3.7.6git.so.0.0.0 on my system. 

```

machs@electricSheep:~$ find /usr/ | grep radio-pmt
/usr/share/doc/libgnuradio-pmt3.7.10
/usr/share/doc/libgnuradio-pmt3.7.10/changelog.Debian.gz
/usr/share/doc/libgnuradio-pmt3.7.10/copyright
/usr/lib/x86_64-linux-gnu/libgnuradio-pmt.so
/usr/lib/x86_64-linux-gnu/libgnuradio-pmt.so.3.7.10

```

I believe my paths are set-up correctly.


```

machs@electricSheep:~$ echo $PYTHONPATH
/usr/local/lib/python2.7/dist-packages/
machs@electricSheep:~$ echo $LD_LIBARY_PATH
/usr/lib/x86_64-linux-gnu/
machs@electricSheep:~$ 

```

Any thoughts on what I can try next?

---

### Post by Perfect Storm on 2017-08-22
Have you tried symblink the two?

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libgnuradio-pmt.so.3.7.10 /usr/lib/x86_64-linux-gnu/libgnuradio-pmt-3.7.6git.so.0.0.0
```

---

### Post by machs on 2017-08-22
Hmm Slightly different error message; 

```

(/usr/local/lib/python2.7/dist-packages/pmt/_pmt_swig.so: undefined symbol: _ZN3pmt5PMT_FE)

```

perhaps there is something wrong with the pmt package?

---

### Post by Perfect Storm on 2017-08-23
Seems symblink won't help in this case. You can remove it again:
```
sudo rm -rf /usr/lib/x86_64-linux-gnu/libgnuradio-pmt-3.7.6git.so.0.0.0
```

Perhaps purge the ppa's yuo added and use GNURadio from the original repo to see if it works.

---

### Post by machs on 2017-08-23
So I removed all of my gnuradio packages from the other repositories. 
```

sudo apt-get purge --auto-remove gqrx
sudo apt-get purge --auto-remove gqrx-sdr
sudo apt-get purge --auto-remove libgnuradio*

```

and I disabled the five custom repos using the software centre.  I reinstalled gqrx and gnuradio with apt and it pulled gnuradio version 3.7.9 from the ubuntu archives along with libgnuradio-pmt3.7.9.  When I run gnuradio from the prompt i get the same error message; 

```

Cannot import gnuradio.

Is the python path environment variable set correctly?
    All OS: PYTHONPATH

Is the library path environment variable set correctly?
    Linux: LD_LIBRARY_PATH
    Windows: PATH
    MacOSX: DYLD_LIBRARY_PATH


(libgnuradio-pmt-3.7.6git.so.0.0.0: cannot open shared object file: No such file or directory)
```

Same message - why is gnuradio looking for pmt3.7.6git when everything else is 3.7.9?  does the git have any significance?

---

### Post by Perfect Storm on 2017-08-23
Strange. I can't that package in the ubuntu package (homepage for all the packages). I guess you're out of luck with that applications, seems broken.
Your only option may be installing it from the source. Uninstall GNUradio first thhen:
```
wget http://www.sbrac.org/files/build-gnuradio && chmod a+x build-gnuradio && ./build-gnuradio
```

More here: [https://wiki.gnuradio.org/index.php/InstallingGRFromSource](https://wiki.gnuradio.org/index.php/InstallingGRFromSource)

---

### Post by David2009 on 2018-06-02
I am hoping to begin SDR listening.  After all of the adjustments / installations / etc for GNURADIO, was a usable solution found?  Thank you for reading.

David

---

### Post by machs on 2018-06-03
In the end i downloaded the GNUradio live CD and boot from that to play with GNU radio.   My ubuntu install is probably 4 or 5 years old has gone through multiple distribution upgrades.  At one point I'd installed gnuRadio from source,  I suspect that's why i have these problems.

---

