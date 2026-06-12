---
title: "no output from glxgears"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-07-27
This might sound stupid, but when I run glxgears I get no output to the console, just the little box opening with the gears running, and not very smoothly. Is there some switch to use with glxgears from the command line?

Also, what kind of results should I expect from an nVidia 6200 PCI-E 64MB (256MB with turbocache) on an AMD64 3400+ with 1 GB of RAM? I installed the ubuntu i386 version without thinking, and don't know if the AMD64 version will radically improve things, so don't want to go to the trouble of downloading and wiping my installation if it's not a major benefit.

I forgot to bring a copy of my xorg.conf with me (no inet at home), but can do it next time.

---

### Post by patbuntu on 2006-07-27
Try:
```
glxgears -printfps
```
That should do it.

-Pat

---

### Post by cblanquer on 2006-07-27
Hi,

That did not work with the parameter "-printfps" but rather "-info" instead.

> glxgears -info

---

### Post by fabertawe on 2006-07-28
> **patbuntu said:**
> Try:
```
glxgears -printfps
```
That should do it.

-Pat

Thanks very much for that, been scratching my head for ages!

Paul

---

### Post by pickarooney on 2006-07-29
it worked with -printfps for me, but the results were crud - 600 fps only. I checked glxinfo and for the server entry nvidia is installed. Hard to explain, but I haven't the output file with me once again. Is there an easy guide for installing 2D and 3D acceleration on nvidia cards somewhere?

---

### Post by tseliot on 2006-07-29
> **pickarooney said:**
> it worked with -printfps for me, but the results were crud - 600 fps only. I checked glxinfo and for the server entry nvidia is installed. Hard to explain, but I haven't the output file with me once again. Is there an easy guide for installing 2D and 3D acceleration on nvidia cards somewhere?

here you go:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by pickarooney on 2006-07-30
Sweet, I'll have my own connection in a couple of eeks and will sort this out then. Thanks a million. :)

---

