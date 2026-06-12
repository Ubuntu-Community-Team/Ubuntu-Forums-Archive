---
title: "Curious problems when I replaced a geforce card for a ati card"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by Rollinpizza on 2007-09-05
Well, yesterday I decided to change my graphic card and I borrowed a friend an Ati x1600 AGP de 512M to test if it works in Ubuntu Feisty because I've read that  Ati support sucks frequently in this operating system. Anyway, I checked the compatibility card with ubuntu looking in some forums and there are people that they got it to work this card perfectly.

In my case, the card works with 3d activation included, but there is a group of things that I didn't have when I had installed my geforce 4 card. Firstly, if I want to run some application that requires 3D, I have to run it as root (with sudo) because if I run it as user, the application doesn't work with 3D (For example: Cedega or Frets On Fire). Finally, I can't activate the xgl server (important for beryl or compiz-fusions). I modified a lot the configuration script of xgl session following several guides without success.

I use the driver fglrx from the restricted modules manager.

I searched a lot of guides but everything begin from a clean installation and this isn't my case. It may be I have to modify a thing that isn't in the guides. I don't know...

Thanks in advance. ;)

Regards. :popcorn:

---

### Post by Rollinpizza on 2007-10-30
Finally, I solved my problem installing Gutsy and fglrx 8.42.3

---

