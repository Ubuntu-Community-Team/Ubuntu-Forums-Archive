---
title: "LibDVDCSS Not Available?"
date: 2012-09-14
forum: Multimedia Software
---

### Post by CybaCowboy on 2012-09-14
So I'm trying to configure the ability to read commercial (copyright-protected) DVDs as per this page:
[http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu/](http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu/)

However "LibDVDCSS" is not found in the Ubuntu Software Center and installing it via Terminal gives the following:
```

gregoryopera@gregory-pc:~$ sudo apt-get install libdvdcss
[sudo] password for gregoryopera: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss' has no installation candidate
gregoryopera@gregory-pc:~$ 

```

The other two packages mentioned at the link above ("LibDVDRead4" and "LibDVDNav4") are already installed according to the Ubuntu Software Center, so it seems to be that "LibDVDCSS" is the missing key to the puzzle...

Any help would be appreciated...

---

### Post by SlugSlug on 2012-09-14
try 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by newb85 on 2012-09-14
Actually, the package you need is libdvdread4, and you'll probably also want libdvdnav4 for your DVD experience.

Ubuntu-restricted-extras is a large metapackage that installs both of the aforementioned packages, along with a few proprietary MS fonts, codecs needed for reading and ripping proprietary media files (like .mp3, .wma, .m4a), etc.

Slugslug's advice will install the whole shebang.  If you just want the ones for playing DVDs,

```
$ sudo apt-get install libdvdread4 libdvdnav4
```

If you do that, you can always install ubuntu-restricted-extras for the rest of the stuff later.

---

### Post by newb85 on 2012-09-14
Oh, sorry CybaCowboy, I should have looked at the link you provided.  You probably already installed those two packages.

Once those are installed, you need run the following (per [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")):

$ sudo /usr/share/doc/libdvdread4/install-css.sh

That should get things working.

---

### Post by CybaCowboy on 2012-09-14
> **newb85 said:**
> Ubuntu-restricted-extras is a large metapackage that installs both of the aforementioned packages, along with a few proprietary MS fonts, codecs needed for reading and ripping proprietary media files (like .mp3, .wma, .m4a), etc.

Slugslug's advice will install the whole shebang.

Yeah, it's cool - one can never have too many codecs and fonts, etc... ;)


> **newb85 said:**
> Once those are installed, you need run the following (per [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")):

$ sudo /usr/share/doc/libdvdread4/install-css.sh

That should get things working.

Nope:

```

gregoryopera@gregory-pc:~$ $ sudo /usr/share/doc/libdvdread4/install-css.sh
$: command not found
gregoryopera@gregory-pc:~$ 

```

And Totem Movie Player says:
[i]**An error occured**
Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.[/i]

---

### Post by newb85 on 2012-09-14
> **CybaCowboy said:**
> Yeah, it's cool - one can never have too many codecs and fonts, etc... ;)




Nope:

```

gregoryopera@gregory-pc:~$ $ sudo /usr/share/doc/libdvdread4/install-css.sh
$: command not found
gregoryopera@gregory-pc:~$ 

```

And Totem Movie Player says:
[i]**An error occured**
Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.[/i]

Hmm...Please give the output of
```
$ ls -l /usr/share/doc/libdvdread4
```

---

### Post by mc4man on 2012-09-14
Assuming libdvdread4 is installed
It's 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Not 
```
$ sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by CybaCowboy on 2012-09-14
> **mc4man said:**
> Assuming libdvdread4 is installed
It's 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Not 
```
$ sudo /usr/share/doc/libdvdread4/install-css.sh
```

Yeah that did the trick, thanks!

Now I just need to get [my NAS server issue]("http://ubuntuforums.org/showthread.php?t=2056378") sorted and I'm good to go (for now!)...

---

### Post by newb85 on 2012-09-14
> **CybaCowboy said:**
> Yeah that did the trick, thanks!

Now I just need to get [my NAS server issue]("http://ubuntuforums.org/showthread.php?t=2056378") sorted and I'm good to go (for now!)...

FYI, it's common practice to use $ to indicate that the following command should be entered at the command prompt.  Commands don't actually start with $.

---

### Post by CybaCowboy on 2012-09-14
Ah, okay.

Thanks!

---

