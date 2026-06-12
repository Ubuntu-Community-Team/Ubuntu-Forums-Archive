---
title: "Converting to avi no libxvid"
date: 2011-11-20
forum: Multimedia Software
---

### Post by WelshChris on 2011-11-20
Just managed to solve this, so I thought I'd post my solution to help others.

My problem - converting a a mkv video to avi.

There were so many suggestions from various locations which led to dead ends.

One suggestion was that my ffmpeg version was wrong, and that I needed the medibuntu version and not the plain ubuntu version.

Tried to install the medibuntu repository.  The medibuntu wiki helpfully provided a script which downloaded a new sources.list using wget.  Unfortunately, this stalled, even using several mirrors.
  This annoyed me no end.  I knew all I had to was add the line to sources.list, and update.  Why on earth use this script which was meant to make things easier, but ended up making things impossible?

So, ignoring the helpful but ultimately useless medibuntu wiki, I added this line to my /etc/apt/sources.list :
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free # Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 

Then, updated the database using :
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 


I reinstalled ffmpeg :
sudo apt-get install ffmpeg.

This still didn't solve the problem, but I eventually managed the find the right package from another website.
Find and install  libavcodec-extra-52  via synaptic, or ubuntu's software centre.

The conversion is now progressing successfully.

Hope this helps others in the same position.

---

### Post by SeijiSensei on 2011-11-20
Or you could just use mencoder: [http://en.gentoo-wiki.com/wiki/Mencoder](http://en.gentoo-wiki.com/wiki/Mencoder)

---

