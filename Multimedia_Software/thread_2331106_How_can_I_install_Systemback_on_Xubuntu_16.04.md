---
title: "How can I install Systemback on Xubuntu 16.04?"
date: 2016-07-18
forum: Multimedia Software
---

### Post by mariusfisher on 2016-07-18
Hi everybody,

yes, the titel has already said what I would like to know:

Can someone help me to install Systemback on Xubuntu 16.04? Or any tools like Systemback?

Thank you for any posts.

Marius

---

### Post by QDR06VV9 on 2016-07-18
For Systemback:
```
sudo add-apt-repository ppa:nemh/systemback
sudo apt-get update
sudo apt-get install systemback
```
This PPA contains the stable version of Systemback.
His PPA is here: [https://launchpad.net/~nemh/+archive/ubuntu/systemback](https://launchpad.net/~nemh/+archive/ubuntu/systemback)
Be aware your are update-ing your system with unsupported packages from           this untrusted PPA  **(Normal warning we give when adding outside Sources)**

---

### Post by Bucky Ball on 2016-07-18
Welcome. Here's a little something for the handbook about adding a PPA. I would *avoid* adding too many third-party PPAs. They are *not* officially supported by Canonical or Ubuntu and you add them at your own risk. :) I usually use a neat little app called Zim for keeping notes and links. It is in Synaptics.

The best place to start is always  with a search, for instance 'install systemback ubuntu' and see what pops up. Append the release number if you need to get more specific. I found the [Launchpad page here]("https://launchpad.net/~nemh/+archive/ubuntu/systemback"). Go there and click 'Technical details about this PPA' then select your Ubuntu release.

Disregard that there is no Xubuntu version. There isn't. You will be dragging in whatever it needs to survive in your xfce4 environment.

Now, on your machine, Applications> Software and updates> Other software> Add. Copy the lines on over as requested. Read carefully the examples it gives you. 

When you're done, Software and Updates should update the system. Open Synaptics and Systemback should be there.

As you've added the PPA, Systemback will update automatically when you update. Any issues or questions, post. If there's problems with your system after installing the PPA, disable the PPA in S and Updates. Good luck. :)

* Ninja-ed by runrickus ... ;)

---

### Post by danbosse1 on 2016-07-18
Hi

I realize that you want to install SystemBack, but Timeshift is a lot better and much easier to use. (don't hit return to program when to erase copies)

```
sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install timeshift
```

---

### Post by mariusfisher on 2016-07-27
Hi, thanks.

When I install this, I would able to uninstall this program. :)

I do not want to install something when I will not uninstall it.

---

### Post by QDR06VV9 on 2016-07-27
Yes you can uninstall it...and remove the PPA you choose to install it with.
Using PPA purge: [http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

---

