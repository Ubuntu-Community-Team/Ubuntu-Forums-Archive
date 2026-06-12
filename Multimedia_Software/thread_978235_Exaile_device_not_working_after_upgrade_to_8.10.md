---
title: "Exaile device not working after upgrade to 8.10"
date: 2008-11-10
forum: Multimedia Software
---

### Post by s1300045 on 2008-11-10
Exaile will not transfer file to device after upgrading to 8.10. Below is what I get if I run it in console.

```

location: /usr/lib/xulrunner-1.9.0.3/libxpcom.so 
before 3
Exaile 0.2.14
Plugins 'Mass Storage Driver' version '0.3.4' loaded successfully
Plugins 'MTP Device Manager' version '0.4.0' loaded successfully
Plugins 'AWN' version '0.7.4' loaded successfully
Plugins 'iPod Device Driver' version '0.4.6' loaded successfully
Plugins 'IM Status' version '0.12.1' loaded successfully
Plugins 'Mini Mode' version '0.4.9' loaded successfully
Plugins 'Enhanced Playlist Tabs' version '0.1' loaded successfully
Plugins 'Update Notifier' version '0.3.3' loaded successfully
Plugins 'Current song' version '0.1' loaded successfully
Created db for thread Thread-2
{'Thread-2': <sqlite3.Connection object at 0x1dca7c8>}
Activated gnome mmkeys for gnome 2.22.x
Using multimedia keys from: gnome
[Last.FM]: Logged in successfully
loading tracks...
Starting scan timer at 25.0
Closed db for thread Thread-2
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/s1300045/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0
we have connected, and scanned 2 files!
set percent to 0.0
set percent to 0.125
Exception in thread Thread-16:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/exaile/xl/panels/device.py", line 141, in start_transfer
    driver.put_item(item)
  File "/home/s1300045/.exaile/plugins/massstoragedriver.py", line 123, in put_item
    item = copy.deepcopy(item)
  File "/usr/lib/python2.5/copy.py", line 173, in deepcopy
    y = copier(memo)
TypeError: gobject.GObject descendants' instances are non-copyable


```

I tried searching keyword gobject and exaile but it didn't seem others have had this problem before. Any ideas?

---

