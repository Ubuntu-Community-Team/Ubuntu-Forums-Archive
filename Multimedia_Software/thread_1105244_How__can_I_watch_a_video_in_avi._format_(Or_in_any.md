---
title: "How  can I watch a video in avi. format???? (Or in any other format)"
date: 2009-03-24
forum: Multimedia Software
---

### Post by eeter on 2009-03-24
For now after two hours of Google'ing and searching the forum, while trying different kinds of tricks how to play avi. files, I'm more frustrated than ever by the fact that there seems to be no clear solution for this and that in Ubuntu. Seems Like no-one knows exactly how to make thing work in Ubuntu. What should I do now??? - My girlfriend fell asleep while I was dealing with this problem and it's pretty obvious that I'm not going to get it work in near future. Or is it possible?

I have Ubuntu Studio 8.04 installed on my machine and I have installed all the updates.
I tried installing: MPlayer, gxine, Totem, Totem (xine), Kaffeine, VLC... And some stuff I did not understand and remember... There was some restricted formats thing too which failed while installing...

Any suggestions?

You know it sucks awfully if one is unable to watch movies...:(

---

### Post by cariboo on 2009-03-24
I would suggest you install the ubuntu-restricted-extras meta package. THis will install java, flash, mscorefonts and most of the codecs you need for most types of audio/video media. The ubuntu-restricted-extras package is in the repositories and you can use Synaptic Package Manager to install it. If you haven't installed any codecs yet, this will install approximately 60 more packages.

Jim

---

### Post by eeter on 2009-03-24
Nothing changed. Still the same error in Totem (xine):

[B]Totem could not play 'file:///home/urmo/systeem/Filmid/movie.avi'.

There is no plugin to handle this movie.[/B]

Kaffeine just won't start playing the file. 
VLC shows 00:00 on time line.
MPlayer does some freaky blinking thing and screams for error, but won't let me to close it. After 30 second the blinking stops and following error occurs: 
[B]Fatal error!
FATAL: Could not initialize video filters (-vf) or video output (-vo).[/B]

---

