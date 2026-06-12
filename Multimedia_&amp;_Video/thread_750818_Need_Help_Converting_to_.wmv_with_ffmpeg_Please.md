---
title: "Need Help Converting to .wmv with ffmpeg Please"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by esc1 on 2008-04-09
I have winff set up. I can convert most files like an avi to xvid for psp and such.  I can't for the life of me get it to convert to wmv. I have medibuntu in my sources, but I'm not sure I got it set up correct. I ran the following command mistakingly to remove the non-free components:

sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

as shown here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I think I may have corrected that.  I added:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

to my sources.list

Can anyone help me?


sudo apt-get install w32codecs  tells me I have the newest

and 

wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

tells me 

 w32codecs depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.

The way I understand it I have to update from feisty to get libc6?

---

### Post by mc4man on 2008-04-09
> The way I understand it I have to update from feisty to get libc6?
no you already have it - version of libc6 on system is 2.5-0ubuntu14., which is the feisty version and you don't want to change. It also said you have w32codecs installed. If your not pleased with version installed, uninstall and try 
[http://debian-multimedia.org/pool/main/w/w32codecs/](http://debian-multimedia.org/pool/main/w/w32codecs/)

---

### Post by esc1 on 2008-04-09
I tired the version you linked to and still can't convert.  

Winff gives me:

echo -n "\033]0; Converting RCS2E1.avi (1/1)\007"
/usr/bin/ffmpeg -i "/home/username/Desktop/RCS2E1.avi" -vcodec wmv2  -acodec wmav2 "/home/username/RCS2E1.wmv"
rm "/home/username/.winff/ff080409233138.sh"

---

### Post by esc1 on 2008-04-10
Bump :(

---

### Post by esc1 on 2008-05-01
Still need some help getting this working if anyone has some ideas.

---

