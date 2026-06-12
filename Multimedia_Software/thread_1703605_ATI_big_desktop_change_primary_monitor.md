---
title: "ATI big desktop change primary monitor"
date: 2011-03-09
forum: Multimedia Software
---

### Post by wsonar on 2011-03-09
So i was searching around my big desktop was working fine by default but I couldn't figure out how to switch my primary monitor and all the threads on this topic where real old and the fglrx drivers kept messing me up

so I went to my profile and showed hidden files and found a cool .xml file called monitors under .config

opend it up and chooses the primary monitor I wanted 

very Nice Yes

---

### Post by djahma on 2011-06-11
hi wsonar,
I'm looking to get the same visual config as you have with your monitors. Could you show me the content of your monitors.xml file please? I'd like to compare with mine, I'm guessing I should set up 2 outputs under one configuration tag...but I don't know how to start with that;)
Mine looks like the following, and indeed, my second monitor doesnt seem to be set up:
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DFP1">
      </output>
      <output name="CRT1">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
          <vendor>ACR</vendor>
          <product>0x000e</product>
          <serial>0x74600c6d</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DVI-0">
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="DFP1">
      </output>
      <output name="DFP2">
      </output>
      <output name="CRT1">
      </output>
      <output name="CRT2">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>
```

thanks

---

