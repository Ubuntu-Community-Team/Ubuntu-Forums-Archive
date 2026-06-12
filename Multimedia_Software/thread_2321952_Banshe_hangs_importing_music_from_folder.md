---
title: "Banshe hangs importing music from folder"
date: 2016-04-25
forum: Multimedia Software
---

### Post by eclay on 2016-04-25
Hello,  I've been using banshee for many years on ubuntu and have run into an issue where it just stops responding when attempting to import music.  I don't get any errors it just stops responding and I finally give up and click the X to close the browse button.

Steps to reproduce this issue

- Launch banshee
- click Media > import media > folder then click choose folders
- navigate to the directory that the mp3 files are in and click the import button

At th is point nothing seems to happen.  I've attempted to launch it via console and don't see any errors either.

I'm running Ubuntu 16.04 with the Mate desktop.

Anyone else having this same experience?  

Any thoughts on how to resolve?

---

### Post by QDR06VV9 on 2016-04-25
This is a common bug with banshee's database. To solve it, delete your banshee.db in <**~/.config/Banshee-1**>. The next time you scan or import it should work without freezing.

If not try running banshee from the terminal and try importing again and paste back the errors.

---

### Post by eclay on 2016-04-26
I've removed the ~/.config/banshee-1/banshee.db file and tried to import files/music again without luck.  Still not seeing any errors but do see some workings when launching banshee via terminal.
```
$ banshee 
[Info  13:09:36.581] Running Banshee 2.6.2: [Ubuntu 16.04 LTS (linux-gnu, x86_64) @ 2016-04-18 13:50:09 UTC]
[Warn  13:09:36.763] Cannot connect to NetworkManager or Wicd - An available, working network connection will be assumed

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkComponent) to class (__gtksharp_49_Hyena_Gui_BaseWidgetAccessible)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkSelection) to class  (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkTable) to class  (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init
[Warn  13:09:37.024] Initialization of accessibility support for  ListView widgets failed - System.ArgumentException: Invalid signal name:  model_changed (in `glib-sharp')
  at GLib.Signal.Emit (GLib.Object instance, System.String  detailed_signal, System.Object[] args) <0x41857ea0 + 0x004df> in  <filename unknown>:0 
  at  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].EmitModelChanged ()  <0x41857e20 + 0x0003b> in <filename unknown>:0 
  at Hyena.ThreadAssist.ProxyToMain (Hyena.InvokeHandler handler) <0x41857d50 + 0x00037> in <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].OnModelChanged  (System.Object o, System.EventArgs a) <0x41857c60 + 0x000d3> in  <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T]..ctor  (GLib.Object widget) <0x41852820 + 0x0045f> in <filename  unknown>:0 
  at Hyena.Data.Gui.ListViewAccessibleFactory`1[T].Init () <0x418516e0 + 0x00093> in <filename unknown>:0 

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkSelection) to class  (__gtksharp_55_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkTable) to class  (__gtksharp_55_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init
[Warn  13:09:37.044] Initialization of accessibility support for  ListView widgets failed - System.ArgumentException: Invalid signal name:  model_changed (in `glib-sharp')
  at GLib.Signal.Emit (GLib.Object instance, System.String  detailed_signal, System.Object[] args) <0x41857ea0 + 0x004df> in  <filename unknown>:0 
  at  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].EmitModelChanged ()  <0x41857e20 + 0x0003b> in <filename unknown>:0 
  at Hyena.ThreadAssist.ProxyToMain (Hyena.InvokeHandler handler) <0x41857d50 + 0x00037> in <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].OnModelChanged  (System.Object o, System.EventArgs a) <0x41857c60 + 0x000d3> in  <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T]..ctor  (GLib.Object widget) <0x41852820 + 0x0045f> in <filename  unknown>:0 
  at Hyena.Data.Gui.ListViewAccessibleFactory`1[T].Init () <0x418516e0 + 0x00093> in <filename unknown>:0 

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkSelection) to class  (__gtksharp_60_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkTable) to class  (__gtksharp_60_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init
[Warn  13:09:37.053] Initialization of accessibility support for  ListView widgets failed - System.ArgumentException: Invalid signal name:  model_changed (in `glib-sharp')
  at GLib.Signal.Emit (GLib.Object instance, System.String  detailed_signal, System.Object[] args) <0x41857ea0 + 0x004df> in  <filename unknown>:0 
  at  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].EmitModelChanged ()  <0x41857e20 + 0x0003b> in <filename unknown>:0 
  at Hyena.ThreadAssist.ProxyToMain (Hyena.InvokeHandler handler) <0x41857d50 + 0x00037> in <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].OnModelChanged  (System.Object o, System.EventArgs a) <0x41857c60 + 0x000d3> in  <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T]..ctor  (GLib.Object widget) <0x41852820 + 0x0045f> in <filename  unknown>:0 
  at Hyena.Data.Gui.ListViewAccessibleFactory`1[T].Init () <0x418516e0 + 0x00093> in <filename unknown>:0 

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkSelection) to class  (__gtksharp_65_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkTable) to class  (__gtksharp_65_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init
[Warn  13:09:37.056] Initialization of accessibility support for  ListView widgets failed - System.ArgumentException: Invalid signal name:  model_changed (in `glib-sharp')
  at GLib.Signal.Emit (GLib.Object instance, System.String  detailed_signal, System.Object[] args) <0x41857ea0 + 0x004df> in  <filename unknown>:0 
  at  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].EmitModelChanged ()  <0x41857e20 + 0x0003b> in <filename unknown>:0 
  at Hyena.ThreadAssist.ProxyToMain (Hyena.InvokeHandler handler) <0x41857d50 + 0x00037> in <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].OnModelChanged  (System.Object o, System.EventArgs a) <0x41857c60 + 0x000d3> in  <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T]..ctor  (GLib.Object widget) <0x41852820 + 0x0045f> in <filename  unknown>:0 
  at Hyena.Data.Gui.ListViewAccessibleFactory`1[T].Init () <0x418516e0 + 0x00093> in <filename unknown>:0 

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkSelection) to class  (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init

(Banshee:11531): GLib-GObject-WARNING **: attempting to add an interface  (AtkTable) to class  (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d)  after class_init
[Warn  13:09:37.059] Initialization of accessibility support for  ListView widgets failed - System.ArgumentException: Invalid signal name:  model_changed (in `glib-sharp')
  at GLib.Signal.Emit (GLib.Object instance, System.String  detailed_signal, System.Object[] args) <0x41857ea0 + 0x004df> in  <filename unknown>:0 
  at  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].EmitModelChanged ()  <0x41857e20 + 0x0003b> in <filename unknown>:0 
  at Hyena.ThreadAssist.ProxyToMain (Hyena.InvokeHandler handler) <0x41857d50 + 0x00037> in <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T].OnModelChanged  (System.Object o, System.EventArgs a) <0x41857c60 + 0x000d3> in  <filename unknown>:0 
  at Hyena.Data.Gui.Accessibility.ListViewAccessible`1[T]..ctor  (GLib.Object widget) <0x41852820 + 0x0045f> in <filename  unknown>:0 
  at Hyena.Data.Gui.ListViewAccessibleFactory`1[T].Init () <0x418516e0 + 0x00093> in <filename unknown>:0 
[Info  13:09:37.164] Updating web proxy from GConf
[Warn  13:09:37.204] Caught an exception - System.ApplicationException:  No support GNOME Settings Daemon could be reached. (in  `Banshee.MultimediaKeys')
  at  Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize  () <0x41896ce0 + 0x0037f> in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension  (Mono.Addins.TypeExtensionNode node) <0x41881f70 + 0x00169> in  <filename unknown>:0 
[Warn  13:09:37.204] Extension  `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support  GNOME Settings Daemon could be reached.
[Warn  13:09:37.216] Caught an exception - System.ApplicationException:  No support GNOME Settings Daemon could be reached. (in  `Banshee.MultimediaKeys')
  at  Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize  () <0x41896ce0 + 0x0037f> in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension  (Mono.Addins.TypeExtensionNode node) <0x41881f70 + 0x00169> in  <filename unknown>:0 
[Warn  13:09:37.216] Extension  `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support  GNOME Settings Daemon could be reached.
[Info  13:09:37.216] All services are started 0.517241
[Info  13:09:37.380] AmazonMP3 store redirect URL: [http://integrated-services.banshee.fm/amz/redirect.do/](http://integrated-services.banshee.fm/amz/redirect.do/)
[Info  13:09:37.540] nereid Client Started
[Info  13:09:37.567] GStreamer version 1.8.0.0, gapless: True, replaygain: False

```

And then I have to force stop the import.

---

### Post by QDR06VV9 on 2016-04-26
Humm! Have you tried to disable the "bpm" plugin.

---

### Post by eclay on 2016-04-26
Disabling the "bpm" plugin didn't make a difference.

---

### Post by QDR06VV9 on 2016-04-26
I am at a loss here?
To be sure
```
sudo apt-get install ubuntu-restricted-extras
```
I am assuming you have the necessary gstreamer plugins installed.
If that fails you might consider filing a bug against [banshee]("https://bugzilla.gnome.org/")
Sorry I could not be of more help here.
Kind Regards

---

### Post by eclay on 2016-04-29
What seemed to fix this for me was to launch banshee and disable every extension except for apple i support, mass storage and MTP device extensions.  Now I'm able to launch banshee and import files.

Thanks

---

### Post by QDR06VV9 on 2016-04-29
> **eclay said:**
> What seemed to fix this for me was to launch banshee and disable every extension except for apple i support, mass storage and MTP device extensions.  Now I'm able to launch banshee and import files.

Thanks

Nice! Glad you got it  resolved.
And Thank You for sharing your solution.
I took the liberty to mark this as solved, but if something comes up and you need it changed back just post here.
Kind Regards

---

### Post by mc4man on 2016-05-01
From what I can see in 16.04 it's the DAAP extension
(- fixed here by disabling that extension, closing banshee, deleting .config/banshee-1/banshee.db, restarting banshee

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1577205](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1577205)

---

