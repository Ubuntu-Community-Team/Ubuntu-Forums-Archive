---
title: "Opening WebGL powered site causing force logout on chrome / chromium"
date: 2011-01-11
forum: Multimedia Software
---

### Post by thejdev on 2011-01-11
I read somewhere that --enable-webgl allowed software rendering for Intel graphics users so I gave it a shot. 

I opened an instance of google chrome using the options 
--enable-plugins --enable-webgl and tried to open a WebGL powered site ( in this case, [http://bodybrowser.googlelabs.com](http://bodybrowser.googlelabs.com) ). The page loaded partially (the UI alone) and then I got logged out automatically. Can someone help me fix this ?

I tried another WebGL powered page: [http://gratrix.net/polyhedra/webgl/poly.xhtml](http://gratrix.net/polyhedra/webgl/poly.xhtml) . 

This time I didn't crash but my CPU-usage went haywire and I got a blank page. I ran the browser from the command-line; here's the result:

<code>

$ uname -a
Linux jubuntu-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

$ /opt/google/chrome/google-chrome --enable-plugins --enable-webgl %U
[2637:2637:1256361653:ERROR:app/gfx/gl/gl_context_linux.cc(539)] glXChooseFBConfig failed.

</code>

I have a Dell Inspiron 1525, with a 2 GHz Core2Duo T6400 (2 MB Cache); 3 GB DDR2 RAM and Intel GM965/GL960 integrated graphics. I run Ubuntu 10.04 .

---

### Post by thejdev on 2011-01-11
Also, can someone tell me how to get WebGL to work in Firefox 4 ? I tried to open bodybrowser.googlelabs.com in Firefox 4 but it says I don't have WebGL.

---

### Post by Amaranth on 2011-02-04
What you're seeing is a crash in your driver which is the reason Firefox and Chrome have disabled WebGL for your driver.

---

