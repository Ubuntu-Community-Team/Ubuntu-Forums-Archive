---
title: "Rosegarden 1.2.4 Dapper"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by damo21 on 2006-08-14
Well, I could have compiled the new Rosegarden 1.2.4 release from source, but I found an easier way.

Download the latest rpm binary from sourceforge [here]("http://sourceforge.net/project/showfiles.php?group_id=4932&package_id=4959&release_id=431923")
Run the following in the directory where you downloaded:
```
sudo apt-get install alien
sudo alien <filename of rpm> --scripts
sudo dpkg -i <filename of new deb>
sudo ln -s /usr/lib/liblrdf.so /usr/lib/liblrdf.so.2
sudo ln -s /usr/lib/libjack.so /usr/lib/libjack.so.0
```

Worked for me, with fluidsynth-dssi plugin working straight away :D

---

### Post by floogy on 2006-08-14
Hmmm.. How did you manage, to hear something with rosegarden4 ?
I connected rosegarden with the alsa_pcm playback_1 and 2 in the connections window, but I didn't hear anything, but the imported hydrogen project played in rosegarden, and the volume meter on each line works...

---

### Post by edev on 2006-08-14
> Hmmm.. How did you manage, to hear something with rosegarden4 ?

You need to load a sounfont with a softsynth and then connect rosegarden to that softsynth using Rosegarden Studio 
>composition>studio>MIDI-devices

See : [http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html#2_1](http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html#2_1)

Section - 2.1.3.2.2 QSynth

Everything you need to know how to easily get sound out of Rosegarden is written in that section.

Hope this helps,

Eric,

---

### Post by floogy on 2006-08-15
Ah thank you. I thought about something like that, but I didn't find it. I'll try to use the fresh Titanic 200 GMGS v1.2 Soundfont for Rosegarden. Is that one a good choice?

---

### Post by rytmisk on 2006-08-15
Hi

I follow your advice but after finishing I receive the following error: rosegarden: error while loading shared libraries: liblrdf.so.2: cannot open shared object file: No such file or directory

Any advice? I had 1.2.3 going before (the one compiled by someone in this forum

Best
Ketil

---

### Post by floogy on 2006-08-15
[http://rpmseek.com/rpm-pl/liblrdf.html?hl=en&cs=liblrdf.so.2:FN:1,3,5,11,27:75,80,82,86:0:0](http://rpmseek.com/rpm-pl/liblrdf.html?hl=en&cs=liblrdf.so.2:FN:1,3,5,11,27:75,80,82,86:0:0)
[http://rpmseek.com/rpm-dl/liblrdf-0.4.0-7.fc6.i386.html?hl=en&cs=liblrdf.so.2:FN:1,3,5,11,27:75,80,82,86:0:0:2962600](http://rpmseek.com/rpm-dl/liblrdf-0.4.0-7.fc6.i386.html?hl=en&cs=liblrdf.so.2:FN:1,3,5,11,27:75,80,82,86:0:0:2962600)
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=liblrdf.so.2&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=liblrdf.so.2&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

turned out, that this lib maybe is that recent, that you only find it in fedora core (?) I suggest to use alien again.
[http://rpmseek.com/download/http://ftp.tu-chemnitz.de/pub/linux/fedora-core-extras/development/i386/liblrdf-0.4.0-7.fc6.i386.rpm?hl=com&nid=27352](http://rpmseek.com/download/http://ftp.tu-chemnitz.de/pub/linux/fedora-core-extras/development/i386/liblrdf-0.4.0-7.fc6.i386.rpm?hl=com&nid=27352)

But You may try to symlink the lib with the ubuntulib:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=liblrdf&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=liblrdf&searchon=names&subword=1&version=dapper&release=all)
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=liblrdf0&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=liblrdf0&version=dapper&arch=i386)

I don't know if that works, though.

---

### Post by rytmisk on 2006-08-17
Hm

It worked to alienize the link you sent. (Thanks a lot for your effort!!) However it seems to lead me to new problems: Writing rosegarden at the prompt now gives me:
...............
rosegarden: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/liblrdf.so.2)
..............

However the file /lib/tls/libc.so.6 exists as a symlink to /lib/libc-2.3.6.so - I don't know what GLIBC_2.4 refers to though. Any pointers?

Best
Ketil

---

### Post by floogy on 2006-08-17
[http://www.linuxquestions.org/questions/showthread.php?t=374929](http://www.linuxquestions.org/questions/showthread.php?t=374929)

or [try a google search]("http://www.google.de/search?q=%22%60GLIBC_2.4%27+not+found+%28required+by+%2Fusr%2Flib%2F%22").

Although it seems, that you're using the recent version. Maybe you need the headers of the dev package?

There might be compatibility versions to glibc 2.4? i don't know.
I may look into this later.

---

### Post by floogy on 2006-08-18
Try **ldd `which rosegarden4`** , to see what libraries rosgarden4 isn't able to find, and to get more informations. GLIBC_24 refers to libc6, so it's maybe a version mismatch. I don't know.

```
gerhard@ubuntu:~$ ldd  `locate liblrdf.so.0`
/usr/lib/liblrdf.so.0.0.0:
[...]
        libc.so.6 => /lib/libc.so.6 (0x00002b14cd45f000)
[...]
```

this is on dapper amd64

You may put /lib/tls/ to your /etc/ld.so.conf, and run **sudo ldconfig** 
. But this all is guesing...

---

### Post by djst on 2006-08-19
> **rytmisk said:**
> Hi

I follow your advice but after finishing I receive the following error: rosegarden: error while loading shared libraries: liblrdf.so.2: cannot open shared object file: No such file or directory

Any advice? I had 1.2.3 going before (the one compiled by someone in this forum

Best
Ketil

I can't say I know what I'm doing, but I was able to solve the problem by just doing this:

```
# remove dead link
sudo rm /usr/lib/liblrdf.so.2
# create working link instead...
sudo ln -s /usr/lib/liblrdf.so.0 /usr/lib/liblrdf.so.2
```

---

### Post by jsmanness on 2006-08-20
Hello,

I have downloaded both the source code and the rpm package of Rosegarden.  I am having problems with the scons setup (see the other thread) so I figured I try installing Rosegarden this way.  However, I am not sure how to open up a rpm package.  If some can tell me which software to download so I can run the rpm, I would appreciate it!

Thanks,

Jon Manness

---

### Post by rytmisk on 2006-08-21
You the man!!

Thank you! it worked!

Ketil

---

