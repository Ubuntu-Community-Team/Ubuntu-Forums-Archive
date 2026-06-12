---
title: "Can't play DVD's"
date: 2009-02-28
forum: Multimedia Software
---

### Post by eshababy1 on 2009-02-28
Can anyone help me i'm new to ubuntu.
Im trying to play DVD's but keep getting this error message!
This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first. 

Switch to the 'synaptic' package manager to resolve this conflict.

That's the easy bit! the hard bit is i don't know which software i need to remove.::

---

### Post by taurus on 2009-02-28
You need libdvdcss2 to play commercial DVD's.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by eshababy1 on 2009-03-05
Thanks for your reply.
I have downloaded libdvdcss but now i don't know what to do with the file or where to put it.
i clicked on the install icon and got this message A typical way to configure libdvdcss is:

   ./configure --prefix=/usr

See `./configure --help' for more information

That sounds great but i don't know what to do with this information, As i said i'm new to ubuntu So i think any information will have to be in a very basic form.
Thanks again.

---

### Post by thraxy on 2009-03-05
The best way is to add the medibuntu repository. A repository is like a download location for different packages (software). Medibuntu has some packages that can't be added to the normal repository for legal reasons. It's perfectly legal for you to download the packages yourself and install them though.

You need to open up your terminal (Applications -> Accessories -> Terminal) and put in the code from this site [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories"), remember to put in the code for your version of Ubuntu + the GPG key mentioned no the site.

After that, simply type in terminal,
```
sudo apt-get install libdvdcss2
```

With the medibuntu repository added, you can also install other software the same way, like for example Skype
```
sudo apt-get install skype
```

or Google Earth
```
sudo apt-get install googleearth
```

Hope this helps you out :)

---

### Post by eshababy1 on 2009-03-09
Thanks for that thraxy!
I now understand how to input the data. My dvd's play now but i still have a problem. Ive tried using VLC media player and also movie player and all my dvd's flicker.
Have you any idea's 

Thanks again i'm getting there!

---

### Post by binbash on 2009-03-09
> **eshababy1 said:**
> Thanks for that thraxy!
I now understand how to input the data. My dvd's play now but i still have a problem. Ive tried using VLC media player and also movie player and all my dvd's flicker.
Have you any idea's 

Thanks again i'm getting there!

Go to vlc preferences and change the video output to X11

---

### Post by eshababy1 on 2009-03-14
Thanks for your help  everythings working o k now!
It's taken me some time to get everything working but with the help of people from the ubuntu forum I'm starting to get the hang of the system.

---

