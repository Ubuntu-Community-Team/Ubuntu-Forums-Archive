---
title: "Unable to connect to Oracle due to JBDC Connectivity issue"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by Meher_Siva on 2013-08-12
Dear All,

I need to use an ETL Tool in Ubuntu. Setup is ready and when i try to create the connection to oracle on remote desktop, there was an issue which caused the interruption.
The following error occured when i try to connect to Oracle 11g. 

I understood that ODBC/JDBC Drivers are not available. please suggest me how can i install the Oracle ODBC/JDBC Driver in Ubuntu., Where can i get the drivers for download.
Please help me friends., i was struggling from the past one week to resolve this connectivity issue.

Thanks in advance..

Regards..,

Meher Siva,
Bangalore.


The error is as follows.


xception while loading class
oracle.jdbc.driver.OracleDriver


    at org.pentaho.di.core.database.Database.normalConnect(Database.java:366)
    at org.pentaho.di.core.database.Database.connect(Database.java:315)
    at org.pentaho.di.core.database.Database.connect(Database.java:277)
    at org.pentaho.di.core.database.Database.connect(Database.java:267)
    at org.pentaho.di.core.database.DatabaseFactory.getConnectionTestReport(DatabaseFactory.java:86)
    at org.pentaho.di.core.database.DatabaseMeta.testConnection(DatabaseMeta.java:2464)
    at org.pentaho.ui.database.event.DataHandler.testDatabaseConnection(DataHandler.java:533)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.pentaho.ui.xul.impl.AbstractXulDomContainer.invoke(AbstractXulDomContainer.java:329)
    at org.pentaho.ui.xul.impl.AbstractXulComponent.invoke(AbstractXulComponent.java:139)
    at org.pentaho.ui.xul.impl.AbstractXulComponent.invoke(AbstractXulComponent.java:123)
    at org.pentaho.ui.xul.swt.tags.SwtButton.access$500(SwtButton.java:26)
    at org.pentaho.ui.xul.swt.tags.SwtButton$4.widgetSelected(SwtButton.java:119)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(Unknown Source)
    at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.eclipse.jface.window.Window.runEventLoop(Window.java:820)
    at org.eclipse.jface.window.Window.open(Window.java:796)
    at org.pentaho.ui.xul.swt.tags.SwtDialog.show(SwtDialog.java:378)
    at org.pentaho.ui.xul.swt.tags.SwtDialog.show(SwtDialog.java:304)
    at org.pentaho.di.ui.core.database.dialog.XulDatabaseDialog.open(XulDatabaseDialog.java:115)
    at org.pentaho.di.ui.core.database.dialog.DatabaseDialog.open(DatabaseDialog.java:62)
    at org.pentaho.di.ui.spoon.delegates.SpoonDBDelegate.newConnection(SpoonDBDelegate.java:493)
    at org.pentaho.di.ui.spoon.delegates.SpoonDBDelegate.newConnection(SpoonDBDelegate.java:478)
    at org.pentaho.di.ui.spoon.Spoon.newConnection(Spoon.java:7851)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.pentaho.ui.xul.impl.AbstractXulDomContainer.invoke(AbstractXulDomContainer.java:329)
    at org.pentaho.ui.xul.impl.AbstractXulComponent.invoke(AbstractXulComponent.java:139)
    at org.pentaho.ui.xul.impl.AbstractXulComponent.invoke(AbstractXulComponent.java:123)
    at org.pentaho.ui.xul.jface.tags.JfaceMenuitem.access$100(JfaceMenuitem.java:26)
    at org.pentaho.ui.xul.jface.tags.JfaceMenuitem$1.run(JfaceMenuitem.java:85)
    at org.eclipse.jface.action.Action.runWithEvent(Action.java:498)
    at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:545)
    at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:490)
    at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:402)
    at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.pentaho.di.ui.spoon.Spoon.readAndDispatch(Spoon.java:1221)
    at org.pentaho.di.ui.spoon.Spoon.waitForDispose(Spoon.java:7044)
    at org.pentaho.di.ui.spoon.Spoon.start(Spoon.java:8304)
    at org.pentaho.di.ui.spoon.Spoon.main(Spoon.java:580)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.pentaho.commons.launcher.Launcher.main(Launcher.java:134)
Caused by: org.pentaho.di.core.exception.KettleDatabaseException: 
Exception while loading class
oracle.jdbc.driver.OracleDriver

    at org.pentaho.di.core.database.Database.connectUsingClass(Database.java:421)
    at org.pentaho.di.core.database.Database.normalConnect(Database.java:350)
    ... 55 more
Caused by: java.lang.ClassNotFoundException: oracle.jdbc.driver.OracleDriver
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:169)
    at org.pentaho.di.core.database.Database.connectUsingClass(Database.java:412)
    ... 56 more

---

