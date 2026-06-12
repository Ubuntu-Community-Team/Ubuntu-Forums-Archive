---
title: "I want to remove puddletag."
date: 2010-09-15
forum: Multimedia Software
---

### Post by jauntybluefish on 2010-09-15
Hi,
I installed python puddletag yesterday after having problems with Audio Tag Tool corrupting some folders on an sd card.
Firstly it will not run because it seems to think that there is no pyparsing module installed which there most definitely is, and secondly I have had enough messing about with it so i want to remove it totally plus all the dependencies.

I thought I could do it through root terminal but it will not uninstall.so I think I must be using the wrong command. I tried ```
apt-get remove python puddletag
``` within the directory of puddletag.

Please can someone let me know the proper command to remove this app.

Thanks
Andy

---

### Post by kostkon on 2010-09-15
How did you install it?

---

### Post by jauntybluefish on 2010-09-15
```
sudo apt-get install python-qt4 python-pyparsing python-mutagen python-configobj python-musicbrainz2 python-imaging
```
To get the dependencies and then


```
python setup.py install
```

to install the program. It shows up in the applications menu but does not run, nor does it run by using 
```
python puddletag
```

in a terminal.

But all I need to do is remove it now.

Thanks

---

### Post by kostkon on 2010-09-15
Did you try to install it by giving
```
sudo python setup.py install
```
or just
```
python setup.py install
``` ?

---

### Post by jauntybluefish on 2010-09-15
As I was already in root terminal I did not need to sudo. 
If I had not been root already I imagine the result would be a failure to install wouldn't it?;)


It's funny how different ways of doing things can give such different results isn't it?
Yesterday I ranted at Audio Tag Tool for messing up some folders on a micro sd card and today it worked perfectly by using a usb card reader instead of the usb cable to my phone.

---

### Post by egd on 2010-09-16
> **jauntybluefish said:**
> Hi,
I installed python puddletag yesterday after having problems with Audio Tag Tool corrupting some folders on an sd card.
Firstly it will not run because it seems to think that there is no pyparsing module installed which there most definitely is, and secondly I have had enough messing about with it so i want to remove it totally plus all the dependencies.Rather than deny yourself the opportunity to work with the best audio tagger available for Linux and OS X why don't you post the error message generated when attempting to run it.  My guess is that whilst you may have pyparsing installed it's an earlier release than is required.

---

### Post by jauntybluefish on 2010-09-16
OK...when run from the terminal in the Puddletag directory I get this
```
****@computer:~/Downloads/puddletag-0.9.4$ python puddletagThe PyParsing module wasn't found. Did you install it correctly?

```

When trying to run it from the menu it just does not start or do anything at all.
When trying to run using the Run Application shortcut, same applies.


Thats about it I think.
Thanks
Andy

---

### Post by egd on 2010-09-17
Am I correct in surmising you're running Ubuntu 9.04?  If so, the pyparsing module you've installed is older than that required by puddletag.  Download and install the latest version from [http://pyparsing.wikispaces.com/Download+and+Installation](http://pyparsing.wikispaces.com/Download+and+Installation) -- instructions are included on that page.

puddletag's dependencies are set out [**here**](http://puddletag.sourceforge.net/)

---

