---
title: "Hauppauge PVR 150 IR Blaster Install"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by ptipton on 2007-01-14
I am installing mythth backend on a headless server which has gone smoothly with the exception of getting the pvr 150 irblaster working to change channels on my satellite box.

I have been following the instructions for Edgy Mythtv install in the community documentation including the LIRC and External Changer documents. At one point the remote was working albeit as a " Hauppauge_350" , however, after trying various different lircd.conf files, now when i run IRW I get " Connection refused".

As a backend server I dont actually need the remote to work just the IR Blaster but have had no luck whatsoever in this respect. 

I have found this page on the subject [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) which requires the download of a patched lirc and ir blaster firmware but I am unsure if this is the correct thing to do in edgy.

Any advice on how to set this up would be much appreciated, i'm a realtive newbie and the mythtv install has gone very well excluding this, however without the ir blaster to change channel on the satelite box mythtv is basically useless.

---

### Post by ptipton on 2007-01-18
Was told by superm1 that currently the only option is to avoid the packages and compile from source. I used the instructions fron the link in my original post and now remote and ir blaster working perfectly. Thanks for the help superm1.

---

### Post by ickyb0d on 2007-02-12
will that tutorial work with the pvr500 MCE kit?  and will it affect any of the current lirc packages i have installed now? i think i actually installed/patched my lirc from superm1's repository on the howto page.

[here]("http://registration.hauppauge.com/webstore/images/pvr500mcekit_big.jpg") is what my receiver looks like, and [here]("http://www.irblaster.info/tivo_irblaster_small.jpg") is my blaster that plugs into the back of my receiver.  I'm really just wondering what the best way is to get started on this.  any help would be appreciated.  thanks!

---

