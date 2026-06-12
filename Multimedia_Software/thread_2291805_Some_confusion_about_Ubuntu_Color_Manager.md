---
title: "Some confusion about Ubuntu Color Manager"
date: 2015-08-22
forum: Multimedia Software
---

### Post by KOSKERS on 2015-08-22
hi.
why the same pictures has different color.

NEF is adjusted in Aftershot pro 2 and export to jpeg with sRGB profile

They looks so different.[ATTACH=CONFIG]264000[/ATTACH]

May u tell me why?

---

### Post by Keith_Helms on 2015-08-25
While you can use software like Argyll to color calibrate the image from Linux for a specific monitor, there is no "Color Manager" that is going to change the colors from one picture format to another.,

I would imagine the problem you describe is due to the Aftershot Pro 2 software not correctly handling the color profile for raw photos from the Nikon camera you're using.  You would need to research Aftershot Pro 2, color profiles, and the Nikon DSLR (I assume it's a DSLR) you're using.

---

### Post by KOSKERS on 2015-08-30
Thx a lot.

---

### Post by tgalati4 on 2015-08-30
You can spend a lot of time playing with color gamut.  Understand that there is a difference between Adobe sRGB and standard [sRGB]("https://www.google.com/search?q=srgb+gamut&espv=2&biw=1280&bih=738&tbm=isch&imgil=ZIo4oWZ9CWIyNM%253A%253BZC14Sz3FCA0orM%253Bhttp%25253A%25252F%25252Fdot-color.com%25252Fcategory%25252Fcolor-gamut-standards%25252F&source=iu&pf=m&fir=ZIo4oWZ9CWIyNM%253A%252CZC14Sz3FCA0orM%252C_&usg=__NROI_zQ7cS98TlrsboIw9lLaPM8%3D&ved=0CDgQyjdqFQoTCO7NjML_0McCFYSRDQodgeUMzw&ei=WhDjVe64B4SjNoHLs_gM#imgrc=ZIo4oWZ9CWIyNM%3A&usg=__NROI_zQ7cS98TlrsboIw9lLaPM8%3D").

Was the original image a JPEG or RAW image?  Any post processing will upscale the image's color space to allow the manipulation in a higher-precision manner--similar to upconverting an mp3 music track to WAV to allow filters to be applied.  When compressing this post-processed file back to its original form, changes will result--sometimes [unexpected]("https://www.youtube.com/watch?v=icruGcSsPp0").

---

