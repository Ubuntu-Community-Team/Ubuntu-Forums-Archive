---
title: "Can someone help a newbie out?"
date: 2008-04-29
forum: Multimedia Software
---

### Post by elorm9 on 2008-04-29
Hi, I'm new to linux. I installed it today on my computer and I was fascinated about how easy it was to get everything set up but, I can't play any of my flv files. I've searched the boards and I found out that I have to install that vlc package. I tried to install it and noticed that there were specific packages for different PC Architectures. I asked my dad which architecture this PC was using and he said it was i386. I downloaded the i386 package and tried to install it but it didn't work. I get this error "Dependency is not satisfiable: vlc-nox". How do I fix this?

---

### Post by CAsurfer on 2008-04-29
You should be able to install VLC via Synaptic. Go to System -> Administration -> Synaptic Package Manager. To run Synaptic, you can't have another package manager running.

---

### Post by criskat777 on 2008-04-29
if that dose not work go here and download the ubuntu file. it sould be a deb file so install will be a breeze. 



[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by scragar on 2008-04-29
just install via the command line or synaptic, all the dependencies should be downloaded then:
```
sudo apt-get install vlc
```

failing that(can't imagine why) you can always manual download it from the packages list:

[http://packages.ubuntu.com/search?keywords=vlc-nox&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=vlc-nox&searchon=names&suite=all&section=all)

---

### Post by elorm9 on 2008-04-29
Thanks for the help guys :). The Synaptic Manager thing actually worked.

---

