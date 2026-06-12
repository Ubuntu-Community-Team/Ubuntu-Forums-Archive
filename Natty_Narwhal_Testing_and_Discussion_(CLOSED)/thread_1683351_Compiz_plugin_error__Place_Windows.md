---
title: "Compiz plugin error : Place Windows"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-02-07
The official Compiz forums is a bit slow so im wondering if someone here can help. 
Whenever I click on the "Place Windows" option, the window fails to load and I receive this error.
```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1304, in ShowPlugin
    pluginPage = PluginPage(plugin)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 128, in __init__
    groupPage = GroupPage(name, group)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1380, in __init__
    sga = SubGroupArea(subGroupName, subGroup)
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 1482, in __init__
    multiList.Read()
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 132, in Read
    self._Read()
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 759, in _Read
    self.Store.append(values)
TypeError: value is of wrong type for this column

```

---

### Post by r_u on 2011-02-17
rm .config/compiz-1/compizconfig/config

---

### Post by tjeremiah on 2011-02-17
> **r_u said:**
> rm .config/compiz-1/compizconfig/config

I removed it and it didnt solve the problem.

---

