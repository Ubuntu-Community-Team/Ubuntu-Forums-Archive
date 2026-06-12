---
title: "Compiling Gyachi in Natty 11.04"
date: 2011-05-10
forum: Multimedia Software
---

### Post by ydjluv on 2011-05-10
[LEFT]
First you need to download the source code from
[http://prdownloads.sourceforge.net/gyachi/gyachi-1.1.71.tar.gz?download](http://prdownloads.sourceforge.net/gyachi/gyachi-1.1.71.tar.gz?download)

Next you need to make sure you have all the dependencies in order to complete the build. All of the dependencies can be acquired with apt as usual.
 [U][B]
Dependencies[/B][/U]:

[B]libtool
automake
libgraphicsmagick1-dev
libjasper-dev
libgtkhtml2-dev
libgpgme11-dev
libasound2-dev
libxcomposite-dev
libgtk2.0-dev
libglib2.0-dev
libmcrypt11-dev[/B]
**libv4l-dev**

Once you have made sure all the dependencies are installed you need to type the following command so the build can find it:

> sudo cp /usr/include/libv4l1-videodev.h /usr/include/linux/videodev.hNow change to the directory where you extracted the gyachi source (typically ~/gyachi-1.2.10)
Type the following commands:

> ./autogen.sh
./configure --enable-maintainer-mode --disable-rpathIf you do not want to install to the default directory /usr/local/gyachi then add prefix=/your/directory to the configure options. Also, if you encounter an error regarding gpgme.h then add --disable-plugin_gpgme to the configure options unless you want to download and compile gpgme yourself with LFS support. I will not go into this procedure in this guide. After the source has been configured to your liking then issue the following commands:

> make
sudo make installNow you can run the program from terminal or from your menu[B].

If you encounter the error:

([/B]gyachi: error while loading shared libraries: libgyachi.so: cannot open  shared object file: No such file or directory**)**
This error means libgyachi.so does not exist in /usr/lib and is easily fixed with the following commands:

> cd /usr/lib
sudo ln -s /usr/local/gyachi/libgyachi.so libgyachi.soHopefully if all went well then Gyachi should be installed in  /usr/local/gyachi unless you specified a prefix option to configure**.** Now you can run the Gyachi program from the shell or your menu[B].

[/B]If anyone has any further questions then feel free to leave a comment and I will reply as soon as possible.[/LEFT]

---

### Post by Yellow Pasque on 2011-05-10
You should use --prefix=/usr as an option for configure to avoid that error.

---

### Post by ydjluv on 2011-05-10
yea that would work too :)

---

