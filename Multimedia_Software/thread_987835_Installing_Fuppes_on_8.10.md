---
title: "Installing Fuppes on 8.10"
date: 2008-11-19
forum: Multimedia Software
---

### Post by dreakon99x on 2008-11-19
I just downloaded the latest source code from Fuppes' offical site and I am trying to compile it. Everything seems to be going great until I have to run the "make" command. I keep getting this error

lib/SSDP/UDPSocket.cpp:175: error: ‘strlen’ was not declared in this scope
make[2]: *** [UDPSocket.lo] Error 1
make[2]: Leaving directory `/home/dreakon/Fuppes/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/dreakon/Fuppes/src'
make: *** [install-recursive] Error 1

Any ideas?

Thanks

---

### Post by dreakon99x on 2008-11-20
Bump!

---

### Post by mtron on 2008-11-20
well fuppes is a tricky ******* :)

The code is not maintained any more, so it will die pretty soon, if no other developers show interest in it.

Anyway, i've successfully compiled it with ffmpeg support, after some minor changes to the source, for transcoding (use the medibuntu ffmpeg version with the -unstripped libavcodec set)

Attached package is just a quick'n dirty checkinstall package build on ubuntu intrepid (32bit). So it might or might not work on your system ;)

---

### Post by dreakon99x on 2008-11-20
Seems to work, thanks alot, much appreciated!

---

### Post by tomplast on 2008-11-22
> **dreakon99x said:**
> Seems to work, thanks alot, much appreciated!

Really? I just get a segmentation fault when I try to run it :/

---

### Post by mtron on 2008-11-23
> **tomplast said:**
> Really?

Well, as i wrote above, checkinstall packages are like playing roulette..

Anyway, it works here with the package above, (run dependencies are not part of checkinstall packages, you need to install those seperatly. see [fuppes wiki]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux"))

So, you should compile it for yourself. The instructions on the wiki page linked above are up to date.

---

### Post by glymph on 2008-11-23
I've tried following the instructions, and I seem to get similar errors compiling fuppes SVN-578 under Ubuntu 8.10:

lib/SSDP/UDPSocket.cpp: In member function 'bool CUDPSocket::SetupSocket(bool, std::string)':
lib/SSDP/UDPSocket.cpp:58: warning: deprecated conversion from string constant to 'char*'
lib/SSDP/UDPSocket.cpp:71: warning: deprecated conversion from string constant to 'char*'
lib/SSDP/UDPSocket.cpp:93: error: 'memset' was not declared in this scope
...and the rest appear to be errors resulting from this.

I have attached the full text of the error to this post.

This thread seems to be going in circles, unless I'm misunderstanding how checkinstall works - I downloaded the .deb provided above, and it installed with "dpkg -i" without giving any dependancy errors, presumably indicating that I haave all the required packages installed. 

Is there a way to modify the source to allow it to compile, given the error above?

For reference, my newly installed Ubuntu 8.10 system has:
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 

[edit: I'm running a 32-bit OS, by the way]

thanks

Dom

---

### Post by glymph on 2008-11-23
Apologies, I didn't realise there's a new version of fuppes available from the SVN repository.

The instructions here appear to work fine:

[http://ubuntuforums.org/showthread.php?t=828649](http://ubuntuforums.org/showthread.php?t=828649)

---

### Post by PorchSong on 2008-11-24
Thanks for the link to my post, but there is even a newer version out v627.  Here is my install guide for Ubuntu 8.10:

[http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes]("http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes")

Hope this helps.

---

