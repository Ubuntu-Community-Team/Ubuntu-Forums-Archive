---
title: "How can you install butt in Xubuntu 12.10?"
date: 2012-11-25
forum: Multimedia Software
---

### Post by Dcn Joseph Suaiden on 2012-11-25
](*,)

I cannot figure out for the life of me how to install b.u.t.t. (butt.sourceforge.net) in Xubuntu 12.10.

I tried following the older instructions using xterminal on this page:
[http://www.omgubuntu.co.uk/2010/09/broadcast-on-icecastshoutcast-using-butt](http://www.omgubuntu.co.uk/2010/09/broadcast-on-icecastshoutcast-using-butt)

And it appears there is no package for 'portaudio' or 'libfltk-dev' and when I hit the last command it says it installed fine, and then I don't see any place to run it.

I am completely lost here. :confused:

Is this still a viable program for connecting to a Shoutcast server? There hasn't been an update in over a year.

---

### Post by monkeybrain2012 on 2012-11-26
If you open synaptic and check you will find some versions of libportaudio and libfltk1.1-dev and libfltk1.3-dev, so try to install some of those. The names of these packages might have changed. 

This is one reason why I prefer to use synpatic rather than sudo apt-get install blah blah because with the later you have to know the exact names of the packages and sometimes it doesn't work just because of a trivial name change.

---

### Post by Dcn Joseph Suaiden on 2012-11-26
> **monkeybrain2012 said:**
> If you open synaptic and check you will find some versions of libportaudio and libfltk1.1-dev and libfltk1.3-dev, so try to install some of those. The names of these packages might have changed. 

This is one reason why I prefer to use synpatic rather than sudo apt-get install blah blah because with the later you have to know the exact names of the packages and sometimes it doesn't work just because of a trivial name change.

I prefer Synaptic also, but it couldn't find b.u.t.t. If anyone knows the repository for it I'd be much obliged!

I'll try that.

---

### Post by Dcn Joseph Suaiden on 2012-11-27
> **monkeybrain2012 said:**
> If you open synaptic and check you will find some versions of libportaudio and libfltk1.1-dev and libfltk1.3-dev, so try to install some of those. The names of these packages might have changed. 

This is one reason why I prefer to use synpatic rather than sudo apt-get install blah blah because with the later you have to know the exact names of the packages and sometimes it doesn't work just because of a trivial name change.

No luck. in xterminal I get "./configure: no such file or directory" after installing libportaudio and libfltk1.1-dev in synaptic.

If anyone knows what old repository if any to find b.u.t.t that would help massively.

---

### Post by monkeybrain2012 on 2012-11-27
> **Dcn Joseph Suaiden said:**
> No luck. in xterminal I get "./configure: no such file or directory" after installing libportaudio and libfltk1.1-dev in synaptic.



You need to first cd (change directory) into the folder where the configure script is. So if your folder is called butt and it is on the desktop you have to first type
```

cd Desktop/butt
```

Note the capital D

and then ./configure.

---

### Post by Dcn Joseph Suaiden on 2012-11-27
> **monkeybrain2012 said:**
> You need to first cd (change directory) into the folder where the configure script is. So if your folder is called butt and it is on the desktop you have to first type
```

cd Desktop/butt
```

Note the capital D

and then ./configure.

Thanks for your patience. I am really not good at installing from source. Does it matter if I put the extracted folder in the Downloads folder? This is what I get:

> 
me:~/Downloads/butt-0.1.12-linux-bin$ ./configure && make
bash: ./configure: No such file or directory


There is also an "install.sh" file. Is there a way to run that?

The butt directory (I hate the name of this thing) has the following in it

> butt	   install     KNOWN_BUGS  player_plugins  uninstall.sh
ChangeLog  install.sh  LICENSE	   README


I am sure I am doing something wrong, but totally clueless as to what.

---

### Post by stinkeye on 2012-11-27
Found butt in this [**_[COLOR="DarkRed"]PPA[/COLOR]_**]("https://launchpad.net/~ys/+archive/radio-battletoads").
Know nothing about it, but the deb for quantal installed and
the gui opens when running **butt** in terminal or the alt+f2 run command.

---

### Post by Dcn Joseph Suaiden on 2012-11-27
That worked. 

Thank you both.

---

