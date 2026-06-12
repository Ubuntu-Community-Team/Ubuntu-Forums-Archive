---
title: "Unable to convert a large PNG to JPEG using ImageMagick"
date: 2023-06-01
forum: Multimedia Software
---

### Post by Paddy Landau on 2023-06-01
I can easily convert PNG images to JPEG using ImageMagick's [FONT=courier new]convert[/FONT].

For example:
```
[COLOR=#0000ff]$[/COLOR] convert Sample-1688×3000.png -quality 95 Sample-1688×3000.jpeg
```
However, I have a file that won't convert because it's too large:
```
[COLOR=#0000ff]$[/COLOR] convert Sample-27008×48000.png -quality 95 Sample-27008×48000.jpeg
convert-im6.q16: no images defined `Sample-27008×48000.jpeg' @ error/convert.c/ConvertImageCommand/3229.
```
[This answer]("https://stackoverflow.com/a/69903175/2678429") on Stack Overflow suggests changing the ImageMagick policy to allow for larger images.

I've tried this, and I am stuck; I cannot get past the limits.

As the file name implies, the size of the PNG file is 27,008×48,000 pixels, with a resulting size of 1,296,384,000 pixels. The physical disk size is 231 MiB.

I've increased the policy for several items as follows:
```
<policy domain="resource" name="memory" value="8GiB"/>
<policy domain="resource" name="map" value="8GiB"/>
<policy domain="resource" name="width" value="49KP"/>
<policy domain="resource" name="height" value="49KP"/>
<policy domain="resource" name="area" value="6GP"/>
```
Now the error message has changed; [FONT=courier new]convert[/FONT] fails *immediately* with this error message, so clearly it's something needed in the policy file:
```
$ convert Sample-27008×48000.png -quality 99 Sample-27008×48000.jpg
convert-im6.q16: cache resources exhausted `Sample-27008×48000.png' @ error/cache.c/OpenPixelCache/4095.
convert-im6.q16: no images defined `Sample-27008×48000.jpg' @ error/convert.c/ConvertImageCommand/3229.
```
What can you suggest, please?

Thank you

---

### Post by SeijiSensei on 2023-06-01
Can you open it in the [GIMP]("https://gimp.org/")?

```
sudo apt install gimp
```

If so, you can use File > Export and pick JPEG.

---

### Post by Paddy Landau on 2023-06-01
I tried GIMP, but it crashed on out-of-memory (most likely, I'd need to increase my swap space significantly).

That's why I thought that convert would make better sense, as it's a base CLI. I believe that GIMP uses ImageMagick, but I might be wrong.

---

### Post by Dennis N on 2023-06-01
Try the little utility named "Converter". See if it can handle your file.

---

### Post by Paddy Landau on 2023-06-02
> **Dennis N said:**
> Try the little utility named "Converter". See if it can handle your file.
Thank you. I found Converter on flatpak and installed it. (According to [OMG Ubuntu!]("https://www.omgubuntu.co.uk/2023/01/gtk-image-converter-app-for-linux"), Converter uses ImageMagick.)

Bizarrely, it had no permission to access any folder whatsoever, so used Flatseal to grant it permission to access my home.

Unfortunately, two problems. While it worked with smaller PNG files, it has no option to change the level of compression; I need that.

Worse, when trying to convert my large file, it ran out of memory just reading the file, before I even got a chance to ask it to convert.

Alas, it didn't work :(

---

### Post by Holger_Gehrke on 2023-06-02
You might try a larger value for the 'disk' resource, it's set to 1 GiB in the policy.xml that Ubuntu has per default. Commenting that out gives unlimited cache on disk. You can find details on ImageMagicks use of memory at [https://imagemagick.org/script/architecture.php#cache](https://imagemagick.org/script/architecture.php#cache)

Holger

---

### Post by Paddy Landau on 2023-06-02
> **Holger_Gehrke said:**
> You might try a larger value for the 'disk' resource …
This did the trick, thank you so much!

---

### Post by Dennis N on 2023-06-02
> While it worked with smaller PNG files, it has no option to change the level of compression
Wouldn't compression level be the quality setting? You can set that. See secreenshot &#8595;

Also, you can resize at the same time to a specified percentage of the original size, or exact pixels.

---

### Post by Paddy Landau on 2023-06-02
> **Dennis N said:**
> Wouldn't compression level be the quality setting?
Yes, that is what I mean.

But&#8230;
> **Dennis N said:**
> You can set that. See secreenshot &#8595;
Ah! I didn't see those options! They are (on my machine) hidden below the bottom of the window. I had tried the menu at the top, and was confused as to why there were no options!

I've enlarged the window, and now I see them.

Thank you :)

EDIT: Unfortunately, Converter also ran out of memory. Presumably, it's using the default settings for ImageMagick.

---

