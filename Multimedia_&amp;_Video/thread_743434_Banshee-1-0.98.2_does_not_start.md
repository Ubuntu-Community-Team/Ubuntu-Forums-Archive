---
title: "Banshee-1-0.98.2 does not start"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by Kummerpaule on 2008-04-02
hi all,

since i installed banshee-1-0.98.2 it does not start but gives me the following error message:

An unhandled exception was thrown: Could not load file or assembly 'Mono.Addins, Version=0.3.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

  at <0x00000> <unknown method>
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /home/marvin/Desktop/Banshee/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /home/marvin/Desktop/Banshee/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.22.14

Assembly Version Information:

Mono.Posix (2.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
Hyena.Gui (0.98.2.41828)
gtk-sharp (2.10.0.0)
Hyena (0.98.2.41826)
Banshee.Core (0.98.2.41832)
Banshee.Services (0.98.2.41834)
Banshee.ThickClient (0.98.2.41838)
Nereid (0.98.2.41839)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.22-14-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

[/etc/debian_version]
lenny/sid

Also the old banshee 0.34... does not work anymore when i install it! however, right now its not installed, so it cannot mess with the new version.

Anyone has a clue what this error message tries to say? :)

---

### Post by simius on 2008-04-02
Just got the same problem. I installed Mono.Addins with /home/sander as the prefix, and now Mono couldn't find the right Global Assembly Cache directories. I worked around this problem by starting Banshee with:

MONO_PATH=/home/sander/lib/mono/gac/Mono.Addins.Gui/0.3.0.0__0738eb9f132ed756/:/home/sander/lib/mono/gac/Mono.Addins/0.3.0.0__0738eb9f132ed756/ ./banshee-1

Something similar might work for you, just make sure that you pick the right directories.

---

### Post by Kummerpaule on 2008-04-03
My installation prefix for Mono.Addins was /usr/local so I adjusted MONO_PATH variable accordingly. However, now I get the following errors:

```

marvin@Kummerpaule:~/Desktop/mono-addins-0.3$ MONO_PATH=/usr/local/lib/mono/gac/Mono.Addins.Gui/0.3.0.0__0738eb9f132ed756/:/usr/local/lib/mono/gac/Mono.Addins/0.3.0.0__0738eb9f132ed756/ banshee-1
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Xml.XmlException: Document element did not appear.  Line 1, position 1.
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlReader.MoveToContent () [0x00000] 
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot () [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.ServiceStack.ServiceManager.Run () [0x00036] in /home/marvin/Desktop/Banshee/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:100 
  at Banshee.ServiceStack.Application.Run () [0x0001e] in /home/marvin/Desktop/Banshee/src/Core/Banshee.Services/Banshee.ServiceStack/Application.cs:64 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x000b7] in /home/marvin/Desktop/Banshee/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:106 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /home/marvin/Desktop/Banshee/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /home/marvin/Desktop/Banshee/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 


```

---

