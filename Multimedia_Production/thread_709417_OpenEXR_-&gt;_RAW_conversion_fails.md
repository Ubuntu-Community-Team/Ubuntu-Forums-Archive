---
title: "OpenEXR -&gt; RAW conversion fails"
date: 2008-02-27
forum: Multimedia Production
---

### Post by ijustam on 2008-02-27
So, I'm trying to do some terrain work in Blender and EXR under Gutsy:

I have ImageMagick installed from the repos, along with libopenexr2c2a and openexr from the repos.  The 'convert' command exists, so I tried:

```
me@chapek:~$ convert mymap.exr -depth 16 -size 1025x1025 -endian LSB gray:mymap.raw
convert: no decode delegate for this image format `mymap.exr'.
convert: missing an image filename `gray:mymap.raw'.
```

After some Googling I found to see if EXR is writable by running 'identify -list format':
```
me@chapek:~$ identify -list format | grep exr
me@chapek:~$ identify -list format | grep EXR
me@chapek:~$ 
```

What gives with that?  Is there a package I'm missing, or do I need to compile something with EXR support?  Blender seems to save it fine, but the conversion fails from the EXR to RAW.

Any information would be greatly appreciated, thank you!

---

### Post by xxv on 2008-04-03
As best as I can tell, there are NO open source utilities to convert digital cameras' RAW images to EXR. You'd probably need to take some source from ufraw and hack it into imagemagick's HDRI system. 

Also, for HDRI (EXR and friends) support in Imagemagick, it needs to be version 6.4 or above and it needs to be explicitly compiled in.

---

