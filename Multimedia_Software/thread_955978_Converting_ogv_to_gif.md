---
title: "Converting ogv to gif?"
date: 2008-10-22
forum: Multimedia Software
---

### Post by rocky5051 on 2008-10-22
Does anyone know of any software that can convert an ogv video file to a gif animation? If there isn't any program that can do that directly, does anyone know of a method?

Thanks. :)

---

### Post by kretyn on 2011-05-04
And I also searched for it, but I couldn't find anything.

You can indirectly convert *.ogv to *.avi and then to *.gif.
First step you can do with FFMPEG ([here's]("http://my.opera.com/ubuntunerd1/blog/2009/06/17/how-to-convert-ogv-files-to-other-formats-with-winff") how to do it with GUI cover WinFF ).
Second step you can do with GIMP plugin [Ubuntu forum]("http://ubuntuforums.org/showthread.php?t=220486").

---

### Post by FakeOutdoorsman on 2011-05-04
> **kretyn said:**
> And I also searched for it, but I couldn't find anything.

You can indirectly convert *.ogv to *.avi and then to *.gif.
First step you can do with FFMPEG ([here's]("http://my.opera.com/ubuntunerd1/blog/2009/06/17/how-to-convert-ogv-files-to-other-formats-with-winff") how to do it with GUI cover WinFF ).

You can use FFmpeg directly with any input. Example:
```
ffmpeg -i input -loop_output 0 -pix_fmt rgb24 -r 10 -s 320x240 output.gif
```
You can change the number of times the output will loop with *-loop_output* (0 means loop forever), and you can change output frame rate with *-r*. A lower frame rate will be jerky, but will create a smaller output file size.

---

