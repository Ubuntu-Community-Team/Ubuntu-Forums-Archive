---
title: "gtkpod won't open mp4 for transfer to ipod"
date: 2008-10-19
forum: Multimedia Software
---

### Post by garglebog on 2008-10-19
Hi all,

I just got a new ipod nano 4th gen, and I want to use it without invoking the ugly name of iTunes. Everything works great with a combination of gtkpod and rhythmbox, except for some minor album art problems and this:

I cannot transfer video in the mp4 format to my ipod via gtkpod. When I try, I get the following error.

> Could not open '<filename>' for reading, or file is not an mp4 file.
The following track could not be processed (filetype is known but analysis failed): '<filename>'

Does anyone know of a possible cause/fix?

---

### Post by wbrokow1 on 2008-12-26
I get the same error.

I found a howto but I needed libacformat and when I tried to install that 
it could not get it.

I am just searching the posts to see if someone has this working.

If I find something about this I will reply to this thread.


THanks

---

### Post by wbrokow1 on 2008-12-26
This is the link I found:

[http://ubuntuforums.org/showthread.php?t=114946&highlight=put+video+on+a+ipod](http://ubuntuforums.org/showthread.php?t=114946&highlight=put+video+on+a+ipod)


Let me know if it works for you.

---

### Post by pedrosanta on 2010-12-01
Greetings.

I'm using Maverick Merkaat and I too had this issue. The gtkpod-aac package was transitional.

You should install the **libmp4v2-0** package (available on multiverse) to fix this. (Then you just restart the gtkpod and it should work.)

```
sudo apt-get install libmp4v2-0
```I found out about this when I was searching for the gtkpod-aac package and found this page: [https://launchpad.net/ubuntu/maverick/sparc/gtkpod-aac](https://launchpad.net/ubuntu/maverick/sparc/gtkpod-aac)

Hope it helps.

Cheers.

---

