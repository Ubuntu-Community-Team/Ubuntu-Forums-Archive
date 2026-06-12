---
title: "Why can't I play DVDs within Ubuntu using VLC?"
date: 2010-03-23
forum: Multimedia Software
---

### Post by cAlpha on 2010-03-23
I just un- and reinstalled VLC, including updates and I'm still unable to play a DVD on my Inspiron 1525.  

Am I missing a codec?  Something else I need to install or to check?

---

### Post by n0dix on 2010-03-23
Did you try with other programs, like mplayer, totem?
Did you get an error?

---

### Post by cAlpha on 2010-03-23
Yeah, trying with Mplayer I get a "Could not read from resource" error.  

I should be able to play DVDs, as there's a 'DVD Rom' emblem on the side...any other thoughts?

---

### Post by n0dix on 2010-03-23
Do you have installed libdvdcss package?

---

### Post by Brandel Valico on 2010-03-23
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

follow the instructions for your version

---

### Post by cAlpha on 2010-03-23
> **n0dix said:**
> Do you have installed libdvdcss package?

"Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source" 

When I tried installing at the command line, and it isn't present within Synaptic.

> **Brandel Valico said:**
> [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

follow the instructions for your version

I'll take a look, thanks.

---

### Post by n0dix on 2010-03-23
Try with this packages:
- w32codecs (or sometimes called win32codecs or win32all),
- libdvdread3
- libdvdcss2

---

### Post by 2hot6ft2 on 2010-03-23
I believe you have to enable the medibuntu repositories to get libdvdcss2,
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
Or if you want all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```

---

### Post by lidex on 2010-03-23
Follow the instructions in 2hot6ft2's post then in a terminal run this command:
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by cAlpha on 2010-03-25
> **2hot6ft2 said:**
> I believe you have to enable the medibuntu repositories to get libdvdcss2,
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
Or if you want all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```

> **lidex said:**
> Follow the instructions in 2hot6ft2's post then in a terminal run this command:
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Worked like a charm and I'm now able to play the DVD in Mplayer.  Thanks, guys!  

Any thoughts for how to get it working in VLC though?  Still no dice...

---

### Post by insecureboy on 2010-03-25
Hmmmmm this question is actually an interesting law topic 

In 2005 (i think) a judge ruled it "illegal to play DVDs on Linux" (I know ....... I'll explain it a bit) and he banned DeCSS from being hosted on any US server which was the then only solution on Linux to decrypt DVDs to watch them.

the Digital Millennium Copyright Act of 1998 in U.S. makes it illegal to "**circumvent**"  a **"technological measure"** (examples: **"encryption"** of digital tv or DVD movies) or to provide means like **"software" **or to **"promote"** them or to "**import****"** them to the United States .... to **"assist someone to circumvent"** that technological measure....

The thing that happens in Windows is that You buy a DVD it has encryption on it ( to prevent copying) that encryption algorithm is not secret ( it is CSS for example ) but it requires a secret key to play the DVD. 

That key is owned by movie companies. these companies license guys like InterVideo or powerDVD or other DVD hardware and software companies and give them the secret keys. So if u are InterVideo u get a license from sony, one from universal, one from paramount, ....... and u put those keys in ur software and ur software is now able to decrypt and view the content of DVD so that user can watch.

But that license u get from movie companies require you to do some things:
- keep the encryption keys secret
- your software should only use the decrypted data to view it and not allow copying of it 
- your software should not allow fast forward when the FBI notice is displayed 
- .....
if your software doesn't comply with these terms movie studios won't give you the license  to view their copyrighted works.

the problem with Linux is that everything is open source and if you write a DVD player software for Linux, because of the terms of the GNU General Public License you will have to release the source code of your programs, which means you can't comply with the licenses from the movie companies. 

Imagine if the InterVideo winDVD software was open source I could just get it, cut out some lines from it and modify it  to save an unencrypted copy of the movie after viewing it . 
That was the funky problem and so you couldn't have a legal software that complied both with the GNU General Public License and the movie companies license at the same time. 

of course there used to be illegal ways of doing the thing, especially when the open source community  is mad.....

but i think they found a legal solution to that as well...
  some thing  like writing a software and releasing most of its source to comply with GPL and keep secret some of the source that had the secret encryption keys in it so the movie companies were happy too 

any way that was just a history lesson that i think is interesting u can search it to find out more

---

### Post by Chronon on 2010-03-25
That applies to DeCSS.  As far as I know, libdvdcss2 has never been legally challenged.

---

### Post by insecureboy on 2010-03-26
yeaaa the case was on DeCSS

---

