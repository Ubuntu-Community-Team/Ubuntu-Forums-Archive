---
title: "Playing WMV files?"
date: 2009-04-28
forum: Multimedia Software
---

### Post by sandman3838 on 2009-04-28
Hello

I have UBUNTU 9.04 at the moment I can't play WMV files.

(Windows Media Video (WMV) is a compressed video file format for several proprietary codecs developed by Microsoft.)

If I remember correctly I need to install win32codecs files and VLC?

Is this correct and would any of you happen to know or have a link to an up to date page that is for Ubuntu 904.

I should note that I just did a clean install and my system is really clean I don't think there will any unknown issues from other installed programs?

Thanks for your help.

---

### Post by SuperSonic4 on 2009-04-28
That sounds right. Remember to enable the medibuntu repos first

---

### Post by sandman3838 on 2009-04-28
Hello

What do you think about this!
Should work?

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

then

Code:

sudo apt-get install w32codecs


Code:

sudo apt-get install non-free-codecs

---

### Post by kiridude on 2009-04-28
I installed "ubuntu-restricted-extras" codecs and vlc and can play everything...

sudo apt-get install ubuntu-restricted-extras vlc

---

### Post by kiridude on 2009-04-28
I used this for medibuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

then import the gpg key and update package list:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by sandman3838 on 2009-04-28
So you suggesting.......

1st
Code:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

import the gpg key and update package list:

2nd
Code:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then

3rd
Code:

sudo apt-get install w32codecs

4th
Code:

sudo apt-get install non-free-codecs

and I shouldn't worry about:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

### Post by SuperSonic4 on 2009-04-28
Both methods will work so use whichever you like. I always use the method described in the sticky in this forum:

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

[Source]("http://ubuntuforums.org/showthread.php?t=766683")

```
sudo apt-get install ubuntu-restricted-extras
``` would be better than ```
sudo apt-get install w32codecs
``` although I believe the latter does not include java or flash. Bear in mind that you may need to change w32codecs to w64codecs if you run a 64 bit system, you can find out by typing ```
uname -m
``` (i386 is 32bit and x86_64 is 64bit)

---

### Post by sandman3838 on 2009-04-28
What I have is:
uname -m
i686

Got it I didn't see 
(i386 is 32bit and x86_64 is 64bit)

I'll let you know how it goes with:

CODE:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update


CODE:
sudo apt-get install ubuntu-restricted-extras

---

### Post by kiridude on 2009-04-28
I thought you had already tried what you have.

So, I would suggest trying what you have already as it corresponds to the Medibuntu tutorial, which is [here]("https://help.ubuntu.com/community/Medibuntu")

Another way to do it is what I posted.

Try it out, and if you have any problems, let us know. And don't forget the vlc player.

---

### Post by sandman3838 on 2009-04-28
Got it!

This did it for me:

CODE:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update


CODE:
sudo apt-get install ubuntu-restricted-extras

Next after this I installed MPLAYER & VLC and everything was working!

Thank you all so much for your help!  :)

---

