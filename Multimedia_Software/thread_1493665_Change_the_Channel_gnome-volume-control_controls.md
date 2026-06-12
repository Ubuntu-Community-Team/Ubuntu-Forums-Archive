---
title: "Change the Channel gnome-volume-control controls"
date: 2010-05-26
forum: Multimedia Software
---

### Post by zarqoon on 2010-05-26
How do i change the channel gnome-volume-control controls?
I want it to control pcm but it controls master front.
There used to be a setting right in the sound preferences but i think it disappeared with the 9.10 upgrade or at least i can not find it anymore.

I've looked on the at gnome alsa mixer while changing the volume and master front gets controlled while pcm is always set to max. The problem with this is that master front does almost nothing to change the actual volume.

If i control pcm with the alsa mixer the volume range is fine.

I've found a manual for gnome-volume-control on [http://library.gnome.org/users/gnome-volume-control/stable/gnome-volume-control-getting-started.html.en]("http://library.gnome.org/users/gnome-volume-control/stable/gnome-volume-control-getting-started.html.en") and the pic there actually looks like i remember it looking. But i can not get to that screen. What i have looks completely different. Its a window with the tabs Sound Effects | Hardware | Input | Output | Applications. But there is no sight of any channel settings and the only slider there does the same as the applet one.

---

### Post by zarqoon on 2010-06-07
No one knows this? There has to be a way except downgrading to whatever ubuntu version had the old sound settings manager. Perhaps a config file somewhere. I am getting sick of having to use the alsa mixer to change my volume.

---

### Post by RINKO on 2010-06-07
Im not sure if my problem is similar. But.

I decided to delete evo mail client off my panel and that was a mistake.  By deleting evolution mail i also seem to have lost my volume slider.  I have re-installed the volume indicator from the software menu.  no help.  I understand how to add to panel and whatnot, i am not seeing it.  Adding notification areas automatically puts my connection monitor back but no volume slider yet.


I would appreciate some guidance on this issue.  Ive been busy with work and find myself becoming very frustrated that this simple issue is a *uck*ng task! its not advanced but retarded. 


Info:

Running newest version Lucid 10.04
3.2 gb of memory
3 ghz processors X 2
about 5 gbs of disk space (could this be an issue?)

right now im just keeping sound preferences open to adjust master volume.  

I'm almost positive that the slider was no longer present after i deleted/removed Evolution mail client from the panel.

Thanks for your time ladies and gents.  Hopefully a solution can be executed.  

Brinko

---

### Post by tsh on 2010-06-07
I have a similar problem. gnome-volume-control only gives me about a 20dB range, and seems to be acting as a linear fader, not a log one. Myth-TV volume control is similarly broken.

---

### Post by zarqoon on 2010-06-08
@ rinko.
I had the same problem but thats easily fixable. Just add ```
gnome-volume-control-applet
``` as a startup application in your preferences menu. This gives you the old volume control back the one that has nothing whatsoever to do with an email client. 
The new one also displays if you get new mail in evolution and some other stuff so it probably does not work without evolution.

You can try out if this will work by just starting gnome-volume-control-applet. It should appear directly.

Edit: just noticed you use xubuntu. I've no idea if the gnome-volume-control-applet works with xcf as it is for gnome. But there should be an equivalent old one for xcf but i do not know how its called.

My problem is that the channel it controls does not make a lot difference to the actual volume in my setup and the menu to select the channel was removed in some "upgrade"

Sometimes i am tempted to install 8.04 again.

@tsh
open gnome-alsamixer and change the volume with the pcm channel. If this works you got the same problem i have. I do not use myth-tv but the volume control in vlc does not work right either.

---

### Post by Yellow Pasque on 2010-06-08
The new screen is for pulseaudio, the old one was gstreamer. For those that remove pulseaudio, they can get the old-style mixer by getting gnome packages from [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
The ppa was originally intended for OSS4 users, but some users remove pulseaudio and just use ALSA. It works that way, but I really don't recommend that unless you're confident in your ability to reconfigure everything to use ALSA.

EDIT: You can also make scripts that make use of the amixer command and bind them to shortcut keys to control an ALSA track in that manner.

---

### Post by EXCiD3 on 2010-06-09
I'm trying to accomplish the same thing. I can't find any way to configure the volume shortcuts and applet to control the PCM channel instead of what controlling master front.

---

### Post by lidex on 2010-06-09
Have a look here:
[http://ubuntuforums.org/showpost.php?p=8243843&postcount=2]("http://ubuntuforums.org/showpost.php?p=8243843&postcount=2")
In the command, you may want to replace 'nano' with 'gedit'

More stuff:
[http://ubuntuforums.org/showthread.php?t=1317562]("http://ubuntuforums.org/showthread.php?t=1317562")

---

### Post by EXCiD3 on 2010-06-10
> **lidex said:**
> Have a look here:
[http://ubuntuforums.org/showpost.php?p=8243843&postcount=2]("http://ubuntuforums.org/showpost.php?p=8243843&postcount=2")
In the command, you may want to replace 'nano' with 'gedit'

More stuff:
[http://ubuntuforums.org/showthread.php?t=1317562]("http://ubuntuforums.org/showthread.php?t=1317562")

That worked! I love you!

---

### Post by zarqoon on 2010-06-13
If i uncomment load-module module-alsa-mixer there is no sound and every application that tries to play sound has to be killed -9. But the post lead me to a solution anyway.
after reading the comments in ```
/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
``` I finaly understood what was happening.
Pulseaudio adjusts the channel in a way that they keep their relation to one another in a relative way and not in an absolute. I.E. if channel a is set to 2 and channel b to 5 and you double the volume channel a will be set to 4 and channel b to 10. Pulseaudio goes through the list of channels and adjusts each one. But if it finds one that does not support this it only does not modify any other channels.

The first channel in my config is Master Front which for some reason does exactly nothing. And as a bonus does not seem to support the above mentioned process. The Effect was that only master front was modified which had no effect at all.

My solution is now setting this channel to ```
 volume=ignore
``` in the file ```

/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf
``` 

The PCM channel is still not changed but that does not matter since pulseaudio now modifies front, center, surround, and side at the same time, which works just fine and i think this is how its supposed to be working.

Thx to everybody

---

### Post by EXCiD3 on 2010-06-13
> **zarqoon said:**
> If i uncomment load-module module-alsa-mixer there is no sound and every application that tries to play sound has to be killed -9. But the post lead me to a solution anyway.
after reading the comments in ```
/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
``` I finaly understood what was happening.
Pulseaudio adjusts the channel in a way that they keep their relation to one another in a relative way and not in an absolute. I.E. if channel a is set to 2 and channel b to 5 and you double the volume channel a will be set to 4 and channel b to 10. Pulseaudio goes through the list of channels and adjusts each one. But if it finds one that does not support this it only does not modify any other channels.

The first channel in my config is Master Front which for some reason does exactly nothing. And as a bonus does not seem to support the above mentioned process. The Effect was that only master front was modified which had no effect at all.

My solution is now setting this channel to ```
 volume=ignore
``` in the file ```

/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf
``` 

The PCM channel is still not changed but that does not matter since pulseaudio now modifies front, center, surround, and side at the same time, which works just fine and i think this is how its supposed to be working.

Thx to everybody

That sounds like a much more proper fix. If there is a bug report on Launchpad for this, you mention it in the comments.

I have noticed the previous method posted causes crackling of the audio quite often, but its easy to fix by pausing and resuming.

---

