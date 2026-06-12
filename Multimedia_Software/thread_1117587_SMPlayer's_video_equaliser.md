---
title: "SMPlayer's video equaliser"
date: 2009-04-06
forum: Multimedia Software
---

### Post by Robbyx on 2009-04-06
I tried to use the equaliser to adjust  a video but it did nothing. No changes took place. Is this to be expected currently?

---

### Post by rvm4000 on 2009-04-06
The video equalizer works with some video output drivers but not all (for instance it doesn't work with x11). In that case you need to enable the software equalizer in preferences -> general -> video.

---

### Post by Robbyx on 2009-04-07
Thank you. It now works.

I have noticed that deblocking is not on by default. Could you please point me to a list showing the syntax of extra options and video filters that I can put into the advanced options for MPlayer in the preferences. I clicked on help but it does not show the syntax of the command line options. 

Also is there an advanced mplayer option that you have found always improves the output to a nvidia 7600 card so should be on by default?

---

### Post by rvm4000 on 2009-04-07
All options and filters of mplayer:
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

---

### Post by Robbyx on 2009-04-08
> **rvm4000 said:**
> All options and filters of mplayer:
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

I found the syntax in that file very hard to follow. Would you mind advising me what to put into  smplayer's mplayer video options to maximise deblocking without noticeable loss of frame rate?

---

### Post by rvm4000 on 2009-04-08
The deblocking can be done (for example) with *pp=vb/hb* (copy it to the video filters field in preferences -> advanced)

---

### Post by Robbyx on 2009-04-08
> **rvm4000 said:**
> The deblocking can be done (for example) with *pp=vb/hb* (copy it to the video filters field in preferences -> advanced)

Thank you. I have put it into the filter field as suggested. 

It so happens that the sample you gave me does not appear on a search at the url you quoted above. I thought that I would find it and perhaps better understand the syntax, but my search came up with no match!

---

### Post by rvm4000 on 2009-04-08
It's there, although it can be hard to see:
> 
pp[=filter1[:option1[:option2...]]/[&#8722;]filter2...] (also see &#8722;pphelp)
	
Enables the specified chain of postprocessing subfilters. Subfilters must be separated by &#8217;/&#8217; and can be disabled by prepending a &#8217;&#8722;&#8217;. Each subfilter and some options have a short and a long name that can be used interchangeably, i.e. dr/dering are the same. All subfilters share common options to determine their scope:
	
a/autoq
	
Automatically switch the subfilter off if the CPU is too slow.
	
c/chrom
	
Do chrominance filtering, too (default).
	
y/nochrom
	
Do luminance filtering only (no chrominance).
	
n/noluma
	
Do chrominance filtering only (no luminance).
	
NOTE: &#8722;pphelp shows a list of available subfilters.

Available subfilters are
	
hb/hdeblock[:difference[:flatness]]
	
horizontal deblocking filter
	
<difference>: Difference factor where higher values mean more deblocking (default: 32).
<flatness>: Flatness threshold where lower values mean more deblocking (default: 39).
	
vb/vdeblock[:difference[:flatness]]
	
vertical deblocking filter
	
<difference>: Difference factor where higher values mean more deblocking (default: 32).
<flatness>: Flatness threshold where lower values mean more deblocking (default: 39).
	
ha/hadeblock[:difference[:flatness]]
	
accurate horizontal deblocking filter
	
<difference>: Difference factor where higher values mean more deblocking (default: 32).
<flatness>: Flatness threshold where lower values mean more deblocking (default: 39).
	
va/vadeblock[:difference[:flatness]]
	
accurate vertical deblocking filter
	
<difference>: Difference factor where higher values mean more deblocking (default: 32).
<flatness>: Flatness threshold where lower values mean more deblocking (default: 39).
	
The horizontal and vertical deblocking filters share the difference and flatness values so you cannot set different horizontal and vertical thresholds.
	
h1/x1hdeblock
	
experimental horizontal deblocking filter
	
v1/x1vdeblock
	
experimental vertical deblocking filter
	
dr/dering
	
deringing filter
	
tn/tmpnoise[:threshold1[:threshold2[:threshold3]]]
	
temporal noise reducer
	
<threshold1>: larger -> stronger filtering
<threshold2>: larger -> stronger filtering
<threshold3>: larger -> stronger filtering
	
al/autolevels[:f/fullyrange]
	
automatic brightness / contrast correction
	
f/fullyrange: Stretch luminance to (0&#8722;255).
	
lb/linblenddeint
	
Linear blend deinterlacing filter that deinterlaces the given block by filtering all lines with a (1 2 1) filter.
	
li/linipoldeint
	
Linear interpolating deinterlacing filter that deinterlaces the given block by linearly interpolating every second line.
	
ci/cubicipoldeint
	
Cubic interpolating deinterlacing filter deinterlaces the given block by cubically interpolating every second line.
	
md/mediandeint
	
Median deinterlacing filter that deinterlaces the given block by applying a median filter to every second line.
	
fd/ffmpegdeint
	
FFmpeg deinterlacing filter that deinterlaces the given block by filtering every second line with a (&#8722;1 4 2 4 &#8722;1) filter.
	
l5/lowpass5
	
Vertically applied FIR lowpass deinterlacing filter that deinterlaces the given block by filtering all lines with a (&#8722;1 2 6 2 &#8722;1) filter.
	
fq/forceQuant[:quantizer]
	
Overrides the quantizer table from the input with the constant quantizer you specify.
	
<quantizer>: quantizer to use
	
de/default
	
default pp filter combination (hb:a,vb:a,dr:a)
	
fa/fast
	
fast pp filter combination (h1:a,v1:a,dr:a)
	
ac
	
high quality pp filter combination (ha:a:128:7,va:a,dr:a)
	
EXAMPLE:
	
&#8722;vf pp=hb/vb/dr/al
	
horizontal and vertical deblocking, deringing and automatic brightness/contrast
	
&#8722;vf pp=de/&#8722;al
	
default filters without brightness/contrast correction
	
&#8722;vf pp=default/tmpnoise:1:2:3
	
Enable default filters & temporal denoiser.
	
&#8722;vf pp=hb:y/vb:a
	
Horizontal deblocking on luminance only, and switch vertical deblocking on or off automatically depending on available CPU time.


---

### Post by Robbyx on 2009-04-08
Thank you I am beginning to understand the syntax. I thought I would try out the following:

horizontal and vertical deblocking, deringing and automatic brightness/contrast

&#8722;vf pp=de/&#8722;al

I am a bit surprised to see the - sign in front because according to your quoted passage that disables the sub filter!


Trying to view a video with the &#8722;vf pp=de/&#8722;al has just  produced an exit code 1

with a log message;

Option vf-add: &#8722;vf pp doesn't exist.
Error parsing option on the command line: -vf-add
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

Any ideas why this does not work?

---

### Post by rvm4000 on 2009-04-08
In the video filters field in smplayer preferences you should not enter *-vf* (that's done automatically by smplayer) just the argument: *pp=de/-al*

Also be carefully with the dash (if you copy and paste the options). The HTML version of the manpage uses a different simbol (&#8722;) which looks like a dash (-) but it's not, and mplayer can't understand it.

---

