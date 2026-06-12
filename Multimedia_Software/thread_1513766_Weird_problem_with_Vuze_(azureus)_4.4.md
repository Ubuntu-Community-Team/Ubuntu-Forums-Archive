---
title: "Weird problem with Vuze (azureus) 4.4"
date: 2010-06-20
forum: Multimedia Software
---

### Post by Lrpbpb on 2010-06-20
Sometime ago I had Vuze 4.4 installed in my system and working with no problems. I did a number of changes to my system after that, including installing cardapio, cairo-dock and reinstalling JRE and open JDK (which I think would have been the most influential). You can only install vuze 4.3 from the sofwtare center and this version doesn't come with the ability to use Vuze's "HD Network", reason as to why I wanted to install 4.4.

Anyways, since 4.4 doesn't come in the repos, I downloaded it from the official site: [http://www.vuze.com/](http://www.vuze.com/), and it came in a tar.bz2. I know that these kinds of files usually contain source code, but I extracted it anyway. Inside there is a folder called vuze, and inside there is vuze.bin. When I run vuze.bin the first time all works well, the app opens and I can use it. However, if I close it and run it a second time it doesn't open.

In trying to figure out what happened I tried running it in a terminal and found out the following:
1. When vuze.bin is run the first time, it creates a directory called .azureus in the home folder.
2. When it is run the second time nothing happens, there is a JRE error shown in the terminal.
3. If you erase the folder .azureus, then run vuze.bin, the program opens again.
So it is obvious to see that the .azureus is causing the problem. However, the folder is needed by the program (seeing it creates it on first run)

This is what appears in the terminal when vuze.bin is run (and later closed) and .azureus is nonexistant:
```

Starting Azureus...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Java exec found in PATH. Verifying...
find: `/home/david/.azureus/plugins': No such file or directory

** (SWT:6210): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/david/Downloads/vuze" -Dazureus.install.path="/home/david/Downloads/vuze" -Dazureus.script="/home/david/Downloads/vuze/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/david/Downloads/vuze/Azureus2.jar ; file:/home/david/Downloads/vuze/swt.jar ; file:/home/david/Downloads/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Sat Jun 19 23:50:42 ECT 2010  Successfully migrated key management
MainWindow: constructor
UIFunctions/ImageLoad took 0ms
new shell took 202ms
new shell setup took 76ms
skinlisteners init took 0ms
skin init took 100ms

** (Vuze:6236): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
MainMenu init took 276ms
createWindow init took 0ms
skin layout took 0ms
pre skin widgets init took 251ms
hooks init took 0ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@16c163f
skin widgets (1/2) init took 552ms
skin widgets init took 204ms
pre SWTInstance init took 0ms
Init Core Columns took 125ms
SWTInstance init took 0ms
shell.layout took 355ms
---------SHOWN AT 1277009445136;3202ms
---------DONE DISPATCH AT 1277009446393;4459ms
---------READY AT 1277009446418;4484ms
shell.open took 1282ms
processStartupDMS took 0ms
vuzeactivities init took 0ms
Locale Initializing took 0ms
45817:    Core: 51ms for activity between 'Loading Plugin: aefeatman_v' and 'Loading Plugin: azupnpav'
45858:    Core: 50ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: azplugins'
45906:    Core: 13ms for activity between 'Initializing Global Torrent Manager' and 'Loading Plugin: azrating'
45921:    Core: 13ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: azupdater'
45945:    Core: 25ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: Start/Stop Rules'
45987:    Core: 28ms for activity between 'Loading Plugin: Start/Stop Rules' and 'Loading Plugin: Torrent Removal Rules'
45989:    Core: 13ms for activity between 'Loading Plugin: Torrent Removal Rules' and 'Loading Plugin: Share Hoster'
46028:    Core: 25ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
46048:    Core: 13ms for activity between 'Loading Plugin: DHT' and 'Loading Plugin: DHT Tracker'
46062:    Core: 12ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
46088:    Core: 13ms for activity between 'Loading Plugin: Local Tracker' and 'Loading Plugin: Network Status'
46232:    Core: 114ms for activity between 'Loading Plugin: RSS' and 'Initializing Plugin: Vuze Feature Manager'
46253:    Core: 28ms for activity between 'Initializing Plugin: UPnP Media Server' and 'Initializing Plugin: Tracker Static Pages'
46301:    Core: 50ms for activity between 'Initializing Plugin: Tracker Static Pages' and 'Initializing Plugin: Rating'
46323:    Core: 20ms for activity between 'Initializing Plugin: Start/Stop Rules' and 'Initializing Plugin: Download Remove Rules'
46370:    Core: 13ms for activity between 'Initializing Plugin: Universal Plug and Play (UPnP)' and 'Initializing Plugin: Distributed DB'
46376:    Core: 13ms for activity between 'Initializing Plugin: Distributed Tracker' and 'Initializing Plugin: CoreUpdater'
46416:    Core: 20ms for activity between 'Initializing Plugin: azplatform2' and 'Initializing Plugin: LAN Peer Finder'
46445:    Core: 13ms for activity between 'Initializing Plugin: azintrss' and 'Initializing Plugin: Friends'
Core Initializing took 871ms
DEBUG::Sat Jun 19 23:50:53 ECT 2010::com.aelitis.azureus.core.versioncheck.VersionCheckClient$2::run::191:
  Timeout waiting for version check to complete
    UtilitiesImpl$DelayedTaskImpl::run::1635,UtilitiesImpl$8::run::1098,AEThread2$threadWrapper::run::299
Analysing /home/david/Downloads/vuze/hs_err_pid5747.log
DEBUG::Sat Jun 19 23:50:55 ECT 2010::com.aelitis.azureus.ui.swt.skin.SWTSkinObjectBasic::dispose::885:
  Warning: Disposal failed
    SWTSkin::removeSkinObject::1394,SideBarEntrySWT::widgetDisposed::913,TypedListener::handleEvent::-1,EventTable::sendEvent::-1,Widget::sendEvent::-1,Widget::sendEvent::-1,Widget::sendEvent::-1,Widget::release::-1,Tree::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Widget::release::-1,Control::release::-1,Composite::releaseChildren::-1,Canvas::releaseChildren::-1,Decorations::releaseChildren::-1,Shell::releaseChildren::-1,Widget::release::-1,Control::release::-1,Widget::dispose::-1,Shell::dispose::-1,SWTThread::terminate::338,Initializer$9::runSupport::586,AERunnable::run::38,Utils::execSWTThread::616,Utils::execSWTThread::740,Initializer::stopIt::584,MainWindow::_dispose::1160,MainWindow$25::runSupport::1097,AERunnableBoolean::run::40,Utils::execSWTThread::616,Utils::execSWTThread::740,Utils::execSWTThreadWithBool::1301,Utils::execSWTThreadWithBool::1258,MainWindow::dispose::1094,UIFunctionsImpl::dispose::231,SystemTraySWT$15$1::runSupport::300,AERunnable::run::38,RunnableLock::run::-1,Synchronizer::runAsyncMessages::-1,Display::runAsyncMessages::-1,Display::readAndDispatch::-1,SWTThread::<init>::268,SWTThread::createInstance::63,Initializer::<init>::158,NativeConstructorAccessorImpl::newInstance0::-2,NativeConstructorAccessorImpl::newInstance::57,DelegatingConstructorAccessorImpl::newInstance::45,Constructor::newInstance::532,Main::<init>::114,Main::main::290,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,MainExecutor$1::run::37,Thread::run::636
java.lang.NullPointerException
    at com.aelitis.azureus.ui.swt.browser.BrowserContext$5.completed(BrowserContext.java:224)
    at org.eclipse.swt.browser.Mozilla$21.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.syncExec(Unknown Source)
    at org.eclipse.swt.widgets.Display.syncExec(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.OnStateChange(Unknown Source)
    at org.eclipse.swt.browser.Mozilla$10.method3(Unknown Source)
    at org.eclipse.swt.internal.mozilla.XPCOMObject.callback3(Unknown Source)
    at org.eclipse.swt.internal.mozilla.XPCOM._JS_EvaluateUCScriptForPrincipals(Native Method)
    at org.eclipse.swt.internal.mozilla.XPCOM.JS_EvaluateUCScriptForPrincipals(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.execute(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.onDispose(Unknown Source)
    at org.eclipse.swt.browser.Mozilla$5.handleEvent(Unknown Source)
    at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Widget.dispose(Unknown Source)
    at org.gudy.azureus2.ui.swt.Utils.disposeSWTObjects(Utils.java:184)
    at com.aelitis.azureus.ui.swt.skin.SWTSkinObjectBasic.dispose(SWTSkinObjectBasic.java:885)
    at com.aelitis.azureus.ui.swt.skin.SWTSkin.removeSkinObject(SWTSkin.java:1394)
    at com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBarEntrySWT.widgetDisposed(SideBarEntrySWT.java:913)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(Unknown Source)
    at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Tree.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Decorations.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Shell.releaseChildren(Unknown Source)
    at org.eclipse.swt.widgets.Widget.release(Unknown Source)
    at org.eclipse.swt.widgets.Control.release(Unknown Source)
    at org.eclipse.swt.widgets.Widget.dispose(Unknown Source)
    at org.eclipse.swt.widgets.Shell.dispose(Unknown Source)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.terminate(SWTThread.java:338)
    at com.aelitis.azureus.ui.swt.Initializer$9.runSupport(Initializer.java:586)
    at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:616)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:740)
    at com.aelitis.azureus.ui.swt.Initializer.stopIt(Initializer.java:584)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow._dispose(MainWindow.java:1160)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow$25.runSupport(MainWindow.java:1097)
    at org.gudy.azureus2.core3.util.AERunnableBoolean.run(AERunnableBoolean.java:40)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:616)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:740)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThreadWithBool(Utils.java:1301)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThreadWithBool(Utils.java:1258)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow.dispose(MainWindow.java:1094)
    at com.aelitis.azureus.ui.swt.shells.main.UIFunctionsImpl.dispose(UIFunctionsImpl.java:231)
    at org.gudy.azureus2.ui.systray.SystemTraySWT$15$1.runSupport(SystemTraySWT.java:300)
    at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:268)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:63)
    at com.aelitis.azureus.ui.swt.Initializer.<init>(Initializer.java:158)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:114)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:290)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
DEBUG::Sat Jun 19 23:50:55 ECT 2010::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
  org.eclipse.swt.SWTException: Widget is disposed
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.widgets.Widget.error(Unknown Source)
    at org.eclipse.swt.widgets.Widget.checkWidget(Unknown Source)
    at org.eclipse.swt.browser.Browser.checkWidget(Unknown Source)
    at org.eclipse.swt.widgets.Control.isVisible(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.GetVisibility(Unknown Source)
    at org.eclipse.swt.browser.Mozilla$13.method6(Unknown Source)
    at org.eclipse.swt.internal.mozilla.XPCOMObject.callback6(Unknown Source)
    at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
    at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.eclipse.swt.widgets.Display.release(Unknown Source)
    at org.eclipse.swt.graphics.Device.dispose(Unknown Source)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.terminate(SWTThread.java:346)
    at com.aelitis.azureus.ui.swt.Initializer$9.runSupport(Initializer.java:586)
    at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:616)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:740)
    at com.aelitis.azureus.ui.swt.Initializer.stopIt(Initializer.java:584)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow._dispose(MainWindow.java:1160)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow$25.runSupport(MainWindow.java:1097)
    at org.gudy.azureus2.core3.util.AERunnableBoolean.run(AERunnableBoolean.java:40)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:616)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThread(Utils.java:740)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThreadWithBool(Utils.java:1301)
    at org.gudy.azureus2.ui.swt.Utils.execSWTThreadWithBool(Utils.java:1258)
    at com.aelitis.azureus.ui.swt.shells.main.MainWindow.dispose(MainWindow.java:1094)
    at com.aelitis.azureus.ui.swt.shells.main.UIFunctionsImpl.dispose(UIFunctionsImpl.java:231)
    at org.gudy.azureus2.ui.systray.SystemTraySWT$15$1.runSupport(SystemTraySWT.java:300)
    at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:268)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:63)
    at com.aelitis.azureus.ui.swt.Initializer.<init>(Initializer.java:158)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:114)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:290)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)

core.stop
54800:    Core: 8352ms for activity between 'Initializing Plugin: Friends' and 'Unloading Torrents'
core.stop done in 2745
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

```This is the output if .azureus exists:
```
Starting Azureus...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Java exec found in PATH. Verifying...

** (SWT:6749): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/david/Downloads/vuze" -Dazureus.install.path="/home/david/Downloads/vuze" -Dazureus.script="/home/david/Downloads/vuze/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/david/Downloads/vuze/Azureus2.jar ; file:/home/david/Downloads/vuze/swt.jar ; file:/home/david/Downloads/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
MainWindow: constructor
UIFunctions/ImageLoad took 0ms
new shell took 107ms
new shell setup took 99ms
skinlisteners init took 0ms
skin init took 50ms

** (Vuze:6775): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
MainMenu init took 126ms
createWindow init took 0ms
skin layout took 0ms
pre skin widgets init took 25ms
hooks init took 0ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@1e2ca7
skin widgets (1/2) init took 125ms
skin widgets init took 105ms
pre SWTInstance init took 0ms
Init Core Columns took 50ms
SWTInstance init took 0ms
shell.layout took 176ms
---------SHOWN AT 1277009573017;1551ms
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x0189ea8e, pid=6775, tid=3069836144
#
# JRE version: 6.0_18-b18
# Java VM: OpenJDK Client VM (14.0-b16 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.8
# Distribution: Ubuntu lucid (development branch), package 6b18-1.8-0ubuntu1
# Problematic frame:
# C  [libglib-2.0.so.0+0x3ea8e]  g_main_context_prepare+0x16e
#
# An error report file with more information is saved as:
# /home/david/Downloads/vuze/hs_err_pid6775.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/home/david/Downloads/vuze/vuze: line 188:  6775 Aborted                 ${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" -Dazureus.script="$0" $JAVA_PROPS $START_CLASS "$@"
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
```The output says it is an error in JRE, however if I run vuze without the folder .azureus, or other java based programs such as JDownloader, there is no problem.
Can any of you Linux Gurus help me with this problem, the program is next to unusable because of this problem. Is it really a problem with java? Don't forget, I had already vuze working before using the same method, with no problems. Please help me! ;)

---

### Post by Javich on 2010-06-24
Hey Lrpbpb, I have azureus 4.4 up'n running, here's what I did:
- Went to [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) and downloaded the vuze tar (file I got was "Vuze_Installer.tar.bz2"
- Save it to your desktop, then right click and select "Extract Here", don't worry, it will be extracted inside a folder named "vuze"
- Then move that "vuze" folder to a location you'd like (i.e. I have it in "/home/myuser/vuze"
- Then to run, just open the vuze folder, then double click on the file named "vuze" (the one that by default, when extracted, had execute permission); it'll prompt what you want to do, select "Run in Terminal" or "Run".
- If you want a shortcut, I'd recommend you to create it manually

I have ubuntu 9.10 (32bit) running on a sun java 6 vm (if you don't know which one you have, open a terminal, then type: ```
java -version
```

Hope this helps.

Javier

---

### Post by doas777 on 2010-06-24
azureus ships it's own version of the swt libraries, which can be incompatible with other versions. if you have a weird java version, then it may not work correctly.

---

### Post by Lrpbpb on 2010-07-02
Vuze now works! Nothing seemed to fix it, so I just gave up, then a number of updates came, I installed them and VOILA! It works. I guess this reminds us how important updates really are....

---

