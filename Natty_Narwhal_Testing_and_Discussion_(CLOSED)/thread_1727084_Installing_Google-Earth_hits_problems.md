---
title: "Installing Google-Earth hits problems"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-04-12
I am trying again to install Google-Earth following the instructions here> [http://www.liberiangeek.net/2011/03/install-google-earth-ubuntu-11-04-natty-narwhal/]("http://www.liberiangeek.net/2011/03/install-google-earth-ubuntu-11-04-natty-narwhal/")

After "sudo make-googleearth-package --force" I get lots of warnings like this example:
> Checking shlib deps: libauth.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libreporting.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'

However, it creates a goggle.......deb file alright. Trying to install this the Software-Center refuses. Using the terminal it complains only about 3 missing packages:
>   Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package msttcorefonts is not installed.


Am still hunting for the msttcorefonts! Will this turn out all right?

Michael

---

### Post by beew on 2011-04-12
This seems unnecessarily complicated. 

-Install lsb-core and gdebi from Synaptic.
-Download the .deb file for the latest stable version  from google earth
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Right click the .deb file and choose open with gdebi and click install and that's it (gdebi is needed only for installing .deb files, it is a lot faster than using the Software Center,--which is a bloated piece of junk IMO)

I have installed ge since Natty alpha 3 and it is working great.

P.S. Installing with googleearth-package (to make the .deb file) works in Maverick, I have done that too, but some libraries or dependencies may be missing in Natty.

---

### Post by coffeecat on 2011-04-12
> **Yumi said:**
> Am still hunting for the msttcorefonts! Will this turn out all right?


You need the package ttf-mscorefonts-installer.

---

