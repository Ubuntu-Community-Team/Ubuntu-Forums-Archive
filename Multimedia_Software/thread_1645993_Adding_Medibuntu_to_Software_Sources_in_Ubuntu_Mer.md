---
title: "Adding Medibuntu to Software Sources in Ubuntu Mervick"
date: 2010-12-15
forum: Multimedia Software
---

### Post by Akhnatoun on 2010-12-15
When I installed maverick and started to install the software packages, I opened the terminal to run the command of adding Medibuntu repository to my sources list. I followed the instructions mentioned in this page:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

However, when i ran this command, i got this error:

```
$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

/etc/apt/sources.list.d/medibuntu.list: No such file or directory

```

Then I tried to add it manually by following this method and it has succeeded  with me with my Maverick Meerkat, run this command in the Terminal:

```
$ sudo nano /etc/apt/sources.list
```

This should allow you to edit the file in the terminal. Add the following line at the end of the file:

**deb [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick free non-free**

Press ctrl+X to save file and exit.

N.B: You can do this also in GUI by adding the same two lines separately to the Software Sources which you can reach from Applications > Ubuntu Software Center > Edit > Software Sources. In the &#8220;Other Software&#8221; tab, press the &#8220;Add&#8221; button, and type this line in the pop up window:
[B]
deb [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick free non-free[/B]

Then, run this command to add Medibuntu's GPG key to your keyring, which is needed to authenticate the Medibuntu packages. 

```
$ sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Hope this be helpful for someone. Good luck. ;)

---

