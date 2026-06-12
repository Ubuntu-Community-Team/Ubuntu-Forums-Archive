---
title: "Panorama image as in Irfanview..."
date: 2011-10-08
forum: Multimedia Software
---

### Post by shantiq on 2011-10-08
a really nice function in irfanview is the Panoramic image


see attached


I have so far failed to see a linux equivalent
maybe some of you know of one
or maybe there is an existing script about


Irfanview does not normally install under Wine
But the latest non-install  version does
i have attached it here if you are interested (plugins do not work tho as it is not installed)

---

### Post by WasMeHere on 2011-10-08
The following programs can do panoramic pictures by fitting the edges of different views:
*hugin* and
*fotoxx*

But looking at your picture (4 portraits) I am not sure that is the same kind of panorama that you want. Anyway, it is certainly possible to make a big canvas and put pictures onto it with
*gimp* and
*imagemagick*

Have fun
Olle

---

### Post by ajgreeny on 2011-10-08
That is not a panorama, it's just 4 images stitched together, which any graphics program can do.

Irfanview _*will*_ install and run in wine without a problem but needs the missing dll (mfc32.dll I think) from winetools first;  I did use it for a while, but then realised that I didn't really need it.

---

### Post by shantiq on 2011-10-08
> **ajgreeny said:**
> That is not a panorama, it's just 4 images stitched together, which any graphics program can do.

Irfanview _*will*_ install and run in wine without a problem but needs the missing dll (mfc32.dll I think) from winetools first;  I did use it for a while, but then realised that I didn't really need it.


with respect Greeny programs can do that manually but not the way irfanview does it

As regards the install could you explain about mfc32.dll    what one should do   tried mfc42 and mfc30 into system 32 but   i am not sure      thanx    shan

---

### Post by WasMeHere on 2011-10-08
Try imagemagick! The tutorials on the internet are very good.

You can certainly have fun testing several of the tools and features :-)
Olle

---

### Post by shantiq on 2011-10-08
> **Olle Wiklund said:**
> Try imagemagick! The tutorials on the internet are very good.

You can certainly have fun testing several of the tools and features :-)
Olle


looks cool will av a look:KS

Programs run from a terminal:

> animate, compare, composite, conjure, convert, display, identify, import, mogrify, montage, stream

---

### Post by ajgreeny on 2011-10-08
> **shantiq said:**
> with respect Greeny programs can do that manually but not the way irfanview does it

As regards the install could you explain about mfc32.dll    what one should do   tried mfc42 and mfc30 into system 32 but   i am not sure      thanx    shan
I'd love to, but it's too long since I did it and it is now all forgotten in detail.  I could easily have got the .ddl name wrong as well.  I don't even remember irfanview being capable of doing that type of panorama, maybe because it is not something I've ever wanted.

---

### Post by shantiq on 2011-10-08
see next==

---

### Post by shantiq on 2011-10-08
Well Greeny that is something that i want and value and insofar as i know only irfanview does it this well as a GUI and this quickly; also i have always loved and respected Irfanview always was free and nifty

I think of it as a bona fide Linux application [ which happens to be on Windows:KS]



If anyone else  knows how to install full version of Irfanview under Wine please tell us:KS



In the meantime started to fiddle with [**ImageMagick**]("http://www.imagemagick.org/Usage/")   very nice application too Thank you Olle for bringing it to my attention


and this  does the same as the Irfanview function

```
montage 1.gif 2.gif 3.gif 4.gif \ -mode Concatenate  -tile x1  montage_cat.jpg
```

Works with most extensions too




Excellent.  Problem solved.


=======================================

=

---

### Post by shantiq on 2011-10-08
ok GOT IT  much info i got from [**here **]("http://ubuntuforums.org/showpost.php?p=7599178&postcount=4")

First install winetricks from synaptic



then enter   ```
winetricks
```

 it opens with the Select the default wineprefix click Ok
 tick Install a windows ddl  and install mfc42 comctl32


Then to the installer [**iview430_setup.exe**]("http://dw.com.com/redir?edId=3&siteId=4&oId=3000-2192_4-10021962&ontId=2192_4&spi=dec4d9a1c351590ac56b0d0a4f05dd16&lop=link&tag=tdw_dltext&ltype=dl_dlnow&pid=11911096&mfgId=59333&merId=59333&pguid=TpCePgoOYIwAADIuXA8AAAJu&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-2192_4-10021962.html%3Fspi%3Ddec4d9a1c351590ac56b0d0a4f05dd16%26part%3Ddl-IrfanView")

Install Plugins either through the exe;  or the zip to place in manually


All works perfect on Natty    and glad about it as it is a great light program with fantastic functions and filters  
POp Art and Harry's Filters especially



[CENTER][[IMG]http://img713.imageshack.us/img713/1008/ajumanasenyana41.th.png[/IMG]](http://img713.imageshack.us/img713/1008/ajumanasenyana41.png)

"New" irfanview icons for fun[/CENTER]

---

