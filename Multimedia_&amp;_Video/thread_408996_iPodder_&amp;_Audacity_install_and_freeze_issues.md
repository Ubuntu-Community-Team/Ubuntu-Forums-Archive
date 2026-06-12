---
title: "iPodder &amp; Audacity install and freeze issues"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by ratbagradio on 2007-04-14
** Audio install and run issues:iPodder & Audacity**
Ubuntu Week 3:-- my third week coming in cold to Ubuntu
*I had posted this message to Newbie list but I thoiught maybe it belonged here as I think I mucked up the audio system perhaps.*

I of course don't know what I did wrong....It was all jim dandy until this glitch.

Tonight I was installing LAME for Audacity[Audio editor] and got that to work(so Auadacity could save to Mp3) but there after two problems kicked in:

Audacity would not close. and then my copy of iPodder [podcast catcher] failed to boot.It would start to kick in but soon give up.

I uninstalled both and re-installed ipodder but it still won't boot. I got rid of the Lame file too from the system too.

And Audacity wont install because: Cannot install 'audacity'
This application conflicts with other installed software. To install 'audacity' the conflicting software must be removed before.Switch to the advanced mode to resolve this conflict.

?????????

The Audacity dependencies suddenly are: audacity:
Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

But I had no such issues when I first installed Audacity.
I'm on Dapper 6.06. And I think I did something wrong in the audio setup to cause this double whammy problem.

Here is my read out for ipodder.Somthing's amiss, tight?

ratbagradio@Ratbag:~$ ipodder
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Traceback (most recent call last):
File "/usr/share/ipodder/iPodderGui.py", line 3531, in ?
main()
File "/usr/share/ipodder/iPodderGui.py", line 3525, in main
myApp = iPodderGui(ipodder)
File "/usr/share/ipodder/iPodderGui.py", line 590, in __init__
wx.App.__init__(self, False, None)
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
self._BootstrapApp()
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
return _core_.PyApp__BootstrapApp(*args, **kwargs)
File "/usr/share/ipodder/iPodderGui.py", line 1460, in OnInit
self.PopulateDownloadsTab()
File "/usr/share/ipodder/iPodderGui.py", line 3233, in PopulateDownloadsTab
self.DownloadTabLog(encinfo,prune=False)
File "/usr/share/ipodder/iPodderGui.py", line 3143, in DownloadTabLog
index = self.downloads.InsertStringItem(0,encinfo.item_tit le)
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 4764, in InsertStringItem
return _controls_.ListCtrl_InsertStringItem(*args, **kwargs)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 1-3: invalid data
ratbagradio@Ratbag:~$

---

### Post by ratbagradio on 2007-04-14
Looks like I'm missing elements big time. I've also lost my mp3 playing capacity with Amarok.

---

### Post by ratbagradio on 2007-04-14
I've fixed up the ipodder issue but still stuck with Audacity. I'm exploring at th4e Audacity Forums

---

