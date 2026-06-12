---
title: "Cinelerra Instalation Help"
date: 2008-02-27
forum: Multimedia Production
---

### Post by GeoffVanstone on 2008-02-27
Okay, I am following the steps at this site below to install Cinelerra:
```

http://www.g-raffa.eu/cin_compilation.html
```

and I get stuck at the part where it says:

> Then run:

    ./autogen.sh

    ./configure --enable-mmx --without-pic --with-buildinfo=svn/recompile

I ran the autogen.sh by clicking on it in the folder and saying run, but the second one when I put it in it says the command does not exist? What do I do? Please help.

Thanks, Geoff

---

### Post by rouge568 on 2008-02-27
I highly recommend using a packed version. Here is the text off of the cinelerra website:
> 
Ubuntu
Gutsy Gibbon | Feisty Fawn | Edgy Eft | Dapper Drake

    Here are the Ubuntu packages repositories. Detailed instructions for installation can be found in the Manual.

7.10 Gutsy Gibbon

    for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
    deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main

    Notes:
    - Installations from this repository need an authentication key. Add it by typing the following command in your terminal:
    wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add -
    - Cinelerra package is available in 5 variants:

        cinelerra (all x86 and x86_64 without opengl 2.0 video card)
        cinelerra-generic (all x86 and x86_64 with opengl 2.0 video card)
        cinelerra-k7 (all amd32 without opengl 2.0 video card)
        cinelerra-k7gl (all amd32 with opengl 2.0 video card)
        cinelerra-k8 (all amd64 with opengl 2.0 video card)

    - These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
    - Please, report any package bug to akir4d at gmail dot com

    for i386 (not working on amd 32 bits), by Valentina Messeri:
    deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

    for AMD64 (and also Core Duo Intel64), by Valentina Messeri:
    deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
    Note:
    - If your package manager complains that it does not have the right version of libfaac (1.25) you can try installing libfaac0.


It worked on my installation. Good luck!

---

### Post by GeoffVanstone on 2008-02-27
so do i type:
```

wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
```

in the terminal?

because when I did it still didnt work, or atleast install it all the way....? I put in my pass, and it said ok. Am I supposed to something else?

---

### Post by stooshbunutu on 2008-02-28
You now need to go into System >>> Administration >>> Synaptic Packagemanager

Search for Cinelerra and rightclick "Mark for installation" and then click on the apply button.

alternatively:
```
sudo apt-get install cinelerra
```

Hope this helps :)

---

### Post by cotcot on 2008-02-28
If the repository installation does not work checkout the way i do my compilation. It is in the 1éth post of [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911&page=2") thread. I guess that you miss some package to make autogen.sh working.

---

### Post by Fonsis on 2008-03-05
> **rouge568 said:**
> I highly recommend using a packed version. Here is the text off of the cinelerra website:


It worked on my installation. Good luck!

Worked perfectly on my 7.10, too! :)

---

