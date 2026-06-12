---
title: "IcePodder fails to open"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by ratbagradio on 2007-04-27
When I upgraded to Feisty iPodder (podcatcher for podcasts)wouldn't work on my desktop. So I installed IcePodder which is the Linux oriented version of ipodder/Juice/Lemon.

But now, suddenly I have the same problem as I had with ipodder: 

* on open  (and I have to open by using "sudo ipodder" in Terminal) the program kicks in, opens for a second then fails to proceed leaving me a Terminal readout:

> [<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
ratbagradio@Ratbag:~$ sudo icepodder
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "CastPodderGui.py", line 1533, in OnInit
    self.PopulateDownloadsTab()
  File "CastPodderGui.py", line 3359, in PopulateDownloadsTab
    self.DownloadTabLog(encinfo,prune=False)
  File "CastPodderGui.py", line 3254, in DownloadTabLog
    index = self.downloads.InsertStringItem(0,encinfo.item_title)
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 4809, in InsertStringItem
    return _controls_.ListCtrl_InsertStringItem(*args, **kwargs)
  File "encodings/utf_8.py", line 16, in decode
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 1-3: invalid data


---

### Post by spankminister on 2007-05-23
Sorry for the uber-late reply, but you can fix this problem by deleting the config directory in iPodderData.  I'm not sure what's going on with it, but another user reported a similar problem.

---

