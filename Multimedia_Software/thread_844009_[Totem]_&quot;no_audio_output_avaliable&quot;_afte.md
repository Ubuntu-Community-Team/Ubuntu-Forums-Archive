---
title: "[Totem]: &quot;no audio output avaliable&quot; after watching video in firefox"
date: 2008-06-29
forum: Multimedia Software
---

### Post by isaaca on 2008-06-29
I get the error:
> "This is an audio-only file, and there is no audio output available."
From Totem when I try to play an audio file after watching video (both through flash and MPlayer) online in firefox. It seems that the audio output is locked up and no app can playback sound.

I go hunting for hung processes and such, but can't find anything obviously misbehaving (firefox is closed, as are any processes that I know would be involved in sound playback). I don't have much experience messing with sound on ubuntu, so I really don't know what to look for or what to try restarting. The only thing that comes to mind is "/etc/init.d/alsa restart" which doesn't help. In desperation, I restarted gnome with Ctrl-Alt-Backspace and logged back in but was greeted with a gnome settings daemon error:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

and totem still gives the same error. Restarting the computer fixes all the above problems. This occurs when either watching flash video or using the MPlayer plugin. It started when I upgraded to hardy (and firefox 3 too). I don't believe that it happens every time I watch a video, but can't swear to it. I've tried goggling and searching the forums, but I don't have anything specific to search for yet. 

I'm hoping somebody can give me some pointers about what to look for/restart so I can get a better idea what's going on, or at least get the sound to work without a complete restart.

Thanks
Isaac

---

### Post by phil0stine on 2009-11-03
Wow no replies? I know it is probably an afterthought for **isaaca**, but I have the exact same problem.

I thought my problem would have been a recent development, since it happened just after I installed updates. 

The only other clue I have is that I installed Firefox 3.5 before it hit the repositories, but until now it hasn't come back to bite me.

As always, ANY help is appreciated.

---

