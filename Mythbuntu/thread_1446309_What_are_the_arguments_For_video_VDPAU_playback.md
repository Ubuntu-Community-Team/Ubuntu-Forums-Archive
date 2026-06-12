---
title: "What are the arguments For video VDPAU playback?"
date: 2010-04-03
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2010-04-03
I you media setting for internal video playback what arguments do you us for VDPAU playback?
I think the default is some thing like:
mplayer -fs -zoom -quiet -vo xv %s

I have tried
mplayer -fs -zoom -quiet -vo vdpau %s
but was wondering if there are any more tricks, options, or tweeks.

will -vo vdpau,colorspace=0 correct for proper studio levels?

---

### Post by epi 1:10,000 on 2010-04-24
In Utilities/settup -> setup -> Media Settings -> Videos Settings -> Player Settings 

The correct arguments/options for VDPAU playback of your Mpeg1 or 2 videos are:

mplayer -fs -zoom -quiet -vo vdpau:deint=4:colorspace=0 -vc ffmpeg12vdpau

for my  nvidia 9500 GT

Where deint=4 is similar to temporal 2x deinterlacing  (deint should be reduced to 3 or less on 9400 gt or less powerful graphics cards). Colorspace=0 (jyavenard build) alows for the detection of correct studio color levels on a TV that doesn't have a DVI, Sub-D input, or support computer monitor color levels over HDMI

The -vc or video codec will have to be changed if you want vdpau acceleration of codecs other than Mpeg 1 or 2.
 See man mplayer
 (-vc ffmpeg12vdpau, ffwmv3vdpau, ffvc1vdpau or ffh264vdpau)

If you have a 9600 GT, 220 GT, or better you can do all the bells and wistles such as

mplayer -fs -zoom -quiet -vo vdpau:sharpen=.5:denoise=1:deint=4:chroma-deint:pullup:colorspace=0 -vc ffmpeg12vdpau

[The above section with a smiley face should read as "chroma-deint : pullup" without the spaces. I don't know how to turn off emotocons.]

Which is the similar to Advanced 2x Deintelacing with noise reduction and image sharpening controls

sharpen=<-1 to 1>  example ->   :sharpen=-.25 will soften the image and sharpen=.44 will sharpen the image 

denoise can be a positive number from 0 to 1 and allows for adjustable noise reduction




Taken from man mplayer

vdpau (with -vc ffmpeg12vdpau, ffwmv3vdpau, ffvc1vdpau or ffh264vdpau)
              Video output that uses VDPAU to decode video via hardware.  Also
              supports displaying of software-decoded video.
                 
sharpen=<-1-1>
                      For positive values, apply a sharpening algorithm to the
                      video,  for  negative  values  a blurring algorithm (de&#8208;
                      fault: 0).
                 
denoise=<0-1>
                      Apply a noise reduction algorithm to the video (default:
                      0, no noise reduction).
                 
deint=<0-4>
                      Chooses  the  deinterlacer  (default: 0).  All modes > 0
                      respect -field-dominance.
                         -0    No deinterlacing.
                         -1    Show only first field, similar to -vf field.
                         -2    Bob deinterlacing, similar to -vf tfields=1.
                         -3    Motion  adaptive  temporal  deinterlacing.   May
                              lead  to  A/V  desync  with  slow video hardware
                              and/or high resolution.  This is the default  if
                              "D" is used to enable deinterlacing.
                         -4    Motion   adaptive  temporal  deinterlacing  with
                              edge-guided spatial interpolation.   Needs  fast
                              video hardware.
                 
chroma-deint
                      Makes  temporal  deinterlacers  operate both on luma and
                      chroma (default).  [U]Use nochroma-deint to solely use luma
                      and  speed  up advanced deinterlacing.  [/U][U]Useful with slow
                      video memory.[/U]
                 
pullup
                      Try to apply inverse  telecine,  needs  motion  adaptive
                      temporal deinterlacing.

---

