---
title: "Blue colour cast removal?"
date: 2015-04-04
forum: Multimedia Software
---

### Post by Keith_Beef on 2015-04-04
Hello, all.

I went on a skiing trip and stupidly left my camera phone set to "indoor"  or to "tungsten", or something similar, so all my photos of the trip have a strong blue colour cast.

I've been trying to remove it with Image Magick, and especially with [Fred's ImageMagick Autocolor script]("http://www.fmwconcepts.com/imagemagick/autocolor/"), but with not much success.

Since my colour vision is not that great anyway (red-green colour blindness), I wonder if anybody has faced a similar problem and has a ready set of parameters or a script to do the job?

Here is a sample straight from the phone.

[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_original_zpssaphyocm.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_original_zpssaphyocm.jpg.html)

Now when processed with Fred's script [SIZE=1](before anybody points this out, I know I renamed the output files "sample_autolor*n*.jpg")[/SIZE].

autocolor -m recolor -c separate sample_original.jpg sample_autolor1.jpg
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_autolor1_zpsfjnb9nsh.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_autolor1_zpsfjnb9nsh.jpg.html)

autocolor -m gamma -c separate sample_original.jpg sample_autolor2.jpg
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_autolor2_zpsatsfjxso.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_autolor2_zpsatsfjxso.jpg.html)

autocolor -m none -c separate sample_original.jpg sample_autolor3.jpg
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_autolor3_zpstobp07eq.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_autolor3_zpstobp07eq.jpg.html)

autocolor -m recolor -c together sample_original.jpg sample_autolor4.jpg
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_autolor4_zpsklc9y2gf.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_autolor4_zpsklc9y2gf.jpg.html)

autocolor -m gamma -c together sample_original.jpg sample_autolor5.jpg
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_autolor5_zpslp51jni9.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_autolor5_zpslp51jni9.jpg.html)

Of all those, number 4 with arguments "-m recolor -c together" looks the closest, but is too dark and grainy.

---

### Post by tgalati4 on 2015-04-04
Well, you do have snow in the image, so you can use that as the "white point" and adjust the color levels based on that, but that requires using GIMP and interactively picking the white point and adjusting levels based on that.  Unfortunately, when you mess up the blue channel, you run out of adjustment to get the correct color rendition.  Green or red errors are easier to adjust, but blue is difficult--as you have discovered.

You may have better luck using "desaturate" and turn the photos into black and white.  There are a few techniques to do this, do a web search to find one that works for you.  Or use "posterize" or some other filters and make some crazy images--that's about all you can do at this point.

---

### Post by mcduck on 2015-04-04
In this case GIMP's automatic color balance tool will work just fine.

If you want to use Imagemagick, you could try this: [http://www.fmwconcepts.com/imagemagick/autowhite/index.php]("http://www.fmwconcepts.com/imagemagick/autowhite/index.php")

I'm sure could try to determine the (more or less) exact color correction from tungsten to overcast outside, but since the overcast color temperature isn't exact anyway, you might as well go for automatic as it's not going to be fully accurate anyway. Converting between two fully known color temperatures would of course be a different case.

edit: Here's what the single-click auto color balance in GIMP would give:
[ATTACH=CONFIG]261093[/ATTACH]

---

### Post by Keith_Beef on 2015-04-05
Thanks to both tgalati4 and mcduck.

My version of Gimp has Colours -> Auto -> White Balance, that gave good results.

I also tried the autowhite script suggested by mcduck. This gave a somewhat paler image than Gimp, but it's still much better than the original.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_fred-autowhite_zpsf8izmtvd.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_fred-autowhite_zpsf8izmtvd.jpg.html)

Below are the histograms.

First from the original with the blue cast.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_original_histo_zpsw8m5vpgq.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_original_histo_zpsw8m5vpgq.jpg.html)

Next from the auto white-balanced image made in Gimp.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_gimp_colours-auto-whitebalance_histo_zpsw4vzirga.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_gimp_colours-auto-whitebalance_histo_zpsw4vzirga.jpg.html)

Finally, the histogram from the image corrected using Fred's script.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/sample_fred-autowhite_histo_zpsykmy6wft.jpg[/IMG]](http://s71.photobucket.com/user/Keith_Beef/media/Ubuntu/sample_fred-autowhite_histo_zpsykmy6wft.jpg.html)

Now that's quite a surprise&#8230;

---

### Post by tgalati4 on 2015-04-05
As you can see, the blue channel is all the way to the right and clipped.  When that happens, you lose blue information (any blue value that is over 255 is set to 255).  When you try to correct it, you shift it back to the left, but the blue information is lost because it was stored as overblown in the file.

---

