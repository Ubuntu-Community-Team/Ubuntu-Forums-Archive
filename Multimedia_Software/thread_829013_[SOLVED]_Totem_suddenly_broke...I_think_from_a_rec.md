---
title: "[SOLVED] Totem suddenly broke...I think from a recent update"
date: 2008-06-14
forum: Multimedia Software
---

### Post by timzak on 2008-06-14
I don't use Totem very often...usually to watch YouTube videos with the new Hardy plugin.  I think a recent update broke Totem, as I tried to start it this morning and got a strange error.  I will paste the portion that is visible to me:

```
Couldn't load the '/usr/share/totem/properties.ui' interface. Error on line 811 char 27: Invalid UTF-8 encoded text - not valid '<?xml version="1.0" ?>
<!--*- mode: xml -*--><!DOCTYPE glade-interface
  SYSTEM 'http://glade.gnome.org/glade-2.0.dtd'>
<interface>

<object class="GtkVBox" id="vbox1">
  <property name="border_width">6</property>
  <property name="visible">True</property>
  <property name="homogeneous">False</property>
  <property name="spacing">18</property>

  <child>
    <object class="GtkVBox" id="general_vbox">
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">6</property>

      <child>
	<object class="GtkLabel" id="bvwp_general_label">
	  <property name="visible">True</property>
	  <property name="label" translatable="yes">General</property>
	  <property name="use_underline">False</property>
	  <property name="use_markup">True</property>
	  <property name="justify">GTK_JUSTIFY_LEFT</property>
	  <property name="wrap">False</property>
	  <property name="selectable">False</property>
	  <property name="xalign">0</property>
	  <property name="yalign">0.5</property>
	  <property name="xpad">0</property>
	  <property name="ypad">0</property>
	  <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
	  <property name="width_chars">-1</property>
	  <property name="single_line_mode">False</property>
	  <property name="angle">0</property>
	</object>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">True</property>
	  <property name="fill">True</property>
	</packing>
      </child>

      <child>
```

Can anyone help me fix this?  I'm reasonably sure I did nothing to cause this.  

Any help appreciated.

---

### Post by timzak on 2008-06-14
Nevermind...I used synaptic to uninstall and reinstall and it works again.

---

