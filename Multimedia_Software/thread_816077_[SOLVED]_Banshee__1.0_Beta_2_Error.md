---
title: "[SOLVED] Banshee  1.0 Beta 2 Error"
date: 2008-06-02
forum: Multimedia Software
---

### Post by Flashgordon20 on 2008-06-02
I just installed Banshee 1.0 Beta 2 and I cannot get it to work. After the install, it did not appear as a menu item. I tried running it through the terminal and got the following:
```
stephen@stephen-laptop:~$ banshee-1
[Info  07:58:47.632] Running Banshee 0.99.3
[Warn  07:58:48.357] Rolling back database migration
[Error 07:58:48.358] Error initializing required service DbConnection
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> Mono.Data.SqliteClient.SqliteSyntaxException: duplicate column name: ExternalID
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-0.99.3/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 --- End of inner exception stack trace ---

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-0.99.3/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-0.99.3/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-0.99.3/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-0.99.3/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 
stephen@stephen-laptop:~$ 

```
I am not a programming/code kind of guy and have no idea what that all means. Can someone point me in the direction and tell me how to resolve this error? I know it's the beta but I should at least be able to start the program. Thanks in advance for any help.

---

### Post by rockin_goliath on 2008-06-02
I'm not a code guy either, that's why I love apt-get and deb packages :)
There is a more recent version of Banshee, RC1, which has some Ubuntu repositories available.
[http://banshee-project.org/Releases/0.99.3]("http://banshee-project.org/Releases/0.99.3") This is the link for the latest version. Following the Ubuntu link will get you here. [https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive") They have some debian repositores listed here. Hope that works for you.

---

### Post by Flashgordon20 on 2008-06-03
> **rockin_goliath said:**
> I'm not a code guy either, that's why I love apt-get and deb packages :)
There is a more recent version of Banshee, RC1, which has some Ubuntu repositories available.
[http://banshee-project.org/Releases/0.99.3]("http://banshee-project.org/Releases/0.99.3") This is the link for the latest version. Following the Ubuntu link will get you here. [https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive") They have some debian repositores listed here. Hope that works for you.

Hello,
I deleted my installation and added those repos. Reinstalled through synaptic and I still get the same error. Any other ideas?

---

### Post by Jst on 2008-06-05
Try removing ~/.config/banshee-1

---

### Post by Flashgordon20 on 2008-06-05
> **Jst said:**
> Try removing ~/.config/banshee-1

That worked. After I removed it, I reinstalled through synaptic. Works perfect now. Had to set up my own menu shortcut, but no big deal. Thank you!:)

---

