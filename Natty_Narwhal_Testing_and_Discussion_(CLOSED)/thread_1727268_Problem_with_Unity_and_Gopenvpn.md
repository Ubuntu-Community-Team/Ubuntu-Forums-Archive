---
title: "Problem with Unity and Gopenvpn"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by franceskiello on 2011-04-12
I'm trying the Natty Narwhal Beta 1.
I did the upgrade directly from 10.10 64bit.
I often use gopenvpn, a simple OpenVpn client frontend
[gopenvpn.sourceforge.net]("http://ubuntuforums.org/gopenvpn.sourceforge.net")
 
After the upgrade, starting with Unity, I cannot find the gopenvpn icon in the upper tray anymore, despite the process gopenvpn is running.
 
If I end the session and log in as Ubuntu classic with gnome, the gopenvpn icon is correctly displayed.
 
[IMG]http://gopenvpn.sourceforge.net/images/dropdown.png[/IMG]
 
An suggestion to have the icon displayed with Unity?
 
Thanks in advance.
 
Francesco

---

### Post by mc4man on 2011-04-12
You can try adding to the systray whitelist, it may work correctly, it may not not.
can be added manually thru gconf-editor (desktop >unity > panel or from cli with gsettings
adding to the current set w/ gsetting would likely be this (not sure if capitalizing first letter matters
```
gsettings set com.canonical.Unity.Panel  systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'gopenvpn']"
```

(there is an "all" setting for the whitelist, prefer to do individually here
you probably need a logout/in after adding

---

### Post by franceskiello on 2011-04-12
Thank you very much Mc4man, it worked perfectly.
I first read the key with 
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
then I did gsetting set adding 'gopenvpn' at the end, then logoff/logon
and the icon was in the systray :D
Thank you again.

Francesco

---

