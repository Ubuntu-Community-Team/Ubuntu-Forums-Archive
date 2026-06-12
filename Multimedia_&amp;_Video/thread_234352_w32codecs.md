---
title: "w32codecs"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by somi38 on 2006-08-11
i have w32 codecs but i have no idea about its install.
how can i install w32codecs
 please help me

---

### Post by dyoung66 on 2006-08-11
Instructions to install w32codecs are here:
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)

try this: (from above link)


wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)

sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

(youll need to change the file name to whatever you downloaded..)
hope this helps

---

### Post by somi38 on 2006-08-11
i have ubuntu5.10 u send me links that are for ubuntu6.06
please tell me what i do

---

### Post by tseliot on 2006-08-11
> **somi38 said:**
> i have ubuntu5.10 u send me links that are for ubuntu6.06
please tell me what i do

Do this as he said:
wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)

sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

It works on Breezy as well

---

### Post by somi38 on 2006-08-11
please send me total commands 
and will w32codecs pack run

---

### Post by somi38 on 2006-08-11
i have w32codecs pack 
please help me

---

### Post by tseliot on 2006-08-11
> **somi38 said:**
> i have w32codecs pack 
please help me

1) Put the deb file in your home folder

2) then open Terminal or Konsole and type:
```
sudo dpkg -i w32codecs*.deb
```

---

### Post by somi38 on 2006-08-11
salman@salman:~$ sudo dpkg -i w32codecs*.deb
(Reading database ... 72752 files and directories currently installed.)
Preparing to replace w32codecs 20060611-1plf1 (using w32codecs_20050412-0unoffic ialubuntu2_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20050412-0unofficialubuntu2) ...
salman@salman:~$


output is this 
please tell me now what i do

---

### Post by tseliot on 2006-08-11
> **somi38 said:**
> salman@salman:~$ sudo dpkg -i w32codecs*.deb
(Reading database ... 72752 files and directories currently installed.)
Preparing to replace w32codecs 20060611-1plf1 (using w32codecs_20050412-0unoffic ialubuntu2_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20050412-0unofficialubuntu2) ...
salman@salman:~$


output is this 
please tell me now what i do

Now you have installed the codecs.

You need to use either totem or kaffeine with a xine backend:

If you use GNOME:
```
sudo apt-get install totem-xine
```

If you use KDE:
```
sudo apt-get install kaffeine-xine
```


OR if you prefer Mplayer:
```
sudo apt-get install mplayer-386
```

---

### Post by somi38 on 2006-08-12
salman@salman:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libtotem-plparser0
E: Package totem-xine has no installation candidate
salman@salman:~$ 


out put is this 
now what i do

---

### Post by clauguia on 2006-08-13
somi38 dont install totem-xine. ubuntu comes with totem-gstreamer wich is as good as xine.

Do this at the terminal:
$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly

Enter your pass and it should be ok.

---

### Post by somi38 on 2006-08-13
how can i install totern-gstreamer
websit
instrutions

---

### Post by ishift on 2006-08-14
hi..

i actually went the totem-xine way, and, although the video works, there is no sound. i tested a wmv file.

any help would be greatly appreciated. thanks.

---

