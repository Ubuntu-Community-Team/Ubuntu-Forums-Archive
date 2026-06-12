---
title: "Movies on DVD"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by mrtn-- on 2007-08-22
Hi,

I wrote a post on this topic yesterday, but didn't get any answers. I guess I wasn't clear enough in stating my problem. The thing is that I can't watch DVD movies on my ubuntu laptop. I have installed all the Gstream plugins, gxine and ogle but it still doesn't work. gxine doesn't recognize the stream format, and when I use mplayer in a terminal I can never read the main track. On some discs I can read other tracks such as extra material etc, but even then there is a problem with image quality, which is far from that of a DVD.

What I find most puzzling is that sometimes I can hardly even browse the disc. The DVD player keeps reading and reading but it's futile. I know this sounds like there's a problem with the disc, but I've tried about five or six discs and none work properly. In some cases I've been able to play  a bit of the main track, but it doesn't run smoothly and I can't forward or rewind.

I have a China bought Lenovo laptop, and all the discs I've played are Chinese pirated DVDs. They are usually lower quality than other discs but a normal computer can always execute them. And the fact that I can never watch the DVD menu is enough to convince me that this is some kind of software problem.

Thanks in advance,

Mårten.

---

### Post by wolfen69 on 2007-08-22
did you install libdvdcss2 and libdvdread3 from synaptic?

---

### Post by mrtn-- on 2007-08-22
In fact I think a friend helped me get libdvdcss2 but not libdvdread3. However, I'm too much of a noob to actually see if I have them installed or not. Nothing comes up when I search in Synaptic for them, so I don't know how to install them. I tried writing sudo apt-get libdvdread3 but it didn't work. How do I install them?

---

### Post by tahaselim on 2007-08-22
you should try writing :

sudo apt-get install libdvdread3

Taha Selim

---

### Post by mrtn-- on 2007-08-22
Oh... Turns out I had both of the packages installed already. And it still doesn't work. I just don't get it...

---

