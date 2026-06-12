---
title: "ImageMagick 7.0.10-23: 'magick' not working properly"
date: 2020-07-23
forum: Multimedia Software
---

### Post by claus on 2020-07-23
Hi,

after downloading the latest version of ImageMagick, I can't invoke 'magick' properly. ```
$ magick -version
``` doesn't work. Instead, I have to invoke magick via ```
$ sudo ./magick -version
```. Did anyone else experience the same problem, and is there a solution? I installed 'magick' under ```
$HOME/Software/ImageMagick
```.

Thanks,

Claus

P. S.: When I type ```
$ magick -version
```, I am getting

```
Command 'magick' not found, did you mean:

  command 'magic' from deb magic (8.2.157+ds.1-1)

Try: sudo apt install <deb name>
```

And the permissions for 'magick':

[https://res.cloudinary.com/dxaodmaf4/image/upload/v1595493972/magick_permission_g0aj5i.png]("https://res.cloudinary.com/dxaodmaf4/image/upload/v1595493972/magick_permission_g0aj5i.png")

---

### Post by &amp;KyT$0P# on 2020-07-23
Does
```
./magick -version
```
work (without sudo)?

Did you add the directory containing the actual [FONT=Courier New]magick[/FONT] binary to your [FONT=Courier New]PATH[/FONT] ?

---

### Post by claus on 2020-07-23
> **halogen2 said:**
> Does
```
./magick -version
```
work (without sudo)?

Did you add the directory containing the actual [FONT=Courier New]magick[/FONT] binary to your [FONT=Courier New]PATH[/FONT] ?

Yes, [FONT=Courier New]'./magick -version'[/FONT] works. And yes, I added the directory to my [FONT=Courier New]PATH[/FONT].

Claus

---

### Post by &amp;KyT$0P# on 2020-07-23
> **claus said:**
>  I added the directory to my [FONT=Courier New]PATH[/FONT].

By what method?  Could you please share all the details of how you did it?

If you edited [FONT=Courier New]~/.bashrc[/FONT] or [FONT=Courier New]~/.profile[/FONT], did you log out and back in?

Just to confirm, is it listed if you run -
```
echo "$PATH"
```

---

### Post by claus on 2020-07-23
To add the [FONT=Courier New]PATH[/FONT], I used [FONT=Courier New]$ export MAGICK_HOME="$HOME/Software/ImageMagick"[/FONT], and no, this directory is not in my [FONT=Courier New]PATH[/FONT]. :(
[FONT=Courier New]echo "$PATH"[/FONT] gives the output [FONT=Courier New]"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"[/FONT]. I followed the [recommendations]("https://imagemagick.org/script/download.php#unix") on the IM download page.

Claus

---

### Post by &amp;KyT$0P# on 2020-07-23
Assuming you put the [FONT=Courier New]magick[/FONT] binary at [FONT=Courier New]$HOME/Software/ImageMagick/magick[/FONT] , you'd need to do
```
export PATH="$HOME/Software/ImageMagick:$PATH"
```

---

### Post by claus on 2020-07-23
Thanks, now [FONT=Courier New]'magick -version'[/FONT] works! :)

Claus

P. S.: Alas, this only worked once. Now, when I type [FONT=Courier New]'magick -version'[/FONT], I am getting

[FONT=Courier New]Command 'magick' not found, did you mean:

  command 'magic' from deb magic (8.2.157+ds.1-1)

Try: sudo apt install <deb name>
[/FONT]

again. :( I performed a reboot, but this didn't help, either. I tried [FONT=Courier New]export PATH="$HOME/Software/ImageMagick:$PATH"[/FONT] again in a new shell, and immediately after that it worked, but when I closed the shell and opened a new one, the problem was still there.

---

### Post by tea for one on 2020-07-24
Using Ubuntu 20.04 with Gnome version 3.36.3

Does this command work?

```
display -version
```

Result

```
removed@removed:~$ display -version
Version: ImageMagick 6.9.10-23 Q16 x86_64 20190101 https://imagemagick.org
Copyright: © 1999-2019 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC Modules OpenMP 
Delegates (built-in): bzlib djvu fftw fontconfig freetype jbig jng jpeg lcms lqr ltdl lzma openexr pangocairo png tiff webp wmf x xml zlib
```

Edit: I've just noticed that you have a different version of ImageMagick - my comment may not apply

---

### Post by &amp;KyT$0P# on 2020-07-24
> **claus said:**
> I tried [FONT=Courier New]export PATH="$HOME/Software/ImageMagick:$PATH"[/FONT] again in a new shell, and immediately after that it worked, but when I closed the shell and opened a new one, the problem was still there.

If you want this to persist, you need to add it to [FONT=Courier New]~/.profile[/FONT] in the same way as the existing additions to [FONT=Courier New]PATH[/FONT] there are done -
```
# set PATH so it includes user's custom ImageMagick bin if it exists
if [ -d "$HOME/Software/ImageMagick" ] ; then
    PATH="$HOME/Software/ImageMagick:$PATH"
fi
```

Then log out and log back in to ensure everything picks up the change.

---

