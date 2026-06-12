---
title: "Creating parnoramic pictures using the shell with no gui"
date: 2010-03-23
forum: Multimedia Software
---

### Post by xela74 on 2010-03-23
Hi everyone,

I know that it's possible to create panoramic photos very easily with hugin. But I would like to create a script for nautilus where I select my picture and then create a panoramic without any questions.

I guess it's possible but I can't find on google, each time I find something about hugin.

Is it possible to call hugin from the command line and hide the interface during the process ?

May I use the libpano lib directly ?

Thanks for your help.
Alex

---

### Post by kdford on 2010-03-23
You can install the hugin-tools package (from synaptic) and that will give you command line programs that can be used to script this process.  Since you won't have the GUI to locate control points for stitching, you'll be relying on the software to attempt to auto locate these and that will work *some* of the time.  There is a [post]("http://groups.google.com/group/hugin-ptx/browse_thread/thread/95d6134fa8eb7b16?pli=1") that describes the high level process.

Hope this helps

---

### Post by xela74 on 2010-03-23
Thanks for your asnwer.

That's waht I did, I installed the hugin tools and I wrote my script using this tutorial [http://wiki.panotools.org/Panorama_scripting_in_a_nutshell]("http://wiki.panotools.org/Panorama_scripting_in_a_nutshell").

Here what I do in the script (someone could need it).

1) align the photos together
```
autopano-complete -s 1600 -o test.pto 1.jpg 2.jpg 3.jpg
```

2) optimize the key points
```
autooptimiser -a -l -s -o test.pto test.pto
```

3) render the photos to be scaled and transformed
```
nona -m TIFF_m -o test test.pto
```

4) Blend the photo and then create the panoramic photo 
```
enblend -o pano.jpg test0000.tif test0001.tif test0002.tif 
```

thanks for your answer.
alex

---

### Post by mocha on 2010-07-10
Thanks very much for this method!  I find it to actually make better panoramics than using the Hugin GUI with it's defaults.

One question though, I don't fully understand the use of the -s 1600 in autopano-complete.  The docs say "If any of the image dimensions exceed this side, the image is resized so the longer side of the images will be this size."  To me that means it will resize the input images to have the longest size be 1600 pixels.

I'm using input photos with 3648x2736 resolution, and it appears the only thing the -s 1600 does is to make the processing time take a lot longer. If I completely remove the option, the output files are exactly the same output resolution and size.  So I'm not sure what it's doing.

---

