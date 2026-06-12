---
title: "Compiling CinePaint 1.0-4"
date: 2020-07-27
forum: Multimedia Software
---

### Post by claus on 2020-07-27
Hi,

right now I am trying to compile CinePaint 1.0-4 from source, but I am getting various error messages:

[https://claus-cyrny.net/wordpress/wp-content/uploads/2020/07/cinepaint_01.png]("https://claus-cyrny.net/wordpress/wp-content/uploads/2020/07/cinepaint_01.png")

My question: Does anyone know where I can get all the libraries, as well as Oyranos & littleCMS? There used to be a web site where one could download all the .deb files, but I can't find it anymore. :(

TIA,


Claus

---

### Post by monkeybrain20122 on 2020-07-28
littleCMS is liblcms2-dev in the repo (you need the -dev files for compiling stuffs) oyranos is [here]("https://github.com/oyranos-cms/oyranos") but you have to compile from source. FLTK is libfltk1.1-dev or libfltk1.3-dev, there are two versions in Ubuntu 20.04's repo.

I doubt that it would work though since cinepaint 10.4 came out at 2013 so the libs may not be compatible (e.g it might need liblcms instead of liblcms2) and your compiler version (gcc) is probably too new as well. [These guys]("https://www.linuxmintusers.de/index.php?topic=31932.0") tried in 2016 and failed.I would find a modern replacement.

---

### Post by claus on 2020-07-31
Hi,

thanks for your feedback. In the meantime I found a .deb file and managed to install it successfully (see [here]("https://claus-cyrny.net/wordpress/index.php/2020/07/29/cinepaint-1-0-4-unter-ubuntu-installieren/")). Alas, color management isn't working (-> CinePaint crashes). According to project leader, Robin Rowe, a new version of CinePaint is about to be released.

---

