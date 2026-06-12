---
title: "flash download and watching dvd's"
date: 2009-12-23
forum: Multimedia Software
---

### Post by Dieter3 on 2009-12-23
I'm very new to linux and am developing a huge respect. 

Could some one please explain how i can install flash. I have downloaded it and am getting negative notices when i try to install.

What will i need to do in order to watch any dvd using movie player? Or is another player necessary?

And finally, can anyone recommend websites with linux downloads for creating spider diagrams?

Thanks!

---

### Post by proxess on 2009-12-23
First off, to get proper codec support for Ubuntu, you should add the medibuntu repositories. As stated on their website, open a terminal (Applications=>Accessories=>Gnome Terminal) and copy paste the following command in:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
When prompted for your password, just type it in and press enter.

Now when that is done, open the Synaptic Package Manager (Somewhere in the System menu) and hit the reload button. After that add in the following packages:
```
flashplayer-installer
w32codecs (w64codecs if you have a 64bit Ubuntu)
libdvdcss2
ubuntu-restricted-extras
```
After selecting them, just hit the install button and say yes to all the annoyances like "are you sure?" and "do you accept the license?".
With that I think you're pretty much set to go.

---

### Post by scottuss on 2009-12-23
I'd also recommend VLC as a great all round media player (I've yet to find something it can't play! - within reason!! :) )

---

### Post by Dieter3 on 2009-12-23
Your information has been spot on, easy to follow and led to me learning a little more. Thank you very much!

---

