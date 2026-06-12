---
title: "Shrinking image file size without dropping resolution"
date: 2011-09-02
forum: Multimedia Software
---

### Post by akand074 on 2011-09-02
I made a few images using gimp and exported them as PNG files (has to be this type) and set them to max compression. File size ended up around 500KB. My question is, is there a good way to compress these files even more, or simply another way to cut the file size down as much as possible without dropping the resolution. If so what would be the best way to do this with the least amount of damage to quality?

I figured it could be possible as I see full movies being compressed to as low as 300MB for a 720p video while others are north of 5GB  even though both are using x264 codec and mkv container. So I assume there's some sort of compression (bitrate drop). Not sure if a similar concept can be done to photos.

---

### Post by akand074 on 2011-09-02
I managed to solve this. What I did first was download trimage image compressor from the repositories. This does lossless image compression. Some images dropped as much as 65% in size, others dropped as little as 2% in size without any damage to the quality at all. 

Afterwards I opened up GIMP and went to Image > Mode > Indexed (instead of RGB). Set it to 255 colours and used different dithering settings (none giving the smallest size). Though this did damage the quality of the image, so you can vary settings or not use it at all based on how important the quality is. I managed to get my 500KB PNG down to below 150KB in size. I ended up keeping the 175KB in size one as it had minimal loss but huge drop in size.

---

### Post by shantiq on 2011-09-03
hi akand there is also this format [**tiff**]("http://en.wikipedia.org/wiki/Tagged_Image_File_Format") which allows really big compression and is still lossless

used by many image professionals

it is in gimp

i realize you said has to be png but thought i would add this info

---

