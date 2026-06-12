---
title: "Help: FFTW operation doesn't work in imagemagick"
date: 2010-09-26
forum: Multimedia Software
---

### Post by wild_tiger on 2010-09-26
When I type the following command,

[B]convert 2522.jpeg -fft +delete magnitude.jpeg
[/B]
shell gives me a message as below

[B]convert: delegate library support not built-in `2522.jpeg' (FFTW) @ fourier.c/ForwardFourierTransformImage/611.
convert: missing an image filename `magnitude.jpeg' @ convert.c/ConvertImageCommand/2838.[/B]

It seems that imagemagick might miss some libs. Does the version along  with ubuntu 10.04 NOT include the FFTW libs? If so, what should I do?  Any help will be appreciated.

---

### Post by yoyoq on 2011-05-18
same problem here, any suggestions?

---

### Post by hwttdz on 2011-06-09
Grab the source from [https://launchpad.net/imagemagick](https://launchpad.net/imagemagick)
configure, ensure that fft is set to yes in the output of configure.  If not you may need to install fftw.
Add /usr/local/lib to your ld_library_path.  
sudo make install.  
Should be good to go.

---

