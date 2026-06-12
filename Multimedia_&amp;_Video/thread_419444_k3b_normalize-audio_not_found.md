---
title: "k3b normalize-audio not found"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by snowstorm on 2007-04-23
k3b claims it can not find normalize-audio although it has been installed, the search path exists and k3b was rebooted after installing normalize-audio. What could be the problem?

---

### Post by BLTicklemonster on 2007-04-26
Tis a bug:

[k3b uses wrong normalize binary name](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/44524)

And I see no alternatives.

---

### Post by snowstorm on 2007-04-28
Yes, I've read that, but k3b already looks for normalize-audio, but still claims it can not find it though it is installed. So it seems that fixing the previous bug created a new one...

---

### Post by hvthao on 2007-04-30
Just upgrade to k3b 1.0.1 and all the problems solved!

---

### Post by BLTicklemonster on 2007-04-30
Right, yes, upgrade. I downloaded the source, extracted it, and ran ./configure

*oh, this neat little tidbit of information is on their site in the "how to compile" section:

```
Configure the source:

# ./configure

(with older versions of K3b one needed to provide a prefix but the new KDE build system is able to guess it properly)
```

Nice, huh? IT GUESSES THE PREFIX!!! WOO HOOO!!!


Then I get this error:

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
bill@bill-desktop:~/k3b-1.0.1$ 


```

Wheeee!!!!

So I'm installing kde... 

(but k3b worked fine, why do I need to do this now? Oh, to get normalized audio, maybe?)

heh heh, maybe if I'd learn to read:

> The first thing to do is to get the requirements installed (see the requirements page). You need at least install the Qt and kdelibs devel packages.
For a working audio player you need the kdemultimedia devel package.
For mp3 decoding support you need to install libmad.
For FLAC decoding and encoding support you need to install the FLAC++ libraries and headers.
For Ogg Vorbis decoding and encoding you need to install the Ogg Vorbis libraries and headers.

:lolflag:

---

### Post by hvthao on 2007-04-30
Another solution is to normalize audio files before making audio CD by using the command 'normalize' (or normalize-mp3, or normalize-ogg). For example, 
$normalize-mp3 -b *.mp3
will normalize all mp3s in the current directory. (See manpage for more options)

---

### Post by BLTicklemonster on 2007-05-01
How would I normalize and entire directory, and at what audio level would they be normalized to? I don't want to go freaking up a whole collection of Lithuanian Yodeling Medleys, you know!

Anyway, I installed kde, and still it would not compile. I'll look at the other recommended stuff and try again, but I don't think that will help, because it was the same kde error.

---

### Post by hvthao on 2007-05-01
As I stated before, you can normalize an entire directory by using option -b of the command normalize-mp3. If you want to do that, simply change to that directory, and run the command : "normalize-mp3 -b *.mp3". It will convert all the mp3s to the same volume level, the default is -12dBFS (you can change it by using option -a).

Because k3b requires many dependencies, the best way to install it is to go to the website of Debian ([http://packages.debian.org/unstable/otherosfs/k3b](http://packages.debian.org/unstable/otherosfs/k3b))  and get the .deb. If your system requires dependencies, just follow the instructions when installing to get the required packages!

---

### Post by BLTicklemonster on 2007-05-01
Dependency hell. I'll work on this later.

Thanks!!!

---

### Post by BLTicklemonster on 2007-05-25
```
bill@bill-desktop:~/Desktop/musicproject$ normalize-mp3 -b *.mp3
Decoding King Crimson - 21st Century Schizoid Man.mp3...
Can't exec "": No such file or directory at /usr/bin/normalize-mp3 line 553.
Error decoding, stopped at /usr/bin/normalize-mp3 line 558.
```


```
	}
	$ret = system(@decode_args);** (line 553)**
	if ($verbose < 2) {
	    close(STDOUT);
	    open(STDOUT, ">&OLDOUT");
	}
	$ret == 0 || die "Error decoding, stopped";
    }
```

Dang.

---

### Post by ricardisimo on 2007-06-04
Uggh... a word of warning to any nübs like myself: Don't try this. I attempted to install the1.01 version with all of the dependencies and now update manager, synaptic and a slew of other thing look to be totally broken. Wish me luck fixing this.

---

