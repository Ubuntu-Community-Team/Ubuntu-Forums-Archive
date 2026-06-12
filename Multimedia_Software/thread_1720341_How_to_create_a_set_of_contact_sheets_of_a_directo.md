---
title: "How to create a set of contact sheets of a directory of digital photo files?"
date: 2011-04-03
forum: Multimedia Software
---

### Post by rocksockdoc on 2011-04-03
The only thread on creating a contact sheet appears to be years old & locked:
- [**(photography) how to create a single jpg /tif contact sheet?**]("http://ubuntuforums.org/showthread.php?t=90303&highlight=contact+sheet")

So may I ask what's the most common method today of creating a set of contact sheets of a directory of, say, 500 photos (on Ubuntu 10.04 lucid)?

The only thing I really want to specify is the grid (e.g., 4 photos by 6 photos, or something like that).

In that ancient thread, the following were suggested:

[LIST]
[*]imagemagick
[*]gThumb
[/LIST]
For example:
```
montage -label "%f" -frame 5  -pointsize 10  -geometry +4+6 *.jpg index1.jpg  

```
This supposedly creates an 4x6 grid of images with a label under each image (of  pointsize 10).

Here's another example from the net:
 	      - [ImageMagick Thumbnails and Contact Sheets]("http://www.velvetcache.org/2009/03/30/imagemagick-thumbnails-and-contact-sheets")
       
[URL="http://www.velvetcache.org/2009/03/30/imagemagick-thumbnails-and-contact-sheets"]
[/URL] 
What do YOU use to create a decent contact sheet set out of a large directory of photos?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187947&stc=1&d=1301827844[/IMG]

---

### Post by rocksockdoc on 2011-04-03
> **rocksockdoc said:**
> what's the most common method today of creating a set of contact sheets of a directory of, say, 500 photos (on Ubuntu 10.04 lucid)?

Despite not knowing the most common (and easiest) way to make a contact sheet, I was able to make a set of numbered contact sheets using the aforementioned script:

```

[COLOR=#666666]*#!/bin/bash*[/COLOR]
 
[COLOR=#666666]*# Digital camera thumbnail/contact sheet tool.*[/COLOR]
[COLOR=#666666]*# http://www.velvetcache.org/2009/03/30/imagemagick-thumbnails-and-contact-sheets*[/COLOR]
[COLOR=#666666]*# http://github.com/jmhobbs/helper-scripts*[/COLOR]
[COLOR=#666666]*#*[/COLOR]
[COLOR=#666666]*# Copyright (c) 2009-2010 John Hobbs*[/COLOR]
[COLOR=#666666]*#*[/COLOR]
[COLOR=#666666]*# Permission is hereby granted, free of charge, to any person*[/COLOR]
[COLOR=#666666]*# obtaining a copy of this software and associated documentation*[/COLOR]
[COLOR=#666666]*# files (the "Software"), to deal in the Software without*[/COLOR]
[COLOR=#666666]*# restriction, including without limitation the rights to use,*[/COLOR]
[COLOR=#666666]*# copy, modify, merge, publish, distribute, sublicense, and/or sell*[/COLOR]
[COLOR=#666666]*# copies of the Software, and to permit persons to whom the*[/COLOR]
[COLOR=#666666]*# Software is furnished to do so, subject to the following*[/COLOR]
[COLOR=#666666]*# conditions:*[/COLOR]
[COLOR=#666666]*#*[/COLOR]
[COLOR=#666666]*# The above copyright notice and this permission notice shall be*[/COLOR]
[COLOR=#666666]*# included in all copies or substantial portions of the Software.*[/COLOR]
[COLOR=#666666]*#*[/COLOR]
[COLOR=#666666]*# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,*[/COLOR]
[COLOR=#666666]*# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES*[/COLOR]
[COLOR=#666666]*# OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND*[/COLOR]
[COLOR=#666666]*# NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT*[/COLOR]
[COLOR=#666666]*# HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,*[/COLOR]
[COLOR=#666666]*# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING*[/COLOR]
[COLOR=#666666]*# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR*[/COLOR]
[COLOR=#666666]*# OTHER DEALINGS IN THE SOFTWARE.*[/COLOR]
 
[COLOR=#666666]*# CHANGELOG*[/COLOR]
[COLOR=#666666]*# 2010-06-14 - Fixed contact sheet problem, thanks to Glenn Turnbull. (John Hobbs)*[/COLOR]
[COLOR=#666666]*# 2009-03-30 - Created script. (John Hobbs)*[/COLOR]
 
[COLOR=#666666]*### SETTINGS ###*[/COLOR]
 
[COLOR=#666666]*# Scaling Methods:*[/COLOR]
[COLOR=#666666]*# resize (Best/Slow)*[/COLOR]
[COLOR=#666666]*# scale (Middle/Middle)*[/COLOR]
[COLOR=#666666]*# sample (Worst/Fast)*[/COLOR]
[COLOR=#007800]METHOD[/COLOR]=[COLOR=#FF0000]"sample"[/COLOR]
 
[COLOR=#666666]*# Thumbnail Size*[/COLOR]
[COLOR=#007800]THUMBSIZE[/COLOR]=[COLOR=#FF0000]"600x600"[/COLOR]
[COLOR=#666666]*# Thumbnail Directory*[/COLOR]
[COLOR=#007800]THUMBDIR[/COLOR]=[COLOR=#FF0000]"thumb"[/COLOR]
[COLOR=#666666]*# Thumbnail Quality*[/COLOR]
[COLOR=#007800]THUMBQUALITY[/COLOR]=[COLOR=#FF0000]"80"[/COLOR]
 
[COLOR=#666666]*# Contact Item Size*[/COLOR]
[COLOR=#007800]CONTACTSIZE[/COLOR]=[COLOR=#FF0000]"200x200"[/COLOR]
[COLOR=#666666]*# Contact Sheet Max Width*[/COLOR]
[COLOR=#007800]CONTACTWIDTH[/COLOR]=[COLOR=#FF0000]"3"[/COLOR]
[COLOR=#666666]*# Contact Sheet Max Height*[/COLOR]
[COLOR=#007800]CONTACTHEIGHT[/COLOR]=[COLOR=#FF0000]"4"[/COLOR]
[COLOR=#666666]*# Horizontal Spacing*[/COLOR]
[COLOR=#007800]CONTACTSPACINGH[/COLOR]=[COLOR=#FF0000]"3"[/COLOR]
[COLOR=#666666]*# Vertical Spacing*[/COLOR]
[COLOR=#007800]CONTACTSPACINGV[/COLOR]=[COLOR=#FF0000]"3"[/COLOR]
[COLOR=#666666]*# Contact Sheet Directory*[/COLOR]
[COLOR=#007800]CONTACTDIR[/COLOR]=[COLOR=#FF0000]"contact"[/COLOR]
[COLOR=#666666]*# Contact Sheet Quality*[/COLOR]
[COLOR=#007800]CONTACTQUALITY[/COLOR]=[COLOR=#FF0000]"100"[/COLOR]
 
[COLOR=#666666]*################*[/COLOR]
 
 
[COLOR=#007800]CONTACTCOUNT[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$CONTACTWIDTH[/COLOR] [COLOR=#000000]*****[/COLOR] [COLOR=#007800]$CONTACTHEIGHT[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
[COLOR=#007800]PIX[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#C20CB9]**ls**[/COLOR] [COLOR=#660033]-l[/COLOR] [COLOR=#000000]*****[/COLOR].jpg [COLOR=#000000]**|**[/COLOR] [COLOR=#C20CB9]**wc**[/COLOR] -l[COLOR=#7A0874]**)**[/COLOR]
 
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"Processing [COLOR=#007800]$PIX[/COLOR] Images"[/COLOR]
[COLOR=#7A0874]**echo**[/COLOR]
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"Creating Thumbnails"[/COLOR]
 
[COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#660033]-p[/COLOR] [COLOR=#007800]$THUMBDIR[/COLOR]
[COLOR=#007800]CTR[/COLOR]=[COLOR=#000000]0[/COLOR]
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-n[/COLOR] [COLOR=#FF0000]"0%"[/COLOR]
[COLOR=#000000]**for**[/COLOR] i [COLOR=#000000]**in**[/COLOR] [COLOR=#000000]*****[/COLOR].jpg; [COLOR=#000000]**do**[/COLOR]
    [COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-ne[/COLOR] [COLOR=#FF0000]"[COLOR=#000099]**\r**[/COLOR]"[/COLOR]
    [COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-n[/COLOR] [COLOR=#FF0000]"[COLOR=#007800]$((100 * $CTR / $PIX)[/COLOR])%"[/COLOR]
    convert [COLOR=#660033]-strip[/COLOR] [COLOR=#660033]-quality[/COLOR] [COLOR=#800000]${THUMBQUALITY}[/COLOR] -[COLOR=#800000]${METHOD}[/COLOR] [COLOR=#800000]${THUMBSIZE}[/COLOR] [COLOR=#FF0000]"[COLOR=#007800]$i[/COLOR]"[/COLOR] [COLOR=#FF0000]"[COLOR=#007800]${THUMBDIR}[/COLOR]/[COLOR=#007800]${i}[/COLOR]"[/COLOR]
    [COLOR=#007800]CTR[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$CTR[/COLOR] + [COLOR=#000000]1[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
[COLOR=#000000]**done**[/COLOR]
 
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-ne[/COLOR] [COLOR=#FF0000]"[COLOR=#000099]**\r**[/COLOR]"[/COLOR]
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"100%"[/COLOR]
 
[COLOR=#7A0874]**echo**[/COLOR]
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"Creating Contact Sheets"[/COLOR]
 
[COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#660033]-p[/COLOR] [COLOR=#007800]$CONTACTDIR[/COLOR]
[COLOR=#007800]CTR[/COLOR]=[COLOR=#000000]0[/COLOR]
[COLOR=#007800]PAGES[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$PIX[/COLOR] [COLOR=#000000]**/**[/COLOR] [COLOR=#007800]$CONTACTCOUNT[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
[COLOR=#000000]**if**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] $[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$PIX[/COLOR] [COLOR=#000000]**%**[/COLOR] [COLOR=#007800]$CONTACTCOUNT[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR] [COLOR=#660033]-ne[/COLOR] [COLOR=#000000]0[/COLOR] [COLOR=#7A0874]**]**[/COLOR]; [COLOR=#000000]**then**[/COLOR]
    [COLOR=#007800]PAGES[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$PAGES[/COLOR] + [COLOR=#000000]1[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
 
[COLOR=#007800]PAGE[/COLOR]=[COLOR=#000000]1[/COLOR]
[COLOR=#007800]LIST[/COLOR]=[COLOR=#FF0000]""[/COLOR]
[COLOR=#000000]**for**[/COLOR] i [COLOR=#000000]**in**[/COLOR] [COLOR=#800000]${THUMBDIR}[/COLOR][COLOR=#000000]**/***[/COLOR].jpg; [COLOR=#000000]**do**[/COLOR]
    [COLOR=#000000]**if**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] $[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$CTR[/COLOR] [COLOR=#000000]**%**[/COLOR] [COLOR=#007800]$CONTACTCOUNT[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR] [COLOR=#660033]-eq[/COLOR] [COLOR=#000000]0[/COLOR] [COLOR=#7A0874]**]**[/COLOR] [COLOR=#000000]**&&**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] [COLOR=#007800]$CTR[/COLOR] [COLOR=#660033]-ne[/COLOR] [COLOR=#000000]0[/COLOR] [COLOR=#7A0874]**]**[/COLOR]; [COLOR=#000000]**then**[/COLOR]
        [COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"[COLOR=#007800]$PAGE[/COLOR] of [COLOR=#007800]$PAGES[/COLOR]"[/COLOR]
        montage [COLOR=#660033]-label[/COLOR] [COLOR=#000000]**%**[/COLOR]f [COLOR=#660033]-quality[/COLOR] [COLOR=#007800]$CONTACTQUALITY[/COLOR] [COLOR=#660033]-frame[/COLOR] [COLOR=#000000]5[/COLOR] [COLOR=#660033]-tile[/COLOR] [COLOR=#800000]${CONTACTWIDTH}[/COLOR]x[COLOR=#800000]${CONTACTHEIGHT}[/COLOR] [COLOR=#660033]-geometry[/COLOR] [COLOR=#800000]${CONTACTSIZE}[/COLOR]+[COLOR=#800000]${CONTACTSPACINGH}[/COLOR]+[COLOR=#800000]${CONTACTSPACINGV}[/COLOR] [COLOR=#007800]$LIST[/COLOR] jpg:- [COLOR=#000000]**>**[/COLOR] [COLOR=#800000]${CONTACTDIR}[/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#800000]${PAGE}[/COLOR].jpg
        [COLOR=#007800]LIST[/COLOR]=[COLOR=#FF0000]""[/COLOR]
        [COLOR=#007800]PAGE[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$PAGE[/COLOR] + [COLOR=#000000]1[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
    [COLOR=#000000]**fi**[/COLOR]
    [COLOR=#007800]LIST[/COLOR]=[COLOR=#FF0000]"[COLOR=#007800]$LIST[/COLOR] [COLOR=#007800]$i[/COLOR]"[/COLOR]
    [COLOR=#007800]CTR[/COLOR]=$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#007800]$CTR[/COLOR] + [COLOR=#000000]1[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
[COLOR=#000000]**done**[/COLOR]
 
[COLOR=#000000]**if**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] [COLOR=#FF0000]""[/COLOR] [COLOR=#000000]**!**[/COLOR]= [COLOR=#FF0000]"[COLOR=#007800]$LIST[/COLOR]"[/COLOR] [COLOR=#7A0874]**]**[/COLOR]; [COLOR=#000000]**then**[/COLOR]
    [COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"[COLOR=#007800]$PAGE[/COLOR] of [COLOR=#007800]$PAGES[/COLOR]"[/COLOR]
    montage [COLOR=#660033]-label[/COLOR] [COLOR=#000000]**%**[/COLOR]f [COLOR=#660033]-quality[/COLOR] [COLOR=#007800]$CONTACTQUALITY[/COLOR] [COLOR=#660033]-frame[/COLOR] [COLOR=#000000]5[/COLOR] [COLOR=#660033]-tile[/COLOR] [COLOR=#800000]${CONTACTWIDTH}[/COLOR]x[COLOR=#800000]${CONTACTHEIGHT}[/COLOR] [COLOR=#660033]-geometry[/COLOR] [COLOR=#800000]${CONTACTSIZE}[/COLOR]+[COLOR=#800000]${CONTACTSPACINGH}[/COLOR]+[COLOR=#800000]${CONTACTSPACINGV}[/COLOR] [COLOR=#007800]$LIST[/COLOR] jpg:- [COLOR=#000000]**>**[/COLOR] [COLOR=#800000]${CONTACTDIR}[/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#800000]${PAGE}[/COLOR].jpg
[COLOR=#000000]**fi**[/COLOR]

```

---

