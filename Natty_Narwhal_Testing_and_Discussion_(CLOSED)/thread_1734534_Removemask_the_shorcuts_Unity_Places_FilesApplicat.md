---
title: "Remove/mask the shorcuts Unity Places Files/Applications"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mohegan on 2011-04-20
A little trick to hide Place files and applications shorcuts in unity (but they work with the global shortcut / ubuntu logo) !
Just modify this files : /usr/share/unity/places/applications.place and /usr/share/unity/places/files.place :
```
sudo gedit /usr/share/unity/places/*.place
```

Edit those files like this :
=> For applications.place :
```
[Place]
DBusName=com.canonical.Unity.ApplicationsPlace
DBusObjectPath=/com/canonical/unity/applicationsplace

[Entry:Files]
DBusObjectPath=/com/canonical/unity/applicationsplace/applications
Icon=/usr/share/unity/themes/applications.png
Name=Applications
Description=
SearchHint=Search Applications
Shortcut=a
ShowEntry=false

[Entry:Runner]
DBusObjectPath=/com/canonical/unity/applicationsplace/runner
Name=Commands
SearchHint=Run a command
ShowGlobal=false
ShowEntry=false

[Activation]
URIPattern=unity-(install|runner)://.+
MimetypePattern=application/x-unity-available-application
Priority=0

[Desktop Entry]
X-Ubuntu-Gettext-Domain=unity-place-applications

```

=> For files.place :
```
[Place]
DBusName=com.canonical.Unity.FilesPlace
DBusObjectPath=/com/canonical/unity/filesplace

[Entry:Files]
DBusObjectPath=/com/canonical/unity/filesplace/files
Icon=/usr/share/unity/themes/files.png
Name=Files & Folders
Name[da]=Filer og mapper
Description=Find documents, downloads, and other files
Description[da]=Find dokumenter, downloads og andre filer
SearchHint=Search Files & Folders
Shortcut=f
ShowEntry=false

[Desktop Entry]
X-Ubuntu-Gettext-Domain=unity-place-files

```

I just added the line "ShowEntry=false" at the good place.

Finally, disconnect and reconnect you. :)

---

