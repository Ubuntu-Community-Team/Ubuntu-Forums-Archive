---
title: "VLC Notification Area Options Bug"
date: 2012-11-07
forum: Multimedia Software
---

### Post by sorc3r3r on 2012-11-07
Hi
I updated my Ubuntu from Ubuntu 11.04 to Ubuntu 11.10  two days back. Everything is working fine. I did the upgrade option by choosing the 'UPGRADE TO 11.10 ' from the Update Manager.
Everything is working fine. The upgrade was uneventful and smooooooth.
VLC was already installed on 11.04 prior to the upgrade. I am using VLC Version 1.1.12
But, I found a small issue with the VLC player. I am using the Unity Interface. When I launch the VLC player it automatically puts the VLC Icon in the notification area ( A new feature in 11.10 I presume] and it give various options when you click on it.

The issue is, when the song is being played, the drop down menu shows ''PAUSE" option. Now when you click the 'PAUSE' button; the music playback  pauses but the Drop Down Menu Option doesn't change to 'PLAY'. Isn't is supposed to be that way?

I have attached a screen shot.
As you can see from the screen shot that, the playback of the music is paused, but on the menu instead of 'PLAY' its 'PAUSE'. 
a)Why doesn't  the drop down menu option change to play when paused and vice versa.
b)Why is it that all the menu options are active but not inactive/dimmed according to the conditions?
_________________

I am using a TOSHIBA Satellite C650 Laptop.
Processor: Pentium Dual Core CPU(2.2 GHz)
RAM:3 MB

Ubuntu
Release: 11.10 Oneric
Kernel Linux 3.0.0-26-Generic
Genome 3.2.1

---

### Post by mc4man on 2012-11-07
You are using a 'vlc' indicator provided by the sni-qt package. 
Overall the indicator is terrible, was in 11.10 when it was introduced & still is in 12.10

You can switch over to the vlc systray icon which works much better. There is no way to configure sni-qt so basically you'd need to - 

Add vlc to unity's systray whitelist in dconf (gsettings or dconf-editor
Uninstall  the sni-qt package so the actual systray icon is used

I don't have a 11.10 atm but should be easy to search out how to add Vlc to it, either from a terminal or manually in dconf-editor
(dconf-editor is in dconf-tools package in 11.10

(- the command to keep current whitelist defaults & add vlc in 11.10 should be this
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Vlc']"
```

Then make sure systray icon is enabled in vlc - screen, remove the sni-qt package & you may need to do a log out/in to get going

Old bug I have on sni-qt
[https://bugs.launchpad.net/ubuntu/+source/sni-qt/+bug/859499](https://bugs.launchpad.net/ubuntu/+source/sni-qt/+bug/859499)

The 2nd screen shows the setting in dconf-editor though this is in 12.10 & I've removed all the default apps & just added 3 apps I wanted. Location in 11.10 is the same..

---

