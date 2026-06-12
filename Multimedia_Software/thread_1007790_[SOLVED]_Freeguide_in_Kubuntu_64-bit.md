---
title: "[SOLVED] Freeguide in Kubuntu 64-bit"
date: 2008-12-10
forum: Multimedia Software
---

### Post by sbennettgso on 2008-12-10
I'm having trouble with listings showing up in Freeguide.  I've just installed Kubuntu 64-bit on a PC I've just rebuilt.  I've used Freeguide for over a year on various machines with 32-bit Ubuntu and Xubuntu.  Don't know if the issue is Kubuntu, the 64-bit implementation, or something I haven't thought of.

When I run Freeguide from the terminal, here's a portion of the terminal output I get:

```
Dec 10, 2008 8:15:19 PM freeguide.plugins.storage.serfiles.StorageSerFilesByDay load                                                                            
WARNING: Error read file /home/scott/.freeguide/day-2008-12-17-A.ser            
java.lang.ClassNotFoundException: freeguide.common.lib.fgspecific.data.TVChannel
        at java.lang.ClassLoader.findClass(ClassLoader.java:375)                
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)                
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)                
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)        
        at java.lang.Class.forName0(Native Method)                              
        at java.lang.Class.forName(Class.java:264)                              
        at java.io.ObjectInputStream.resolveClass(ObjectInputStream.java:621)   
        at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1592)                                                                              
        at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1513) 
        at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1749)
        at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
        at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
        at java.util.TreeMap.buildFromSorted(TreeMap.java:2404)
        at java.util.TreeMap.buildFromSorted(TreeMap.java:2387)
        at java.util.TreeMap.buildFromSorted(TreeMap.java:2387)
        at java.util.TreeMap.buildFromSorted(TreeMap.java:2387)
        at java.util.TreeMap.buildFromSorted(TreeMap.java:2345)
        at java.util.TreeMap.readObject(TreeMap.java:2291)
        at sun.reflect.GeneratedMethodAccessor11.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at java.io.ObjectStreamClass.invokeReadObject(ObjectStreamClass.java:991)
        at java.io.ObjectInputStream.readSerialData(ObjectInputStream.java:1865)
        at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1770)
        at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
        at java.io.ObjectInputStream.defaultReadFields(ObjectInputStream.java:1963)
        at java.io.ObjectInputStream.readSerialData(ObjectInputStream.java:1887)
        at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1770)
        at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1346)
        at java.io.ObjectInputStream.readObject(ObjectInputStream.java:368)
        at freeguide.plugins.storage.serfiles.StorageSerFilesByDay.load(StorageSerFilesByDay.java:167)
        at freeguide.plugins.storage.serfiles.StorageSerFilesByDay.findEarliest(StorageSerFilesByDay.java:325)
        at freeguide.plugins.reminder.alarm.AlarmReminder.getNextTime(AlarmReminder.java:241)
        at freeguide.common.plugininterfaces.BaseModuleReminder$Scheduler.run(BaseModuleReminder.java:279)

```

Anyone have any ideas?  Any help would be appreciated.

Thanks,
Scott

---

### Post by sbennettgso on 2008-12-12
I got this working just a few minutes ago.  Apparently you have to have the "right" version of Java installed per the Freeguide WWW site.

```
sudo apt-get install openjdk-6-jre
```

Once I did this it worked like a charm.

Thanks,
Scott

---

