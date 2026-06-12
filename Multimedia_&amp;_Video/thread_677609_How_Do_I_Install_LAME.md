---
title: "How Do I Install LAME?"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by LinuxLlama422 on 2008-01-25
...cuz i have no idea.

i tryed downloading and compiling it

it gives me a makefile error

and i can't find it on any of the update, or add/remove programs etc...:confused:

---

### Post by wolfen69 on 2008-01-25
go to system>admin>software sources. make sure all boxes are checked. close and reload.

go here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and install the medibuntu repositories.

then you should be able to find LAME in synaptic package manager.

---

### Post by disturbed1 on 2008-01-25
It's in synaptic under the multiverse repo. Make sure that repo is enabled.

It should be noted that lame **is not** in the Medibuntu repos.

---

### Post by LinuxLlama422 on 2008-01-25
thanks, that was fairly easy...

now I can sync the music from my Zen to my laptops new hard drive, and start streaming audio :guitar:

---

### Post by andrew.46 on 2008-02-13
Hi,

 I see that you have resolved your issue:

> **LinuxLlama422 said:**
> ...cuz i have no idea.
i tryed downloading and compiling it
it gives me a makefile error
and i can't find it on any of the update, or add/remove programs etc...:confused:

but can I ask what the error was? Lame usually compiles without too much trouble; sometimes the error relates to the fact that Ubuntu does not have compiling tools by default. The following is required:

```
$ sudo apt-get install build-essential checkinstall
```

This would solve error messages such as 'gcc not found'.

                Andrew

---

### Post by 47_MasoN_47 on 2008-05-14
I know this is bringing back an old thread, but for people who may be Googling this in the future here's an easy way to do it.  Enter the following into a terminal.
```
sudo aptitude install lame
```
That's all I did and it installed fine.  It installs to /usr/bin/lame also if you need to point an application to it.

---

