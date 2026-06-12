---
title: "Xine Installation guide"
date: 2010-01-09
forum: Multimedia Software
---

### Post by AndrewSimoes on 2010-01-09
I have managed to compile it on 32-bit Ubuntu Lucid Lynx.
By no means are the instructions comprehensive , they are what worked for me.

1. Follow this tutorial and install ffmpeg : [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

2. Download the latest xine-lib tarballs from the site : [http://www.xine-project.org/releases](http://www.xine-project.org/releases)

3. Extract and rename the folder xine-lib.

4. Execute the command : 
  sudo apt-get build-dep xine-lib.

5. Now to compile:
     
 
    cd xine-lib

   ./autogen.sh

   ./configure --with-external-ffmpeg

    make

   sudo checkinstall --pkgname=xine-lib --pkgversion "1.1.x.x" --backup=no --default
Subsitute the right numbers in the --pkgversion option above

---

