---
title: "'Cook' RealAudio problems"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Semirrahge on 2008-02-26
I can play RM formats, but last night I found out that there are multiple codecs used in my RM files, and thus: .rmvb files with the 'Cook' audio encoding have their audio mangled. There is a very fast noise, sorta like machine noise from a bad ground, but it is either very loud or it is part of some very heavy attenuation/channel mixing because the sound is very difficult to understand.

I have all the restricted codecs installed (including w32codecs). I am using the Xine version of Totem.

Oh, I am also running the amd64 kernel. I had to manually install part of the codecs... But now I don't remember exactly what. I'll see if I can dig up some logs and get back with that.

Does anyone have any ideas? I'm up for any interesting guesses, even, because AFAIK my problem is unique.

---

### Post by TheIdiot on 2008-02-26
You're not alone. Xine was working fine for me up till about two weeks ago. I had a friend test, who recently moved from Feisty to Gutsy. In Feisty he had Totem-Xine working fine for rmvb files When I asked him to try again two nights ago, totem xine didn't work.

If you try using another xine gui, (e.g. xine-ui), you'll notice that it says cook.so (RealAudio) and drvc.so (RealVideo) are missing. Doing a "locate cook.so" and "locate drvc.so" in terminal will show that the codecs exist in "/usr/lib/codecs" (and also "/usr/lib/w32" if you installed the codecs a while ago.)

Anyway, here's another thread showing that you aren't alone:
[http://ubuntuforums.org/showthread.php?t=440031&highlight=rmvb+xine](http://ubuntuforums.org/showthread.php?t=440031&highlight=rmvb+xine)

---

### Post by The_Knight on 2008-03-03
Edit the ~/.xine/config and ~/.gnome2/Totem/xine_config, then change the following uncommented lines;

# path to RealPlayer codecs
# string, default:
decoder.external.real_codecs_path:

# path to Win32 codecs
# string, default: /usr/lib/codecs
decoder.external.win32_codecs_path:

To:

# path to RealPlayer codecs
# string, default:
decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/codecs
decoder.external.win32_codecs_path:/usr/lib/win32

Where /usr/lib/win32 is the path of the codecs.

Enjoy.

P.S. : It does work for me.

---

### Post by msayed2004 on 2008-04-19
Brilliant=D>!

---

