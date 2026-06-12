---
title: "Advanced Video Editing: Need it Now"
date: 2007-08-25
forum: Multimedia Production
---

### Post by VideoProducer on 2007-08-25
I need to do some video editing in the coming weeks. I need at least:

- crossfades
- the ability to zoom / crop / pan

As far as I know, no Ubuntu software can do this yet. Am I mistaken?

Do I have to install a Windows XP partition, and use Sony Vegas (which I was using before Ubuntu). Or are there other options I should look into?

Thank you.

---

### Post by solar george on 2007-08-25
Kdenlive:
[http://www.kdenlive.org/](http://www.kdenlive.org/)
Jahshaka:
[http://www.jahshaka.org/](http://www.jahshaka.org/)

---

### Post by SpiritIsReality on 2007-08-26
howdy

here's a search, you'll recognize the first listing, 
[http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=video+editing+advanced&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgVrMf__LYkktWikvSQOq7m9PpLibh5w4ltViaoIqiAlj7Csbw-YzFEIPUUMYo2bCo9zx1wgtWZQoXtipUDSZR5f1Sf5NJ1V_UREEPOrOhhzslhOxU2rbvrl3z2XG73guJV2fkiw6EtGTQIRM_BXOZiIbV2XA3I4BIqeauokhMrpZqUbywzqMi8tShpbXc3Tql6y-EaCOhyD6p6Fq2WeAjHY8-3i-A&client=pub-7825705102693166&channel=3833691868](http://www.google.com/custom?cx=002165917076592449621%3Ay8jmiivon3o&q=video+editing+advanced&sa=Search&cof=AH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BDIV%3A%23cccccc%3BFORID%3A1%3BGFNT%3A%23666666%3BL%3Ahttp%3A%2F%2Fwww%2Egoogle%2Ecom%2Fcoop%2Fimages%2Fgoogle_custom_search_sm%2Egif%3BLH%3A55%3BLP%3A1%3B&adkw=AELymgVrMf__LYkktWikvSQOq7m9PpLibh5w4ltViaoIqiAlj7Csbw-YzFEIPUUMYo2bCo9zx1wgtWZQoXtipUDSZR5f1Sf5NJ1V_UREEPOrOhhzslhOxU2rbvrl3z2XG73guJV2fkiw6EtGTQIRM_BXOZiIbV2XA3I4BIqeauokhMrpZqUbywzqMi8tShpbXc3Tql6y-EaCOhyD6p6Fq2WeAjHY8-3i-A&client=pub-7825705102693166&channel=3833691868)

the second listing, here, worth a read
[http://www.linux.com/articles/60837](http://www.linux.com/articles/60837)

if you decide to dual boot
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

trails

---

### Post by VideoProducer on 2007-08-26
I forgot to mention, I also need to rotate the image 90 degrees.

I'll follow all the links posted above, and report what I find. Thanks for the assistance.

---

### Post by kayosiii on 2007-08-26
Cinelerra will do the tasks you ask. Search the forums for instructions on installing it. Expect to need to read the manual (you can hunt that down inline)... 

I should mention that it is a bit picky about input and output formats. Generally is it seems to be better behaved with uncompressed video and getting compressed output that is usefull can be diffucult. H264 is probably the best option for output.

---

### Post by salsaman on 2007-08-26
You could also use [LiVES]("http://www.getdeb.net/app.php?name=LiVES"), of course. Surprising that nobody mentioned it already.

---

### Post by KoRnholio on 2007-08-27
I would definitely recommend Cinelerra.  Its not that hard to install anymore - there's a Feisty repository, this method worked perfectly for me:

[http://www.kiberpipa.org/~gandalf/blog/?p=77](http://www.kiberpipa.org/~gandalf/blog/?p=77)

---

### Post by eye208 on 2007-08-29
> **VideoProducer said:**
> I need to do some video editing in the coming weeks. I need at least:

- crossfades
- the ability to zoom / crop / pan

As far as I know, no Ubuntu software can do this yet. Am I mistaken?
Yes you are. Blender can do it.

You can use any video clip as a texture, put it on a mesh (e.g. a plane), animate the mesh in various ways (2D and 3D) while the video is playing, and export the result as a new video clip. You can do the editing in Blender's sequence editor. You can use Blender's node editor for compositing and transitioning effects.

[http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)

---

### Post by variona on 2007-08-29
You can check out LiVes and Cinelerra with the dyne:bolic live distribution (CD) without the need to install it. See [www.dynebolic.org](www.dynebolic.org)
variona

---

### Post by Amazona aestiva on 2007-08-31
See the first link in my signature!

---

### Post by SpiritIsReality on 2007-08-31
howdy

thanks for the link,
great article

trails

---

### Post by mimsmall on 2007-10-24
> **salsaman said:**
> You could also use [LiVES]("http://www.getdeb.net/app.php?name=LiVES"), of course. Surprising that nobody mentioned it already.

This package didn't install in my Feisty installation.

---

### Post by MarkieB on 2007-10-28
Mencoder is quite good for the additional tasks that kino doesn't do; rotate, adjust brightness, convert .Mov to .avi, etc; I can't seem to get cinelerra to import either of .Mov/.Avi nor to get kino to create .Mov files

for instance to brighten + rotate a video clockwise
```
mencoder -vf rotate=1,eq2=1:1:0.2:1:1:1:1:1 -ovc lavc -oac pcm inputfile.mov -o outputfile.avi
```

---

