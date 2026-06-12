---
title: "Play WMV files in Ubuntu [Lucid 10.04]"
date: 2010-06-30
forum: Multimedia Software
---

### Post by focaccio on 2010-06-30
I was having a terrible time playing some WMV files and I finally got it working this way:

[based on this: [http://ubuntuguide.net/add-medibuntu-sources-to-install-more-useful-softwares-in-ubuntu]("http://ubuntuguide.net/add-medibuntu-sources-to-install-more-useful-softwares-in-ubuntu")]

Step 1 Add the Medibuntu repositories to sources
```
gksudo gedit /etc/apt/sources.list
```
by adding this at the bottom of the file then saving
```

#medibuntu repositories
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

```
Step 2 Update for that change to take effect
```
sudo apt-get update
```
Step 3 Install the w32codecs [you won't find it if Medibuntu repositories are not in place]
```
sudo apt-get install w32codecs
```
Step 4 Install Kplayer [so far the only player I can get to work for WMV files]
```
sudo apt-get install kplayer
```

Cheers,
Greg

---

### Post by dsiembab on 2011-05-19
try installing libdvdcss2 too.

---

### Post by sudoalb on 2011-05-25
focaccio, thanks.

it works perfectly.

I have been trying to make those file work by doing stuff, but just couldnt. :)

---

### Post by kilopez90 on 2011-07-11
Hi..
After i placed the code> sudo apt-get update i got this error message at the end of the process>
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
.what will i do?Thank yhou

---

### Post by Ashisganguly on 2012-01-23
I tried..but failed to run .wmv it can play only .wma

---

### Post by drmrgd on 2012-01-23
> **Ashisganguly said:**
> I tried..but failed to run .wmv it can play only .wma

This thread is quite old.  Nevertheless, you should be able to play .wmv files with VLC Player available in the repos.  Try that.

---

### Post by SeijiSensei on 2012-01-23
Maybe, maybe not.  See [this thread](http://ubuntuforums.org/showthread.php?t=1705713) for details.

---

### Post by JRV on 2012-01-23
Try ubuntu-restricted-extras:
```

sudo apt-get install ubuntu-restricted-extras
```

This will install the following:
[LIST]
[*]Audio/Video Codecs
[*]Microsoft Core Fonts
[*]Java
[*]Flash
[*]RAR decode/encode
[/list]

You can also find it in the Software Center if you prefer to not use the command line.

---

### Post by SeijiSensei on 2012-01-23
If you read the thread to which I linked, there's a problem with using the w32codecs on the 64-bit Linux platform.  Adding restricted-extras won't resolve this.  The only solution is to use 32-bit Linux.  For those of us with 64-bit processors and large amounts of memory, that's not an attractive alternative.

---

### Post by keithspg on 2012-04-01
This needs to be resolved.

---

### Post by claytonscm on 2012-06-06
worked for me l have a 32bit ubuntu....

---

### Post by floorripper on 2012-09-26
> **kilopez90 said:**
> Hi..
After i placed the code> sudo apt-get update i got this error message at the end of the process>
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
.what will i do?Thank yhou


Use this command to add GPG key:
 ```
sudo apt-get install medibuntu-keyring
sudo apt-get update
```

---

### Post by floorripper on 2012-09-26
Step 4 Install Kplayer [so far the only player I can get to work for WMV files sudo apt-get install kplayerCheers,
Greg.


it was working with some small errors, I do not like to run  KDE programs, on the GNOME desktop enviroment, so For those who are on the old good  Gnome and 10.04 like me, try this:
```
apt-get install gnome-mplayer
```for me it worked like a charm!

---

### Post by laigdotcom on 2013-01-22
thanks, i have terrbible time with .wmw files as well.
i run the command lines above with some errors, but finally the .wmw can play already.

---

### Post by i argor on 2013-03-02
just use the latest vlc player :popcorn:

---

