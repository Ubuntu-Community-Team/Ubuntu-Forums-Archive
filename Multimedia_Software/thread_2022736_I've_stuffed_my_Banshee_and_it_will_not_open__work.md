---
title: "I've stuffed my Banshee and it will not open / work."
date: 2012-07-11
forum: Multimedia Software
---

### Post by piloti on 2012-07-11
I've stuffed up my Banshee. This is what I did. 

I was 're-scanning' my folders for new audio and, at the same time, I deleted / emptied my trash.
Banshee crashed.

When I restart Banshee I get the error message below. I have removed and re-installed Banshee through the Ubuntu Software Centre, but no luck.

SO, my questions are:
1: is there a 'quick fix'
2: DO I need to remove SQLite, and all the related packages that use it [through the Ubuntu Software Centre] and then re-install everything again?
3: If I do '2', will I lose all my podcast URL's [not a big issue, but mildly annoying]?

One thing to note is I am pretty useless at understanding how Ubuntu works, so if there are terminal instructions, please make them simple so that an idiot can follow them [I am an idiot!]

Thanks.
P.



An unhandled exception was thrown: Sqlite error 14: unable to open database file (SQL: UPDATE CorePrimarySources SET CachedCount = 908 WHERE PrimarySourceID = 1)

  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0

.NET Version: 4.0.30319.1
OS Version: Unix 3.2.0.27

---

### Post by shantiq on 2012-07-11
hey no worries we are all idiots and have all done this:KS:KS


now this is what i would do here


places/home folder/ CTRL +h   to see hidden folders

see if there is a   .Banshee   or  .banshee  folder   if there is look in there  and then   delete it

any stored info will be gone




go to .config     open   see if there   is a banshee folder   if there is delete too


now that should take care of many of the settings



now


in terminal


```
sudo apt-get remove --purge banshee
```


for an in-depth cleanse


restart computer



```
sudo apt-get install banshee

```




see if that cures it/ resets it all

---

### Post by piloti on 2012-09-06
Shantiq, thanks for this.
In the end I got it working. Yours were the last things I did, because I also noticed afterwards that I was running on a 98% full hd. So, that may have been the reason it crashed in the end. Still, once that was sorted, then your instructions, it has been running smoothly now for a while.
Thanks.
P.

---

