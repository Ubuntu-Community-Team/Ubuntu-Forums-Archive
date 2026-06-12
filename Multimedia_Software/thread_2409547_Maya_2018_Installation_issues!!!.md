---
title: "Maya 2018 Installation issues!!!"
date: 2019-01-03
forum: Multimedia Software
---

### Post by calebak98 on 2019-01-03
I am trying to install maya 2018 and the terminal keeps giving me errors when I run ./setup Here are some screenshots...

---

### Post by QIII on 2019-01-03
Hello!

I've thumbnailed your image.

Images like that are sometimes hard to see clearly.  When posting terminal commands and their output, it is best to copy the text and post that between code tags.

To use code tags, either:

1.  Click the # button in the toolbars above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

Cheers!

---

### Post by calebak98 on 2019-01-04
@QIII This is the text in my terminal...I know it is hard to read. I am not seeing any '#' on my end. Basically I am just tryng to run the setup file. "sudo ./setup" and it gives me "error while loading shared libraries: libpng12.so.0: cannot open shared object file: no such file or directory"
shar
```

kozma@caleb-Inspiron:~/maya2018_setup$ ls
''$'\r'                                   libQtNetwork.so.4
 adlmapps14-14.0.23-0.x86_64.rpm          libQtScript.so.4
 adlmflexnetclient-14.0.23-0.x86_64.rpm   libQtSql.so.4
 adlmflexnetserver-14.0.23-0.x86_64.rpm   libQtXml.so.4
 adlmreg                                  licensechooser
 Bifrost2018_64-2018.0-7880.x86_64.rpm    Maya2018_64-2018.0-7880.x86_64.rpm
 BifrostToArnold.rpm                      package.zip
 EULA                                     resources
 libadlmPIT.so                            setup
 libadlmPIT.so.11                         setup.sh
 libadlmutil.so                           setup.xml
 libadlmutil.so.11                        support
 libQt3Support.so.4                       unix_installer.py
 libQtCore.so.4                           unix_installer.sh
 libQtGui.so.4
kozma@caleb-Inspiron:~/maya2018_setup$ sudo ./setup
[sudo] password for kozma: 
./setup: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory
kozma@caleb-Inspiron:~/maya2018_setup$
```

---

### Post by &amp;KyT$0P# on 2019-01-04
Please post the output from running these commands in Terminal -
```
lsb_release -a
dpkg-query -W | grep -i libpng12
apt-cache policy libpng12-0
```

---

### Post by QIII on 2019-01-04
@calebak97 --

Please enclose all terminal commands and their output in code tags.  That preserves formatting and makes your posts easier to read.

To use code tags, either:

1.  Click the # button in the toolbars above the text input box, place your cursor between the code tags that appear and type or paste your text.  Alternately, type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

---

### Post by calebak98 on 2019-01-05
After running ```
 lsb_release-a 
``` it says that no lsb modules are available.
The "apt-cache..." command came back with ```
 libpng12-0:  Installed: (none)
  Candidate: 1.2.54-1ubuntu1
  Version table:
     1.2.54-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

---

### Post by &amp;KyT$0P# on 2019-01-05
Try installing that package -
```
sudo apt-get install libpng12-0
```

Does it work now?

---

### Post by calebak98 on 2019-01-05
Yes it worked but then I tried to run ./setup and it gave me this error
```
 X Error: BadAccess (attempt to access private resource denied) 10  Extension:    130 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x2c0000a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 5 (X_ShmCreatePixmap)
  Resource id:  0x2c00010
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x2c00011
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x2c00011
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x2c00011
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x2c00011
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2c00011
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 2 (X_ShmDetach)
  Resource id:  0x2c00010



```

---

### Post by calebak98 on 2019-01-05
I am not sure why this is so darn hard to install. I switched from ubuntu to windows because windows was running so slow but now I am contemplating going back because everything is giving me errors. The autodesk website said that all i had to do was run ./setup and it would run but its been such a headache

---

