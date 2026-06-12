---
title: "Compiz desktop effects not working on Ubuntu 10.04"
date: 2010-07-01
forum: Multimedia Software
---

### Post by manavendra on 2010-07-01
I recently installed compiz, but it's not working. The Desktop effects is also not opening from the System Setting menu. I crashes everytime I try to open Desktop effects from System Settings. However I am able to open Desktop Effects from searching "Desktop Effects" in the Kickoff Application Launcher. When launched, all it's options are shaded/disabled and shows the info "Compositing is not supported on your system." 

Also, why is "glxinfo" giving "segmentation fault". Any help would be appreciated to make compiz work on my system. I hope the following output would be of help to investigate:

```
mnm@nci:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

``````
mnm@nci:~$ glxinfo
name of display: :0.0
Segmentation fault

``````
mnm@nci:~$ compiz --replace
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x1600021
kwin(2220) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
kwin(2220) KWin::Extensions::init: Extensions: shape: 0x "11"  composite: 0x "4"  render: 0x "a"  fixes: 0x "40"
kwin(2220) KWin::Workspace::setupCompositing: Compositing is turned off in options or disabled
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/mnm/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, initial: 153668
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 153668
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 27263613 ;WMCLASS: "plasma" : "plasma" ;Caption: "plasma-desktop" ' :153668
kwin(2220) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(2220) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(2220) KWin::Workspace::updateClientArea: Done.
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, initial: 162383
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 162383
kwin(2220) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 18874473 ;WMCLASS: "firefox" : "navigator" ;Caption: "Ubuntu Forums -Post New Thread - Mozilla Firefox" ' : 162383
kwin(2220) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(2220) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(2220) KWin::Workspace::updateClientArea: Done.

```

---

