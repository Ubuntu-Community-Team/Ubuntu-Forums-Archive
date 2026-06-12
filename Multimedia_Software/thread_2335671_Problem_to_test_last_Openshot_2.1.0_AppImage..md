---
title: "Problem to test last Openshot 2.1.0 AppImage."
date: 2016-08-31
forum: Multimedia Software
---

### Post by Portaro on 2016-08-31
Hello for all.
At this time I have problems to test the last version of Openshot that I download from there&#8594;
[http://www.openshot.org/download/](http://www.openshot.org/download/)

I choose the AppImage to test this new release but I receive a error message when I try to launch it on terminal&#8594;

[1205][joao:/home/joao]$ cd /home/joao/1template
[1206][joao:/home/joao/1template]$ OpenShot-v2.1.0.AppImage
OpenShot-v2.1.0.AppImage: comando não encontrado
[1207][joao:/home/joao/1template]$ 

Command not found is the message.

My experience with AppImages is poorly so I unknow if I stay well in the sintax command to launch an AppImage or how to debug  this message with AppImages.

My system is based on 14.04 Lubuntu.

Thanks a lot.

---

### Post by howefield on 2016-08-31
Using a terminal, navigate to the folder containing the appimage and type..

```
chmod a+x OpenShot-v2.1.0.AppImage.AppImage
```

and then..

```
./OpenShot-v2.1.0.AppImage
```

---

### Post by Portaro on 2016-08-31
Thanks for help.

The problem still present but with the command I receive other different message

[1210][joao:/home/joao/1template]$ ./OpenShot-v2.1.0.AppImage
bash: ./OpenShot-v2.1.0.AppImage: cannot execute binary file: Erro de formato de executável




[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]

---

### Post by howefield on 2016-08-31
OK, I downloaded it and tried albeit in Ubuntu 16.04, and also got an error but different to yours.

```
hugh@xenial-laptop:~/Downloads$ ./OpenShot-v2.1.0.AppImage 
/tmp/.mount_Dar23k/usr/bin/openshot-qt.wrapper
Loaded modules from current directory: /tmp/.mount_Dar23k/usr/bin
      launch:INFO ------------------------------------------------
      launch:INFO    OpenShot (version 2.1.0)
      launch:INFO ------------------------------------------------
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqeglfs.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqeglfs.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "eglfs"
        ]
    },
    "className": "QEglFSIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqeglfs.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqeglfs.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqlinuxfb.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqlinuxfb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "linuxfb"
        ]
    },
    "className": "QLinuxFbIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqlinuxfb.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqlinuxfb.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimal.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimal.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "minimal"
        ]
    },
    "className": "QMinimalIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimal.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimal.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimalegl.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimalegl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "minimalegl"
        ]
    },
    "className": "QMinimalEglIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimalegl.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqminimalegl.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqoffscreen.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqoffscreen.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "offscreen"
        ]
    },
    "className": "QOffscreenIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqoffscreen.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqoffscreen.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "xcb"
        ]
    },
    "className": "QXcbIntegrationPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/platforms" ... 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqeglfs.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqeglfs.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "eglfs"
        ]
    },
    "className": "QEglFSIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("eglfs") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqkms.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqkms.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "kms"
        ]
    },
    "className": "QKmsIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("kms") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqlinuxfb.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqlinuxfb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "linuxfb"
        ]
    },
    "className": "QLinuxFbIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("linuxfb") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqminimal.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqminimal.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "minimal"
        ]
    },
    "className": "QMinimalIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("minimal") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqminimalegl.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqminimalegl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "minimalegl"
        ]
    },
    "className": "QMinimalEglIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("minimalegl") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqoffscreen.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqoffscreen.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "offscreen"
        ]
    },
    "className": "QOffscreenIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("offscreen") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/platforms/libqxcb.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/platforms/libqxcb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.2",
    "MetaData": {
        "Keys": [
            "xcb"
        ]
    },
    "className": "QXcbIntegrationPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("xcb") 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/platforms" ... 
loaded library "/tmp/.mount_Dar23k/usr/bin/platforms/libqxcb.so" 
loaded library "Xcursor" 
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/platformthemes" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platformthemes/libappmenu-qt5.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platformthemes/libappmenu-qt5.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformThemeFactoryInterface.5.1",
    "MetaData": {
        "Keys": [
            "appmenu-qt5"
        ]
    },
    "className": "AppMenuPlatformThemePlugin",
    "debug": true,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platformthemes/libappmenu-qt5.so:
  Plugin uses incompatible Qt library (5.5.1) [debug]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platformthemes/libappmenu-qt5.so' uses incompatible Qt library. (5.5.1) [debug]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/platformthemes" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/platformthemes" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QPlatformInputContextFactoryInterface.5.1",
    "MetaData": {
        "Keys": [
            "compose"
        ]
    },
    "className": "QComposePlatformInputContextPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libibusplatforminputcontextplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libibusplatforminputcontextplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QPlatformInputContextFactoryInterface.5.1",
    "MetaData": {
        "Keys": [
            "ibus"
        ]
    },
    "className": "QIbusPlatformInputContextPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libibusplatforminputcontextplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libibusplatforminputcontextplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/platforminputcontexts" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/platforminputcontexts" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevkeyboardplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevkeyboardplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "EvdevKeyboard"
        ]
    },
    "className": "QEvdevKeyboardPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevkeyboardplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevkeyboardplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevmouseplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevmouseplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "EvdevMouse"
        ]
    },
    "className": "QEvdevMousePlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevmouseplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevmouseplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtabletplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtabletplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "EvdevTablet"
        ]
    },
    "className": "QEvdevTabletPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtabletplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtabletplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtouchplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtouchplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "EvdevTouch"
        ]
    },
    "className": "QEvdevTouchScreenPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtouchplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqevdevtouchplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqlibinputplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqlibinputplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "libinput"
        ]
    },
    "className": "QLibInputPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqlibinputplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqlibinputplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqtuiotouchplugin.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqtuiotouchplugin.so, metadata=
{
    "IID": "org.qt-project.Qt.QGenericPluginFactoryInterface",
    "MetaData": {
        "Keys": [
            "TuioTouch"
        ]
    },
    "className": "QTuioTouchPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqtuiotouchplugin.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/generic/libqtuiotouchplugin.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/generic" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/generic" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/styles" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/styles" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/styles" ... 
         app:INFO openshot-qt version: 2.1.0
         app:INFO libopenshot version: 0.1.1
         app:INFO platform: Linux-4.4.0-34-generic-x86_64-with-Ubuntu-16.04-xenial
         app:INFO processor: x86_64
         app:INFO machine: x86_64
         app:INFO python version: 3.4.3
         app:INFO qt5 version: 5.2.1
         app:INFO pyqt5 version: 5.2.1
    language:INFO Qt Detected Languages: ['en-GB', 'en']
    language:INFO LANG Environment Variable: en_GB.UTF-8
    language:INFO LOCALE Environment Variable: en_GB
    language:INFO Attempting to load qt_en_GB.UTF-8 in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load qtbase_en_GB.UTF-8 in '/usr/share/qt5/translations'
    language:INFO Attempting to load qtbase_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en_GB.UTF-8 in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qt_en in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qtbase_en_GB.UTF-8 in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qtbase_en in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load en_GB.UTF-8/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Attempting to load en/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Attempting to load qt_en_GB in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load qtbase_en_GB in '/usr/share/qt5/translations'
    language:INFO Attempting to load qtbase_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en_GB in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qt_en in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qtbase_en_GB in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load qtbase_en in '/tmp/.mount_Dar23k/usr/bin/locale/QT'
    language:INFO Attempting to load en_GB/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Successfully loaded en_GB/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Exiting translation system (since we successfully loaded: en_GB)
project_data:INFO Setting default profile to HDV 720 24p
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/iconengines" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/iconengines/libqsvgicon.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/iconengines/libqsvgicon.so, metadata=
{
    "IID": "org.qt-project.Qt.QIconEngineFactoryInterface",
    "MetaData": {
        "Keys": [
            "svg",
            "svgz",
            "svg.gz"
        ]
    },
    "className": "QSvgIconPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/iconengines/libqsvgicon.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/iconengines/libqsvgicon.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/iconengines" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/iconengines" ... 
logger_libopenshot:INFO Connecting to libopenshot with debug port: 5556
    language:INFO Attempting to load qt_en_GB.UTF-8 in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load en_GB.UTF-8/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Attempting to load en/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Attempting to load qt_en_GB in '/usr/share/qt5/translations'
    language:INFO Attempting to load qt_en in '/usr/share/qt5/translations'
    language:INFO Attempting to load en_GB/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
    language:INFO Successfully loaded en_GB/LC_MESSAGES/OpenShot in '/tmp/.mount_Dar23k/usr/bin/locale'
         app:INFO Setting font to /tmp/.mount_Dar23k/usr/bin/images/fonts/Ubuntu-R.ttf
         app:INFO Setting custom dark theme
     metrics:INFO Track metric: {'pragma': 'no-cache', 'last-modified': 'Sun, 17 May 1998 03:00:00 GMT', 'content-location': 'http://www.google-analytics.com/collect?cd4=5.2.1&aip=1&ul=en-gb&t=screenview&an=OpenShot+Video+Editor&cid=1c9b87e1-0913-46bd-b818-4143d52e0b80&cd=initial-launch-screen&ua=Mozilla%2F5.0+%28X11%3B+Linux+x86_64%29+AppleWebKit%2F537.36+%28KHTML%2C+like+Gecko%29+Chrome%2F37.0.2062.120+Safari%2F537.36&tid=UA-4381101-5&av=2.1.0&aid=org.openshot.openshot-qt&cd2=3.4.3&cd3=5.2.1&v=1&cd5=Ubuntu-16.04-xenial&cd1=0.1.1', 'access-control-allow-origin': '*', 'content-type': 'image/gif', 'status': '200', 'date': 'Mon, 29 Aug 2016 21:48:34 GMT', 'x-content-type-options': 'nosniff', 'expires': 'Mon, 01 Jan 1990 00:00:00 GMT', 'age': '141823', 'cache-control': 'no-cache, no-store, must-revalidate', 'server': 'Golfe2', 'content-length': '35'} (b'GIF89a\x01\x00\x01\x00\x80\xff\x00\xff\xff\xff\x00\x00\x00,\x00\x00\x00\x00\x01\x00\x01\x00\x00\x02\x02D\x01\x00;')
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqgif.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqgif.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "gif"
        ],
        "MimeTypes": [
            "image/gif"
        ]
    },
    "className": "QGifPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqgif.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqgif.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqico.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqico.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "ico",
            "cur"
        ],
        "MimeTypes": [
            "image/vnd.microsoft.icon"
        ]
    },
    "className": "QICOPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqico.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqico.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqjpeg.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqjpeg.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "jpg",
            "jpeg"
        ],
        "MimeTypes": [
            "image/jpeg",
            "image/jpeg"
        ]
    },
    "className": "QJpegPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqjpeg.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqjpeg.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqsvg.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqsvg.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "svg",
            "svgz"
        ],
        "MimeTypes": [
            "image/svg+xml"
        ]
    },
    "className": "QSvgPlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqsvg.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats/libqsvg.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/imageformats" ... 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/imageformats/libqgif.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/imageformats/libqgif.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "gif"
        ],
        "MimeTypes": [
            "image/gif"
        ]
    },
    "className": "QGifPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("gif") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/imageformats/libqico.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/imageformats/libqico.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "ico"
        ],
        "MimeTypes": [
            "image/vnd.microsoft.icon"
        ]
    },
    "className": "QICOPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("ico") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/imageformats/libqjpeg.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/imageformats/libqjpeg.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "jpg",
            "jpeg"
        ],
        "MimeTypes": [
            "image/jpeg",
            "image/jpeg"
        ]
    },
    "className": "QJpegPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("jpg", "jpeg") 
QFactoryLoader::QFactoryLoader() looking at "/tmp/.mount_Dar23k/usr/bin/imageformats/libqsvg.so" 
Found metadata in lib /tmp/.mount_Dar23k/usr/bin/imageformats/libqsvg.so, metadata=
{
    "IID": "org.qt-project.Qt.QImageIOHandlerFactoryInterface",
    "MetaData": {
        "Keys": [
            "svg",
            "svgz"
        ]
    },
    "className": "QSvgPlugin",
    "debug": false,
    "version": 328193
}


Got keys from plugin meta data ("svg", "svgz") 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/imageformats" ... 
loaded library "/tmp/.mount_Dar23k/usr/bin/imageformats/libqsvg.so" 
link SVGID_18_-5 hasn't been detected!
link SVGID_18_-5 hasn't been detected!
link SVGID_22_-5 hasn't been detected!
link SVGID_24_-2 hasn't been detected!
link SVGID_24_-2 hasn't been detected!
loaded library "/tmp/.mount_Dar23k/usr/bin/imageformats/libqgif.so" 
loaded library "/tmp/.mount_Dar23k/usr/bin/imageformats/libqico.so" 
loaded library "/tmp/.mount_Dar23k/usr/bin/imageformats/libqjpeg.so" 
     metrics:INFO Track metric: {'pragma': 'no-cache', 'last-modified': 'Sun, 17 May 1998 03:00:00 GMT', 'content-location': 'http://www.google-analytics.com/collect?cd4=5.2.1&aip=1&ul=en-gb&t=screenview&an=OpenShot+Video+Editor&cid=1c9b87e1-0913-46bd-b818-4143d52e0b80&cd=main-screen&ua=Mozilla%2F5.0+%28X11%3B+Linux+x86_64%29+AppleWebKit%2F537.36+%28KHTML%2C+like+Gecko%29+Chrome%2F37.0.2062.120+Safari%2F537.36&tid=UA-4381101-5&av=2.1.0&aid=org.openshot.openshot-qt&cd2=3.4.3&cd3=5.2.1&v=1&cd5=Ubuntu-16.04-xenial&cd1=0.1.1', 'access-control-allow-origin': '*', 'content-type': 'image/gif', 'status': '200', 'date': 'Mon, 29 Aug 2016 21:48:34 GMT', 'x-content-type-options': 'nosniff', 'expires': 'Mon, 01 Jan 1990 00:00:00 GMT', 'age': '141824', 'cache-control': 'no-cache, no-store, must-revalidate', 'server': 'Golfe2', 'content-length': '35'} (b'GIF89a\x01\x00\x01\x00\x80\xff\x00\xff\xff\xff\x00\x00\x00,\x00\x00\x00\x00\x01\x00\x01\x00\x00\x02\x02D\x01\x00;')
     metrics:INFO Track metric: {'pragma': 'no-cache', 'last-modified': 'Sun, 17 May 1998 03:00:00 GMT', 'content-location': 'http://www.google-analytics.com/collect?sc=start&cd4=5.2.1&aip=1&ul=en-gb&t=screenview&an=OpenShot+Video+Editor&cid=1c9b87e1-0913-46bd-b818-4143d52e0b80&cd=launch-app&ua=Mozilla%2F5.0+%28X11%3B+Linux+x86_64%29+AppleWebKit%2F537.36+%28KHTML%2C+like+Gecko%29+Chrome%2F37.0.2062.120+Safari%2F537.36&tid=UA-4381101-5&av=2.1.0&aid=org.openshot.openshot-qt&cd2=3.4.3&cd3=5.2.1&v=1&cd5=Ubuntu-16.04-xenial&cd1=0.1.1', 'access-control-allow-origin': '*', 'content-type': 'image/gif', 'status': '200', 'date': 'Mon, 29 Aug 2016 21:48:34 GMT', 'x-content-type-options': 'nosniff', 'expires': 'Mon, 01 Jan 1990 00:00:00 GMT', 'age': '141824', 'cache-control': 'no-cache, no-store, must-revalidate', 'server': 'Golfe2', 'content-length': '35'} (b'GIF89a\x01\x00\x01\x00\x80\xff\x00\xff\xff\xff\x00\x00\x00,\x00\x00\x00\x00\x01\x00\x01\x00\x00\x02\x02D\x01\x00;')
     ui_util:INFO Initializing UI for MainWindow
     ui_util:INFO Binding event MainWindow:actionNew_trigger
     ui_util:INFO Binding event MainWindow:actionOpen_trigger
     ui_util:INFO Binding event MainWindow:actionSave_trigger
     ui_util:INFO Binding event MainWindow:actionUndo_trigger
     ui_util:INFO Binding event MainWindow:actionSaveAs_trigger
     ui_util:INFO Binding event MainWindow:actionImportFiles_trigger
     ui_util:INFO Binding event MainWindow:actionImportImageSequence_trigger
     ui_util:INFO Binding event MainWindow:actionRedo_trigger
     ui_util:INFO Binding event MainWindow:actionRemoveClip_trigger
     ui_util:INFO Binding event MainWindow:actionRemoveTransition_trigger
     ui_util:INFO Binding event MainWindow:actionExportVideo_trigger
     ui_util:INFO Binding event MainWindow:actionUploadVideo_trigger
     ui_util:INFO Binding event MainWindow:actionAddTrack_trigger
     ui_util:INFO Binding event MainWindow:actionPreferences_trigger
     ui_util:INFO Binding event MainWindow:actionPlay_trigger
     ui_util:INFO Binding event MainWindow:actionJumpStart_trigger
     ui_util:INFO Binding event MainWindow:actionRewind_trigger
     ui_util:INFO Binding event MainWindow:actionFastForward_trigger
     ui_util:INFO Binding event MainWindow:actionJumpEnd_trigger
     ui_util:INFO Binding event MainWindow:actionArrowTool_trigger
     ui_util:INFO Binding event MainWindow:actionSnappingTool_trigger
     ui_util:INFO Binding event MainWindow:actionAddMarker_trigger
     ui_util:INFO Binding event MainWindow:actionPreviousMarker_trigger
     ui_util:INFO Binding event MainWindow:actionNextMarker_trigger
     ui_util:INFO Binding event MainWindow:actionFilesShowAll_trigger
     ui_util:INFO Binding event MainWindow:actionFilesShowVideo_trigger
     ui_util:INFO Binding event MainWindow:actionFilesShowAudio_trigger
     ui_util:INFO Binding event MainWindow:actionFilesShowImage_trigger
     ui_util:INFO Binding event MainWindow:actionTransitionsShowAll_trigger
     ui_util:INFO Binding event MainWindow:actionTransitionsShowCommon_trigger
     ui_util:INFO Binding event MainWindow:actionEffectsShowAll_trigger
     ui_util:INFO Binding event MainWindow:actionEffectsShowVideo_trigger
     ui_util:INFO Binding event MainWindow:actionEffectsShowAudio_trigger
     ui_util:INFO Binding event MainWindow:actionTimelineZoomIn_trigger
     ui_util:INFO Binding event MainWindow:actionTimelineZoomOut_trigger
     ui_util:INFO Binding event MainWindow:actionTitle_trigger
     ui_util:INFO Binding event MainWindow:actionAnimatedTitle_trigger
     ui_util:INFO Binding event MainWindow:actionFullscreen_trigger
     ui_util:INFO Binding event MainWindow:actionAbout_trigger
     ui_util:WARNING Icon theme gtk-info not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionThumbnailView_trigger
     ui_util:WARNING Icon theme view-preview not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionDetailsView_trigger
     ui_util:WARNING Icon theme view-list-details not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionReportBug_trigger
     ui_util:INFO Binding event MainWindow:actionAskQuestion_trigger
     ui_util:WARNING Icon theme im-message-new not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionTranslate_trigger
     ui_util:WARNING Icon theme stock_person not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionDonate_trigger
     ui_util:INFO Binding event MainWindow:actionHelpContents_trigger
     ui_util:INFO Binding event MainWindow:actionSimple_View_trigger
     ui_util:INFO Binding event MainWindow:actionAdvanced_View_trigger
     ui_util:WARNING Icon theme get-hot-new-stuff not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionFreeze_View_trigger
     ui_util:WARNING Icon theme locked not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionUn_Freeze_View_trigger
     ui_util:WARNING Icon theme locked not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionShow_All_trigger
     ui_util:INFO Binding event MainWindow:actionProfile_trigger
     ui_util:INFO Binding event MainWindow:actionAdd_to_Timeline_trigger
     ui_util:INFO Binding event MainWindow:actionPreview_File_trigger
     ui_util:INFO Binding event MainWindow:actionRemove_from_Project_trigger
     ui_util:INFO Binding event MainWindow:actionFile_Properties_trigger
     ui_util:INFO Binding event MainWindow:actionRemoveTrack_trigger
     ui_util:INFO Binding event MainWindow:actionRemoveMarker_trigger
     ui_util:INFO Binding event MainWindow:actionAddTrackAbove_trigger
     ui_util:INFO Binding event MainWindow:actionAddTrackBelow_trigger
     ui_util:INFO Binding event MainWindow:actionRemoveEffect_trigger
     ui_util:INFO Binding event MainWindow:actionSplitClip_trigger
     ui_util:INFO Binding event MainWindow:actionProperties_trigger
     ui_util:INFO Binding event MainWindow:actionRenameTrack_trigger
     ui_util:WARNING Icon theme gtk-edit not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionUpdate_trigger
     ui_util:INFO Binding event MainWindow:actionTutorial_trigger
     ui_util:WARNING Icon theme im-message-new not found. Will use backup icon.
     ui_util:INFO Binding event MainWindow:actionAnimation_trigger
     ui_util:INFO Binding event MainWindow:actionLockTrack_trigger
     ui_util:INFO Binding event MainWindow:actionUnlockTrack_trigger
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/sensors" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/sensors" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/sensors" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer" ... 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqconnmanbearer.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqconnmanbearer.so, metadata=
{
    "IID": "org.qt-project.Qt.QBearerEngineFactoryInterface",
    "MetaData": {
        "Keys": [
            "connman"
        ]
    },
    "className": "QConnmanEnginePlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqconnmanbearer.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqconnmanbearer.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqgenericbearer.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqgenericbearer.so, metadata=
{
    "IID": "org.qt-project.Qt.QBearerEngineFactoryInterface",
    "MetaData": {
        "Keys": [
            "generic"
        ]
    },
    "className": "QGenericEnginePlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqgenericbearer.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqgenericbearer.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() looking at "/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqnmbearer.so" 
Found metadata in lib /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqnmbearer.so, metadata=
{
    "IID": "org.qt-project.Qt.QBearerEngineFactoryInterface",
    "MetaData": {
        "Keys": [
            "networkmanager"
        ]
    },
    "className": "QNetworkManagerEnginePlugin",
    "debug": false,
    "version": 328961
}


In /usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqnmbearer.so:
  Plugin uses incompatible Qt library (5.5.1) [release]
"The plugin '/usr/lib/x86_64-linux-gnu/qt5/plugins/bearer/libqnmbearer.so' uses incompatible Qt library. (5.5.1) [release]" 
         not a plugin 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bin/bearer" ... 
QFactoryLoader::QFactoryLoader() checking directory path "/tmp/.mount_Dar23k/usr/bearer" ... 
 files_model:INFO updating files model.
transition_model:INFO updating transitions model.
     version:INFO Found current version: {'content-location': 'http://www.openshot.org/version/json/', 'content-type': 'application/json', 'server': 'Apache/2.2.22 (Ubuntu)', 'status': '200', 'content-length': '29', 'date': 'Wed, 31 Aug 2016 13:20:01 GMT'} (b'{"openshot_version": "2.1.0"}')
 main_window:INFO foundCurrentVersion: Found the latest version: 2.1.0
timeline_webview:INFO Qt Found!
timeline_webview:INFO $scope.Qt = true;
timeline_webview:INFO UpdateLayerIndex
effects_model:INFO updating effects model.
effects_model:INFO category: Video
effects_model:INFO category: Video
effects_model:INFO category: Video
effects_model:INFO category: Video
effects_model:INFO category: Video
effects_model:INFO category: Video
effects_model:INFO category: Video
properties_model:INFO updating clip properties model.
 main_window:INFO Clear all thumbnails: /home/hugh/.openshot_qt/thumbnail
preview_thread:INFO QThread Start Method Invoked
preview_thread:INFO initPlayer
 main_window:INFO Clear all animations: /home/hugh/.openshot_qt/blender
*** Error in `/tmp/.mount_Dar23k/usr/bin/launch': munmap_chunk(): invalid pointer: 0x00007f3aca0d9f40 ***
 main_window:INFO Clear all backups: /home/hugh/.openshot_qt/backup
```

I can only suggest the PPA route which does work, at least it works in 16.04 - can't speak for 14.04

---

### Post by Portaro on 2016-08-31
Yes you receive a messagee error different of mine, no work on 14.04 and in 16.04.
:D

Thanks for your help.

---

