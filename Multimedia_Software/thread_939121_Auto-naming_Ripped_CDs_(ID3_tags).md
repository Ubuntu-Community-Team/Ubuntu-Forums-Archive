---
title: "Auto-naming Ripped CDs (ID3 tags)"
date: 2008-10-05
forum: Multimedia Software
---

### Post by TomDaBomb2u on 2008-10-05
Hello,

I am in the process of completely switching over from Windows to Ubuntu. I'm looking for a program that automatically names my CDs when inserted and ID3 tags them when ripped, like Windows Media Player. 

Any suggestions???
Thanks!

-Thomas

---

### Post by surfed on 2008-10-05
I have always found grip to give me exellent results in both ripping quality and free-cddb naming and tagging of disks and songs.

---

### Post by FakeOutdoorsman on 2008-10-05
I like abcde.  It's quick and easy.
[abcde: Command Line Music CD Ripping for Linux]("http://www.andrews-corner.org/abcde.html")

---

### Post by TomDaBomb2u on 2008-10-07
> **FakeOutdoorsman said:**
> I like abcde.  It's quick and easy.
[abcde: Command Line Music CD Ripping for Linux]("http://www.andrews-corner.org/abcde.html")

Thanks guys! abcde seems pretty cool. But is there a way I can change the text editor from nano to gedit when I have to edit CDDB info??

-Thomas

---

### Post by FakeOutdoorsman on 2008-10-07
Try adding this to your .abcde.conf file:
```
EDITOR=/usr/bin/gedit
```

---

### Post by TomDaBomb2u on 2008-10-07
> **FakeOutdoorsman said:**
> Try adding this to your .abcde.conf file:
```
EDITOR=/usr/bin/gedit
```

Nope. That didn't work. I think I still like it though. Just not too fond of Nano lol.

I'm gonna look for some more documentation on the program, but it looks really promising. Thanks again!

---

### Post by FakeOutdoorsman on 2008-10-07
I made a guess as to where gedit might be since I don't have it, so it may be located elsewhere for you, or maybe it's not even named gedit:
```
whereis gedit
```
Maybe it needs single quotes:
```
EDITOR='/usr/bin/gedit'
```

---

### Post by andrew.46 on 2008-10-24
Hi Tom:

> **TomDaBomb2u said:**
> Thanks guys! abcde seems pretty cool. But is there a way I can change the text editor from nano to gedit when I have to edit CDDB info??

Glad you liked the guide :-). abcde reads the $EDITOR variable and I believe that this is the easiest way to change to gedit. To alter this you could try:

```
$ gedit $HOME/.bashrc
```

and then add the following:

```
 EDITOR=/usr/bin/gedit && export EDITOR 
```

I tried this on my own system, where normally I use vim, and it worked well enough.

  Andrew

---

### Post by NewDream on 2008-11-01
Just as a quick side note, with grip you do all of this from the GUI.  In the panel under config -> Encoding you can set all the tag information.

Good luck !

---

