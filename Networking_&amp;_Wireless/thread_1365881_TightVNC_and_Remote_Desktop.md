---
title: "TightVNC and Remote Desktop"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by GoofyUy on 2009-12-27
Hi gurus!
 
I'm a newbie making it's road into the Ubuntu world and I must say that I'm doing it well (thanks to the help in the forum).
However, I've came across a situation that I could not resolve, I did not find any related thread in here, and I would like to solve this one for all.
 
I have an old box running karmic at home, with autologon and remote desktop enabled, being used as a file and internal web server.
I use tightVNC through a lan connection from a laptop using windows to connect to the remote desktop.
Up to here, all looks well.
The problem is, that when I try to copy & paste something in the karmic box, let's say that not only by pressing Ctrl-C, Shift-Ctrl-C, or even when clicking on Edit>>Copy, the VNC window closes, saying that received an error when waiting for a response from the server.
Any attempt to reconnect, returns a "Failed to connect to server".
 
If I reboot everything is well, until I copy & paste again. I also must say that not always the result is that. Sometimes (the fewer), the copy & paste works as expected.
 
I would try to restart the rdesktop service (via webmin or ssh), but I do not know which one is the proccess I must restart.
 
May somebody help me solving the root problem, or at least telling me which is the process to restart?
 
Pls take in mind that sometimes, the karmic box is processing a lot of info where the problem happens, so the solution for the second option is not to restart (unless I wait a day or two until the information processing is surely done)...
 
[[COLOR=teal]*Update]: I'm going to test this issue with RealVNC in the karmic box and see if it could be a TightVNC issue. I tested this steps on another box with the almost the same configuration but with RealVNC instead of TightVNC, and I wasn't able to obtain the same error. Thinking that could be a TightVNC client problem, although I'm worried about not being able to reconnect (maybe the session remains opened at the karmic box)*[/COLOR]
 
Thanks
GoofyUy

---

### Post by GoofyUy on 2009-12-30
Well... Right now I think that nobody is reading my post.
I will continue updating although. Perhaps somebody someday reads it.

I've installed RealVNC (the free viewer). I've used it for only one day until now. I've just receive a similar result.

I was working on a term window in the karmic box from the XP laptop through RealVNC. I've listed (ls) some files on a folder, selected them with the mouse, and after clicking on "Editar" (spanish for Edit), I've clicked on "Copiar" (spanish for Copy).
The VNC window closed without throwing a message (remember that TightVNC did), and after trying to reconnect to the box, I've inmediately received a critical error message "unable to connect to host: Connection refused (10061).

Could somebody give me at least a clue to see where could this problem be? I'm just asking not to solve it now... Just a plain "I've read your post and I feel sorry about you." at least, would be nice... Right now I think nobody is reading this.

Regards
Goofy

---

### Post by aplonis on 2009-12-31
Just another newbie guessing. But in TightVNC there is an Option named "Disable clipboard transfer" which does I know not what. Have you tried it both ways?

I may be shortly needing post on my present inability to use mouse and keyboard from TightVNC on Vista over into the new Ubuntu KK box.

---

### Post by GoofyUy on 2009-12-31
> **aplonis said:**
> Just another newbie guessing. But in TightVNC there is an Option named "Disable clipboard transfer" which does I know not what. Have you tried it both ways?

I may be shortly needing post on my present inability to use mouse and keyboard from TightVNC on Vista over into the new Ubuntu KK box.

Hi Aplonis, thanks for passing by.
I've never mind about "Disable clipboard transfer", because that option it's used for "sending" the remote clipboard into the local clipboard. That was not my need anyway, and the problem is that I had replicated the same issue with RealVNC.

Other thing I could find it's that vino-server process it's not running when doing a netstat through webmin, so that could be the reason for the failure to reconnect.
Right now I'm seeking the way to restart from remote the vino-server without webmin, because webmin wants to start vino-server as a local application, and thus, returning an error because it has not phisical nor logical display.

I think this is more related to a bug in vino-server, but I want to confirm it before posting an issue on that. So, if someone there could give a hand, it would be nice...

Regards
Goofy

---

### Post by kapetanski on 2010-01-01
I have the same problem when using ctrl+c from jollysfastvnc on mac, maybe you can use something in like this:
[http://ubuntuforums.org/archive/index.php/t-266981.html](http://ubuntuforums.org/archive/index.php/t-266981.html)

on my old ubuntu server I used to start x11vnc from the ssh terminal, and it worked pretty good as well.

---

### Post by GoofyUy on 2010-01-04
Thanks kapetanski for passing by.

I'm going to open an ssh port on my kk box and try that solution.
But this it's going to happen in a day or two... 
Again vino-server crashed and it's processing information, so I must wait until it ends...
 
I'll be back

Regards
Goofy

---

### Post by GoofyUy on 2010-01-22
> **GoofyUy said:**
> Thanks kapetanski for passing by.
 
I'm going to open an ssh port on my kk box and try that solution.
But this it's going to happen in a day or two... 
Again vino-server crashed and it's processing information, so I must wait until it ends...
 
I'll be back
 
Regards
Goofy
 
Well... This is the last update I'm going to do on this topic.
The issue seems to be originating from the vino-server process, because I have detected that is that process the one that aborts when Ctrl-C or Clipboard it's used on a remote desktop connection.
No matter the VNC client used, the issue was found amongst all of them.
Actually I'm thinking to forget about using clipboard on the kk box, or the plan B, that is to install a vncserver and stop using vino-server.
 
Thanks to everyone who passed by.
 
Regards
Goofy

---

### Post by zyperion on 2012-10-18
If it makes you feel any better this is still happening to me on 12.04 LTS. :(

---

### Post by Malac on 2013-02-05
And 12.10

---

### Post by wildmanne39 on 2013-02-05
Old thread closed.

---

