---
title: "VNC prompt"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by k4rizma on 2013-03-07
I'm trying to create a script so that I dont have to manually configure my ubuntu machine each time I do a fresh install on new hardware.  The remote desktop sharing default is setup to confirm each access to the machine.  What config file does this use?  

I tried toggling the options and cat out 

```
~/.gconf/desktop/gnome/remote_access/%gconf.xml to see any changes made.  
```

When I make changes to the other options like "show notification area icon" which changed values in the config file. I thought the following line would change when toggling for promting access but it hasn't. 

```
 <entry name="prompt_enabled" mtime="1362680456" type="bool" value="false"/>
```



Thoughts? help? 

Thanks guys.

---

### Post by steeldriver on 2013-03-07
I'm not sure about this, but I suspect that since the move from gconf to dconf, the %gconf files just reflect info that's actually held in the dconf database (by default ~/.conf/dconf/user I think) and manual changes to the file maybe don't propagate back to the db - you could try writing directly to the dconf db instead

```

dconf write /desktop/gnome/remote-access/prompt-enabled false
dconf update

```

In fact it seems like the %gconf file lags any updates to the actual db:

```
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="**true**"/>
$ 
$ dconf **write** /desktop/gnome/remote-access/prompt-enabled **false**
$ dconf update
$ dconf **read** /desktop/gnome/remote-access/prompt-enabled
**false**
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="**true**"/>
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="true"/>
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="true"/>
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="true"/>
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695685" type="bool" value="true"/>
$ grep prompt_enabled ~/.gconf/desktop/gnome/remote_access/%gconf.xml 
    <entry name="prompt_enabled" mtime="1362695796" type="bool" value="**false**"/>
```

---

### Post by k4rizma on 2013-03-10
Thanks for the reply!!  Very helpful :)

---

