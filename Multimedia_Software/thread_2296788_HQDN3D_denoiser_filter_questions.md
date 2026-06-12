---
title: "HQDN3D denoiser filter questions"
date: 2015-09-28
forum: Multimedia Software
---

### Post by mark bower on 2015-09-28
1) Can the hqdn3d arguments be increased for 1440x1080P vs  720 x480P and the appearance remain about the same?  The default argument values of 4,3,6,4.5 are given by the author, but no comment on whether their optimal values may be a function of file(frame) size.  In other words, are the values of "4,3,6,4.5" possibly related to a particular file size.

2) When using the "vf" filter, what is the correct sequence for the following and why?
 -vf "setpts=1.333*PTS,hqdn3d= "**_ or_**  -vf "hqdn3d=,setpts=1.333*PTS".  In other words, should the frames be duplicated before or after noise reduction, or is there interference depending on the order of application?

3)  What is the meaning/difference of spatial and temporal values for luma and chroma?

4) And finally, what does the last argument, "restart", do?  Should I consider using it?  The default for it is given as "lt+1".  I have not a clue of what this means?

The 1440x1080P frames size comes from digitizing my super 8mm film; nearly all of the runtime display appears noticeably grainy.  Please no answer to any question unless you have a real understanding/expertise of how the denoiser filter works/interacts with respect to the question.

---

### Post by mark bower on 2015-10-07
Well, this is not going well - help is still requested.  

Perhaps a viewer knows how I can get in touch with Loren Merritt who "owns" the HQDN3D filter?

---

### Post by FakeOutdoorsman on 2015-10-09
I was going to write some stuff, but then I read your last sentence and I wouldn't call myself an expert on this filter.

This isn't the best forum for these questions. I recommend asking the ffmpeg-user mailing list or doom9 forum. There are probably some experts in those places.

As for "restart" it appears you are reading the Avisynth wiki or docs on this filter but using ffmpeg? The ffmpeg implementation appears to lack that parameter.

---

### Post by mark bower on 2015-10-10
I found "restart" at the following link, only place I have seen it.  Merritt, author, is the one who calls it out, but again, I find no further discussions on it or its use.

[http://akuvian.org/src/avisynth/hqdn3d/hqdn3d.txt](http://akuvian.org/src/avisynth/hqdn3d/hqdn3d.txt)

o.k., I may take your advice and post at other sites.  In the meantime, the post at the following link seems authoritative, and generally pretty good.  I have posted my questions there.  The author does suggest that higher resolution allows for higher argument settings; I specifically posed that question again.

[https://mattgadient.com/2013/06/29/in-depth-look-at-de-noising-in-handbrake-with-imagevideo-examples/](https://mattgadient.com/2013/06/29/in-depth-look-at-de-noising-in-handbrake-with-imagevideo-examples/)

mark

---

