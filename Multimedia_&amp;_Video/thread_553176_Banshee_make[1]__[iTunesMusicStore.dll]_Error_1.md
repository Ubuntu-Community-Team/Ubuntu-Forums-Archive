---
title: "Banshee: make[1]: *** [iTunesMusicStore.dll] Error 1"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by Prosis on 2007-09-17
Hello

I'm trying to install the iTunesStore plugin for Banshee, but when I use the make command I get these errors:

```
./MusicStorePlugin.cs(59,4): error CS0103: The name `RegisterConfigurationKey' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(60,4): error CS0103: The name `RegisterConfigurationKey' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(61,4): error CS0103: The name `RegisterConfigurationKey' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(62,21): error CS0117: `Banshee.Base.Globals' does not contain a definition for `Configuration'
./MusicStorePlugin.cs(100,26): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(104,16): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(110,26): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(114,16): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(122,26): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
./MusicStorePlugin.cs(126,16): error CS0103: The name `ConfigurationKeys' does not exist in the context of `Banshee.Plugins.MusicStore.MusicStorePlugin'
Compilation failed: 10 error(s), 0 warnings
make[1]: *** [iTunesMusicStore.dll] Error 1
make[1]: quittant le répertoire « /home/daniel/banshee-itunes-plugin/src »
make: *** [all-recursive] Error 1

```

How can I get rid of this problem?

Thank You

---

### Post by Prosis on 2007-09-17
No one?

---

### Post by Ric_ on 2007-10-10
I'm getting the same did you ever fix this?

---

