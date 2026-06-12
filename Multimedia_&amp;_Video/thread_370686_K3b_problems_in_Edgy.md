---
title: "K3b problems in Edgy"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by trents on 2007-02-26
Anybody else having problems running K3b in Edgy? I installed it with Synaptic and it seemed to load the first time. After installing the firegl drivers for my Radeon 9700 and some other updates K3b won't even load now. Gnome Baker seems to work fine, however.

---

### Post by louis_nichols on 2007-02-26
What kind of error do you get? Did you try to start it from console and se ethe output?

---

### Post by trents on 2007-02-26
I'm not familiar with console. Is that where you leave the GUI shell and go to a command line operation? Ctrl Alt F1 or something like that? What would I type in to run k3b? As you may have gathered, I am no linux expert but I am learning and appreciate all the help I have received from the community.

Steve

---

### Post by taurus on 2007-02-26
Are you using Gnome or KDE?  With Gnome, 

Applications -> Accessories -> Terminal
```
k3b
```

---

### Post by trents on 2007-02-26
Gnome. Thanks.

---

### Post by trents on 2007-02-26
Here's the output when I execute K3b from terminal:

steve@Edgy:~$ k3b
DCOP aborting call from 'anonymous-6337' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP aborting call from 'anonymous-6326' to 'k3b'
ERROR: Communication problem with k3b, it probably crashed.
steve@Edgy:~$

Does that tell us anything?

Thanks, Steve

---

### Post by louis_nichols on 2007-02-27
hm... actually, it does. Try this: after logging in, open a terminal window and type:

```
kdeinit
```
After this, assuming of course it runs without any errors, try to execute:
```
k3b
```

---

### Post by trents on 2007-02-28
This is what I get when executing "kdeinit" in terminal:

steve@Comp1Ubuntu:~$ kdeinit
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
steve@Comp1Ubuntu:~$

I just did a fresh intall of Dapper and tested K3b before installing firegl drivers. K3b loaded fine. But after installing the firegl drivers I got the errors  above when executing kdeinit.

Steve

---

