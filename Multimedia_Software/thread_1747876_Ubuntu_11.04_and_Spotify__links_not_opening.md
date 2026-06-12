---
title: "Ubuntu 11.04 and Spotify : links not opening"
date: 2011-05-03
forum: Multimedia Software
---

### Post by ant1fr on 2011-05-03
Hello everyone,


I a heavy user of Spotify (available in Europe) and I use the native linux client.
The native client comes with a spotify-gnome-support package that adds an entry under url-handlers to support the Spotify URI (spotify:) system-wide.

Under Ubuntu 10.10, I had absolutely no problem.

But after my upgrade to Ubuntu 11.04, the URI are not opening anymore. And on my other laptop where I did a fresh install of Natty, it doesn't work at well.

I did a manual entry to url-handlers to be sure that the system would recognize the Spotify URI prefix.
I did :

```
gconftool-2 -t string /desktop/gnome/url-handlers/spotify/command "spotify -uri %s"
gconftool-2 -t bool /desktop/gnome/url-handlers/spotify/needs_temrinal false
gconftool-2 -t bool /desktop/gnome/url-handlers/spotify/enabled true
```

A %gconf.xml has been created under $HOME/.gconf/desktop/gnome/url-handlers/spotify/ showing :

[HTML]<gconf>
<entry name="enabled" mtime="1304411481" type="bool" value="true"/>
<entry name="needs_terminal" mtime="1304411471" type="bool" value="false"/>
<entry name="command" mtime="1304411440" type="string">
    <stringvalue>spotify -uri %s</stringvalue>
</entry>
</gconf>[/HTML]

I also see the entry under gconf-editor.

I tried to logout/login, reboot but nothing works.

When I try xdg-open, I get :

```
xdg-open spotify:track:2QO8cnnFW6khDuAuUAySeV
Error showing url: The specified location is not supported.
```

I really don't understand the behavior of the system and what I did wrong. I am afraid that expands my knowledge.

Can anyone help me on that ?


Thanks a lot !

--ant1

---

### Post by ant1fr on 2011-05-03
FYI, when I try to open "spotify -uri spotify:track:2QO8cnnFW6khDuAuUAySeV", it works very well !

---

### Post by elundmark on 2011-05-04
I'm having the same issue with my custom url-handlers.

I've tried Everything, and can't find a single piece of advice on the internet, which tells me this IS related to 11.04.

Note that I'm talking about links in Google Chrome, Firefox on the other hand doesn't even check the url-handlers so I had to set them up manually using about:config > network.protocol-handler*

So they work in Firefox when added, but in no other browsers.

Google Chrome opens the links with xdg-open [url] as depicted in the attacheds screenshot, but this throws in error, found in .xsession-errors:
```
gvfs-open: svtrip://example.com/: error opening location: The specified location is not supported
```

---

### Post by elundmark on 2011-05-08
(bump) Please help us! :)
xdg-open doesn't include ANY manual entries to gconf > Desktop > Gnome > url-handlers...

---

### Post by ant1fr on 2011-05-09
> **elundmark said:**
> I'm having the same issue with my custom url-handlers.

I've tried Everything, and can't find a single piece of advice on the internet, which tells me this IS related to 11.04.

Note that I'm talking about links in Google Chrome, Firefox on the other hand doesn't even check the url-handlers so I had to set them up manually using about:config > network.protocol-handler*

So they work in Firefox when added, but in no other browsers.

Google Chrome opens the links with xdg-open [url] as depicted in the attacheds screenshot, but this throws in error, found in .xsession-errors:
```
gvfs-open: svtrip://example.com/: error opening location: The specified location is not supported
```

I do agree. This URL are well handled natively by Firefox. However Firefox do not rely on the legacy URL handler like Chrome does. And I am not ready to switch back to Firefox now that I am a heavy user of Chrome.

I assume that this issue is a bug related to Ubuntu 11.04. Let's hope that this one will soon be fixed in an update !

---

### Post by elundmark on 2011-05-09
> **ant1fr said:**
> I assume that this issue is a bug related to Ubuntu 11.04. Let's hope that this one will soon be fixed in an update !

"Glad" to hear we're not alone :P Means it's all the more likely it's a bug.

I'd sure file a bug report, if I only knew what was wrong. I mean it could be *xdg-utils*, *gconftool-2* ( which I'm having trouble with today, I tried deleting all the manual entries to start over, but it won't repond to **any** delete (unset) commands :( ) or it might be some other service that's ment to *translate* the information to *xdg-utils*... :confused:

---

### Post by Waklevören on 2011-05-14
Have you reported the bug to the Spotify crew?

---

### Post by ant1fr on 2011-05-14
> **Waklevören said:**
> Have you reported the bug to the Spotify crew?

The bug is not related to Spotify nor Chrome but to Ubuntu. My Spotify issue is just a symptom of what I believe is a bug on Ubuntu 11.04.

And by the way I want to say about Ubuntu 11.04 that I really hate Unity and I consider that version as a real regression compared to the previous ones!

---

### Post by sprintexec on 2011-05-24
Hi, I just read your post as I plan to install spotify on my clean install of 11.04. Having previously had spotify working with 10.04 and 10.10 what you have to say makes me a little nervous that it won't work under 11.04. Anyhow until I try we won't know. I'll post back here later when I've had a go. Thanks again for your post(s), AJ.

---

### Post by sprintexec on 2011-05-24
Hi,

Further to my earlier post I've just managed to get spotify installed and working at the first attempt. I've kept a copy of the terminal session just in case anyone wants to know what I did. Given your previous experiences this I hope is good news. Regards, AJ

---

### Post by sloopjonb on 2011-05-26
> **sprintexec said:**
> Hi,

Further to my earlier post I've just managed to get spotify installed and working at the first attempt. I've kept a copy of the terminal session just in case anyone wants to know what I did. Given your previous experiences this I hope is good news. Regards, AJ

Hi,

Would love to see how you achieved this. I'm currently a bit stuck and it might be my lack of experience with Ubuntu that's the cause. Please can you summarise your steps....

I run the Spotify Linux preview, and was able to browse select music etc, and am not too worried about browser interaction. However, if I close the spotify window I have no way of getting it back, yet the music plays on.....

If I click on the speaker logo top right I can see the spotify player listed there, but no matter what I do I can't restore the spotify window.

Sorry if I'm being a dufus - just new to Ubuntu......

Hope someone can help.

Cheers,
Jon

---

### Post by finhex on 2011-05-30
> **sprintexec said:**
> Hi,

Further to my earlier post I've just managed to get spotify installed and working at the first attempt. I've kept a copy of the terminal session just in case anyone wants to know what I did. Given your previous experiences this I hope is good news. Regards, AJI am also new Ubuntu user and failed to install Spotify myself so I'd like to see what needs to be done to get it installed.

---

### Post by sprintexec on 2011-06-04
Re: sloopjonb & finhex
Hi, I juts checked back in and saw your msgs. If either of you are still having probs let me know, willpost back. AJ

---

### Post by finhex on 2011-06-04
I haven't tried after my message so if you can send your installation "log", please.

---

### Post by sauen on 2011-06-07
It is gnome-open / xdg-open that is broken. Since chrome uses it to open links.

If you do ```
gconftool -g /desktop/gnome/url-handlers/spotify/command
```
you get 
```
/usr/bin/spotify -uri "%s"

```
which is consistent with
```
gconftool -g /desktop/gnome/url-handlers/http/command
/opt/google/chrome/google-chrome %U
```
which works, but spotify links doesn't.

---

### Post by finhex on 2011-06-07
> **sprintexec said:**
> Re: sloopjonb & finhex
Hi, I juts checked back in and saw your msgs. If either of you are still having probs let me know, willpost back. AJHi,

I just retried and installation was now succesfully finished. I don't know what was problem previously...

---

### Post by fresta on 2011-07-04
I created a custom /usr/share/applications/spotify-url.desktop file with the -url command line and mime type added, as described in [xdg-utils bug 788673]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/788673"):

```

[Desktop Entry]
Name=Spotify
GenericName=Spotify
Comment=Listen to music using Spotify
Icon=spotify-linux-512x512
TryExec=spotify
Exec=spotify -uri %u
Terminal=false
Type=Application
Categories=Qt;AudioVideo
MimeType=x-scheme-handler/spotify
NoDisplay=true
```

After running sudo update-desktop-database, Spotify links work perfectly from Chromium.

The gconf keys make no difference whatsoever AFAIK.

I'm running spotify-client 0.4.9.302 under Ubuntu 11.04 Natty (0.5.1.151 did install but crashed at start).

---

### Post by maartenvdbent on 2011-07-19
I have a different problem with running the Linux client of Spotify under Ubuntu 11.04: although it works perfectly fine with a fresh install, it ceases to work after updating Ubuntu to the most recent version. After that, it keeps crashing at start-up.

At first I thought it might be a problem related to my computer, but I encountered the very same thing after updating another one, so it must have something with some update.

Curiously, the shortcut in the Unity left bar to Spotify also disappears after installing this Ubuntu update.

This is what happens now after I run the command "spotify" from the terminal:

```
17:51:10.506 I [breakpad.cpp:35] Registered Breakpad for product: spotify

17:51:10.507 I [translate.cpp:117] Reloading all languages
17:51:10.514 I [fsevents:403] starting polling thread
17:51:10.557 I [breakpad.cpp:93] Searching for crashdumps: /home/vanderbent/.cache/spotify/*.dmp
```

Any ideas what might be wrong?

Thanks in advance.

---

### Post by isaacj87 on 2011-07-24
> **maartenvdbent said:**
> I have a different problem with running the Linux client of Spotify under Ubuntu 11.04: although it works perfectly fine with a fresh install, it ceases to work after updating Ubuntu to the most recent version. After that, it keeps crashing at start-up.

At first I thought it might be a problem related to my computer, but I encountered the very same thing after updating another one, so it must have something with some update.

Curiously, the shortcut in the Unity left bar to Spotify also disappears after installing this Ubuntu update.

This is what happens now after I run the command "spotify" from the terminal:

```
17:51:10.506 I [breakpad.cpp:35] Registered Breakpad for product: spotify

17:51:10.507 I [translate.cpp:117] Reloading all languages
17:51:10.514 I [fsevents:403] starting polling thread
17:51:10.557 I [breakpad.cpp:93] Searching for crashdumps: /home/vanderbent/.cache/spotify/*.dmp
```

Any ideas what might be wrong?

Thanks in advance.

Trying remove these two folders:

1)
```
~/.config/spotify
```

2)
```
~/.cache/spotify
```

Spotify should start after that.

---

### Post by isaacj87 on 2011-07-24
> **fresta said:**
> I created a custom /usr/share/applications/spotify-url.desktop file with the -url command line and mime type added, as described in [xdg-utils bug 788673]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/788673"):

```

[Desktop Entry]
Name=Spotify
GenericName=Spotify
Comment=Listen to music using Spotify
Icon=spotify-linux-512x512
TryExec=spotify
Exec=spotify -uri %u
Terminal=false
Type=Application
Categories=Qt;AudioVideo
MimeType=x-scheme-handler/spotify
NoDisplay=true
```

After running sudo update-desktop-database, Spotify links work perfectly from Chromium.

The gconf keys make no difference whatsoever AFAIK.

I'm running spotify-client 0.4.9.302 under Ubuntu 11.04 Natty (0.5.1.151 did install but crashed at start).

Awesome tip! Thanks for this. I didn't do anything other than add the new *.desktop file. It works on Kubuntu 11.04 running Spotify (0.5.2.84.g6d797eb9)

---

### Post by gvoima on 2011-09-10
Those of you that have the latest spotify and ubuntu running, does the multimedia keys work? It got the soundmenu integration and a lot of other fixes with the latest update and the reported media key bugs are with the earlier versions.
And I read that with kubuntu they work, what about gnome?

---

