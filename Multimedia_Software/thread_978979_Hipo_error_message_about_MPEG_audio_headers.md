---
title: "Hipo error message about MPEG audio headers"
date: 2008-11-11
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-11-11
When I try to upload mp3s to my ipod classic 120GB using the Hipo iPod Menagement tool, I get the following error:
```
MPEG audio header not found
```
Under details, I find the following:
 ```
 at TagLib.Mpeg.AudioFile.ReadStart (Int64 start, ReadStyle propertiesStyle) [0x00000] 
  at TagLib.NonContainer.File.Read (ReadStyle propertiesStyle) [0x00000] 
  at TagLib.NonContainer.File..ctor (IFileAbstraction abstraction, ReadStyle propertiesStyle) [0x00000] 
  at TagLib.Mpeg.AudioFile..ctor (IFileAbstraction abstraction, ReadStyle propertiesStyle) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
```
Why is that? Very few mp3 files actually **are** transferred to the iPod, so the problem is not that Hipo doesn't recognize mp3s...

---

### Post by juicyoner on 2009-03-09
Solution to this here: [http://ubuntuforums.org/showthread.php?t=803719](http://ubuntuforums.org/showthread.php?t=803719)

---

