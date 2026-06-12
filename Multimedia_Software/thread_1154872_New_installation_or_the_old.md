---
title: "New installation or the old???"
date: 2009-05-10
forum: Multimedia Software
---

### Post by voldemorte on 2009-05-10
Hello I'm new to the world of linux and I recently installed ubuntu9.04 very easily. thank you for that. I only have one question. I need multimedia editing softwares and I found out that ubuntu Studio has all the softwares that I require. I just want to kno that can I install the softwares off the studio DVD on my existing ubuntu installation or do I have to format my drive and install a fresh copy of ubuntu Studio??? If I can install on my existing ubuntu off the studio DVD then How do I do that???  Thanks for the help.....

---

### Post by lovinglinux on 2009-05-10
You can install all the software you like. Is not necessary to install Studio over Ubuntu. For example, if you want pitivi video editor, simply run this on the terminal:

```
sudo apt-get install pitivi
```

There is probably a command to install all stuff related to Studio, but I don't remember. Someone will probably tell you soon.

If you prefer a gui installation method, then you can open "System >> Administration >> Synaptic Package Manager" and search the software you want, mark it for installation and click the "Apply" button.

More info about installation methods:

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

---

### Post by voldemorte on 2009-05-10
I'm going to download ubuntu Studio from a friend anyway so I just want to know how do I add that DVD as a repository on my existing ubuntu installation??? Because I happen to have a limited bandwidth Broadband connection so I cannot get those softwares through your regular online repositories..... Please help

---

### Post by lovinglinux on 2009-05-10
> **voldemorte said:**
> I'm going to download ubuntu Studio from a friend anyway so I just want to know how do I add that DVD as a repository on my existing ubuntu installation??? Because I happen to have a limited bandwidth Broadband connection so I cannot get those softwares through your regular online repositories..... Please help


Go to "System >> Administration >> Software Sources" and tick the option "Installable from CD-ROM/DVD".

---

### Post by voldemorte on 2009-05-10
> **lovinglinux said:**
> Go to &quot;System >> Administration >> Software Sources&quot; and tick the option &quot;Installable from CD-ROM/DVD&quot;.

 OK thanks....

---

### Post by 3l3vans on 2009-05-11
i would also suggest a "real time kernel" . don't know what that is? search it and you will find an explanation.the RT kernel is the main difference between Ubuntu plain and Ubuntu Studio. the packages themselves are interchangable betwixt the two. the kernal will improve your performance while recording/editing, depending on your system you may or may not need it. to get thr RT kernel try this thread 

[http://ubuntuforums.org/showthread.php?t=1094593&highlight=3l3vans](http://ubuntuforums.org/showthread.php?t=1094593&highlight=3l3vans)

i installed it and now when i boot grub gives me the option of which one i want to use...by the way is it "kernel"? or "kernal"? i'm gonna go look that up ;)

---

### Post by voldemorte on 2009-05-11
> **3l3vans said:**
> by the way is it &quot;kernel&quot;? or &quot;kernal&quot;? i'm gonna go look that up ;)

 Well it is kernel n ya I'll look RT kernel up thanks for the info

---

