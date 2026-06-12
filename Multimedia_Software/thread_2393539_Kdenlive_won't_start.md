---
title: "Kdenlive won't start"
date: 2018-06-04
forum: Multimedia Software
---

### Post by dk1936 on 2018-06-04
Hello everyone, I am a new user of ubuntu.

I am trying to launch Kdenlive but this is what I get:

kdenlive: error while loading shared libraries: libQt5Svg.so.5: cannot open shared object file: No such file or directory

Any ideas? Thank you.

---

### Post by kazakore on 2018-06-05
Version of Ubuntu you are using, how you installed kdenlive and full output when trying to start it from the terminal would always help when starting a request like this.

With the limited info I would suggest trying

```
sudo apt-get install --fix-missing
```

And then trying to start it from the commandline. If it still fails post the full output.

Although quite possibly this may fix it too:

```
 sudo apt-get install libqt5svg5
```

---

### Post by dk1936 on 2018-06-05
I am using Ubuntu 18.02 and I have tried to install it with both using terminal and ubuntu software but I have faced the same problem.

I followed your advices but nothing changed.

---

### Post by kazakore on 2018-06-05
> And then trying to start it from the commandline. **If it still fails post the full output.**

??

---

### Post by dk1936 on 2018-06-05
The output stills the same.
> kdenlive: error while loading shared libraries: libQt5Svg.so.5: cannot open shared object file: No such file or directory

---

### Post by kazakore on 2018-06-05
You really only get one single line of output in the terminal when trying to launch it from there? This is what I get on a successull load (nearly all of it is related to the GUI elements, but so would your error be as that's a Qt library by the looks of it.)

```
$ kdenlive
qt5ct: using qt5ct plugin
QApplication: invalid style override passed, ignoring it.
Icon theme "adwaita" not found.
Icon theme "adwaita" not found.
no more csLADSPA plugins
qt5ct: D-Bus global menu: no
qt5ct: palette support is disabled
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/libexec/kf5/klauncher'
kdeinit5: Launched KLauncher, pid = 13138, result = 0
qt5ct: using qt5ct plugin
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit5: opened connection to :0.0
kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so' from launcher.
kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file.so'
QXcbConnection: XCB error: 8 (BadMatch), sequence: 617, resource id: 71303185, major code: 154 (Unknown), minor code: 11
```

You could try adding the dev package for that library but I can't see why it should need it.....

```
sudo apt-get install  libqt5svg5-dev 
```

Also:

Has it ever started? Myself and another user on here have both run into issues with getting the config file to a state where Kdenlive has become unusable (in different ways.) You could try deleting or moving/renaming ~/.config/kdenliverc and see if it then boots. If the Qt5 SVG library is for skin components this could we help by setting it to the default skin.

---

