---
title: "Problems since updating FF2.0.0.4"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by kvgeorge1 on 2007-06-15
I updated FireFox to 2.0.0.4 when it showed up in the updates area (I am using Ubuntu 7.04.).  Now, I can no longer play .WMP files.  I have the MPlayer plug-in and use AutoMatix2 to configure for this, but they just will not run anymore.  I found a similar issue with someone having problems with videos on Yahoo!.  Their solution was to enable the WMP mime-type, but this does not seem possible in FF2.0.0.4 (cannot locate where to enable the mime-type).

I have attempted to enable the .WMP mimetype using Tools->Preferences->Content->File Types->Manage, but I do not seem to have the ability to add a new mime-type (even when running as ROOT)

Any suggestions?

---

### Post by kvgeorge1 on 2007-06-19
I have solved my own issue.

It looks as if the issue happened with FireFox was updated via the Software Updates application.  In the pluginreg.dat located in ~/.mozilla/firefox, the lines for the windows media section looked like this:

```

<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.31<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Windows Media Player Plugin:$
17
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
6:video/x-ms-asf:Media Files:asf,asx,*:$
7:video/x-ms-wm:Media Files:wm,*:$
8:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
9:audio/x-ms-wmv:Windows Media:wmv,*:$
10:video/x-ms-wmp:Windows Media:wmp,*:$
11:video/x-ms-wvx:Windows Media:wvx,*:$
12:audio/x-ms-wax:Windows Media:wax,*:$
13:audio/x-ms-wma:Windows Media:wma,*:$
14:application/x-drm-v2:Windows Media:asx,*:$
15:audio/wav:Microsoft wave file:wav,*:$
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so:$
:$
1169041751000:1:5:$

```

What is should be is this:

```

<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.31<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Windows Media Player Plugin:$
17
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
[color=blue]6:application/x-ms-wmp:Microsoft WMP video:wmp,*:$[/color]
7:video/x-ms-asf:Media Files:asf,asx,*:$
8:video/x-ms-wm:Media Files:wm,*:$
9:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
10:audio/x-ms-wmv:Windows Media:wmv,*:$
11:video/x-ms-wmp:Windows Media:wmp,*:$
12:video/x-ms-wvx:Windows Media:wvx,*:$
13:audio/x-ms-wax:Windows Media:wax,*:$
14:audio/x-ms-wma:Windows Media:wma,*:$
15:application/x-drm-v2:Windows Media:asx,*:$
16:audio/wav:Microsoft wave file:wav,*:$
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so:$
:$
1169041751000:1:5:$

```

Notice that I added line 6 and then renumbered the list through to the end of the section.  The videos now play.

---

