---
title: "Software for converting film negative to positive"
date: 2018-05-21
forum: Multimedia Software
---

### Post by satimis on 2018-05-21
Hi all,

I'm looking for a reliable tool converting film negative to positive, photo.  It shouldn't be too complicate.  I'm not a professional graphic editor and only use it to convert the scanned film negative images to positive.    On google search I found;
Phatch = PHoto & bATCH
[http://photobatch.wikidot.com/](http://photobatch.wikidot.com/)

Any folk on the forum has tried this tool.  Please shed me some light.  Other recommendation would also be appreciated.

Thanks in advance

Remark: I'm aware that GIMP can do the job.

Regards
satimis

---

### Post by kazakore on 2018-05-21
Opps. Thought I was editing this post and posted twice.....

---

### Post by kazakore on 2018-05-21
For bulk processing I would definitely go with Phatch. I have used it for resizing files for upload and similar automated batch tasks like that. It's not too complicated, just be careful to make sure you set you save location as different to where it is reading the file from until you know you have everything set correctly (or backup before starting) as it has no preview.

Also it seems they have removed it from 18.04 for some reason! :(
EDIT: Plus either I'm being an idiot or the dev has changed/removed the actual hompage and there's no Free Download link like it says to find and click on. Anybody know a decent third party ppa which has this compatible with 18.04??
EDIT2: Last stable release was 8 years ago so a working link to the .deb would probably be just as useful as a ppa as it seems no further updates are likely.....

[https://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=phatch&searchon=names](https://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=phatch&searchon=names)

---

### Post by Holger_Gehrke on 2018-05-21
It's a bit like using a hydrogen bomb to kill a single cockroach, but Image Magick should do the trick. It's a highly capable suite of command line tools for image viewing, manipulation and conversion. It's in the repositories (sudo apt install imagemagick).

```

display -negate filename # shows the inverted image
convert filename -negate newfilename # inverts the image and writes it to a new file
mogrify -negate filename # inverts the image and overwrites the old image with the new one

```

with a bit of shell scripting batch processing is easy:
```

for i in negatives/* ; do convert "$i" -negate positives/"$(basename "$i")"; done

```

Holger

PS.: There's a very nice script by Fred Weinhaus using ImageMagick at [www.fmwconcepts.com/imagemagick/neg2pos/](www.fmwconcepts.com/imagemagick/neg2pos/) which automagically crops, inverts and rebalances scanned negatives.

---

### Post by satimis on 2018-05-22
> **kazakore said:**
> For bulk processing I would definitely go with Phatch. I have used it for resizing files for upload and similar automated batch tasks like that. It's not too complicated, just be careful to make sure you set you save location as different to where it is reading the file from until you know you have everything set correctly (or backup before starting) as it has no preview.

Also it seems they have removed it from 18.04 for some reason! :(
EDIT: Plus either I'm being an idiot or the dev has changed/removed the actual hompage and there's no Free Download link like it says to find and click on. Anybody know a decent third party ppa which has this compatible with 18.04??
EDIT2: Last stable release was 8 years ago so a working link to the .deb would probably be just as useful as a ppa as it seems no further updates are likely.....

[https://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=phatch&searchon=names](https://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=phatch&searchon=names)
Hi,

Thanks for your advice.

I'm looking for a bulk process tool to process hundreds of negatives.  It should be not too complicate to use.

I found following way:-

1)
Scan film negatives on GIMP running;```

File -> Create -> xscanimage -> Device Dialogue ...

Scan source [Transparency Adapter]
Bit depth [bit] [8]
[check] Quality calibration
[389x1913:2.1 MB]
-> Scan

```

the film negative images are on .xcf format

2)
Follow below video to process and edit the images
Negative film processing using darktable
[https://www.youtube.com/watch?v=m55G-Va7ZoU](https://www.youtube.com/watch?v=m55G-Va7ZoU)

Remark: .xcf works on Darktable

To save time I'll import and process several film negative strips simultaneously.

Would Phatch be easier to use?  Thanks

Regards
satimis

---

### Post by satimis on 2018-05-22
> **Holger_Gehrke said:**
> It's a bit like using a hydrogen bomb to kill a single cockroach, but Image Magick should do the trick. It's a highly capable suite of command line tools for image viewing, manipulation and conversion. It's in the repositories (sudo apt install imagemagick).

```

display -negate filename # shows the inverted image
convert filename -negate newfilename # inverts the image and writes it to a new file
mogrify -negate filename # inverts the image and overwrites the old image with the new one

```

with a bit of shell scripting batch processing is easy:
```

for i in negatives/* ; do convert "$i" -negate positives/"$(basename "$i")"; done

```

Holger

PS.: There's a very nice script by Fred Weinhaus using ImageMagick at [www.fmwconcepts.com/imagemagick/neg2pos/](www.fmwconcepts.com/imagemagick/neg2pos/) which automagically crops, inverts and rebalances scanned negatives.
Hi,

Thanks for your advice and link.

I run "convert", the tool of ImageMagick, quite often.  It is a convenient tool.

I prefer command operation which is simple and straightforwards.  The only drawback is NOT what-you-see-is what-you-get.

Regards
satimis

---

### Post by kazakore on 2018-05-22
> **satimis said:**
> 
Would Phatch be easier to use?  Thanks

Regards
satimis

The more I read about Phatch at the moment the more I think it's a completely dead project so maybe not worth  bothering with....

> 
I found following way:-

1)
Scan film negatives on GIMP running;```

File -> Create -> xscanimage -> Device Dialogue ...

Scan source [Transparency Adapter]
Bit depth [bit] [8]
[check] Quality calibration
[389x1913:2.1 MB]
-> Scan

```

the film negative images are on .xcf format



Why not do everything in GIMP then and use the batch processing which it provides?

[https://www.maketecheasier.com/batch-process-files-in-gimp/](https://www.maketecheasier.com/batch-process-files-in-gimp/)

---

### Post by satimis on 2018-05-22
> **kazakore said:**
> The more I read about Phatch at the moment the more I think it's a completely dead project so maybe not worth  bothering with....

Why not do everything in GIMP then and use the batch processing which it provides?

[https://www.maketecheasier.com/batch-process-files-in-gimp/](https://www.maketecheasier.com/batch-process-files-in-gimp/)
Hi,

Thanks for your advice and link.

Also I'm considering doing the complete job in GIMP.  I have been away from GIMP for sometime.

I have been searching on Internet a while and found following interesting Youtube video;

Batch Image Manipulation with Gimp and BIMP plugin (ubuntu)
[https://www.youtube.com/watch?v=Ai8-yLPfR8E](https://www.youtube.com/watch?v=Ai8-yLPfR8E)

GIMP Tutorial 2015: How to Batch Edit Photos and Add Watermark
[https://www.youtube.com/watch?v=EJpPYLxWDts](https://www.youtube.com/watch?v=EJpPYLxWDts)

How to batch image manipulation in Gimp (plugin installation)
[https://www.youtube.com/watch?v=pReA0DpALrk](https://www.youtube.com/watch?v=pReA0DpALrk)

How to do Batch Processing in GIMP
[https://www.youtube.com/watch?v=ZBnNbqtIr8M](https://www.youtube.com/watch?v=ZBnNbqtIr8M)

Using Batch Process in GIMP
[https://www.youtube.com/watch?v=sqdquqNNSu4](https://www.youtube.com/watch?v=sqdquqNNSu4)

Regards
satimis

---

