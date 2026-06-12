---
title: "help... MPEG4ip installation problem ......."
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by junquan on 2008-03-22
i am linux newbie, n i wan install the mpeg4ip, after i type ./bootstrap, it come out the problems below:

Mp4live encoder report:
*** ffmpeg encoder is not installed
*** xvid encoder is not installed
*** x264 encoder is not installed
*** lame encoder is not installed
*** faac encoder is not installed
ready to make

but i install the lame, ffmpeg, x264 oledi
root@junquan:/home/junquan/Desktop/mpeg4ip-1.5.0.1# apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded

root@junquan:/home/junquan/Desktop/mpeg4ip-1.5.0.1# apt-get install lame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.

who can help me??

---

### Post by garbage2 on 2008-04-25
Maybe you should install also the "dev" version of those packages. Using the search function from the Synaptic utility in Gnome you can easily find and install all of them. 
I think also that you can achieve best performance now using Ubuntu 8.04 Hardy.

---

### Post by frankki on 2008-06-25
I have the same problem with the install of MPEG4IP : the encoders seems not to be installed. Moreover, those packages may be deprecated on the multiverse depot.
Even with Adept (I'm on kubuntu), I can't find any package related to this.

Can someone please help me?

---

