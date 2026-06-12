---
title: "Colour Problem with Web Images"
date: 2012-07-24
forum: Multimedia Software
---

### Post by gareththered on 2012-07-24
Hi,

I'm pulling my hair out trying to figure out a way to get consistent colours on my website.  The problem is as follows:-

I'm photographing artificial flowers for a website of which many are varying shades of purple.  The problem is that without Color Management disabled in Gimp or digiKam/showFoto, the purple shows up as a horrible blue. If I enable Colour Management, the purple shows up as it should.

Now, if I upload these photos to my online store, they show up as blue.  I figured out that this is because the online shop uses libgd to resize the images and this strips the ICC color profile from the images (a known issue), meaning web browsers show the images like Gimp/digiKam/showFoto do with Colour Management disabled - blue.

I've tried to convert the images with ImageMagick using various commands suggested on the Internet, but they all show up either blue or very pale.

My question is:-

Does anyone know of a way to convert an image so that a sRGB ICC color profile is added (and the colours are modified - blue becomes purple in my case) and then the ICC profile is stripped.  This would allow my website to display un-Colour Managed images in the correct colour.  In other words, I would like to add the compensation created by ICC profiles to the image and save this modified image with no ICC profile.  This (in my mind) would mean that the colours would be correct before and after libgd had resized the image.

I hope all that make sense!

---

